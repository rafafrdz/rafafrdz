[![Header](./pictures/banner.png "Header")](https://rafaelfernandezortiz.com/)

# Rafael Fernández

<p align="left">
  <img src="https://img.shields.io/badge/Scala-%23f61938?logo=scala" />
  <img src="https://img.shields.io/badge/Haskell-5277C3?logo=haskell" />
  <img src="https://img.shields.io/badge/Rust-orange?logo=rust" />
  <img src="https://img.shields.io/badge/Cats-Functional-pink" />
  <img src="https://img.shields.io/badge/ZIO-Effects-%23f61938" />
  <img src="https://img.shields.io/badge/Apache%20Spark-yellow?logo=apachespark" />
  <img src="https://img.shields.io/badge/Apache%20Kafka-purple?logo=apachekafka" />
  <img src="https://img.shields.io/badge/Docker-00c0ff?logo=docker&logoColor=white" />
  <img src="https://img.shields.io/badge/NixOS-Declarative-5277C3?logo=nixos&logoColor=white" />
  <img src="https://img.shields.io/badge/Linux-white?logo=linux&logoColor=black" />
</p>


Functional programmer focused on **type-driven design**, **lawful abstractions**, and **effectful systems**.

My work sits at the intersection of **Scala**, **category theory**, and **systems programming with Rust**. I design software where **types carry meaning**, **effects are explicit**, and **composition is the primary tool**.

\- _If an invariant is not encoded in the type system, it is merely a convention._

## _To code or not to code, that is the question_ <img align="left" alt="png" src="./pictures/craneo.png?raw=true" width="60px"/> - My Writing & Thought Workflow

I write on my [blog](https://blog.rafaelfernandez.dev/) about functional programming, Scala, and software architecture, focusing on practical FP rather than academic exercises.

##  _Coffee time... Let's talk!_ ☕ <img align="left" alt="png" src="./pictures/cup.png?raw=true" width="60px"/> - Freelance

Available for freelance work and technical consulting. See my [website](https://rafaelfernandez.dev/), [CV](https://drive.google.com/file/d/1espEzGL_pYQOV1-mWrgxBdz94TDjYCmF/view) or my [LinkedIn](https://www.linkedin.com/in/rafael-fernandez-ortiz/). If your system is growing faster than your confidence in it, we should talk.

## Design Principles (Non-Negotiable)

- Typeclasses over inheritance
- Algebras over implementations
- Effects are values, not side effects
- Explicit dependencies via parametric polymorphism
- Laws first, optimizations second (but never ignored)
- Make illegal states unrepresentable

## About me

I don’t see Functional Programming as a style or a set of tools, but as a **discipline for reasoning about software**.

My goal is not to write “clever” code, but to build systems that remain understandable, correct, and evolvable under pressure.

### 1. Types are not documentation  
Types are **executable constraints**. If an invariant matters, it belongs in the type system. If a function accepts more states than it can handle, it is lying.

### 2. Effects must be explicit  
Effects are not something that *happens* — they are something that is **described**. An effectful program is a value. Interpretation is a separate concern. Hidden effects are technical debt.

### 3. Abstractions must be lawful  
An abstraction without laws is just an interface. Laws are what allow refactoring without fear and composition without surprise. If an abstraction cannot be reasoned about algebraically, it is probably the wrong abstraction.

### 4. Composition is the only scaling strategy  
Large systems are not built by adding features, but by **composing smaller, well-behaved parts**.

Composition works when:
- Dependencies are explicit
- Effects are controlled
- Data flows are unidirectional

Inheritance does not scale. Composition does.


### 5. Make illegal states unrepresentable  
Every runtime check is a failure to model the domain correctly. The earlier an invalid state is rejected, the cheaper it is. The best error is the one that cannot be expressed.


### 6. Performance is a feature, not an excuse  
Abstractions are allowed. Accidental complexity is not. I care about performance, but never at the cost of correctness or clarity. Good FP and high performance are not opposites — they are often aligned.


### 7. Simplicity is not minimalism  
Fewer concepts do not automatically mean simpler systems. True simplicity comes from **clear boundaries**, **precise models**, and **predictable behavior**. A small but leaky abstraction is worse than a larger but honest one.

## Algebra First, Implementation Later

### 🧬 Scala — Tagless Final, Typeclasses, Laws

The following Scala snippet shows how these principles translate into a real design: algebras expressed as typeclasses, effect-polymorphic programs, and interpreter-free composition.


\- _No inheritance trees. No hidden effects. Only algebras, interpreters, and laws._

```scala
// Domain
final case class Timeline[A](at: Date, value: A)

// Algebra
trait PersonAlg[F[_]] {
  def about: F[Info]
  def experience: F[List[Timeline[Experience]]]
  def education: F[List[Timeline[Education]]]
  def skills: F[Stack]
}

// Program
trait CurriculumVitae[F[_]] {
  def about: F[Info]
  def experience(at: Date): F[List[Experience]]
  def education(at: Date): F[List[Education]]
  def skills: F[Stack]
}

// Interpreter-free construction
object CurriculumVitae {

  def apply[F[_]: MonadFilter](P: PersonAlg[F]): CurriculumVitae[F] =
    new CurriculumVitae[F] {

      def about: F[Info] =
        P.about

      def experience(at: Date): F[List[Experience]] =
        P.experience.map(_.mapFilter(collectUntil(at)))

      def education(at: Date): F[List[Education]] =
        P.education.map(_.mapFilter(collectUntil(at)))

      def skills: F[Stack] =
        P.skills
    }

  def collectUntil[A](at: Date): Timeline[A] => Option[A] = {
     case Timeline(date, value) if date <= at => Some(value)
     case _                                  => None
   }
}
```


### 🦀 Rust — Traits, Ownership, Zero-Cost Abstractions

This Rust example mirrors the same architectural ideas: traits as algebras, explicit effects via `Result`, and correctness enforced by the type system.

\- _Ownership enforces correctness. Traits define behavior. Abstractions compile away._

<details> <summary><strong>Show Scala example</strong></summary>

```rust
use std::collections::HashMap;

// Domain
#[derive(Clone)]
pub struct Timeline<A> {
    pub at: Date,
    pub value: A,
}

// Algebra
pub trait PersonAlg {
    type Error;

    fn about(&self) -> Result<Info, Self::Error>;
    fn experience(&self) -> Result<Vec<Timeline<Experience>>, Self::Error>;
    fn education(&self) -> Result<Vec<Timeline<Education>>, Self::Error>;
    fn skills(&self) -> Result<Stack, Self::Error>;
}

// Program
pub struct CurriculumVitae<P> {
    person: P,
}

impl<P> CurriculumVitae<P>
where
    P: PersonAlg,
{
    pub fn new(person: P) -> Self {
        Self { person }
    }

    fn collect_until<A>(at: Date, xs: Vec<Timeline<A>>) -> Vec<A> {
        xs.into_iter()
            .filter(|t| t.at <= at)
            .map(|t| t.value)
            .collect()
    }

    pub fn experience(&self, at: Date) -> Result<Vec<Experience>, P::Error> {
        self.person.experience().map(|xs| Self::collect_until(at, xs))
    }

    pub fn education(&self, at: Date) -> Result<Vec<Education>, P::Error> {
        self.person.education().map(|xs| Self::collect_until(at, xs))
    }
}

```
</details>
