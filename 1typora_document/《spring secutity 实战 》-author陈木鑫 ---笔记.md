《spring secutity 实战 》-author陈木鑫 ---笔记



# 章2 表单认证



1 . WebSecurityConfigurerAdapter

验证范围
表单验证
http验证 ：通过请求的Authorization属性进行验证

- HttpSecurity 为特定的HTTP请求配置安全策略

successHandler()方法 登陆成功后的处理逻辑
failureHandler() 登陆失败后处理逻辑

# 章3 认证与授权

1.ANT模式的URL匹配器，



2.基于内存的多用户支持

403 用户授权失败
401 认证失败


3. 自定义用户验证
SecurityConfiguration extends WebSecurityConfigurerAdapter
    configure方法上注入UserDetailsService
  UserDetailsService是用户认证的具体实现，如果有验证通过，返回该用户UserDetails；没通过抛异常。
    ClientUserDetails impl UserDetails 用户的用户名、账号密码、用户角色信息，


4. permitAll()之后的是要验证的
.permitAll()
                // 除上面外的所有请求全部需要鉴权认证
                .anyRequest().authenticated();

permitAll()之前不需要验证
.antMatchers(
        "/swagger-ui.html",
        "/swagger-ui/*",
        "/swagger-resources/**",
        "/v2/api-docs",
        "/v3/api-docs",
        "/webjars/**",
        "/actuator/**",
        "/druid/**"
).permitAll()
# ch4 图形验证码



# ch10 单点登录
如果是不同域名，请求的时候不会发送cookie


===============================

5。

10. 单机session管理


=======极客时间
1.基于授权码模式：
1）请求授权服务器，输入账号密码到授权服务器，获取授权码
2）拿到授权码，然后输入授权码、登陆凭证、请求范围、重定向地址，再次请求授权服务器。授权服务器认证通过返回token
3）带着token访问资源服务器

2.lab2中的流程
1）请求资源服务器，输入用户名密码（使用spring security验证）。
2）---》请求成功，--》进入到 1.基于授权码模式 流程。 
用代码封装了之前手动请求授权服务器的流程。
他把access_token和access_token过期时间存在了数据库。
第一次没有access_token的时候去， 获取如下authEndpoint url // 这里会弹出一个弹框,验证第三方授权服务器
http://localhost:8080/oauth/authorize?scope=read_userinfo&response_type=code&redirect_uri=http%3A%2F%2Flocalhost%3A9001%2Fcallback&client_id=clientapp
会去请求授权服务器,
然后输入第三方授权服务器的用户名和密码进行授权--》选择是否同意授权--》同意后回调到资源服务器
3）授权成功后，访问本地资源