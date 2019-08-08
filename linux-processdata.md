
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
