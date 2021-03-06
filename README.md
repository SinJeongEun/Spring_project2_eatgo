
- # @Transactional
    - update시에는 save를 명시적으로 하지않고 @transactional 사용
    - transaction 범위를 잡아주는 동시에 이 범위에서 처리가 벗어났을 때 DB에 내용 적용됨

- # @Pathvariable 
   - 파라미터에 사용하면 URI의 일부를 변수로 전달
- # @RequestBody
    - 어노테이션을 이용하면 HTTP 요청 몸체를 자바 객체로 전달받을 수 있다.

- # LOMBOK

    - ##  @Builder

      - 객체를 만들어 줄때 의미가 잘 들어나도록 코드 변경 가능

        ```java
        Restaurant restaurant1 = Restaurant.builder();
              .id(1004L)
                    .name("JOCKER House")
                    .address("Seoul")
                    .build();
        ```

- # Validation

- ## @Valid 

  - controller에서 사용됨

    ```java
    public RestaurantEntity<?>create(@Valid @RequestBody Restaurant resource)
    ```

    

- ## @NotNull

- ## @NotEmpty

- ## @Size(max =10)



- # 에러처리

  - ## @ControllerAdvice

  - ## @ExceptionHandler

    - @ExceptionHandler(RestaurantNotFOundException.class)
    - ```java
      public class RestaurantNotFoundException extends RuntimeException {

            public RestaurantNotFoundException(Long id) {
                super("Could not find restaurant " + id);
            }
        }
        ```

  - ## @ResponseStatus

    - @ResponseStatus(HttpStatus.NOT_FOUND)

  - ## @ResponseBody
      -  자바 객체를 HTTP 응답 몸체로 전송할 수 있다.   

  - ## ServiceTest에서 에러처리 적용법

    - ``` java
      @Test(expected = RestaurantNotFOundException.class)
      ```

   

   - ## Service에서 에러처리 적용법

      - ```
        Restaurant restaurant = restaurantRepository.findById(id)
        .orElseThrow( ()-> new RestaurantNotFoundException(id));
        ```

- ## 메뉴 관리

  - ## @Transient
     - JPA에 포함된 어노테이션
     - 영속 대상에서 제외

  - ## @JsonInclude

    - @JsonInclude(JsonInclude.Include.NON_DEFAULT)  : 해당 필드가 null이면 나타내지 않음
    
- # 프로젝트 분리

    - ## common-api

      - ```java
        //build.gradle
        //gradle로 테스트 실행
        jar{
            enabled = true
        }
        bootjar{
            enabled = false
        }
        ```



    -  ## admin-api

      - ``` java
        dependencies{
        implementation project(': datgo-commom')
        }
        ```



    - ## customer -api

      - ```java
        dependencies{
        implementation project(': datgo-commom')
        }
        ```





