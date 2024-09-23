# se-invigilaton

将docker-compose脚本整合到项目仓库中统一维护，但提取出独立的mysql密码/token私钥/第三方应用私钥等敏感信息到独立配置文件(.env)，并忽略版本控制单独单独传输，避免泄露生产环境敏感信息。

应用由nginx:1.25/openjdk:21/mysql:8三个容器运行支撑。  
目录结构：  
mysql  
- data，容器运行数据挂载目录   

nginx    
- html，前端编译结果    
- templates，配置文件。docker nginx提供原生脚本自动读取配置并覆盖到default.conf配置    

openjdk，后端编译jar包   
.env，放置敏感信息，此文件不应泄露  
docker-compose.yaml，容器统一编排脚本  

### docker-compose.yaml

mysql服务配置：仅内部访问无需暴露的容器内端口；时区；挂载目录；启动时自动创建数据库；注入root密码；通过healthcheck校验mysql容器启动情况等。 

openjdk服务配置：启动依赖mysql启动情况；仅内部访问无需暴露的容器内端口；挂载目录；时区；注入的连接mysql服务账号密码；执行带运行环境参数命令等。

nginx服务配置：绑定并暴露到宿主机端口；挂载应用目录；挂载配置目录等。