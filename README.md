
# @Transactional
+ update시에는 save를 명시적으로 하지않고 @transactional 사용
+transaction 범위를 잡아주는 동시에 이 범위에서 처리가 벗어났을 때 DB에 내용 적용됨

# LOMBOK

- ##  @Builder

  - 객체를 만들어 줄때 의미가 잘 들어나도록 코드 변경 가능

    ```java
    Restaurant restaurant1 = Restaurant.builder();
          .id(1004L)
                .name("JOCKER House")
                .address("Seoul")
                .build();
    ```



