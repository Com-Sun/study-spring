# 처음 해보는 스프링 프로젝트

학습목표: 스프링을 이용해서 간단한 프로그램을 만들어 본다.

### Java파일을 이용한 프로젝트 실행

스프링: 컨테이너 안에 객체를 모아둔다. 메모리로딩시 스프링 컨테이너라는 큰 그릇에 필요한 객체들을 생성해놓고, 필요할 때마다 객체를 빼와서 사용. 스프링에서는 이 객체를 '빈'이라고 명명함.

빈: 스프링에서 객체를 지시하는 용어

applicationContext.xml: 스프링컨테이너에서 빈(객체)를 만들어 주는 녀석.

먼저, 스프링을 사용하지 않은 순수 자바 파일을 예시로 들어보자.

**MainClass.java**

	package testPjt02;
	
	public class MainClass {
	
		public static void main(String[] args) {
			TransportationWalk transportationWalk = new TransportationWalk();
			transportationWalk.move();
	
		}
	
	}

new 키워드를 이용해 객체를 생성했다.

**TransportationWalk.java**

	package testPjt02;
	
	public class TransportationWalk {
	
		public void move() {
			System.out.println("도보로 이동 합니다.");
		}
	}

위의 소스코드를 보면, 직접 메인 메소드에 다음과 같은 코드를 추가했다. 

			TransportationWalk transportationWalk = new TransportationWalk();
			transportationWalk.move();

그런데, 스프링을 사용해서 .xml파일을 사용하는 경우를 보자.

### spring project

**applicationContext.xml**

	<bean id="tWalk" class="testPjt02.TransportationWalk" />
	
class: 사용하려는 패키지,클래스를 동일하게 입력한다.

위와같이 .xml파일에 빈을 생성하면 메인메소드에서 new를 이용하여 객체를 생성하지 않더라도, applicationContext.xml이 객체를 생성한다(메모리의 스프링 컨테이너라는 부분에 로드).

직접 사용해보자.

		GenericXmlApplicationContext ctx = 
				new GenericXmlApplicationContext("classpath:applicationContext.xml");
				

자바 클래스파일에서 .xml파일에 접근
		
		TransportationWalk transportationWalk = ctx.getBean("tWalk", TransportationWalk.class);
		transportationWalk.move();
		
		ctx.close();

객체를 사용하고 난 뒤에 close