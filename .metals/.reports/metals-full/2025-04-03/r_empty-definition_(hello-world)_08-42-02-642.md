error id: 
file:///D:/Program%20Files/GitHub/Scala_HeThongAo/hello-world/src/main/scala/Main.scala
empty definition using pc, found symbol in pc: 
empty definition using semanticdb
empty definition using fallback
non-local guesses:

offset: 1012
uri: file:///D:/Program%20Files/GitHub/Scala_HeThongAo/hello-world/src/main/scala/Main.scala
text:
```scala
import scala.util.Random

case class Person(personID: Int, personName: String, personAge: Int, personGender: String)

object PersonFriends extends App {
  val random = new Random()
  val persons = Array(
    Person(1, "Alex", 15, "Male"),
    Person(2, "Many", 26, "Female"),
    Person(3, "Jame", 34, "Male"),
    Person(4, "Harry", 23, "Male"),
    Person(5, "Bob", 40, "Male"),
    Person(6, "Tom", 32, "Male"),
    Person(7, "Anna", 18, "Female"),
    Person(8, "Jeff", 45, "Male"),
    Person(9, "Lucia", 45, "Male"),
  )

  // 1. Đếm số lượng nam và nữ
  val maleCount = persons.count(_.personGender == "Male")
  val femaleCount = persons.count(_.personGender == "Female")
  println(s"Male count: $maleCount, Female count: $femaleCount")

  // Tạo ma trận Friend 9x9
  val friendMatrix = Array.ofDim[Int](9, 9)
  for (i <- 0 until 9; j <- 0 until 9 if i != j) {
    friendMatrix(i)(j) = random.nextInt(2) // 0 hoặc 1
    friendMatrix(j)(i) = friendMatrix(i)(j) // Đảm bảo tính đố@@i xứng
  }
  // Tìm số người có tuổi >= 20
  val person20s = persons.filter(_.personAge >= 20)
  println(s"Số người có tuổi >= 20: ${person20s.length}")
  
  // Tìm Person có bạn bè nam ít nhất
  val maleIndexes = persons.zipWithIndex.collect {
    case (p, i) if p.personGender == "Male" => i
  }

  if (maleIndexes.nonEmpty) {
    val minMaleIndex = maleIndexes.minBy(i => friendMatrix(i).sum)
    println(s"Person nam có ít bạn nhất: ${persons(minMaleIndex).personName}")
  } else {
    println("Không có Person nam nào trong danh sách.")
  }

  // Tìm Person nữ có bạn bè nhiều nhất
  val femaleIndexes = persons.zipWithIndex.collect {
    case (p, i) if p.personGender == "Female" => i
  }

  if (femaleIndexes.nonEmpty) {
    val maxFemaleIndex = femaleIndexes.maxBy(i => friendMatrix(i).sum)
    println(s"Person nữ có nhiều bạn nhất: ${persons(maxFemaleIndex).personName}")
  } else {
    println("Không có Person nữ nào trong danh sách.")
  }
}
```


#### Short summary: 

empty definition using pc, found symbol in pc: 