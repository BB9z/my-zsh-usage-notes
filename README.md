# zsh 使用笔记

## Parameter Expansion `#{参数扩展}`

以下部分场景花括号可省略，但为了统一，建议全部使用花括号。

```zsh
var="Hello, World"

# 计算长度
echo ${#var}        # "12"

# 删除从头开始的最短匹配
echo ${var#*o}      # ", World"

# 删除从头开始的最长匹配
echo ${var##*o}     # "rld"

# 删除从尾开始的最短匹配
echo ${var%o*}      # "Hello, W"

# 删除从尾开始的最长匹配
echo ${var%%o*}     # "Hell"
```

变换字符串：

```zsh
# 替换字符串（第一个匹配）
echo ${var/Hello/Goodbye}  # "Goodbye, World"

# 替换全部匹配
echo ${var//o/" * "}  # "Hell * , W * rld"

# 转为大写
echo ${var:u}       # "HELLO, WORLD"

# 转为小写
echo ${var:l}       # "hello, world"
```

截取字符串：

```zsh
# 正向截取
echo ${var:0:5}     # "Hello"
echo ${var:3}       # "lo, World"

# 从尾开始截取
echo ${var: -5:5}   # "World"
echo ${var: -5}     # "World"
echo ${var: -5:1}   # "W"

# 双向截取
echo ${var:3:-2}    # "lo, Wor"
```

路径相关（花括号可省略）：

```zsh
file="./README.md"

# 目录部分
$file:h     # .

# 扩展名，不含点
$file:e     # md

# 文件名
$file:t     # README.md

# 文件名，不含扩展名
$file:r     # ./README
$file:t:r   # README

# 绝对路径
$file:a     # /Users/BB9z/github/my-zsh-usage-notes/README.md

# 可联合
$file:a:h   # /Users/BB9z/github/my-zsh-usage-notes
$file:h:a   # /Users/BB9z/github/my-zsh-usage-notes
```

## Arithmetic Expansion `$((算术扩展))`

可以使用 `$((expression))` 语法进行算术运算：

```zsh
var=5
echo $((var * 2))  # Outputs: 10

echo $(( (5 + 2) * 3 ))  # Outputs: 21
```
