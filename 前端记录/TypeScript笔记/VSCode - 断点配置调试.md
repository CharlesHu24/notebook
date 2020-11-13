# VSCode - 断点配置调试

## 配置步骤

### 第一步: 准备要调试的ts文件

### 第二步: 添加调试配置

- 修改配置内容

```json
{
  // 使用 IntelliSense 了解相关属性。 
  // 悬停以查看现有属性的描述。
  // 欲了解更多信息，请访问: https://go.microsoft.com/fwlink/?linkid=830387
  "version": "0.2.0",
  "configurations": [
    {
      "type": "node",
      "request": "launch",
      "name": "启动程序",
      // ts-node 命令: “直接”运行ts代码
      // 作用: 调试时加载ts-node包(在调试时“直接”运行ts代码)
      "runtimeArgs": ["-r", "ts-node/register"],
      // 此处的 04-循环判断.ts 表示要调试的 TS 文件
      "args": ["${workspaceFolder}/04-循环判断.ts"]
    }
  ]
}
```



### 第三步: 安装调试用到的包

- 在当前目录中，打开终端， 输入以下命令

```
# 注意: 原来通过 -g (全局) 安装的包，在调试时不生效，需要在当前目录中单独安装
# 调试TS代码，依赖这两个包

npm i ts-node typescript
```



## 调试技巧

- 监视变量的值( 1鼠标移入 2**添加到左侧监视窗口**)