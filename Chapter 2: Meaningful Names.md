# Chapter 2: Meaningful Names

> 이름은 소프트웨어 어디에나 존재한다. 우리는 변수, 함수, 매개변수, 클래스, 패키지 등에 이름을 붙인다. 우리는 매우 많이 이름을 짓기 때문에, 우리는 이것을 더 잘해야 한다. "좋은 이름을 붙이는 간단한 규칙"을 알려주겠다.

---

## 의도가 보이는 이름을 사용하라.

* 이름에 의도를 나타내라고 말하는 것은 쉽다.
* 좋은 이름을 고르는 것은 시간이 걸리지만, 그 효과는 배로 시간을 절약한다.
* 너가 더 좋은 것을 발견하면 **그 이름들을 바꿔라**

```
int d
```
* 이름 d는 아무 의미를 나타내지 못한다. 우리는 그것이 무엇을 수행하고 어떤 단위인지 잘 명시되는 이름을 골라야 한다.

```
int elapsedTimeInDays;
int daysSinceCreation;
```
* 코드를 짤 때도 실제로 암시하는 것들을 잘 나타내야 한다.

```
theList -> getBoard

if(x[] == 4) -> if(cell[] == FLAGGED)
```
* 단순히 이름을 바꿈으로써, 더이상 코드가 무엇을 하는지 이해하는게 어렵지 않게 되었다. 이것이 좋은 이름을 짓는 것의 힘이다.

## 잘못된 정보를 피해라.

* 코드의 의미가 **단서, 모호함을 남겨두는 것은 피해라**.
* 우리는 단어가 해석에 따라 의미가 달라지는 단어는 피해야 한다.
* (ex: hp, aix, sco ...)
* list같은 단어도 프로그램이 실제 list일 때 사용해라. (list는 프로그래머에게 특정한 의미를 가져다 주기 때문에)
* `accountList` -> `accoundGroup`

## 의미있는 구별을 만들어라.

* 컴파일러가 변수에 숫자를 매기는 것을 수용하더라도 이것은 매우 좋지 않은 행동이다.
* 숫자를 매기는 방식은 **정보가 없는** 변수다.

```
public static void copyChars(char a1[], char a2[]){
	for (int i=0; i<a1.length; i++){
		a2[i] = a1[i];
	}
}
```
* 이러한 코드는 의도를 전달하지 못하고 단서만 남겨 놓는다.
* Info, Data, String 같은 불용어는 사용하지 말아라. 구분이 힘들다.
* ex)
* `Name`, `NameString`
* `getActiveAccount()`, `getActiveAccounts()`, `getActiveAccountInfo()`

## 발음 할 수 있는 이름을 사용하라.

* 우리 뇌의 중요한 부분은 단어의 개념에 할당되어 있다.
* 우리 뇌의 거대한 부분은 말을 하는 것에 적응 되도록 진화되어 있으므로, 너의 **변수 이름을 발음하기 쉽게 만들어라.**
```
class DtaRcrd102 {
	private Date genymdhms; // 시간을 나타냄.
	private Date modymdhms;
}

class Customer {
	private Date generationTimestamp;
	private Date modificationTimestamp;
}
```
* 위의 코드는 같은 의미를 가지고 있지만, 아래는 지성인 대화가 가능하다.

## 찾을 수 있는 이름을 사용하라.

* 한글자 이름이나 숫자 상수는 쉽게 찾을 수 없는 문제가 있다.
* 7 -> MAX_CLASSES_PER_STUDENT (훨씬 찾기 쉬움)
* 'e' 한글자는 코드의 여러 곳에 있기 떄문에 찾기 힘들다.
* 긴 이름이랑 찾을 수 있는 이름을 쓰는 것이 좋다.
* 짧은 문자를 사용할 때는 작은 스코프 안에서 사용할 변수에만 사용한다.
* ex) for문, for(int j=0; j<34; j++) ..

## Encoding를 피해라.

* 정보를 이름으로 Encoding하는 것은 우리에게 더 많은 짐을 추가하는 것이다.

### 헝가리어 표기법

* 요즘은 많은 시스템 타입을 가지고 있다.
* 자바 프로그래머는 encoding을 필요로 하지 않는다. Object가 타입형태이고, complie하기 전에 에러를 탐지할 수 있기 때문이다.

### 변수 접두사

* 변수 앞에 m_같은 접두사를 붙일 필요가 없다.
* 클래스나 함수는 접두사를 필요로 하지 않을 만큼 충분히 작아야 한다.

```
public class Part {
	private String m_des;
	void setName(String name){
		m_des = name;
	}
}

---

public class Part {
	String description;
	void setDescription(String description){
		this.description = description;
	}
}
```

* 사람들은 변수 이름의 중요한 부분을 보기 위해 접두사를 보통 잊어버린다.
* 코드를 읽을수록 접두사를 보는 것이 적어진다.
* **결국 접두사는 잘 보지 않게 된다.**

### interfaces와 implementations

* 여기에는 특별한 종류의 enccoding이 있다.
* interface의 경우 꾸미지 않은 채로 두는 것을 선호한다.
* ex) ShapeFactoryImp, CShapeFactory...
* 인터페이스 이름을 encoding하는 것은 선호되어 질 수 있다.

## 정신적인 연결을 피해라.

* 읽는 사람들은 너의 변수명을 이미 알고있는 변수명으로 번역하는 것을 막아야 한다.
* 이 문제는 single-letter 변수 명에서 발생한다.
* 예를들어 i, j, k는 반복문에서 카운트로 사용된다. 그러나 대부분의 문맥에서 single-letter 변수명은 좋지 않은 선택이다.
* 일반적으로 프로그래머는 똑똑하므로 정신적인 연결을 좋아할 것이다.
* 똑똑한 프로그래머와 전문적인 프로그래머의 차이는 명백함을 얼마나 잘 나타내느냐 이다.
* 전문적인 프로그래머는 다른 사람들이 이해할 수 있는 좋은 코드의 힘을 이용 할 것이다.

## 클래스 이름

* 클래스 이름은 명사, 명사구로 하는 것이 좋다.
* ex) Customer, WikiPage, AddressParser ...
* 피해야 하는 이름 (Manager, Data, Info)
* **클래스 이름은 동사를 피해야 한다.**

## 메소드 이름

* 메소드 이름은 무조건 **동사, 동사구**로 해야한다.
* ex) postPayment, deletePage ...
* 접근자, 술어, 접두사(get, set, is)는 매우 좋은 표준이다.
* 생성자를 오버로딩 할 때는 변수에 대한 설명을 붙여서 생성 함수를 사용하는 것이 좋다. 
* Complex fulcrumPoint = Complex.FromRealNumber(23.0);
* ~~Complex fulcrumPoint = new Complex(23.0);~~

## 귀엽게 만들지 마라.

* 사람은 영리하기 떄문에 유머나 장난을 치는 사람들을 잘 기억한다.
* HolyHandGrenade 보다는 DeleteItems같은 이름이 더 나을 것이다.
* 장난스런 이름보다는 명백한 이름을 골라라.
* **나타내고자 하는 것을 말하고, 말하고자 하는 것을 나타내라.**

## 한개의 개념에는 한가지 단어만 사용해라.

* get, fetch, retrieve 같이 같은 의미에 다양하게 단어를 사용하면 혼란을 줄 수 있다.
* 그렇지 않으면 이전의 코드를 보기 위해 많은 시간을 사용해야 한다.
* 혼동하여 사용하는 단어 예시
* controller - manager - driver
* 일관적인 단어 사용은 매우 좋은 혜택을 준다.

## 말장난을 하지 마라.

* 다른 목적으로 같은 단어를 사용하는 것을 피해라.
* 다른 아이디어에 같은 단어를 사용하는 것이 **말장난**이다.
* add의 경우 새로운 값을 더하거나, 두개의 변수를 이어 붙이라는 2가지 방식으로 해석될 수 있다.
* 이러한 경우 add는 말장난이 되고, 두 번째의 경우 insert, append같은 방식으로 말장난을 피할 수 있다.

## 해결을 위한 이미 정해진 이름을 사용해라.

* 너의 코드를 읽는 사람이 프로그래머라는 사실을 기억해라.
* 즉, 알고리즘 이름, CS 단어, 패턴 이름, 수학 단어 등등을 사용 할 수 있다.
* 'AccountVisitor'같은 경우 'VISITOR' 패턴을 아는 사람에게는 의미가 잘 전달된다.
* 즉, technical한 변수를 선택하는 것은 적절한 조치다.

## 문제를 위한 이미 정해진 이름을 사용해라

* 문제를 분류하고, 문제에 이미 정해진 이름을 사용 하는 것은 좋은 프로그래머가 해야 할 부분이다.

## 의미있는 문맥을 더해라.

