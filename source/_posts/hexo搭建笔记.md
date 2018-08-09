title: hexo+github搭建笔记
tags:
  - 随笔
  - 笔记
categories: []
toc: true
date: 2018-08-08 15:14:00
---
##### 下载软件
1. 下载[Node.js](https://nodejs.org)
2. 下载[git for windows](https://git-scm.com/download/win)
---
##### 注册Github并创建仓库
1. 注册[Github](https://github.com)帐号
2. 创建个人仓库
---
<!--more-->
##### 安装hexo
1. 运行node.js command promtp
2. 创建blog目录,cd 到这个目录
3. 输入npm install hexo -g 安装hexo
```
npm install hexo -g
```
4. 输入hexo -v，检查hexo是否安装成功
```
hexo -v
```
5. 输入hexo init，初始化该文件夹
```
hexo init
```
6. 输入npm install，安装所需要的组件
```
npm install
```
7. 输入hexo g，生成hexo
```
hexo go
```
8.  输入hexo s，开启服务器，即可利用本地体验hexo
```
hexo s
```
---
##### 配置git上传到github
1. 在blog目录点击Git Base Here
2. 设置自己的用户名和邮箱
```
git config --global user.name "checknao"
git config --global user.email "yx@yxsoft.co"
```
3. 创建ssh 输入ssh-keygen -t rsa -C “yx@yxsoft.co”，连续三个回车，生成密钥，最后得到了两个文件：id_rsa和id_rsa.pub（默认存储路径是：C:\Users\Administrator\.ssh）。
```
ssh-keygen -t rsa -C "yx@yxsoft.co"
```
4. 输入eval "$(ssh-agent -s)"，添加密钥到ssh-agent
```
eval "$(ssh-agent -s)"
```
5. 再输入ssh-add ~/.ssh/id_rsa，添加生成的SSH key到ssh-agent
```
ssh-add ~/.ssh/id_rsa
```
6. 登录Github，点击头像下的settings，将生成的shh添加进去
7. 输入ssh -T git@github.com，测试添加ssh是否成功。如果看到Hi后面是你的用户名，就说明成功了
```
ssh -T git@github.com
```
8. 配置Deployment，在blog文件夹根目录，找到_config.yml文件，修改repo值（在末尾）
```
deploy:
  type: git
  repository: git@github.com:checknao/yxsoft.git
  branch: master
```
9. 新建blog命令hexo new post "new blog"
```
hexo new post "new blog"
```
10. 安装git扩展 
```
npm install hexo-deployer-git --save
```
11. 生成并上传到github
```
hexo d -g
```
12. 如果配置了自己的域名,需要在source目录下创建CNAME文件,在里面保存自己的域名
---
##### 安装个性主题
1. 下载主题
```
git clone https://github.com/litten/hexo-theme-yilia
```
2. 配置blog根目录中的_config.yml文件
```
theme: yilia
```
3. 下载插件 
```
npm i hexo-generator-json-content --save
```
4. 在blog根目录_config.yml中加入下面的代码
```
jsonContent:
  meta: false
  pages: false
  posts:
    title: true
    date: true
    path: true
    text: true
    raw: false
    content: false
    slug: false
    updated: false
    comments: false
    link: false
    permalink: false
    excerpt: false
    categories: false
    tags: true
```