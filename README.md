# zsh 使用笔记

## Parameter Expansion `#{参数扩展}`

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

## Arithmetic Expansion `$((算术扩展))`

可以使用 `$((expression))` 语法进行算术运算：

```zsh
var=5
echo $((var * 2))  # Outputs: 10

echo $(( (5 + 2) * 3 ))  # Outputs: 21
```
