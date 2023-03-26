# Swift 공부 1일차(23.03.26)

1. 조건문:

 -if (isDarkmode == true), if isDarkmode 두 개 같음
 -var title : String = isDarkmode ? "다크모드" : "다크모드 X"
 
 
 
2. foreach 반복문:

 var myArray : [Int] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

 for item in myArray where itme > 5 {
    print("item: \(item)")
 }
 
 
 
 3. enum
 
  -var-> 값 변경 가능
  -let-> 값 변경 불가(상수)
  -print("yourSchool: \(yourSchool)") == print("yourSchool: ", yourSchool)
  
  enum Grade : Int {
    case first = 1
    case second = 2
 }

 let yourGrade = Grade.second // 또는 Grade.second.rawvalue 이렇게
 print("yourSchool: \(yourGrade.rawValue)") => enum이 가지고 있는 값이 출력됨
 
 enum SchoolDetail {
    case elementary(name: String)
    case middle(name: String)
    case high(name: String)

    func getName() -> String {
        switch self {
        case .elementary(let name):
            return name
        case let.middle(name):
            return name
        case.high(let name):
            return name
        }
    }
}

let yourEleSchoolName = SchoolDetail.elementary(name: "천보")

print("yourEleSchoolName: \(yourEleSchoolName.getName())")



4. for 반복문
 
 -0...5 -> 0~5
 -0..<5 -> 0~4

var randomInts: [Int] = []

for _ in 0..<24 { // i 넣고 싶지 않을 때 _ 쓰면 됨
    let randomNumber = Int.random(in: 0...100)
    randomInts.append(randomNumber)
}

print("randomInts: \(randomInts)")



5. Unwrap 옵셔널변수
 












