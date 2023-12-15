# Java 객체지향 기초

## 클래스와 객체
- 클래스는 객체의 설계도이다. 클래스는 필드와 메서드를 갖고 있다.     
- 객체는 클래스로 만들어진 하나의 물건이다. 그걸 인스턴스라고 한다.

여기서 객체와 인스턴스의 차이점은?
객체는 만들 대상이다. 클래스는 자동차의 설계도, 객체는 설계도로 만들 자동차, 인스턴스가 만들어진 자동차이다.

자동차로 예시를 들어보면,
```java
public class Car{
    String name;
    String type;
    int ps;
    int cc;
    int doorNum;
}
```
이렇게 Car 클래스에 이름, 타입, 마력, 배기량과 문의 개수를 지정해놓는다.     
자동차의 설계도를 만든것이다.

이걸 객체로 만든다.
```java
public class main {
    public static void main(String[] args) {
        Car miyata = new Car();
    }
}
```
이렇게 Car 형식으로 미야타라는 인스턴스를 만들었다.
class Car이 클래스인 자동차 설계도,
```Car miyata = new Car();```로 메모리에 올려서 미야타 인스턴스를 만들었다.

## 오버라이딩과 오버로딩
오버라이딩이란 같은 매서드의 이름을 갖지만 함수의 파라미터로 받는 값이 달라서 마치 다른 함수처럼 사용할 수 있는것을 말한다.
오버라이딩은 인터페이스나 추상클래스들을 상속받는 과정에서 매서드를 사용하기 위해 오버라이딩이라는걸 해야한다.
```java
class post{      // 조상 클래스
    int a, b;
    int add(int a, int b){}
}

class get extends post{     // 상속받기 ( 자식 클래스 )
    int add(int a, int b){  // 오버라이딩
        return a + b;
    }
}
```
### 오버로딩
오버로딩은 함수의 이름은 같지만, 파라미터의 갯수, 타입등이 다르면 같은 이름이지만 다른함수처럼 쓸수 있게 해주는 기능이다.
```java
public class math {
    int add(int x, int y){
        return x + y;
    }
    int add(int x, int y, int z){
        return x + y + z;
    }
}
```

## 객체지향의 4원칙
- 추상화    
추상화의 정의는 사물등의 본질, 특성, 공통성 등을 추출하여 파악하는 것 이라고 나와있다. 똑같이 객체지향에서도 각 객체들의 본질, 특성, 공통성 등을 추출하여 정의하는것이다.      
예시를 들어서 자동차와 오토바이의 각각 하위 클래스들은 이동수단이라는 상위 클래스에서 정의할 수 있다.  추상클래스와 인터페이스가 있다.
- 상속      
상속은 함수와 비슷하게 클래스를 재활용하는 것이다. 같은 메서드나 필드를 사용하면, 상위클래스에서 만들고, 상속을 시켜서 코드를 간결화시키고 재사용을 한다.    
예시로  자동차와 오토바이가 부모클래스에서 모델명, 색, 바퀴의 갯수를 상속받을 수 있다.
- 다형성    
다형성은 여러개의 형태를 가질 수 것이다. 부모타입이 여러개의 자식타입들을 가질수 있다. 예시를 들어서 택시의 역할이라는 클래스가 있는데 자동차들의 종류도 들어갈 수 있지만 택시운전사도 받을 수 있다.
- 캡슐화       
데이터를 내부로 묶어서 외부에서 접근하지 못하게 하는것이다. 보안부분에서 많은 장점을 갖는다.

## 추상클래스와 인터페이스
추상클래스는 일반적인 클래스와 다른점은, 추상메서드를 갖는점이 다르다.   
여기서 추상메서드는 선언부만 있는 메서드이다.      
이때 추상클래스를 상속받은 클래스는 오버라이딩을 하지 않으면 상속받은 클래스도 추상클래스가 된다.      
추상클래스를 쓰면 생기는 장점은, 여러 클래스들을 상속해서 코드를 절약하고, 상속한 클래스들을 그룹화 할 수 있다.
```java
public abstract class oil{
    String oilType;
    abstract String getOilType();
}
```

```java
public class Car extends Chusang{
    String carName;

    @Override
    String getOilType(){
        return "oil type is "+this.oil;
    }
}
```

### 인터페이스 
인터페이스는 서로 다른 물건들이 서로 상호작용하기 위해서 사용하는것이다.         
필드는 자동으로 static으로 변환되고, 메서드도 abstract로 변환된다.
```java
public interface speed {
    public int MAX_SPEED = 260;
    public int getMAX_SPEED();
}
```
상속받을때에는 implements키워드를 사용한다. 매서드는 당연히 오버라이딩해서 사용한다.
```java
class Bike implements speed{

    @Override
    public int getMAX_SPEED() {
        return 0;
    }
}
```