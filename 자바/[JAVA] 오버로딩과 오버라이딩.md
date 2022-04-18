# 오버로딩과 오버라이딩의 차이

- 오버로딩
    - 이름은 같지만 시그니처(파라미터의 수, 데이터 타입) 는 다른 메소드로 중복선언하는것을 말한다.
- 오버로딩의 특징
    - 메소드 이름이 같아야한다.
    - 리턴형은 같아,달라 가능하다
    - 파라미터 개수가 달라야 한다.
    - 파라미터 개수가 같을 경우 데이터 타입이 달라야한다.
    
    ```java
    void test(){
    	System.out.println("매개변수 없음");
    }
    
    int test(int a,int b) {
    	System.out.println("매개변수"+a+"와 +"+b);
    }
    
    void test(double b,double a) {
    	System.out.println("매개변수"+b);
    }
    ```
    

- 오버라이딩
    - 부모 클래스의 메소드의 동작 방법을 변경하여 우선적으로 사용하는 것이다.
- 오버라이딩 특징
    - 오버라이드 하고자 하는 메소드가 상위 클래스에 존재해야한다.
    - 메소드 이름이 같아야한다.
    - 메소드 파라미터 개수, 마라미터의 자료형이 같아야한다.
    - 메소드 리턴형이 같아야 한다.
    - 상위 메소드와 동일 하거나 내용이 추가되어야한다.
    
    ```java
    public class People{
    	public String name;
    	public int age;
    	public void print(){
    		System.out.println("안녕");
    	}
    	
    }
    
    public class Student extesnds People {
    	String job;
    //오버라이딩
    	public void print(){
    		System.out.println("안녕");
    //추가된부분
    		System.out.println("추가");
    	}
    }
    ```
    

- 결론
- 오버로딩은 확장, 오버라이딩은 재정의 이다.
