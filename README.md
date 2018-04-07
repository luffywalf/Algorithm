#### Algorithm

###### EdmodKarp for max flow 

  1.利用BFS得到一条src->sink的路径（就是看谁先啦）即增广路径（其实就是普通的能够到达sink的路径）同时要得到增量（增广路径边上的最小值）
  2.对上面的增广路径中的每一条边，改变其正向反向边的capacity with increasement，并sumflow += increasement;
  3.重复1，2直到不再有增广路径，即可得到最大流sumflow
  
  上面每一条增广路径都是走流量的边
  
  

###### Dijkstra最短路径 
http://wangkuiwu.github.io/2013/04/14/dijkstra-c/
原理greedy 最终找到原点到其他各点的最短路径，不能解决带有负值的边

本子上有我的过程图。晚上总结

代码请不要放在这里啦，晚上弄


###### BellmanFord 最短路径
https://www.youtube.com/watch?v=obWXjtg0L64


###### max flow with min cost
果然循序渐进很重要啊，分别弄清楚maxflow and min cost 然后合体瞬间就懂了嘛，之前还弄了那么久。。。真是。。。

就是求max flow 当中 每次求增广路径的步骤换成求最短路径。其他估计都一样。



















