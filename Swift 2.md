# Swift 2
3/28

5. Unwarp 옵셔널변수

 옵셔널: 값이 있을수도 있고 없을수도 있다(값이 있는지 없는지 모르는 상태)
 
 var someVariable : Int? = nil(값이 없다는 뜻)

if someVariable == nil {
    someVariable = 90(여기서 값이 들어가도 얘는 태생부터 옵셔널)
}

print("someVariable : \(someVariable)")

//someVariable : Optional(90) 이렇게 출력됨



언랩핑: 랩, 즉 감싸져 있는 것을 벗기는 것(optinal이라고 감싸져 있는 것을 벗겨야 함)

1. if let 으로 언래핑 하기
if let otherVariable = someVariable { 
(someVariable에 값이 있으면 otherVariable에 값을 넣겠다, 그럼 otherVariable은 값이 있는 것이므로 optional 아님)
    print("언래핑 되었다. otherVariable : \(otherVariable)")
}
else {
    print("값이 없다.")
}
//언래핑 되었다. otherVariable : 90



someVariable = nil

let myvalue = someVariable ?? 10
print("myvalue: \(myvalue)")

//someVariable이 비어있으면(값이 없으면) 기본값으로 설정한 값을 넣겠다.


2. guard let 으로 언래핑 하기

var firstvalue : Int? = 30
var secondvalue : Int? = 50

print("frist: \(firstvalue)")
print("second: \(secondvalue)")

unwrap(parameter: firstvalue) //parameter 넣기 싫으면 밑에
unwrap(parameter: secondvalue)

func unwrap(parameter: Int?) { //func unwrap(_ parameter: Int?) 이렇게 _ 넣으면 됨
    print("unwrap() called")
    guard let unWrappedParam = parameter
    else {
        return
    }
    print("unwrappedParam: \(unWrappedParam) ")
}

6. 클래스 vs 스트럭트(구조체)
 
struct YoutuberStruct { //데이터들의 모음
    var name : String
    var subscribersCount : Int
}

var devJeong = YoutuberStruct(name: "정대리", subscribersCount: 99999)

var devJeongClone = devJeong

print("devJeongClone.name :  \(devJeongClone.name)")

devJeongClone.name="호롤로롤"

print("devJeongClone.name :  \(devJeongClone.name)")
print("devJeongClone.name :  \(devJeong.name)")


class Youtuberclass { //스트럭트랑 똑같으나, 생성자만 만들면 됨, 클래스로 만든 걸 객체라 함
    var name : String
    var subscribersCount : Int
    init(_ name: String, subscribersCount: Int) {
        self.name = name
        self.subscribersCount = subscribersCount
    } //생성자
}

var jeongDaeRi = Youtuberclass("정대리", subscribersCount: 99999)

var jeongDaeRiClone = jeongDaeRi

print("값 넣기 전 devJeongClone.name : \(jeongDaeRiClone.name)")

jeongDaeRiClone.name = "호로로롤"

print("값 넣은 후 devJeongClone.name : \(jeongDaeRiClone.name)")
print("값 넣은 후 devJeong.name : \(jeongDaeRi.name)")

// 스트럭트는 값 넣은 후 클론과 값이 다름(다른 종이에 복사한거라 클론 값 변경해도 영향 x
// 클래스는 값 넣은 후 클론과 값 같음(클론과 서로 연결이 되있어서 클론 값 변경하면 영향 o, 클래스는 같은 메모리 주소를 가리키는 참조임

7. 프로퍼티 옵저버

 var myAge = 0 {
    willSet{
        print("값이 설정될 예정이다. myage: \(myAge)")
    }
    didSet{
        print("값이 설정되었다. myage: \(myAge)")
    }
}

myAge = 10
myAge = 20
print(myAge)

//
값이 설정될 예정이다. myage: 0
값이 설정되었다. myage: 10
값이 설정될 예정이다. myage: 10
값이 설정되었다. myage: 20
20

8. 함수 매개변수 이름

 func myFunction(name: String) -> String { //Stirng으로 반환하겠다.
    return "안녕하세요? \(name) 입니다"
}

myFunction(name: "정대리")
myFunction(name: "쩡쩡대리")


func myFunctionSecond(with name: String) -> String {
    return "안녕하세요? \(name) 입니다"
}

myFunctionSecond(with: "호로로롤")

9. 제네릭

//제네릭-> 어떠한 자료형도 받을 수 있다

struct MyArray<SomeElement> { // 제네릭 보통 <T> 로 둠
    var elements : [SomeElement] = [SomeElement]()
    
    init(_ elements: [SomeElement]) {
        self.elements = elements
    }
}

struct Friend {
    var name : String
}

var mySomeArray = MyArray([1, 2, 3])
print("mySomeArray : \(mySomeArray)")

var myStringArray = MyArray(["가", "나", "다"])
print("myStringArray : \(myStringArray)")

let friend_01 = Friend(name: "철수")
let friend_02 = Friend(name: "영희")
let friend_03 = Friend(name: "수지")

var myFriendsArray = MyArray([friend_01,friend_02,friend_03])
print("myFriendsArray : \(myFriendsArray)")









