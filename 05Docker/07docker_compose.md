# docker compose

docker compse 语法： https://docs.docker.com/reference/compose-file/

顶级元素

- name 名字
- services 服务
- networks 网络
- volumes 卷
- configs 配置
- secrets 密钥

新建 compose.yaml

```yaml
name: myblog
services: 
  mysql: 
    container_name: mysql
    image: mysql:8.0
    ports:
      - "3306:3306"
    environment:
      - MYSQL_ROOT_PASSWORD=root
      - MYSQL_DATABASE=wordpress
    volumes:
      - mysql-data:/var/lib/mysql
      - /app/myconf:/etc/mysql/conf.d
    restart: always
    networks:
      - blog

  wordpress:
    image: wordpress
    ports:
      - "8080:80"
    environment:
      WORDPRESS_DB_HOST: mysql
      WORDPRESS_DB_USER: root
      WORDPRESS_DB_PASSWORD: 123456
      WORDPRESS_DB_NAME: wordpress
    volumes:
      - wordpress:/var/www/html
    restart: always
    networks:
      - blog
    depends_on:
      - mysql

volumes:
  mysql-data:
  wordpress:

networks:
  blog:
```

执行 ` docker compose up -d`  将自动部署应用

常用命令如下：

```shell
# 上线
docker compose up -d

# 下线
docker compose down

# 启动
docker compose start x1 x2 x3

# 停止
docker compose stop x1 x3

# 扩容
docker compose scale x2=3
```

