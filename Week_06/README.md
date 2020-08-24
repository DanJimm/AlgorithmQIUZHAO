学习笔记
week 6
实现各种排序算法的代码放在py文件，随时check和回顾

布隆过滤器
初步的判定一个元素是否存在list中
class BloomFilter:
    def __init__(self,size,hash_num):
        # 初始化传参，分别需要传入二进制列表的大小和hash分布数量两个参数
        self.size = size
        self.hash_num = hash_num
        # 初始化二进制列表
        self.bit_array = bitarray(size)
        self.bit_array.setall(0)
    def add(self,s):
        for seed in range(self.hash_num):
            result = mmh3(seed,s) % self.size
            self.bit_array[result] = 1
    def lookup(self,s):
        for seed in range(self.hash_num):
            if self.bit_array[mmh3(seed,s) % self.size] == 0:return 'Nope'
        return 'Probably'
bf = BloomFilter(10,3)
bf.add('hello')
bf.add('world')
print(bf.lookup('hello'))
print(bf.lookup('bye'))


实现LRU Cache：
from collections import OrderedDict
class LRUCache(object):
    def __init__(self,capacity):
        # 初始化存储字典
        self.dict = OrderedDict()
        # remain是最大存储长度
        self.remain = capacity
    def get(self, key):
        if not key in self.dict:
            return -1
        # 把对应的值取出来，然后还需要存回dict开头
        result = self.dict.pop(key)
        self.dict[key] = result
        return result
    def put(self, key, value):
        if key in self.dict:
            self.dict.pop(key)
        else:
            if self.remain > 0:
                self.remain -= 1
            else:
                # 先弹出最早添加的元素，然后再加入
                self.dict.popitem(last=False)
        self.dict[key] = value
