# 设置npm镜像

#### 1、设置淘宝镜像 cnpm

```
npm config set registry https://registry.npm.taobao.org
```

#### 2、设置npm 官方镜像 

```
npm config set registry https://registry.npmjs.org
```

#### 3、使用nrm包管理

官网:[nrm][nrm]

[nrm]: https://www.npmjs.com/package/nrm	"nrm"



# 如何更新本地安装的包

定期更新你的应用所依赖的包（package）是个好习惯。因为依赖包的开发者更新了代码，你的应用也就能够获得提升。

为了完成这个任务需要：

1. 在 package.json 文件所在的目录中执行`npm update` 命令。

2. 执行 `npm outdated` 命令。不应该有任何输出。

   