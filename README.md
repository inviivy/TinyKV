# 介绍

文件结构
todo: crc32
+时间戳(8字节)+value长度总和(8字节)+节点数量(8字节)+最小key(8字节)+最大key(8字节)+布隆过滤器(8*1024/8)+节点数量x(8字节的k(这里不一定是8,依赖于k的类型)和8字节的offset)+所有的value+


LSM每一层的timestamp应该依赖于它的上一层?或者依赖于当前的时间戳计数?
因为各个文件的[min, max]不会重叠, 所以貌似用当前的时间戳技术也没关系?因为对于下一层的每一个文件,一定不会和之前的存在重复.
现在需要处理的问题是: 如果上一层和下一层的key相同, 那么下一层的key丢弃, 上一层的key保留. 用什么保证呢? 但是貌似可以不适用时间戳?直接使用layer信息即可
如果不是用时间戳, 那么同一层之间的sst就没法分辨了, 所以还是得使用时间戳.



# reference
+ [smhasher](https://github.com/aappleby/smhasher)
+ []()