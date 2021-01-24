---
title: vscode的python开发插件集设定
layout: post
---

### __工作空间设定__
1. 打开vscode的“settings”，workspace是针对单个项目的设置
选择空间设置：
![截图](/assets/vscode的python开发插件集设定/Selection_002.png)
2. 设置json
```
{
    "window.zoomLevel": 0.7, // 窗口缩放等级
    "editor.fontSize": 14,
    "editor.lineHeight": 15,
    "terminal.integrated.fontSize": 14, // terminal 字体大小
    // "editor.formatOnSave": true, // 存档时，是否格式化
    "files.autoSave": "onFocusChange", // 自动保存
    "python.pythonPath": "/home/zhouyang/anaconda3/envs/multimedia-manager/bin/python", // 选择指定的python解释器
    // "python.venvPath": "/home/zhouyang/anaconda3/envs",
    "python.terminal.activateEnvironment": true, // 自动启动虚拟环境
    "python.linting.pylintPath": "/home/zhouyang/anaconda3/envs/multimedia-manager/bin/pylint", // 指定pylint
    "python.linting.pylintEnabled": true,  // 需要安装pylint
    "python.linting.enabled": true,  // 需要

    "extensions.ignoreRecommendations": true, // 显示推荐的插件
    "files.encoding": "utf8", // 指定字符编码
    "files.trimTrailingWhitespace": true, // 保存时，会删除每行后面多余的空格
    "files.autoGuessEncoding": false, // 是否猜测文件编码
    "terminal.integrated.shell.linux": "/usr/bin/bash", // 选择指定shell
    "workbench.welcome.enabled": false, // 关闭 vscode 欢迎画面
    "workbench.startupEditor": "newUntitledFile",
    "explorer.confirmDelete": false,

    // "workbench.colorTheme": "One Dark Pro", // 选择颜色主题，需要去安装颜色主题插件
    // "workbench.iconTheme": "vscode-icons",  // 选择图标主题，需要去安装图标主题插件
}
```
3. 在项目的根目录里创建.env文件，添加项目里要用到的环境变量
在.env中加入PYTHONPATH变量，定义python模块的根路径
```
PYTHONPATH=./src
```
设定后，pylint就会吧src看作python根模块，从src目录开始检查代码。不会报模块导入错误。

4. 设定launch.json
```
{
    // Use IntelliSense to learn about possible attributes.
    // Hover to view descriptions of existing attributes.
    // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "name": "devolop env",
            "type": "python",
            "request": "launch",
            "cwd":"${workspaceFolder}/src", // 进入src目录
            "program": "run.py",            // 执行run.py文件
            "console": "integratedTerminal"
        }
    ]
}
```
