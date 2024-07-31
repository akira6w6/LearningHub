## 创建自定义Exception，继承自已有Exception

- 创建一个自定义异常类 

```java
public class MyCustomException extends IllegalStateException {
    // 无参构造函数
    public MyCustomException() {
        super();
    }

    // 仅带错误消息的构造函数
    public MyCustomException(String message) {
        super(message);
    }

    // 带错误消息和原因的构造函数
    public MyCustomException(String message, Throwable cause) {
        super(message, cause);
    }

    // 仅带原因的构造函数
    public MyCustomException(Throwable cause) {
        super(cause);
    }

    // 可选：重写toString方法，提供自定义的异常消息格式
    @Override
    public String toString() {
        return "MyCustomException: " + getMessage();
    }
}
```

- 使用自定义异常

```java
public class Main {
    public static void main(String[] args) {
        try {
            // 模拟抛出自定义异常
            throw new MyCustomException("Something went wrong!");
        } catch (MyCustomException e) {
            // 捕获自定义异常并打印消息
            System.out.println(e);
        }
    }
}

```