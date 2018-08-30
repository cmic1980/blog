---
layout: componentscan
title: '@ComponentScan详解'
date: 2015-07-30 14:50:41
tags:
---



简单的说@ComponentScan主要作用指定一个或几个包，Spring在创建Bean容器后会自动扫描这些包下面的相关类并加载这些类到容器中。

### 指定扫描范围

我们通过设置@ComponentScan的参数指定Spring扫描范围，比如下面的代码Spring只会在"pro.caifu365"包内扫描。
```java
@ComponentScan(basePackages = {"pro.caifu365"})
public class Application implements CommandLineRunner {
    public static void main(String[] args) {
        SpringApplication.run(Application.class, args);
    }

    @Override
    public void run(String... args) throws Exception {

    }
}
```
大多时候@ComponentScan注解并不需要设置参数，那么这时的扫描范围则是@ComponentScan注解类同包或者其子包。


### @Component注释

并不是所有在被扫描的包中所有类都会被加入到Spring的Bean容器，只有被@Component注释的类才会被加载到Bean容器中。Spring中经常使用的@Controller，@Service，@Repository，@Configuration类都是@Component子类，所有使用这些注释的类会被加载到Bean容器中。

