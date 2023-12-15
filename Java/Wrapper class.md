# Wrapper class
자바에서는 이런식으로 기본형과 참조형으로 선언할 수 있다.    

모든 자료형을 객체로 생성할 순 없다. ```int```형이나 ```float```등등      
하지만 기본형으로 사용하는 변수를 참조형으로 사용할 필요가 있을때가 있다. 
메소드로 객체를 필요로 한다면 기본타입 데이터를 사용하지 못한다.     

이럴때 기본 타입들을 객체로 변환시키는데 wrapper class가 필요하다.       

```java
Integer num1 = new Integer(5);
Integer num1 = 5;

Double num2 = new Double(1.11);
Double num2 = 1.11;
```

wrapper class는 ```int```나 ```char```를 ```Integer```, ```Character```로 풀네임으로 써야한다.

# 박싱과 언박싱
박싱은 기본형을 참조형으로, 언박싱은 참조형을 기본형으로 바꾸는것을 말한다.    
박싱한 변수는 wrapper class에서 연산을 할 수 없다. 생성된 인스턴스의 값을 참조만 하기 때문에 직접 언박싱을 한 후에 값을 바꾸고, 다시 박싱을 해야한다.     
물론 참조형이기때문에 값을 비교하려면 ```==``` 대신 ```equals()```를 쓰는게 맞다.

언박싱할때에는 ```<Type>+Value()```로 언박싱을 하면 된다.    
```java
Integer num = new Integer(20);  // 박싱
int n = num.intValue(); // 언박싱
n = n+2;
num = new Integer(n);   // 다시 박싱
```

# AutoBoxing, UnBoxing
JDK 1.5부터는 자동으로 박싱 작업을 자동을 해준다.
```java
Integer a = 1;
int n = a;
```
```Integer```을 사용하면 자동으로 ```new``` 키워드를 사용해서 자동으로 박싱을 해주고, 연산을 한다면 자동으로 언박싱과 박싱을 해준다.

```java
Integer a = 1;
Integer b = 2;
Integer r = a + b;
a  = r;
```