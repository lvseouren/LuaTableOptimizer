# LuaTableOptimizer
---

原项目 https://github.com/lujian101/LuaTableOptimizer

### 改动
* 修改了metatable的生成方式，现在是以深度作为依据构建metatable，原配置表中的每个深度对应一个metatable（如果需要的话）。此外，对于数组类型的table不会设置metatable
* 移除了本地化相关功能
* 调整了序列化的格式

#### 定义
* 深度：指的是一个访问table中的元素需要的.操作符的次数，比如
```
{
	k11 = 1,
	k12 =
	{
		k21 = 2,
	}
}
```
其中k11和k12属于深度1，而k21属于深度2

* 数组类型的table：指的是满足以下条件的table
1. key为正整数
2. key为1对应的元素存在
3. 当key为i的元素存在时，key为i-1的元素也存在
