The spring framework is a framework designed using P.O.O and inversion of control. In order to do this, they created the `ApplicationContext`. This is responsible for creating, configuring and assembling your services and all kind of stuff during your spring application lifetime. They can be configured through XML, Annotations or both. These implementations are called `AnnotationConfigApplicationContext` and `ClassPathXmlApplicationContext`. The most common way is using `Java-based configuration`. This kind of metadata configuration uses java classes to configure your application context.
## Beans
The metadata defines the objects the context will manage for you. These objects are called beans. These beans are represented as `BeansDefinitions` inside the context. They will have:
- Package-Qualified class name.
- Behavioral configuration, like lifecycle, scope and so forth.
- Dependencies.
- Other configurations.
In order to create a class that configures beans, you should do something like it:
```java
@Configuration
public class AppConfig {

	@Bean
	public MyServiceImpl myService() {
		return new MyServiceImpl();
	}
}
```
Every method annotated with `@Bean` will generate an object that will be managed by the ApplicationContext.