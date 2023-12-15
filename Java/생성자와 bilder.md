# 생성자와 builder

## 생성자
객체를 생성과 동시에 초기화를 할때 사용하는 것이다. class에서 생성자를 작성해서 선언과 동시에 초기화를 시킬 수 있다.

생성자는 반환타입을 갖지 않고 여러개를 갖을 수 있다.

아무런 생성자도 만들지 않으면 자체적으로 기본생성자를 만들어준다.
```java
public class Car {
    private String name;
    private int cc;

    // Public Car(){}
}
```
하지만 우리가 생성자를 한개라도 만들게 되면 기본생성자는 없어진다.

```java
public class Car {
    private String name;
    private int cc;

    public Car() {
        this.name = "";
        this.cc = 0;
    }

    public Car(String name, int cc) {
        this.name = name;
        this.cc = cc;
    }

    public Car(String name){
        this(name, 0);  // 이렇게 더 간단하게 만들 수 있다.
    }

    public static void main(String[] args) {
        Car car1 = new Car(); 
        Car car2 = new Car("Toyota", 2000);
    }
}

```

## Builder
객체를 생성할때에는 여러가지 방법이 있는데, 생성자, 메소드, 빌더등등이 있다.
만약 필드가 많아지면 객체를 생성할때 사용하는 생성자가 매우 많아져서 답이 없다.
```java
public class Car {
    private String name;
    private String Type;
    private int wheel;
    private int doors;
    private int cc;

    public Car() {
        this.name = "";
        this.cc = 0;
    }

    public Car(String name){
        this(name, 0);
    }


    public Car(String name, int cc) {
        this.name = name;
        this.cc = cc;
    }
}


    //..............................
```
이럴때 간편하게 하기 위해서 사용하는게 Builder패턴이다.

사용방법은 별도의 builder 클래스를 만들어서 값들을 받고 build 메소드로 하나의 인스턴스를 만드는 것이다.      
이제는 생성자 오버로딩을 의미없이 만들거나 실수할일도 적어진다.

이정도의 필드가 있다고 하면,
```java
class Car{
    private String name;
    private String Type;
    private int wheel;
    private int doors;
    private int cc;

    public Car(String name, String type, int wheel, int doors, int cc){
        this.name = name;
        // .......
    }
}
```

builder 클래스는 이렇게 만든다.
```java
class carBuilder{
    private String name;
    private String type;
    private int wheel;
    private int doors;
    private int cc;

    public CarBuilder name(String name) {
        this.name = name;
        return this;
    }

    public CarBuilder type(String type) {
        this.type = type;
        return this;
    }

    public CarBuilder wheel(int wheel) {
        this.wheel = wheel;
        return this;
    }

    public CarBuilder doors(int doors) {
        this.doors = doors;
        return this;
    }

    public CarBuilder cc(int cc) {
        this.cc = cc;
        return this;
    }

    public Car build(){
        return new Car(name, type, wheel, doors, cc); // 이렇게 생성자를 호출한다.
    }
}

class main{
    public static void main(String[] args){
        Car miyata = new Car()
            .name("miyata")
            .type("FR")
            .wheel(4)
            .doors(4)
            .cc(3000)
    }
}
```
여기서 각 builder마다 return하는것이 this 즉 자신 객체이다. 그래서 호출할때 ```.aa().bb().cc()```이런식으로 가능하게 된다.