scw: swooleframework框架 阉割版
----
* 全栈框架，提供了数据库操作，模板，Cache，日志，队列，上传管理，用户管理等几乎所有的功能
 
> PHP版本需求： PHP5.4/PHP5.5/PHP5.6/PHP7.0/PHP7.1，不支持PHP5.3

应用服务器
-----
使用内置应用服务器，可节省每次请求代码来的额外消耗。连接池技术可以很好的帮助存储系统节省连接资源。

### Swoole应用服务器支持的特性
* 热部署，代码更新后即刻生效。依赖runkit扩展（ <https://github.com/zenovich/runkit> ）
* MaxRequest进程回收机制，防止内存泄露
* 支持使用Windows作为开发环境
* http KeepAlive，可节省tcp connect带来的开销
* 静态文件缓存，节省流量
* 支持Gzip压缩，节省流量
* 支持MySQL重新连接
* 支持文件上传
* 支持POST大文本
* 支持Session/Cookie
* 支持Http/FastCGI两种协议

### scw应用服务器，需要安装swoole扩展。
```
pecl install swoole
然后修改php.ini加入extension=swoole.so
```

### Nginx URLRewrite配置

```
server {
    listen  80;
    server_name  www.scw.com;
    root  /data/www/www.scw.com;

    location / {
        if (!-e $request_filename){
            proxy_pass http://127.0.0.1:9501;
        }
    }
}
```

###启动server
```
php swc/server/app_server start
```
###访问控制器

```
www.scw.com/page/index
访问的是apps/controllers/Page/index
apps/templates 需要加权限
剩下的自由发挥
```


