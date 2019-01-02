下载 `Visual Studio Code.app`，然后放在 Application 文件夹里面。
就可以在 LaunchPad 里面看到 VS Code。

打开 VS Code，打开控制面板（`⇧⌘P`）,输入 `‘shell command’`，在提示里看到 `Shell Command: Install 'code' command in PATH`，运行它就可以了。

或者手动把下面的配置添加在 `.bash_profile` 文件里：

```bash
export PATH="\$PATH:/Applications/Visual Studio Code.app/Contents/Resources/app/bin"
```

之后就可以在终端中输入 `code .`，使用 VS Code 打开当前文件夹。
或者直接使用 `code filename` 编辑文件。
参考链接： https://code.visualstudio.com/docs/setup/mac
