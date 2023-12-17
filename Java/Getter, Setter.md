# Getter, Setter

클래스의 필드가 ```private```권한이라면 외부에서 접근할 수 없다.     
그래서 인스턴스의 필드값을 수정하고, 가져오는데에 다른 방법이 필요한데 그 방법이 Getter, Setter이다.

일반적으로는,
```java
public class People{
    private int name;
    private int age;
}

class main{
    public static void main(string[] args){
        People Man = new People();

        // Man.name = "홍박사" // 이건 당연히 접근권한이 private이기 때문에 불가능하다.
    }
}
```
하지만 접근을 해서 값을 바꾸거나 가져와야하는 상황이 생기면 Getter, Setter 메소드를 만든다.
```java
public class People{
    private int name;
    private int age;

    String getName(){
        return this.name;
    }

    void setName(String name){
        this.name = name;
    }
    // private 접근권한을 갖는 필드의 클래스 안에 메소드가 있다.
    // Getter, Setter은 권한을 갖는다. 그래서 읽거나 수정이 가능하다.
}

class main{
    public static void main(string[] args){
        People Man = new People();

        Man.setName("홍박사");
        Man.getName();
    }
}
```