##一点前言
- GC的各种算法本质上是由3种基本的算法组合优化来的，即Mark-Sweep标记清除算法、引用计数法和GC复制算法。
- 今天主要学习下Mark-Sweep标记清除算法。

##最基本的Mark-Sweep标记清除算法

- 标记清除算法由标记阶段和清除阶段组成，标记阶段会将当前仍然活跃的对象的mark字段标记为true(数据结构一般是stack)。清除阶段则是遍历所有的对象列表(数据结构一般为队列，链表等)，判断mark为true则将nark置false，mark为false则将该对象加入free链表，用作后续的内存使用。
- 伪码实现：

```
mark_sweep(){
	mark_phase()
	sweep_phase()
}
```

- 标记阶段

```
mark_phase(){
	for(r:&roots){
		mark(*r)
	}
}

mark(obj){
	if(obj.mark == false){
		obj.mark = true
		for(child:children(obj)){
			mark(child)
		}
	}
}
```

-  清除阶段

```
sweep_phase(){
	sweepObj = &heap_start
	while(sweepObj < heap_end){
		if(sweepObj.mark == true){
			sweepObj.mark = false
		}else{
			sweepObj.next = &freeList
			&freeList = sweepObj
		}
		
		sweepObj += sweepObj.size
	}
}
```

##算法的优缺点和对应的改进方法

to be continued