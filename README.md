[![Header](./pictures/banner.png "Header")](https://rafaelfernandezortiz.com/)

# Hello, folks! <img src="https://raw.githubusercontent.com/MartinHeinz/MartinHeinz/master/wave.gif" width="50">

[![Linkedin](https://img.shields.io/badge/Linked-in-369?&logo=linkedin&logoColor=white&color=blue)](https://www.linkedin.com/in/rafael-fernandez-ortiz/)  <a href="https://reddit.com/u/rafafrdz"><img alt="Reddit User Karma" src="https://img.shields.io/reddit/user-karma/combined/rafafrdz?label=karma&logo=reddit&logoColor=white"></a> ![](https://visitor-badge.glitch.me/badge?page_id=rafafrdz.rafafrdz)

I'm a graduated in mathematics specialized in algebra and computer science, and a passionated Scala developer. As fascinated in learning about category theory as playing 80's arcade games. Looking for new challenges and new approaches to develop.

#### release 1.9.94  

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
<h3> And more... </h3>

<a href="https://github.com/rafafrdz/">
  <img align="center" src="https://github-readme-stats.vercel.app/api/top-langs/?username=rafafrdz&hide=XSLT,CSS,SQLPL&layout=compact" alt="rafafrdz-stats">
</a>
<img align="right" src="./pictures/developer.gif?raw=true" alt="myself-gif" style="width:350px">

<br><br><br><br><br>
<h1> To code or not to code, that is the question <img align="left" alt="png" src="./pictures/craneo.png?raw=true" width="60px"/> </h1>

Hi! I would like to show you some posts that I wrote about design patterns, functional programming, scala and so on.
- [Web] [Agregando skills modulares (Spanish)](https://rafaelfernandez.dev/agregando-skills-modulares)
- [Web] [Fechas y expresiones regulares (Spanish)](https://rafaelfernandez.dev/fechas-expresiones-regulares)
- [Reddit] [Free Monad vs Tagless Final (English)](https://www.reddit.com/r/scala/comments/uzoycg/free_monad_vs_tagless_final/)


<h1>  Coffee time... Let's talk!<img align="left" alt="png" src="./pictures/cup.png?raw=true" width="60px"/></h1> 

- 💬 Ask me about anything, I am happy to help;
- 🐤 How to reach me: [@neskeip](https://twitter.com/neskeip);
- 📝 [Resume (Spanish)](https://drive.google.com/file/d/1yE_VHTEpefw8NXSFIBNbB-3VZ2z4E7c9/view)
- 📝 [Resume (English)](https://drive.google.com/file/d/1uqTAWSx0z5iuWpLnNZqaqNmLkj6sB25G/view)
- 🌍 [Website](https://rafaelfernandez.dev)
