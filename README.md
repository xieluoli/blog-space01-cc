# blog.space01.cc

## 本地预览

### 方式 1: Python
```bash
python3 -m http.server 8000
```
打开 http://localhost:8000

### 方式 2: Node.js
```bash
npx serve .
```

### 方式 3: PHP
```bash
php -S localhost:8000
```

## 部署到服务器

### 静态托管 (Vercel / Netlify / GitHub Pages)
直接将项目目录连接到托管平台即可

### 自己的服务器 (Nginx) - blog.space01.cc
```nginx
server {
    listen 80;
    server_name blog.space01.cc;

    root /var/www/blog.space01.cc;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }

    gzip on;
    gzip_types text/html text/css application/javascript;
}
```

部署步骤：
```bash
# 1. 将项目目录复制到服务器
scp -r ./* user@your-server:/var/www/blog.space01.cc/

# 2. 配置 Nginx（如上）
# 3. 重启 Nginx
sudo nginx -t && sudo nginx -s reload
```

### Docker
```dockerfile
FROM nginx:alpine
COPY . /usr/share/nginx/html
```

```bash
docker build -t personal-site .
docker run -p 80:80 personal-site
```

## 添加新文章
1. 将新的 HTML 文件放入 `articles/` 目录
2. 在 `index.html` 中添加对应的链接
3. 将图片资源放入 `assets/` 目录
