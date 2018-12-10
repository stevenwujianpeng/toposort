# 拓扑排序的算法实现详解

## 1.用下图的形式描述顶点之间 Arc 弧

```javascript
// First, we define our edges.
var graph = [
  ['put on your shoes', 'tie your shoes']
, ['put on your shirt', 'put on your jacket']
, ['put on your shorts', 'put on your jacket']
, ['put on your shorts', 'put on your shoes']
]
```

## 2.提取出所有的node（顶点，其实vertex更准确）


```javascript
function uniqueNodes(arr) {
    var res = new Set()
    for (var i = 0, len = arr.length; i < len; i++) {
        var edge = arr[i]
        res.add(edge[0])
        res.add(edge[1])
    }
    return Array.from(res)
}
```

## 3.生成顶点对应的散列表，将名称和序列号关联起来


```javascript
function makeNodesHash(arr) {
    var res = new Map()
    for (var i = 0, len = arr.length; i < len; i++) {
        res.set(arr[i], i)
    }
    return res
}
```

## 4.将顶点之间的依赖关系解析成map存储起来

```
// 伪代码    
{
    A -> [b,c]    
}
```

## 5.遍历node顶点，声明一个sortedArray [nodes.size], 倒置放node。用visited {}记录访问过的节点

```javascript
var sortedArray = [ , , , , , , ];

```
遍历节点：
当出现当前节点是其他节点的时候，就往下递归
```
graph LR
A-->B
A-->C
```

当出现当前节点不是任何节点的前置依赖的时候，就直接放置在sorted最后面，指针往前走一位
```
graph LR
A-->空
```

不断遍历和递归，最终完成整个拓扑排序的算法过程；
