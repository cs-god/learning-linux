

echo

```bash
echo 'Hello world!'
echo -e #支持转义符
#echo "Hello world!"错误
```

### 基础知识

##### 脚本执行

```bash
#第一种方法
chmod 755 hello.sh
./hello.sh
#第二种方法
bash ./hello.sh
```

##### DOS脚本转Bash脚本

```linux
dos2u
```



#### 变量

##### set（查询所有变量，包括环境变量）

##### 环境变量

###### source(等价于.)

功能：强制让当前配置文件生效（更改配置文件后需要重启才能生效，而该命令让配置文件直接生效）



### 输入输出重定向

#### 输出重定向

```bash
#第种：命令 > 文件		以覆盖的方式重定向

#第种：命令 >> 文件	以追加的方式重定向

#第种：命令 &>>文件	将正确输出和错误输出以追加的方式重定向

#第种：命令 >> 文件1 2>>文件2	将正确结果重定向至文件1，错误结果重定向至文件2 
```

#### 输入重定向



### 条件判断

#### 按文件类型判断

| 参数 |          功能          |
| :--: | :--------------------: |
|  -e  |    判断文件是否存在    |
|  -d  |        判断文件        |
|  -f  | 判断文件是否是普通文件 |

