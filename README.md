## frontend blank project

### How to build

initial build

```
$ mvn compile
```

build with only gulp

```
$ ./helper-scripts/gulp build
```

run server

```
$ ./helper-scripts/gulp server
```

### Packaging as jar

create jar

```
$ mvm package
```

You can use jar like  [webjars](http://www.webjars.org/)

#### With Servlet3

> With any Servlet 3 compatible container, the WebJars that are in the WEB-INF/lib directory are automatically made available as static resources. This works because anything in a META-INF/resources directory in a JAR in WEB-INF/lib is automatically exposed as a static resource.

Then simply reference the resource like:
```
<link rel='stylesheet' href='css/app.css'>
```

### With Spring MVC

> Then configure Spring to map requests for /webjars to the /META-INF/resources/webjars directory of all the JARs in the CLASSPATH. This can be done either via XML config:

```
<mvc:resources mapping="/frontend/**" location="classpath:/META-INF/resources/"/>
```
or

```
@Configuration
@EnableWebMvc
public class WebConfig extends WebMvcConfigurerAdapter {

  @Override
  public void addResourceHandlers(ResourceHandlerRegistry registry) {
    registry.addResourceHandler("/frontend/**").addResourceLocations("classpath:/META-INF/resources/");
  }

}
```