[![Header](./pictures/banner.png "Header")](https://rafaelfernandezortiz.com/)

# Hello, folks! <img src="https://raw.githubusercontent.com/MartinHeinz/MartinHeinz/master/wave.gif" width="50px">

I'm a graduated in mathematics specialized in algebra and computer science, and a passionated Scala developer. As fascinated in learning about category theory as playing 80's arcade games. Looking for new challenges and new approaches to develop.

#### release 1.9.94  ![](https://visitor-badge.glitch.me/badge?page_id=rafafrdz.rafafrdz)

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



![](https://img.shields.io/badge/-Scala-%23f61938?logo=scala)![](https://img.shields.io/badge/-Haskell-violet?logo=haskell)![](https://img.shields.io/badge/-Python-blue?logo=python&logoColor=white)![](https://img.shields.io/badge/Apache-Spark-yellow)![](https://img.shields.io/badge/Apache-PySpark-green)<img align="right" alt="GIF" src="./pictures/developer.gif?raw=true" width="400"/>

![](https://img.shields.io/badge/Apache-HDFS-white)![](https://img.shields.io/badge/-SonarQube-blue?logo=sonarqube&logoColor=white)![](https://img.shields.io/badge/-Git-orange?logo=git&logoColor=white)![](https://img.shields.io/badge/-GitHub-black?logo=github&logoColor=white)![](https://img.shields.io/badge/-Docker-00c0ff?logo=docker&logoColor=white)![](https://img.shields.io/badge/-Sbt-red?&logoColor=white)![](https://img.shields.io/badge/-Maven-blue?&logoColor=white)

![](https://img.shields.io/badge/-MySql-yellow?&logoColor=white)![](https://img.shields.io/badge/OS-Windows-informational?style=flat&logo=windows&logoColor=white&color=white)![](https://img.shields.io/badge/OS-Linux-informational?style=flat&logo=linux&logoColor=white&color=2bbc8a)<img src="https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg" alt="Awesome Badge"/>

#### And more...

[![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=rafafrdz&hide=XSLT,CSS,SQLPL&layout=compact)](https://github.com/rafafrdz/)





# Work in progress...<img align="left" alt="png" src="./pictures/github.png?raw=true" width="60px"/>



[![Readme Card](https://github-readme-stats.vercel.app/api/pin/?username=rafafrdz&repo=braids-and-cryptography)](https://github.com/rafafrdz/braids-and-cryptography) [![Readme Card](https://github-readme-stats.vercel.app/api/pin/?username=rafafrdz&repo=g30Loc)](https://github.com/rafafrdz/g30Loc) 

[![Readme Card](https://github-readme-stats.vercel.app/api/pin/?username=rafafrdz&repo=saddle)](https://github.com/rafafrdz/saddle) [![Readme Card](https://github-readme-stats.vercel.app/api/pin/?username=rafafrdz&repo=practice-huffman-coding-algorithm)](https://github.com/rafafrdz/practice-huffman-coding-algorithms)  



# Coffee time... Let's talk!<img align="left" alt="png" src="./pictures/cup.png?raw=true" width="60px"/>



- 💬 Ask me about anything, I am happy to help;
- 🐤 How to reach me: [@neskeip](https://twitter.com/neskeip);
- 📝 [Resume (Spanish)](https://drive.google.com/file/d/1Rp_m1IIS7txtsfOGmYGFnMhyJzWqkZjd/view)
- 🌍 [Website](https://rafaelfernandez.dev)