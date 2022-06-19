# Multi main entrance
很多文件具有main入口，最好的办法就是将其move到一个个目录中。
1. 到某个目录
2. 创建子目录
```
ls *.go | awk -F '.' '{print $1}' | sed 's/_/-/g' | xargs mkdir $1
```
3. 移动文件
```
ls *.go > /tmp/1 && ls *.go | awk -F '.' '{print $1}' | sed 's/_/-/g' > /tmp/2 && paste /tmp/1 /tmp/2 | awk '{print "mv " $1 " " $2}'
```