# 安装

https://github.com/tporadowski/redis/releases

1. 将 Redis 设置为 windows 服务
   `redis-server --service-install redis.windows-service.conf --loglevel verbose`
2. 启动 Windows Redis 服务
   右键点击我的电脑->管理->服务和应用程序->服务->Redis->启动

# 常用的 redis 服务命令

卸载服务：`redis-server --service-uninstall`
开启服务：`redis-server --service-start`
停止服务：`redis-server --service-stop`

# 错误处理

1. Could not connect to Redis at 127.0.0.1:6379: 由于目标计算机积极拒绝，无法连接。
   原因：未启动 Redis 服务
2. 中文乱码
   `redis-cli --raw`
