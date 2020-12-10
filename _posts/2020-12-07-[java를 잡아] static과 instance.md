# static은 나의 분신술 :)

저는 자바를 공부하면서 처음에 `STATIC`은 되게 어렵게 느껴졌습니다. 

때문에 과거를 회상하며 `STATIC`에 대해 간단한 설명을 해보려고 합니다!

`static`은 나의 분신술이라고 써있는 제목을 왜??  라고 생각을 할수도 있을 것 같습니다. 

저만의 이해법, 공부법이니 깊게 들어가지 마시고 이해를 위해서 비유를 들기 위해서이니 이해만 해주시면 되겠습니다!

그림으로 표현한 사진으로 설명을 해보겠습니다. class NARUTO를 만들어 주고 그 안에 2개의 변수를 만들었습니다.



![KakaoTalk_20201209_013238993_01](https://user-images.githubusercontent.com/74045426/101512667-9d444a80-39be-11eb-95d1-db0887c6153f.jpg)

1번 static이 붙어있는 classVar 변수

2번 static이 붙어있지 않은 instanceVar 변수 

즉, 1번은 static이 붙어있기 때문에 클래스소속이고 2번은 static이 붙어 있지 않기 때문에 인스턴스 소속입니다.

이 그림을 코드화합니다.

```java
class NARUTO {
    public static String classVar = "I Class"; // 1번 클래스 소속인 classVar 변수
    public String instanceVar = "I instance var"; //2번 인스턴스 소속인 instatnceVar 변수
}
public static void main(string[] args){
    System.out.println(NARUTO.classVar);
    System.out.println(NARUTO.instanceVar);
}
```

자 이해를 하기 위해 테스트를 한번 해봅시다! 제가 여기서 궁금한 것은 **<u>클래스</u>** NARUTO 를 통해서 classVar에는 접근이 되나 또 클래스를 통해서 instanceVar에는 접근이 되나 테스트를 하면

과연 둘다 접근이 가능할까요???



{: .notice--success}

정답은? 클래스를 통해서는 classVar에만 접근이 됩니다.



둘다 접근이 된다고 했으면 <u>**몽키킥!!**</u>  실행을 해보면 

`System.out.println(NARUTO.instanceVar)`  이 코드에서는 인스턴스 변수에는 클래스가 접근을 할수 없으니 오류가 발생하여 실행이 되지 않습니다. 때문에 이것을 주석처리를 합니다. 실행해보면 I class가 출력이 됩니다. 

왜 그럴까요?  클래스를 통해서는 당연히 클래스 변수에는 접근이 되지만, instanceVar는 에러가 납니다. 즉 인스턴스는 인스턴스를 통해서 사용하도록 고안된 변수입니다.

그다음에는 **static 메소드와 instance 메소드를 만들어 볼 것입니다!** 사진속 그림을 보며 이해를 해봅시다.

![KakaoTalk_20201209_013238993](https://user-images.githubusercontent.com/74045426/101512659-9b7a8700-39be-11eb-92aa-306a0505e4d7.jpg)

자 이 그림을 코드화 시키면

```java
class NARUTO {
    public static String classVar = "I Class"; 
    public String instanceVar = "I instance var";
    
    public static void classMethod() {  //static 메소드 추가
        System.out.println(classVar); // 1.클래스 소속인 classMethod 안에서 클래스 소속인 classVar에 ※접근가능
      //  System.out.println(instanceVar); // 2.클래스 소속인 classMethod 안에서 인스턴스 소속인 instanceVar에 ※접근불가 오류처리 난다. 때문에 주석 처리
    } 
    public void instanceMethod(){ //인스턴스 소속인 메소드 추가
        System.out.println(classVar); // 3.인스턴스 소속인 instanceMethod안에서 클래스 소속인 classVar에 ※접근가능
        System.out.println(instanceVar); // 4.인스턴스 소속인 instanceMethod안에서 인스턴스 소속인 instanceVar에 ※접근가능
    } 
    
}
public static void main(string[] args){
    System.out.println(NARUTO.classVar);
 //   System.out.println(NARUTO.instanceVar); // 오류로 주석처리
}
```



**<u>※</u>** <- 표시에 있는 접근목록을 잘 확인 해주세요. 

2번을 보면 `classmethod`는 `static`으로 <u>클래스소속</u>인 메소드 입니다. 때문에 instanceVar 변수에는 접근이 불가능합니다.

3번을 보면 `instancemethod`는 <u>인스턴스 소속</u>인 메소드 이지만 클래스 소속인 classVar 변수에는 접근이 가능합니다.



{: .notice--success}

이 테스트를 보며 우리가 파악 할 수 있는 것은 

클래스는 클래스소속인 변수와 메소드에 접근이 가능하다. 

인스터스는 클래스 소속, 인스턴스 소속 변수와 메소드에 둘다 접근이 가능하다. 입니다. 



확실히 이해를 돕기위해서 다음으로는 호출을 해보겠습니다. 

```java
class NARUTO {
    public static String classVar = "I Class"; // 1번 클래스 소속인 classVar 변수
    public String instanceVar = "I instance var"; //2번 인스턴스 소속인 instatnceVar 변수
    
    public static void classMethod() {  //static 메소드 추가
        System.out.println(classVar); // 1.클래스 소속인 classMethod 안에서 클래스 소속인 classVar에 ※접근가능
      //  System.out.println(instanceVar); // 2.클래스 소속인 classMethod 안에서 인스턴스 소속인 instanceVar에 ※접근불가 오류처리 난다. 때문에 주석 처리
    } 
    public void instanceMethod(){ //인스턴스 소속인 메소드 추가
        System.out.println(classVar); // 3.인스턴스 소속인 instanceMethod안에서 클래스 소속인 classVar에 ※접근가능
        System.out.println(instanceVar); // 4.인스턴스 소속인 instanceMethod안에서 인스턴스 소속인 instanceVar에 ※접근가능
    } 
    
}
```



{: .notice--warning} 

코드가 너무 길어져 혼란을 가중할 수 있기에 main 메소드를 따로 분리하였습니다.

```java
public static void main(string[] args){
    System.out.println(NARUTO.classVar)
 //   System.out.println(NARUTO.instanceVar) // 오류로 주석처리
       NARUTO.classMethod(); //1번 --> naruto클래스의 classMethod는 호출이 된다.
     //NARUTO.instanceMethod(); //2번 --> naruto클래스의 instanceMethod는 호출이 되지 않는다. 즉 오류구문이기에 주석처리를 해주며 이 구문은 인스턴스 소속이기 때문에 인스턴스로 접근만 허용을 한다. 클래스를 통해서 접근은 금지되어 있는 것입니다.
    
}
```

1번의 주석처리 설명을 읽어보면 NARUTO 클래스에 **클래스소속**인 classMethod()에 호출은 가능하지만

2번의 주석처리 설명을 읽어보면 instanceMethod에는 접근이 **<u>불가능</u>** 합니다.  NARUTO클래스 안에 있는 메소드 이지만 **인스턴스** ***<u>소속 </u>***이기 때문에 **인스턴스로만 접근이 허용이됩니다.**

때문에 인스턴스를 생성해서 테스트를 해봅시다!

```java
public static void main(string[] args){
    System.out.println(NARUTO.classVar)
 //   System.out.println(NARUTO.instanceVar) // 
       NARUTO.classMethod();
     //NARUTO.instanceMethod(); //
     
       NARUTO f1 = new NARUTO(); // 인스턴스 f1 생성
}
```

이렇게 f1이라는 인스턴스를 생성해주면 사진의 그림을 보면서 설명을 하겠습니다.

![KakaoTalk_20201209_013238993_02](https://user-images.githubusercontent.com/74045426/101512670-9ddce100-39be-11eb-8ef4-0bb876320441.jpg)

f1이라는 인스턴스를 생성해주면 인스턴스는 NARUTO 클래스를 원형으로 하기 때문에 f1인스턴스는 생성될 때 클래스의 여러가지 멤버들을 참조, 복제해옵니다.

즉 NARUTO 클래스에 있는 `static String classVar="I class"`는 클래스의 소속이기 때문에 인스턴스에서 <u>***※복제는 하지 않고 링킹하여 참조합니다.***</u> 때문에 클래스에 있는 classVar의 변수의 값이 달라지면 인스턴스에서도 값이 변합니다. 

<u>또한!!</u> f1 인스턴스에서도 classVar의 값이 변한다면 NARUTO 클래스에서도 classVar의 값이 변하게 됩니다. (링킹되어 있으니까 서로에게 영향!)

하지만 NARUTO 클래스에 있는 <u>인스턴스 변수</u>인 `String instanceVar="I instance"`는 f1인스턴스에 참조하는 것이 아니라 **<u>그대로 복제해오는 것</u>**입니다. 그래서 f1 인스턴스에 있는 instanceVar 변수와 클래스에 있는 instanceVar는 <u>서로 링크되어 있지 않기 때문에 값이 변경되어도 서로 무관합니다.</u>



메소드들도 동일하게 이해하면 되겠습니다. 이처럼 설명이 길었지만 머릿속에 제가 그린 그림을 가지고 있다면 이해는 충분히 가실거라고 믿습니다. 오늘도 긴 글 읽어주셔서 감사합니다! 항상 공부하면서 저만의 방법을 쉽게 풀어서 설명하겠습니다!! :)

