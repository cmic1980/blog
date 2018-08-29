---
title: Spring Boot 自动加载组件 （@ComponentScan注解）
date: 2015-07-29 20:35:28
tags:
---
## @ComponentScan注解

一个类被Spring自动加载到Bean容器里面需要2个条件：
1. 这个类需要被@Component或它的子类注释为组件，@Component的常用子类有@Service, @Repository, @Controll，@Configuration 等。
2. 通过ComponentScan注释指定这些注解标识的类包名。

**注：** 
SpringBoot项目都在使用的@SpringBootApplication是一个组合注解，主要组合了@Configuration .+@EnableAutoConfiguration.+@ComponentScan， 它的默认的扫描规则是同包或者其子包的下的注解组件。

    @Target({ElementType.TYPE})
    @Retention(RetentionPolicy.RUNTIME)
    @Documented
    @Inherited
    @SpringBootConfiguration
    @EnableAutoConfiguration
    @ComponentScan(
        excludeFilters = {@Filter(
            type = FilterType.CUSTOM,
            classes = {TypeExcludeFilter.class}
        ), @Filter(
            type = FilterType.CUSTOM,
            classes = {AutoConfigurationExcludeFilter.class}
        )}
    )
    public @interface SpringBootApplication {
        ...
    }


@ComponentScan使用例子：

    // 扫描com.cmic.web 下的Controller组件
    @ComponentScan(basePackages = { "com.cmic.web" })
    // 扫描com.cmic.service 下的Service组件
    @ComponentScan(basePackages = { "com.cmic.service" }) 
    // 扫描com.cmic 下的 Controller、Service以及其他组件
    @ComponentScan(basePackages = { "com.cmic" }) 