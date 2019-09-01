> 本静态文档使用[mkdocs](https://www.mkdocs.org/)生成.

##### 常用命令
```
Commands

创建新项目: mkdocs new [dir-name] - Create a new project.
运行服务: mkdocs serve - Start the live-reloading docs server.
构建: mkdocs build /mkdocs build --clean :- Build the documentation site.
帮助: mkdocs help - Print this help message.
发布: mkdocs gh-deploy -c -b master
发布帮助: mkdocs gh-deploy --help
```
##### 项目布局
```
mkdocs.yml    # The configuration file.
    docs/
        index.md  # The documentation homepage.
        ...       # Other markdown pages, images and other files.
```

##### 写作
1. 新建md
2. mkdocs build
3. mkdocs gh-deploy