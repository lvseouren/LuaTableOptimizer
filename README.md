# LuaTableOptimizer
---

Simple readonly lua table optimizer
---

Lua Table 通常被用来存储游戏的配置数据，如果配置中有很多冗余重复的数据那么将占用较多的内存，严重影响加载速度

Lua table commonly use to store configuration data for games. it takes a lot of memory
if it contains many fields with same value. this optimization could improve memory usage
and loading speed.

### 改动
* 修改了metatable的生成方式，现在是以深度作为依据构建metatable，原配置表中的每个深度对应一个metatable（如果需要的话）
* 移除了本地化相关功能
* 调整了序列化的格式

#### 定义
* 深度：指的是一个访问table中的元素需要的.操作符的次数，比如
```
{
	k11 = 1,
	k12 = {
		k21 = 2,
	}
}
```
其中k11和k12属于深度1，而k21属于深度2


