- 직렬화란
    - 자바 내부에서 사용하는 객체를 외부에서도 데이터를 읽을수 있게(byte)형태로 변환하는 기술입니다.
- 역직렬화란?
    - 직렬화로 바뀐 데이터를 다시 객체로 바꾸는 기술입니다.
- 직렬화를 사용하는 이유는 단순히 객체를 저장 및 복원하는 것이 아니라, 다양한 자바 서비스 간 객체 정보를 유기적으로 공유할 수도 있습니다.
- 직렬화를 주로 어디에 사용하는가?
    - JVM의 메모리에만 상주되어 있는 객체 데이터를 그대로 영속화(persist)가 필요할 때 사용됩니다.
    - 시스템이 종료되더라도 없어지지 않는 장점을 가지며 영속화된 데이터이기 때문에 네트워크로 전송도 가능합니다.
    - 그리고 필요할 때 직렬화 된 객체 데이터를 가져와서 역직렬화하여 객체를 바로 사용할 수 있게 됩니다.

```java
public class Product extends BaseEntity implements Serializable {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long productId;

    private String productName;

    private String productPrice;
```

```java
		@Cacheable(value = "product")
    public Product findProductById(Long productId) {
        return productRepository.addViewCnt(productId);
    }
```
