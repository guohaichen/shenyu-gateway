我在使用shenyu时，接触到一些模块并记录；
- ShenyuAdminBootstrap: 管理控制后台
- ShenyuBootstrapApplication: 网关


客户端注册时，配置文件分析，以 `shenyu-examples-http`，注册中心`nacos`为例
```yaml
server:
  #注意，这里的端口是这是服务端口，注册中心的服务实例端口不是这个端口
  port: 8189

shenyu:
  #注意，这里并非指的是注册中心，而是指的是数据同步，也就是代理请求的具体缓存，例如服务实例，方法名称，参数之类的。
  # 在Apache ShenYu version 2.6.1, ShenYu注册中心只支持http类型，中间件注册类型已经被移除。
  register:
    registerType: http
    serverLists: http://localhost:9095
    props:
      #username和password指的是管理后台的用户名和密码
      username: xxx
      password: xxx
  #接下来就是
  client:
    http:
      props:
        #这里的port也就是服务注册中心的端口，而非上文的sever.port
        port: xxx
  #注册中心配置
  discovery:
    enable: ture
    type: nacos
    #服务定义名称
    registerPath: /shenyu/discovery/http_example
    props: 
      #nacos分组名称
      groupName:xxx
```
