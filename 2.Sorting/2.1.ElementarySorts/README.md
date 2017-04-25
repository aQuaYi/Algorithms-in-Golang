# 目录

## 笔记
书上图2.1.3只显示了交换过程，没有显示比较过程，我的[希尔排序详细轨迹](./ShellSortExample/main.go)两者都有。

## 插入排序
插入排序的关键步骤是
```go
for i:=1;i<n;i++{
    for j:=i;j>0;j--{
        if a[j-1]>a[j]{
            a[j-1],a[j]=a[j],a[j-1]
        }
    }
}
```
在每一个i的循环结束以后，实现了a中的前i+1个元素是按照从小到达的顺序排列的。
插入排序最大的问题是，当a的顺序特别乱的时候，交换的次数特别多。最坏的情况是，当最小值在a的末尾时，最后一个j的循环，每次都要交换。
希尔排序可以解决插入排序交换次数特别多的问题。

## 希尔排序
希尔排序的关键步骤是
```go
n := len(a)
h := 1
hFactor := 3 //h的获取因子，可以是别的正整数， hFactor>=2
for h < n/hFactor { //获取h的值
	h = hFactor*h + 1
}

for h >= 1 { //以下是排序循环
	for i := h; i < n; i++ {
		for j := i; j >= h; j -= h {
			if a[j-h] > a[j] {
				a[j-h], a[j] = a[j], a[j-h]
			}
			count++
		}
	}
	h = h / hFactor
}
```

猛地一看，希尔排序比插入排序多了层for循环，这样会带来更多运算，事实却并非如此。从我的[对"ZYXWVUTSRQPONMLKJIHGFEDCBA"排序](./ShellSortExample-Z2A/main.go)可以看到，在排序初期，头部的Z经过4次交换就到达了尾部，同样的，尾部的A经过4次交换也到达了头部，而不是25次。随着h的减小，各个字母都能很快达到自己所在位置的附近。当h减小为1时，最后一次的ij循环实际上就是一次插入排序，只是此时的序列已经是基本上排序好的了，所以j循环很快就能完成。*总之，排序初期的远距离元素交换位置，是希尔排序快的原因*。详细说明，还可以查看基维百科上的[希尔排序](https://zh.wikipedia.org/wiki/%E5%B8%8C%E5%B0%94%E6%8E%92%E5%BA%8F)
另外，关于获取h的问题，只要在排序循环中，h会终止于1，那么都可以完成排序。上面的h的取值方式，只是在实践中效果较好的取值方式而已。


## 练习解答
* [ ] [2.1.1](./2.1.1/main.go)
* [ ] [2.1.2](./2.1.2/main.go)
* [ ] [2.1.3](./2.1.3/main.go)
* [ ] [2.1.4](./2.1.4/main.go)
* [ ] [2.1.5](./2.1.5/main.go)
* [ ] [2.1.6](./2.1.6/main.go)
* [ ] [2.1.7](./2.1.7/main.go)
* [ ] [2.1.8](./2.1.8/main.go)
* [ ] [2.1.9](./2.1.9/main.go)
* [ ] [2.1.10](./2.1.10/main.go)
* [ ] [2.1.11](./2.1.11/main.go)
* [ ] [2.1.12](./2.1.12/main.go)
* [ ] [2.1.13](./2.1.13/main.go)
* [ ] [2.1.14](./2.1.14/main.go)
* [ ] [2.1.15](./2.1.15/main.go)
* [ ] [2.1.16](./2.1.16/main.go)
* [ ] [2.1.17](./2.1.17/main.go)
* [ ] [2.1.18](./2.1.18/main.go)
* [ ] [2.1.19](./2.1.19/main.go)
* [ ] [2.1.20](./2.1.20/main.go)
* [ ] [2.1.21](./2.1.21/main.go)
* [ ] [2.1.22](./2.1.22/main.go)
* [ ] [2.1.23](./2.1.23/main.go)
* [ ] [2.1.24](./2.1.24/main.go)
* [ ] [2.1.25](./2.1.25/main.go)
* [ ] [2.1.26](./2.1.26/main.go)
* [ ] [2.1.27](./2.1.27/main.go)
* [ ] [2.1.28](./2.1.28/main.go)
* [ ] [2.1.29](./2.1.29/main.go)
* [ ] [2.1.30](./2.1.30/main.go)
* [ ] [2.1.31](./2.1.31/main.go)
* [ ] [2.1.32](./2.1.32/main.go)
* [ ] [2.1.33](./2.1.33/main.go)
* [ ] [2.1.34](./2.1.34/main.go)
* [ ] [2.1.35](./2.1.35/main.go)
* [ ] [2.1.36](./2.1.36/main.go)
* [ ] [2.1.37](./2.1.37/main.go)
* [ ] [2.1.38](./2.1.38/main.go)