# enum
하나의 변수에 특정된 값들만 들어가야만 할 때가 있다.     
예를 들어서 성별 변수에 남자, 여자만 들어갈수 있지 공격형헬리콥터를 넣으면 코드상에서는 에러가 발생하지 않아도, 나중에 여러 작업들을 할때 에러가 발생할 수도 있기 때문에 열거형인 ```enum```을 사용한다.

```java
public class EnumExample{
    public static final String MAN="MAN";
    public static final String WAMAN="WAMAN";

    public static void main(String[] args){
        String gender;

        gender = EnumExample.MAN;
        gender = EnumExample.WOMAN;

        gender = "공격형헬리콥터";
    }
    
}
```
저렇게 두가지의 값만 들어가야하는 ```gender```변수에 예상치 못한 변수가 들어갈 수도 있다.    
이럴때 enum을 사용하면 된다.

```java
public class EnumExample{
    public static final String MAN="MAN";
    public static final String WOMAN="WAMAN";

    public static void main(String[] args){
        Gender gender;

        gender = Gender.MAN;
        gender = Gender.WOMAN;

        // gender = "공격형헬리콥터"; 이젠 이 코드는 에러를 이르킵니다.
    }
}

enum Gender{
    MAN,
    WOMAN;
}
```
이렇게 열거형 enum을 사용하면 내가 원하는 값만 들어갈 수 있고, 만약 다른값이 들어가려고 하면 코드 자체에서 에러를 발생시켜준다.