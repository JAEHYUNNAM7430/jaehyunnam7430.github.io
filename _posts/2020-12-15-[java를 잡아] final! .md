## FINAL

안녕하세요. ! MONKEY.D 입니다 :-) 

요즘 너무 길이 길고 복잡한 것 같아 가독성이 떨어지는 것 같아 오늘은 쉬운 주제를 포스팅 해보려 합니다!

**FINAL ?  이란 무엇일까요?**

***

자바에서는 추상이 상속을 강제하는 것이라면 final은 상속과 변경을 금지하는 규제입니다. 이 정도로 간단히 기억해두고 저를 따라오시죠!

```java
package org_opentutorials.javatutorials.eclipse;
 
class Calculator {
    static final double PI = 3.14;
 
    public void setOprands() {
       1번 //Calculator.PI = 6;
    }
 
   
}
 
public class Helloworld {
 
    public static void main(String[] args) {
 
        Calculator c1 = new Calculator();
        System.out.println(c1.PI);
        2번 //Calculator.PI = 10;
 
    }
}
```

static 변수 앞에 final이 붙어있는 것을 주목해주세요. 그리고 1번과 2번에 Calculator.PI를 통해서 클래스 변수 PI의 값을 변경하려고 하면 어떻게 될까요? 오류가 납니다. 이유는 final로 지정된 변수에는 한번 값이 할당되면 그 값을 바꿀 수 없기 때문입니다.

상수가 변하지 않는 값이라고 배운 기억이 날 것입니다. 그리고 위의 PI 예제는 변하지 않을 값입니다. 수학에서 PI는 3.14xxx..라고 고정값입니다. PI가 3.14 말고 다른숫자가 있나요? (있다고하면 몽키킥!!) 없습니다! 때문에 변하면 안되는 고정 값을 가져야 합니다. 이런 값은 변수 앞에 final을 붙여서 이 값이 변경되는 것을 규제할 수 있습니다. 이러한 특징은 <u>클래스 변수</u>의 예를 들었지만 <u>인스턴스 변수, 클래스, 메소드에도 적용된다는 점</u> 꼭 알아두세요! 

<u>**※ 참고로 static은 되도록이면 사용하지 않는 것이 좋다고 합니다. '악'이라고도 하며 객체지향적이지 못하다고 합니다. 오늘은 여기까지 포스팅하며 글 마치도록 하겠습니다.! :)**</u>

