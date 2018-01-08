# Algorithm


# EdmodKarp for max flow 

  1.利用BFS得到一条src->sink的路径（就是看谁先啦）即增广路径（其实就是普通的能够到达sink的路径）同时要得到增量（增广路径边上的最小值）
  2.对上面的增广路径中的每一条边，改变其正向反向边的capacity with increasement，并sumflow += increasement;
  3.重复1，2直到不再有增广路径，即可得到最大流sumflow
  
  上面每一条增广路径都是走流量的边
  
  

# Dijkstra最短路径 
http://wangkuiwu.github.io/2013/04/14/dijkstra-c/
原理greedy 最终找到原点到其他各点的最短路径，不能解决带有负值的边

本子上有我的过程图。晚上总结

/*
     * Dijkstra最短路径。
     * 即，统计图中"顶点vs"到其它各个顶点的最短路径。
     *
     * 参数说明：
     *       vs -- 起始顶点(start vertex)。即计算"顶点vs"到其它顶点的最短路径。
     *     prev -- 前驱顶点数组。即，prev[i]的值是"顶点vs"到"顶点i"的最短路径所经历的全部顶点中，位于"顶点i"之前的那个顶点。U
     *     dist -- 长度数组。即，dist[i]是"顶点vs"到"顶点i"的最短路径的长度。S
     */
    public void dijkstra(int vs, int[] prev, int[] dist) {
        // default false
        boolean[] flag = new boolean[mVexs.length];
        int[][] path;
        //D(0)
        //dist[vs] = 0;
        flag[vs] = true;
        int now = vs;
        for(int i = 0; i < prev.length; i++) prev[i] = INF;
        while(!areAllTrue(flag)){
            int minIndex = 0;
            int minValue = INF;
            for (int i = 0  ; i < flag.length; i++){
                if(!flag[i]){
                    if (prev[i] > dist[now] + mMatrix[now][i]){
                        prev[i] = dist[now] + mMatrix[now][i];
                    }
                    if(prev[i] < minValue){
                        minIndex = i;
                        minValue = prev[i];
                    }
                }
            }
            dist[minIndex] = minValue;
            now = minIndex;
            flag[minIndex] = true;
        }
        // 打印dijkstra最短路径的结果
        System.out.printf("dijkstra(%c): \n", mVexs[vs]);
        for (int i=0; i < mVexs.length; i++)
            System.out.printf("  shortest(%c, %c)=%d\n", mVexs[vs], mVexs[i], dist[i]);
    }

# BellmanFord 最短路径
https://www.youtube.com/watch?v=obWXjtg0L64

public void bellmanFord(int vs, int[] prev, int[] dist) {
        for(int i = 0; i < dist.length; i++) dist[i] = INF;
        dist[vs] = 0;
        //遍历V-1
        for(int k = 1; k <= mVexs.length - 1; k++) {
            //每次要遍历所有的边
            for(int i=0;i<mVexs.length;i++) {
                for (int j = 0; j < mVexs.length; j++) {
                    if (mMatrix[i][j] != INF) {
                        //if(dis[v[i]]>dis[u[i]]+w[i]) 这种更新方式 是因为它是以边来存储，以边判断点，所以这样写方便啦
                        if (dist[i] + mMatrix[i][j] < dist[j]) {
                            dist[j] = dist[i] + mMatrix[i][j];
                        }
                    }
                }
            }
        }
        // 打印bellmanFord最短路径的结果
        System.out.printf("bellmanFord(%c): \n", mVexs[vs]);
        for (int i=0; i < mVexs.length; i++)
            System.out.printf("  shortest(%c, %c)=%d\n", mVexs[vs], mVexs[i], dist[i]);

    }






















