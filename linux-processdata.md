
### 使用`file`命令查看文件类型
```
file HelloWorld.txt
```
Result:
>> HelloWorld.txt: ASCII text, with no line terminators

### 使用`ls -lh`命令详细显示当前目录中文件信息
```
ls -lh
```
Result:
>> total 4.0K  
 -rw-rw-r-- 1 azureuser azureuser 12 Aug  8 09:06 HelloWorld.txt

### 使用`more`命令显示文本内容
```
more neural-tts.txt
```

### 使用`wc`统计字数
```
wc neural-tts.txt
```

Result:
>>  9   9 362 neural-tts.txt

结果解释为9行362个字符。

### 使用`head -n`显示前n行数据
```
head -n 5 neural-tts.txt
```

### 使用`tail -n`显示后n行数据
```
head -n 1 neural-tts.txt
```

### 使用`more`,`head`,`tail`组合来输出第2行数据
```
more neural-tts.txt | head -n 2 | tail -n 1
```

### 使用`cat`拼接多个文件(纵向拼接）
```
cat HelloWorld.txt neural-tts.txt
```

### 使用`paste`拼接多个文件(横向拼接)
```
paste HelloWorld.txt neural-tts.txt
```

### 使用`grep`在文件中进行查找匹配
```
grep "speech" neural-tts.txt
```

在多个文件中搜索
```
grep "speech" neural-tts.txt HelloWorld.txt
```

使用`-l`参数只列出包含匹配字符串的文件名
```
grep -l "speech" neural-tts.txt
```

使用`-c`参数统计匹配字符串在文件中出现的次数
```
grep -c "speech" neural-tts.txt
```

使用`-i`参数设置查找忽略大小写
```
grep -i "O" neural-tts.txt
```

使用`-v`输出没有匹配上的行

**使用正则表达式规则查找日志文件**
查找以Nov 10开始的日志行
```
grep "^Nov 10" messages
```
查找以terminating.结尾的日志行
```
grep "terminating.$" messages
```

### 使用`awk`命令打印部分列到屏幕
```
awk "{print $2}" 3.txt
```

### 使用`history`命令查看以前输入过的命令
```
history
```
使用个管道|查找对`ls`命令的使用记录
```
history | grep "ls"
```

### 使用`&`符号让命令在后台运行 （当前命令不阻塞后续命令执行），适用于没有数据依赖的命令

```
cppcheck.sh &
churn.sh &
run.sh &

wait
echo "All 3 complete"
```

### 使用`xargs`组合管道`|`将前一个命令的输出作为后一个命令的输入
下载文件中所列出的文件
```
cat url-list.txt | xargs wget -c
```

查找系统中的jpg文件，并压缩
```
find / -name *.jpg -type f -print | xargs tar -cvzf images.tar.gz
```

查找系统中的jpg文件，并拷贝
```
ls *.jpg | xargs -nl -i cp {} /external-hard-drive/directory
```
