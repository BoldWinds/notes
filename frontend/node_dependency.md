# 配置node依赖环境

(on ubuntu 20.04)

## 安装node.js, npm, nvm, pnpm
```bash
    sudo apt-get install node npm
```

使用nvm管理本地的多个node版本
```bash
    curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh | bash
```
如果curl或者wget拿不到install.sh，就直接浏览器访问，然后复制到本地执行

```bash
    wget https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh
    bash install.sh
```

之后重启终端，或者按照以下命令执行来立即使用nvm：
```bash
    export NVM_DIR="$HOME/.nvm"
    [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
    [ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
```

安装pnpm: 
```bash
    npm i -g pnpm
```
