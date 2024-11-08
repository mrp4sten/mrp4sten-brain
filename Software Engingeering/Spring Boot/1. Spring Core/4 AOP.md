Tags:
- [[Java]]
- [[0 Spring Boot]]

Spring AOP (Aspect-Oriented Programming) is a feature of the Spring Framework that allows developers to define certain behaviors (i.e., “aspects”) that cut across multiple classes, such as logging or transaction management. These behaviors, which are called “advices,” can be applied to specific “join points” (i.e., points in the execution of a program) in the application, using “pointcuts” to determine where the advices should be applied.

Spring AOP allows developers to separate the implementation of these cross-cutting concerns from the business logic of the application, making the code more modular and easier to understand. This can also make the application more flexible, since the same advices can be applied to different parts of the code without having to duplicate the code for the advices themselves.

### **Key Concepts in Spring AOP**

- **Aspect**: A module that encapsulates a concern that cuts across multiple classes. For example, a logging aspect might log method calls across the entire application.
- **Join Point**: A point in the execution of a program, such as a method call or field access, where an aspect can be applied.
- **Advice**: The action to be taken at a particular join point. This is the actual code that runs when the aspect is triggered. There are various types of advice, such as `before`, `after`, `around`, etc.
- **Pointcut**: An expression that matches join points. A pointcut defines where (in the code) and when (at which join points) advice should be applied.
- **Weaving**: The process of linking aspects with other application types or objects to create an advised object. Spring AOP uses **runtime weaving**, meaning aspects are woven at runtime rather than compile-time or load-time.
### **Types of Advice in Spring AOP**

- **Before Advice**: Executes before a method is invoked.
- **After Returning Advice**: Executes after a method successfully completes.
- **After Throwing Advice**: Executes if a method throws an exception.
- **After (Finally) Advice**: Executes after a method completes, regardless of its outcome (whether it throws an exception or not).
- **Around Advice**: Surrounds a method call, allowing you to perform actions both before and after the method execution. This is the most powerful type, as it can even control whether the method is executed at all.
### **Implementing AOP in Spring**

Spring AOP is configured using annotations, making it easy to set up and apply.

- **@Aspect**: Marks a class as an aspect.
- **@Before**: Defines a before advice.
- **@AfterReturning**: Defines an after-returning advice.
- **@AfterThrowing**: Defines an after-throwing advice.
- **@After**: Defines an after (finally) advice.
- **@Around**: Defines an around advice.
### **Example**
```java
import org.aspectj.lang.annotation.*;
import org.aspectj.lang.ProceedingJoinPoint;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.stereotype.Component;

@Aspect
@Component
public class LoggingAspect {

    private static final Logger logger = LoggerFactory.getLogger(LoggingAspect.class);

    // Pointcut for all methods in a service package
    @Pointcut("execution(* com.example.service.*.*(..))")
    private void serviceMethods() {}

    // Before advice
    @Before("serviceMethods()")
    public void logBefore() {
        logger.info("Method about to execute");
    }

    // After returning advice
    @AfterReturning("serviceMethods()")
    public void logAfterReturning() {
        logger.info("Method executed successfully");
    }

    // After throwing advice
    @AfterThrowing("serviceMethods()")
    public void logAfterThrowing() {
        logger.error("An exception occurred during method execution");
    }

    // Around advice
    @Around("serviceMethods()")
    public Object logAround(ProceedingJoinPoint joinPoint) throws Throwable {
        logger.info("Method start: " + joinPoint.getSignature().getName());
        Object result = joinPoint.proceed();
        logger.info("Method end: " + joinPoint.getSignature().getName());
        return result;
    }
}
```

- `@Aspect` declares `LoggingAspect` as an aspect.
- `@Pointcut` defines the join points where the aspect applies (in this case, all methods in `com.example.service`).
- `@Before`, `@AfterReturning`, `@AfterThrowing`, and `@Around` annotations specify different types of advice.
- The `logAround` method uses `ProceedingJoinPoint`, allowing it to execute code before and after the method and even control its execution.