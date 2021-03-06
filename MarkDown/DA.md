### 1. 决策树

通过以往经验的总结对后续问题结果的演算

主要构成：根节点、子节点、叶节点

##### 1. 构建

1. 根节点属性的选择。
2. 子节点属性的选择
3. 何时停止取得目标状态叶节点

##### 2. 裁剪

​	如果去掉多余的属性判断同样可以得到较好的结果，可以进行剪枝。

​	过多的属性判断或者样本数量较少都可能产生过拟合，导致模型的泛化能力差。

​	构建决策树主要基于纯度，纯度越高则信息熵越低，反之亦然

##### 3. 纯度：尽量使目标变量的分歧最小

1. 信息增益（ID3算法）

   + 指的是由划分可以带来纯度的提高信息熵的减少，由父亲节点的信息熵减去所有子节点的信息熵

   + $$
     (增益)Gain(D,a) = Entropy(D) - \sum_{i=1}^{k}(\frac{|Di|}{|D|})Entropy(Di)
     $$ { Di/D 代表子节点占父节点的次数,假如D为天气，D1为晴(一次去，两次不去)，D2为阴(三次去两次不去),D3为小雨(两次不去，一次去)}

     

   + 公式中 D 是父亲节点，Di 是子节点，Gain(D,a) 中的 a 作为 D 节点的属性选择。

   + 缺点，一定概率下会将对任务分类没有太多作用的属性选为最有属性

2. 信息增益率（C4.5）

   + 由信息增益比上分裂信息度量(指一个属性分裂的广度和均匀)

   + 样例集合被属性A分割为c个样例子集Si
   
   + $$
  (分裂信息度量)SplitInfoMation(S,A)=-\sum_{i=1}^{c}(\frac{Si}{S})log_2(\frac{Si}{S})
     $$

3. 基尼指数（CART算法）
   + 可以生成分类树或者回归树，只支持二叉树
   
   + 分类树：处理离散数据，输出样本的类别，比如工种
   
   + 回归树：处理连续数据，输出数值，比如样本的年龄
   
   + 基尼指数越小说明样本越稳定，公式表示节点t属于类别C<sub>k</sub>的概率,值为1减去各类别C<sub>k</sub>的概率
   
   + $$
     (基尼指数)GINI(t)=1-\sum_k{[P(C_k|t)]^2}
     $$
   
   + 节点被属性划分为两个节点，则节点的基尼指数为子节点的归一化基尼指数之和

##### 4. 信息熵：代表了信息的不确定度

+ $$
  (熵)Entropy(t) = -\sum_{i=0}^{c-1} P(i|t)log_2P(i|t)
  $$

+ P(i|t) 代表节点 t 为 i 的概率
+ 如：六次决策，一次成功，五次失败
  
  + Entropy = - ( 1/6 ) * log<sub>2</sub> (1/6) -  ( 5/6 ) * log<sub>2</sub> (5/6) = 0.65