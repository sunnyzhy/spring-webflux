# ReactiveFeign(响应式 Feign)

SpringBoot 使用 ReactiveFeign 的步骤如下:

1. 添加依赖
   ```xml
   <dependency>
      <groupId>com.playtika.reactivefeign</groupId>
      <artifactId>feign-reactor-cloud</artifactId>
   </dependency>
   <dependency>
      <groupId>com.playtika.reactivefeign</groupId>
      <artifactId>feign-reactor-spring-configuration</artifactId>
   </dependency>
   <dependency>
      <groupId>com.playtika.reactivefeign</groupId>
      <artifactId>feign-reactor-webclient</artifactId>
   </dependency>
   ```

2. 在启动类上添加注解
   ```java
   @EnableReactiveFeignClients
   ```

3. 定义 Feign 接口
   ```java
   @ReactiveFeignClient(value = "${feign.remote.application.uaa:spring-cloud-uaa}")
   public interface UaaFeign {
      @PostMapping(value = "/api/aut")
      Mono<ResponseEntityVo<UserTo>> aut(@RequestBody AutTo autTo);
   }
   ```

4. 业务模块的 Controller
   ```java
   @RestController
   @RequestMapping(value = "/api")
   public class ApiController {
      /**
      * AUT = Authentication，认证
      * @param autTo
      * @return
      */
      @PostMapping(value = "/aut")
      public Mono<ResponseEntityVo<UserTo>> aut(@RequestBody AutTo autTo) {
         return null;
      }
   }
   ```
