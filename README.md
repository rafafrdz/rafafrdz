[![Header](./pictures/banner.png "Header")](https://rafaelfernandezortiz.com/)

# Hey there, folks! <img src="https://raw.githubusercontent.com/MartinHeinz/MartinHeinz/master/wave.gif" width="50">

[![Linkedin](https://img.shields.io/badge/Linked-in-369?&logo=linkedin&logoColor=white&color=blue)](https://www.linkedin.com/in/rafael-fernandez-ortiz/)

I'm Rafael Fernández Ortiz, a die-hard Scala developer with a rock-solid foundation in mathematics—algebra and computer science are my playgrounds.

My tech journey is an epic blend of the elegant abstractions of category theory and the exhilarating rush of writing code that just clicks. And yes, when I'm not conjuring up functional magic, you’ll find me battling it out in 80's arcade classics! 🎮

I'm always on a quest for new challenges ⚔️, eager to push the boundaries of what's possible in the world of code.

#### Current Version: 1.9.94 🛠️

```scala
 import dev.myself.core._
  trait Person[F[_]] { /* compiled code */ }
  trait CurriculumVitae[F[_]] {
    def about: F[Info]
    def experience(date: Date): F[Info]
    def education(date: Date): F[Info]
    def techStacks: F[Stack]
  }

  def cv[F[_]: MonadFilter](person: Person[F]): CurriculumVitae[F] =
    new CurriculumVitae[F] {
      def about: F[Info] = person.MYLIFE
      def experience(date: Date): F[Info] = person.EXPERIENCE.filter(info => info.date == date)
      def education(date: Date): F[Info] = person.EDUCATION.filter(info => info.date == date)
      def techStacks: F[Stack] = person.SKILLS
    }

  val me: Person[List] = new Person[List] { /* compiled code */ }
  val rafaelFernandezOrtiz: CurriculumVitae[List] = cv(me)
```

<h1> To code or not to code, that is the question <img align="left" alt="png" src="./pictures/craneo.png?raw=true" width="60px"/> </h1>

Welcome to my GitHub corner! Here, I share my thoughts and explorations in design patterns, functional programming, Scala, and more. Check out some of my recent writings:

- **Web** [Agregando skills modulares (Spanish)](https://rafaelfernandez.dev/agregando-skills-modulares)
- **Web** [Fechas y expresiones regulares (Spanish)](https://rafaelfernandez.dev/fechas-expresiones-regulares)
- **Reddit** [Free Monad vs Tagless Final (English)](https://www.reddit.com/r/scala/comments/uzoycg/free_monad_vs_tagless_final/)
  
<br>
<h1>  Coffee time... Let's talk! ☕ <img align="left" alt="png" src="./pictures/cup.png?raw=true" width="60px"/></h1> 

- 💬 Always open to discussions—ask me anything!
- 🌍 [Website](https://rafaelfernandez.dev)
- 📝 [Resume (English)](https://drive.google.com/file/d/1espEzGL_pYQOV1-mWrgxBdz94TDjYCmF/view)


<h1>Tech Stack <img align="left" alt="png" src="./pictures/code.png?raw=true" width="60px"/></h1>

<p align="left">
<a href="https://www.scala-lang.org/"><img align="center" src="https://img.shields.io/badge/-Scala-%23f61938?logo=scala" alt="scala-lang"/></a>
<a href="https://www.haskell.org/"><img align="center" src="https://img.shields.io/badge/-Haskell-blue?logo=haskell" alt="haskell-lang"/></a>
<a href="https://www.erlang.org/"><img align="center" src="https://img.shields.io/badge/-Erlang-purple?logo=erlang" alt="erlang"/></a>
<a href="https://www.rust-lang.org"><img align="center" src="https://img.shields.io/badge/-Rust-orange?logo=rust" alt="rust-lang"/></a>
<a href="https://www.swi-prolog.org/"><img align="center" src="https://img.shields.io/badge/-Prolog-black?logo=prolog" alt="swi-prolog"/></a>
<a href="https://spark.apache.org/"><img align="center" src="https://img.shields.io/badge/Apache-Spark-yellow?logo=apachespark" alt="apache spark"/></a>
<a href="https://kafka.apache.org/"><img align="center" src="https://img.shields.io/badge/Apache-Kafka-purple?logo=apachekafka" alt="apache kafka"/></a>
<a href="https://hadoop.apache.org/"><img align="center" src="https://img.shields.io/badge/Apache-Hadoop-white?logo=apachehadoop" alt="apache hadoop"/></a>
<a href="https://docs.sonarqube.org/latest/"><img align="center" src="https://img.shields.io/badge/-SonarQube-blue?logo=sonarqube&logoColor=white" alt="sonarqube"/></a>
<a href="https://git-scm.com/"><img align="center" src="https://img.shields.io/badge/-Git-white?logo=git&logoColor=orange" alt="git"/></a>
<a href="https://github.com/"><img align="center" src="https://img.shields.io/badge/-GitHub-black?logo=github&logoColor=white" alt="github"/></a>
<a href="https://www.docker.com/"><img align="center" src="https://img.shields.io/badge/-Docker-00c0ff?logo=docker&logoColor=white" alt="docker"/></a>
<a href="https://www.scala-sbt.org/"><img align="center" src="https://img.shields.io/badge/-Sbt-red?&logoColor=white?logo=sbt" alt="sbt"/></a>
<a href="https://mvnrepository.com/"><img align="center" src="https://img.shields.io/badge/-Maven-blue?&logoColor=white?logo=maven" alt="maven"/></a>
<img align="center" src="https://img.shields.io/badge/Linux-informational?style=flat&logo=linux&logoColor=black&color=white" alt="linux"/>
<img align="center" src="https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg" alt="Awesome Badge"/>
</p>

<a href="https://github.com/rafafrdz"><img src="https://github-readme-stats.vercel.app/api/top-langs/?username=rafafrdz&hide=XSLT,CSS,SQLPL&layout=compact" width="41%"> <img src="https://github-readme-stats.vercel.app/api?username=rafafrdz&rank_icon=github" width="52%"></a>
