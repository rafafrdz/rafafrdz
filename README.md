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

#  Tech Stack <img align="left" alt="png" src="./pictures/code.png?raw=true" width="60px"/>

![](https://img.shields.io/badge/-Scala-%23f61938?logo=scala) ![](https://img.shields.io/badge/-Haskell-violet?logo=haskell) ![](https://img.shields.io/badge/-Python-blue?logo=python&logoColor=white) ![](https://img.shields.io/badge/Apache-Spark-yellow) ![](https://img.shields.io/badge/Apache-PySpark-green) ![](https://img.shields.io/badge/Apache-HDFS-white) ![](https://img.shields.io/badge/-SonarQube-blue?logo=sonarqube&logoColor=white) ![](https://img.shields.io/badge/-Git-orange?logo=git&logoColor=white) ![](https://img.shields.io/badge/-GitHub-black?logo=github&logoColor=white) ![](https://img.shields.io/badge/-Docker-00c0ff?logo=docker&logoColor=white) ![](https://img.shields.io/badge/-Sbt-red?&logoColor=white) ![](https://img.shields.io/badge/-Maven-blue?&logoColor=white) ![](https://img.shields.io/badge/OS-Windows-informational?style=flat&logo=windows&logoColor=white&color=white) ![](https://img.shields.io/badge/OS-Linux-informational?style=flat&logo=linux&logoColor=white&color=2bbc8a) <img src="https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg" alt="Awesome Badge"/>

<img align="right" alt="GIF" src="./pictures/developer.gif?raw=true" width="350"/>

#### And more...

[![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=rafafrdz&hide=XSLT,CSS,SQLPL&layout=compact)](https://github.com/rafafrdz/)

# To code or not to code, that is the question <img align="left" alt="png" src="./pictures/craneo.png?raw=true" width="60px"/>

Hi! I would like to show you some posts that I wrote about design patterns, functional programming, scala and so on.
- [Web] [Agregando skills modulares (Spanish)](https://rafaelfernandez.dev/agregando-skills-modulares)
- [Web] [Fechas y expresiones regulares (Spanish)](https://rafaelfernandez.dev/fechas-expresiones-regulares)
- [Reddit] [Free Monad vs Tagless Final (English)](https://www.reddit.com/r/scala/comments/uzoycg/free_monad_vs_tagless_final/)


# Coffee time... Let's talk!<img align="left" alt="png" src="./pictures/cup.png?raw=true" width="60px"/>

- 💬 Ask me about anything, I am happy to help;
- 🐤 How to reach me: [@neskeip](https://twitter.com/neskeip);
- 📝 [Resume (Spanish)](https://drive.google.com/file/d/1yE_VHTEpefw8NXSFIBNbB-3VZ2z4E7c9/view)
- 📝 [Resume (English)](https://drive.google.com/file/d/1uqTAWSx0z5iuWpLnNZqaqNmLkj6sB25G/view)
- 🌍 [Website](https://rafaelfernandez.dev)
