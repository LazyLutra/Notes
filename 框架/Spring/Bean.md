# 作用域
## 概述
默认情况下，Spring应用上下文中所有Bean都是以单例模式(singleton)的形式创建。**也就是说，不管给定的一个Bean被注入到其他Bean多少次，每次所注入的都是同一个实例。** 

**缺陷**：有时候，你所使用的Bean是可变的(mutable)，它们会保持一些状态，因此重用是不安全的。因此，Spring定义了多种作用域。

## 多种作用域
 - 单例(singleton)：在整个应用中，只创建Bean的一个实例（后续的请求也会使用之前创建的对象）。
    - 优点
        - 减少新生成实例消耗
        - 减少jvm垃圾回收
        - 快速获取Bean（除了第一次生成以外，其余都是在缓存中获取）
    - 缺点
        - 线程不安全（多次请求共用一个实例）
 - 原型(prototype)：每次注入或者通过Spring应用上下文获取的时候，都会创建一个新的Bean实例。
 - 会话(session)：在Web应用中，为每个会话创建一个Bean实例。
 - 请求(rquest)：在Web应用中，为每个请求创建一个Bean实例。

## 单例和原型作用域配置方式
### **使用XML配置**
使用scope属性设置作用域。
``` java
<bean id = "test" class = "com.demo.Test" scope = "prototype">
 ```

### **使用注解配置**
在注解配置时，需要使用@Scope注解，有三种写法
 1. **使用组件扫描，发现并声明原型Bean**</br>
    ```java
    @Component
    @Scope(ConfigurableBeanFactory.SCOPE_PROTOTYPE)
    public class Test {}
    ```
 2. **Java配置，声明方法返回为原型Bean**
    ```java
    @Bean
    @Scope(ConfigurableBeanFactory.SCOPE_PROTOTYPE)
    public Test newTest {
        return Test;
    }
    ```

## 会话和请求作用域配置方式
### 