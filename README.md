[![Header](./pictures/banner.png "Header")](https://rafaelfernandezortiz.com/)

# Rafael Fernández
**Senior Software Engineer & Data Engineer | Scala & Rust | Functional Programming**

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

I am a Senior Software Engineer and Data Engineer specializing in the design and implementation of highly concurrent, distributed, and data-intensive systems. My methodology is deeply rooted in the rigorous application of Functional Programming principles, operating at the intersection of applied category theory, robust data engineering, and high-performance systems programming in **Scala** and **Rust**. 

I engineer software architectures where **types carry precise semantic meaning**, **effects are explicitly modeled**, and **algebraic composition is the primary scaling mechanism**.

> *If an invariant is not encoded in the type system, it is merely a convention.*

---

## Consulting & Freelance Services

I provide specialized freelance engineering and technical consulting for organizations aiming to construct resilient, scalable architectures or modernize their existing infrastructure. My core competencies include:

- **Distributed Systems & Data Engineering:** Architecture and implementation of robust data pipelines and streaming platforms (Apache Spark, Apache Kafka).
- **High-Performance Microservices:** Building scalable backend services utilizing advanced Scala (ZIO, Cats) and systems programming in Rust.
- **Architectural Modernization:** Transitioning legacy codebases into strictly typed, functionally pure architectures to drastically reduce technical debt and runtime anomalies.
- **Technical Mentorship:** Elevating engineering teams through the adoption of functional programming disciplines and type-driven design.

**Connect with me:** [Personal Website](https://rafaelfernandez.dev/) | [Curriculum Vitae](https://drive.google.com/file/d/1espEzGL_pYQOV1-mWrgxBdz94TDjYCmF/view) | [LinkedIn](https://www.linkedin.com/in/rafael-fernandez-ortiz/) | [Technical Blog](https://blog.rafaelfernandez.dev/)

---

## Architectural Philosophy & Disciplines

I do not view Functional Programming merely as a stylistic choice or a suite of tools, but rather as a **formal discipline for reasoning about software correctness**. My objective is to engineer systems that remain understandable, provably correct, and adaptable under extreme technical constraints.

### 1. Types as Executable Constraints
Types are not documentation; they are formal, executable constraints. If an invariant is critical to the domain, it belongs in the type system. A function that admits more states than it can safely process is fundamentally dishonest.

### 2. Explicit Effect Management
Effects are not incidental occurrences—they are explicit descriptions of program behavior. An effectful program is a value; its interpretation is a distinct and separate concern. Concealed side effects are the most insidious form of technical debt.

### 3. Lawful Abstractions
An abstraction lacking algebraic laws is merely a fragile interface. Laws provide the formal guarantees required for fearless refactoring and predictable composition. If an abstraction cannot be reasoned about algebraically, it is analytically deficient.

### 4. Composition as the Sole Scaling Strategy
Complex systems are not engineered by arbitrarily appending features, but by **composing smaller, well-behaved, and verifiable components**. True composition requires explicit dependencies, strictly controlled effects, and deterministic data flow.

### 5. Inexpressible Illegal States
Every runtime validation is a belated mitigation of a flawed domain model. The earlier an invalid state is mathematically rejected by the compiler, the safer the system. The optimal error is the one that cannot be syntactically expressed.

### 6. Performance as a Derivative of Correctness
Mathematical abstractions and zero-cost architectures are desirable; accidental complexity is not. High performance and rigorous Functional Programming are not mutually exclusive—they are intrinsically aligned when system boundaries are appropriately drawn.

---

## Structural Examples: Algebra First, Implementation Later

The following examples demonstrate how these principles translate into tangible software architecture: domain algebras expressed as formal traits or typeclasses, explicitly modeled effects, and strict interpreter-free composition.

### 🧬 Scala — Tagless Final, Typeclasses & Laws

This Scala snippet exemplifies type-driven design: enforcing invariants without inheritance hierarchies or hidden side effects, utilizing purely algebraic definitions.

```scala
import cats.Functor
import cats.syntax.functor.*

// Domain
final case class Date(value: Long) extends AnyVal
final case class Timeline[A](at: Date, value: A)

// Algebra
trait PersonAlg[F[_]] {
  def about: F[Info]
  def experience: F[List[Timeline[Experience]]]
  def education: F[List[Timeline[Education]]]
  def skills: F[Stack]
}

// Program Definition
trait CurriculumVitae[F[_]] {
  def about: F[Info]
  def experience(at: Date): F[List[Experience]]
  def education(at: Date): F[List[Education]]
  def skills: F[Stack]
}

// Interpreter-free Program Composition
object CurriculumVitae {

  def apply[F[_]: Functor](P: PersonAlg[F]): CurriculumVitae[F] =
    new CurriculumVitae[F] {

      override def about: F[Info] =
        P.about

      override def experience(at: Date): F[List[Experience]] =
        P.experience.map(_.flatMap(collectUntil(at)))

      override def education(at: Date): F[List[Education]] =
        P.education.map(_.flatMap(collectUntil(at)))

      override def skills: F[Stack] =
        P.skills
    }

  private def collectUntil[A](at: Date): Timeline[A] => List[A] = {
    case Timeline(date, value) if date.value <= at.value => List(value)
    case _                                               => Nil
  }
}
```

### 🦀 Rust — Traits, Ownership & Zero-Cost Abstractions

This Rust implementation mirrors the same architectural rigor: traits as behavioral algebras, explicit effect handling via `Result`, and mathematical correctness enforced by the borrow checker and type system.

<details> <summary><strong>View Rust implementation</strong></summary>

```rust
// Domain
#[derive(Debug, Clone, Copy, PartialEq, Eq, PartialOrd, Ord)]
pub struct Date(u64);

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

// Program Definition
pub struct CurriculumVitae<P> {
    person: P,
}

impl<P: PersonAlg> CurriculumVitae<P> {
    pub fn new(person: P) -> Self {
        Self { person }
    }

    pub fn about(&self) -> Result<Info, P::Error> {
        self.person.about()
    }

    pub fn skills(&self) -> Result<Stack, P::Error> {
        self.person.skills()
    }

    pub fn experience(&self, at: Date) -> Result<Vec<Experience>, P::Error> {
        self.person.experience().map(|xs| Self::collect_until(at, xs))
    }

    pub fn education(&self, at: Date) -> Result<Vec<Education>, P::Error> {
        self.person.education().map(|xs| Self::collect_until(at, xs))
    }

    fn collect_until<A>(at: Date, xs: Vec<Timeline<A>>) -> Vec<A> {
        xs.into_iter()
            .filter(|t| t.at <= at)
            .map(|t| t.value)
            .collect()
    }
}
```
</details>
