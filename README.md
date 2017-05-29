## GA_engine
=========
   


一个采用遗传算法利用多个三角形拟合图片的工具



### Usage
usage: GAengine [-h] [-t TARGET] [-o FOLDER] [-n TRIANGLE_NUM] [-l LOOP] [-p RESULT_NAME]    

### 主要算法
有两个思路:    
1. 计算一个群体(个数大于2),然后在繁衍中有选择,交叉,变异的过程。其中选择的过程是直接筛选掉一部分,然后将最优秀的群体复制一份(维持群体数量并且模拟拥有优秀的基因的个体有更大的机会将自己的基因遗传给后代)    
2. 只有两个个体,parent和child,child复制parent的基因,做一定的mutate,然后进行筛选,既然只有两个,那么就是一个who can who up的节奏了。参考了 [ROGER ALSING WEBLOG](http://rogeralsing.com/2008/12/07/genetic-programming-evolution-of-mona-lisa/)所用算法    


### GA_engine.py
面向了对象(之前的demo都是面向过程...),发现部分数据可以复用,所以速度更快,结合变异率,在一代parent和child中,可以复用的量其实相当多。————多亏了python的引用

### TODO !!!
1.考虑多边形,以及多边形的数量(目前可选且固定,无法变化)     
2.变异规律的变化,现在太单一,变异率也太大了点     
3.取点密度,目前取256乘256除以4个点    
4.支持多种分辨率......之前测试的都是256乘256的,没有试过其他的    
5.alpha?透明度的随机大小的合适值    
6.速度!速度!太慢了! 因为速度慢,放弃了很多...准备试试go,都是纯计算...在合成图片用了pillow(PIL)的接口alpha_composite最费时,试过用[numpy](http://stackoverflow.com/questions/3374878/with-the-python-imaging-library-pil-how-does-one-compose-an-image-with-an-alp)实现的这个接口,不过更慢了...
