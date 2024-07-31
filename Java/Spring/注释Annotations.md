###### @Primary
- @Primary注解用于标记一个bean为首选bean。当Spring容器中存在多个相同类型的bean时，使用@Primary可以指定默认的bean。这样在注入依赖时，如果没有明确指定bean，Spring会使用被标记为@Primary的bean。
- 在下面的例子中，如果有一个依赖MyService的bean，Spring会默认注入ServiceB，因为它被标记为@Primary
```java
@Component
public class ServiceA implements MyService {
    // ...
}

@Component
@Primary
public class ServiceB implements MyService {
    // ...
}
```
###### @Qualifier
- 在这个例子中，@Qualifier("serviceA")指定了ServiceA作为要注入的MyService的实现。
```java
@Component
public class MyComponent {

    private final MyService myService;

    @Autowired
    public MyComponent(@Qualifier("serviceA") MyService myService) {
        this.myService = myService;
    }
}
```
- @Qualifier 的优先级高于 @Primary
```java
@Component
@Primary
public class ServiceA implements MyService {
    // ...
}

@Component
public class ServiceB implements MyService {
    // ...
}

@Component
public class MyComponent {

    private final MyService myService;

    @Autowired
    public MyComponent(@Qualifier("serviceB") MyService myService) {
        this.myService = myService;
    }
}
```