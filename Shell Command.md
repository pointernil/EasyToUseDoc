# Shell 常用指令

## 1. 匹配文件内容
```bash
# 在.xml中，找到带有string的行
find ./*.xml | xargs grep -wn --color <string>
```