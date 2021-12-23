# 1976. number-of-ways-to-arrive-at-destination | 到达目的地的方案数

## Question description

<!--If you want to use the English description, use <p>You are in a city that consists of <code>n</code> intersections numbered from <code>0</code> to <code>n - 1</code> with <strong>bi-directional</strong> roads between some intersections. The inputs are generated such that you can reach any intersection from any other intersection and that there is at most one road between any two intersections.</p>

<p>You are given an integer <code>n</code> and a 2D integer array <code>roads</code> where <code>roads[i] = [u<sub>i</sub>, v<sub>i</sub>, time<sub>i</sub>]</code> means that there is a road between intersections <code>u<sub>i</sub></code> and <code>v<sub>i</sub></code> that takes <code>time<sub>i</sub></code> minutes to travel. You want to know in how many ways you can travel from intersection <code>0</code> to intersection <code>n - 1</code> in the <strong>shortest amount of time</strong>.</p>

<p>Return <em>the <strong>number of ways</strong> you can arrive at your destination in the <strong>shortest amount of time</strong></em>. Since the answer may be large, return it <strong>modulo</strong> <code>10<sup>9</sup> + 7</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/07/17/graph2.png" style="width: 235px; height: 381px;" />
<pre>
<strong>Input:</strong> n = 7, roads = [[0,6,7],[0,1,2],[1,2,3],[1,3,3],[6,3,3],[3,5,1],[6,5,1],[2,5,1],[0,4,5],[4,6,2]]
<strong>Output:</strong> 4
<strong>Explanation:</strong> The shortest amount of time it takes to go from intersection 0 to intersection 6 is 7 minutes.
The four ways to get there in 7 minutes are:
- 0 ➝ 6
- 0 ➝ 4 ➝ 6
- 0 ➝ 1 ➝ 2 ➝ 5 ➝ 6
- 0 ➝ 1 ➝ 3 ➝ 5 ➝ 6
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 2, roads = [[1,0,10]]
<strong>Output:</strong> 1
<strong>Explanation:</strong> There is only one way to go from intersection 0 to intersection 1, and it takes 10 minutes.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 200</code></li>
	<li><code>n - 1 &lt;= roads.length &lt;= n * (n - 1) / 2</code></li>
	<li><code>roads[i].length == 3</code></li>
	<li><code>0 &lt;= u<sub>i</sub>, v<sub>i</sub> &lt;= n - 1</code></li>
	<li><code>1 &lt;= time<sub>i</sub> &lt;= 10<sup>9</sup></code></li>
	<li><code>u<sub>i </sub>!= v<sub>i</sub></code></li>
	<li>There is at most one road connecting any two intersections.</li>
	<li>You can reach any intersection from any other intersection.</li>
</ul>
 instead-->
<p>你在一个城市里，城市由 <code>n</code>&nbsp;个路口组成，路口编号为&nbsp;<code>0</code>&nbsp;到&nbsp;<code>n - 1</code>&nbsp;，某些路口之间有 <strong>双向</strong>&nbsp;道路。输入保证你可以从任意路口出发到达其他任意路口，且任意两个路口之间最多有一条路。</p>

<p>给你一个整数&nbsp;<code>n</code>&nbsp;和二维整数数组&nbsp;<code>roads</code>&nbsp;，其中&nbsp;<code>roads[i] = [u<sub>i</sub>, v<sub>i</sub>, time<sub>i</sub>]</code>&nbsp;表示在路口&nbsp;<code>u<sub>i</sub></code>&nbsp;和&nbsp;<code>v<sub>i</sub></code>&nbsp;之间有一条需要花费&nbsp;<code>time<sub>i</sub></code>&nbsp;时间才能通过的道路。你想知道花费 <strong>最少时间</strong>&nbsp;从路口&nbsp;<code>0</code>&nbsp;出发到达路口&nbsp;<code>n - 1</code>&nbsp;的方案数。</p>

<p>请返回花费 <strong>最少时间</strong>&nbsp;到达目的地的 <strong>路径数目</strong>&nbsp;。由于答案可能很大，将结果对&nbsp;<code>10<sup>9</sup> + 7</code>&nbsp;<strong>取余</strong>&nbsp;后返回。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/07/17/graph2.png" style="width: 235px; height: 381px;">
<pre><b>输入：</b>n = 7, roads = [[0,6,7],[0,1,2],[1,2,3],[1,3,3],[6,3,3],[3,5,1],[6,5,1],[2,5,1],[0,4,5],[4,6,2]]
<b>输出：</b>4
<b>解释：</b>从路口 0 出发到路口 6 花费的最少时间是 7 分钟。
四条花费 7 分钟的路径分别为：
- 0 ➝ 6
- 0 ➝ 4 ➝ 6
- 0 ➝ 1 ➝ 2 ➝ 5 ➝ 6
- 0 ➝ 1 ➝ 3 ➝ 5 ➝ 6
</pre>

<p><strong>示例 2：</strong></p>

<pre><b>输入：</b>n = 2, roads = [[1,0,10]]
<b>输出：</b>1
<b>解释：</b>只有一条从路口 0 到路口 1 的路，花费 10 分钟。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 200</code></li>
	<li><code>n - 1 &lt;= roads.length &lt;= n * (n - 1) / 2</code></li>
	<li><code>roads[i].length == 3</code></li>
	<li><code>0 &lt;= u<sub>i</sub>, v<sub>i</sub> &lt;= n - 1</code></li>
	<li><code>1 &lt;= time<sub>i</sub> &lt;= 10<sup>9</sup></code></li>
	<li><code>u<sub>i </sub>!= v<sub>i</sub></code></li>
	<li>任意两个路口之间至多有一条路。</li>
	<li>从任意路口出发，你能够到达其他任意路口。</li>
</ul>




## Solution

Language: **java**  /  Runtime: 7 ms

```java
//注意：由于两点间距离可达到为10^9，几乎为int最大值的一半，
//因此不能用int的最大值一半来表示无穷大，可用long类型表示路径长!!!
class Solution {
    int mod=(int)(1e9+7);
    long INF=Long.MAX_VALUE/2;
    int n;
    public int countPaths(int n, int[][] roads) {
        this.n=n;
        long[][] wGraph=new long[n][n];
        //初始化权重图
        for(int i=0;i<n;i++){
            for(int j=0;j<n;j++){
                wGraph[i][j]=wGraph[j][i] = i==j?0:INF;
            }
        }
        //存图
        for(int[] road:roads){
            int pOne=road[0],pTwo=road[1],timeN=road[2];
            wGraph[pOne][pTwo]=timeN;
            wGraph[pTwo][pOne]=timeN;
        }
        // Dijkstra 算法求解最短路
        long[] dist=new long[n];
        Arrays.fill(dist,INF);
        dist[0]=0;//只有起点最短路径为0
        boolean[] visited=new boolean[n];
        for(int p=0;p<n;p++){
            //每次找到最短距离最小且未被更新的点
            int nextN=-1;
            for(int i=0;i<n;i++){
                if(!visited[i]&&(nextN==-1 || dist[i]<dist[nextN])){nextN=i;}
            }
            //标记nextN已更新
            visited[nextN]=true;
            for(int i=1;i<n;i++){
                dist[i]=Math.min(dist[i],dist[nextN]+wGraph[nextN][i]);
            }
        }
        //**********
        Map<Integer, List<Integer>> graphM=new HashMap<>();
        for(int[] road:roads){
            int pOne=road[0],pTwo=road[1],timeN=road[2];
            if(dist[pOne]==timeN+dist[pTwo]){
                graphM.putIfAbsent(pTwo,new ArrayList<>());
                graphM.get(pTwo).add(pOne);
            }else if(dist[pTwo]==timeN+dist[pOne]){
                graphM.putIfAbsent(pOne,new ArrayList<>());
                graphM.get(pOne).add(pTwo);
            }
        }
        //记忆化递归
        int[] memo=new int[n];
        Arrays.fill(memo,-1);
        int res=dfs(graphM,memo,0);
        return  res;
    }
    public int dfs( Map<Integer, List<Integer>> graphM,int[] memo,int curN){
        if(curN==n-1){return 1;}
        if(memo[curN]!=-1){return memo[curN];}
        memo[curN]=0;
        List<Integer> tempList=graphM.get(curN);
        if(null!=tempList){
            for(int nextN: tempList){
                memo[curN]= (memo[curN]+dfs(graphM,memo,nextN))%mod;
            }
        }
        return memo[curN];
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/number-of-ways-to-arrive-at-destination/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/number-of-ways-to-arrive-at-destination/description/)

Solution: [LeetCode](https://leetcode.com/articles/number-of-ways-to-arrive-at-destination/)  /  [LeetCode中国](https://leetcode-cn.com/articles/number-of-ways-to-arrive-at-destination/)

[回到目录](../README.md)