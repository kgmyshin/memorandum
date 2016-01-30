Functional Programming Patters v3

@raulraja CTO @47deg


目にするもの全て関数型に表すことができる。

When i build an app
- Free of interpretation        => Free monads
- Support paralel computation   => Free application
- Composable pieces         => coproducts
- Dependency Injection / IDC  => implicits kleisle
- Fault Tolerance => dpendentrly typed checked except


Free monads
a monad on custom algebra that can be run throuugh an interpreter

Let8s build an app that read a Cat, validates some input and stores it

Our first algebra moels our program interaction with end userMap

sealed trait Interact[A]
case class Ask(prompt: String) extends Interact[String]
case class Tell(msg: String) extends Interact[Unit]

Our second algebra is about persistance and data valiation


ダメだ、ついていけんかった

資料
=> http://www.slideshare.net/raulraja/functional-programming-patterns-for-the-pragmatic-programmer
