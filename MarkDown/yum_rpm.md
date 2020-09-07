##### Yum 管理rpm包的包管理器

###### 选项

+ -h 帮助文档
+ -y 确认参数
+ -q 静默安装

###### 1. 列举包文件

- `yum list# 列出资源库中所有可以安装或更新的rpm包`
- `yum list perl* 列出资源库中特定的可以安装或更新以及已经安装的rpm包`
- `yum list updates 列出资源库中所有可以更新的rpm包`
- `yum list installed 列出已经安装的所有的rpm包`
- `yum list extras 列出已经安装的但是不包含在资源库中的rpm包(注:extras是repos.d中定义的资源列表名称)`

###### 2. 列举资源信息

- `yum info # 列出资源库中所有可以安装或更新的rpm包的信息`
- `yum info perl* # 列出资源库中特定的可以安装或更新以及已经安装的rpm包的信息`
- `yum info updates # 列出资源库中所有可以更新的rpm包的信息`
- `yum info installed # 列出已经安装的所有的rpm包的信息`

###### 3. 搜索

- `yum search perl # 搜索匹配特定字符的rpm包`
- `yum provides realplay # 搜索有包含特定文件名的rpm包`

###### 4. 管理包

- `yum install perl # 安装rpm包`
- `yum remove perl* # 删除rpm包,包括与该包有倚赖性的包`

###### 5. 软件组管理

- `yum groupinstall "Chinese Support" # 安装指定的组`
- `yum groupupdate "Chinese Support" # 安装了的组成员软件包更新`
- `yum grouplist "Chinese Support" # 安装了的组和可以安装的组一览显示`
- `yum groupremove "Chinese Support" # 删除指定的组`
- `yum groupinfo "Chinese Support" #指定组所包含的软件包显示`

###### 6. 更新

- `yum check-update # 检查可更新的rpm包`
- `yum update # 更新所有的rpm包`
- `yum update kernel kernel-source # 更新指定的rpm包,如更新kernel和kernel source`
- `yum upgrade # 大规模的版本升级,与yum update不同的是,连旧的淘汰的包也升级`

###### 7. 清空缓存

- `yum clean packages # 清除暂存中rpm包文件`
- `yum clearn headers # 清除暂存中rpm头文件`
- `yum clean oldheaders # 清除暂存中旧的rpm头文件`
- `yum clearn all # 清除暂存中旧的rpm头文件和包文件`

##### Rpm

###### 选项

+ --force 忽略软件包及文件的冲突

+ --nodeps 不检查依赖性关系

###### 1. 安装

+ rpm -i

###### 2. 查询

+ rpm -q

###### 3. 验证

+ rpm -V

###### 4. 删除

+ rpm -e

###### 5. 升级

+ rpm -U   

