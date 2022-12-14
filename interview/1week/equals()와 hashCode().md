자바의 모든 클래스는 Object 클래스를 상속받습니다. 그리고 Object 클래스에는 equals()와 hashCode()라는 메소드가 선언되어 있습니다.
이 메소드들은 각각 어떤 역할일까요? 이둘의 차이점은 무엇일까요?
- equals() 는 객체의 값의 일치여부(boolean)을 반환하는 타입이다.
- hasCode() 는 객체의 주소값(int)을 이용하여 객체 고유의 해시 코드를 리턴하는 함수이다. 
> 해시 코드 작동 방식
> - 해시코드를 간단하게 말하면 해시 알고리즘에 의해 생성된 정수 값입니다.
> - Object 클래스에 의해 정의된 hashCode() 방법은 별개의 개체에 대해 고유한 정수를 반환합니다.
> 
- equals의 오버라이드 시에는 hasCode도 꼭 함께 오버라이드 해야한다.
- hash 값을 사용하는 Collection(HashMap, HashSet, HashTable)은 객체가 논리적으로 같은지 비교할 때
- hasCode() 리턴 값 비교 -> equals() 리턴값 비교 순으로 진행한다. 
- (equals()에서 같아도 hasCode()에서 다르면 다른객체로 인식)

> hashCode 를 잘못 오버라이딩하면 HashMap 등 hash 콜렉션의 성능이 떨어질 수가 있습니다. 어떤 케이스일 때 그럴 수 있을까요?
> - Hash 캐싱
> ```java
> public int hashCode;
>
> @Override
> public int hashCode() {
>  	int result = hashCode;
>  	if (result == 0) {
>     result = areaCode;
>     result = 31 * result + prefix;
>     result = 31 * result + lineNum;
>     hashCode = result;
>   }
>  return result;
> }
> ``` 
- hashCode()의 장점은 주어진 키에 대한 해시 값을 계산하고 내부적으로 이 값을 사용하여 데이트를 저장하는 것입니다.
- hasCode()에서 계속 같은 값을 주면 해시테이블 하나의 버킷 내에 계속 원들이 쌓여 리스트 형태로 연결되어 시간이 늘어나게 됩니다.
- hasCode() 가 반환하는 값의 생성 규칙을 API 사용자에게 자세히 공표하지 않아야 클라리이언트가 이 값에 의지하지 않게되고, 추후에 계산 방식을 바꿀 수 있다.
