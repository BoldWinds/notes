# Linux常用指令

## 文件相关

### 复制

```bash
mv [source] [destination]
```

### 解压缩

```bash
tar -xvf FileName.tar
tar -cvf FileName.tar DirName
```



## 网络相关

### 查看端口占用情况

```bash
lsof -i :[port]
# or
sudo netstat -tuln | grep [port]
```

## 进程相关

### 后台运行

将任务后台挂起

```bash
nohup [command]  &
```

查看该任务的输出

```bash
cat nohup.out
```

查看后台任务的pid并kill

```bash
pgrep -f "[command]"
kill [pid]
```



## 用户与组

### 创建用户

```bash
useradd 选项 用户名
```

### 设置用户的shell为zsh

