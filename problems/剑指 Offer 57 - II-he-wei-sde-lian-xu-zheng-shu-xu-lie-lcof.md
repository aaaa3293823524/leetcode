# 剑指 Offer 57 - II. he-wei-sde-lian-xu-zheng-shu-xu-lie-lcof | 和为s的连续正数序列

## Question description

<!--If you want to use the English description, use <p>English description is not available for the problem. Please switch to Chinese.</p>
 instead-->
<p>输入一个正整数 <code>target</code> ，输出所有和为 <code>target</code> 的连续正整数序列（至少含有两个数）。</p>

<p>序列内的数字由小到大排列，不同序列按照首个数字从小到大排列。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>target = 9
<strong>输出：</strong>[[2,3,4],[4,5]]
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>target = 15
<strong>输出：</strong>[[1,2,3,4,5],[4,5,6],[7,8]]
</pre>

<p>&nbsp;</p>

<p><strong>限制：</strong></p>

<ul>
	<li><code>1 &lt;= target &lt;= 10^5</code></li>
</ul>

<p>&nbsp;</p>




## Solution

Language: **java**  /  Runtime: 20 ms

```java
class Solution {
    public int[][] findContinuousSequence(int target) {
        //int[][]nums=new 
        List<Integer>list=new  ArrayList<Integer>();
        List<List<Integer>>res=new  ArrayList<List<Integer>>();
        HashMap<Integer,Integer>map=new HashMap<Integer,Integer>();
        int k=0,sum=0;
        for(int i=1;i<target;i++){
            if(i==1)k++;
            else{
                sum-=i-1;
                map.remove(i-1);
            }
            while(sum<target){
                map.put(k,1);
                sum+=k;
                //System.out.println(sum);
                k++;
            }
            //System.out.println("************");
            if(sum==target){
                list.clear();
                for(Integer t:map.keySet()){
                    list.add(t);
                    //System.out.println("*:"+t);
                }
                Collections.sort(list);
                res.add(new ArrayList(list));
            }
        }
        int[][]nums=new int[res.size()][];
        
        for(int i=0;i<res.size();i++){
            List<Integer>gg=res.get(i);
            nums[i]=new int[gg.size()];
            for(int j=0;j<gg.size();j++){
                nums[i][j]=gg.get(j);
                //System.out.println("-----:"+gg.get(j));
            }
        }
        // for(int i=0;i<res.size();i++){
        //     List<Integer>l=res.get(i);
        //     if(l!=null){
        //     for(int j=0;j<l.size();j++){
        //         nums[i][j]=l.get(j);
        //     }
        //     }
        // }
        return nums;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/he-wei-sde-lian-xu-zheng-shu-xu-lie-lcof/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/he-wei-sde-lian-xu-zheng-shu-xu-lie-lcof/description/)

Solution: [LeetCode](https://leetcode.com/articles/he-wei-sde-lian-xu-zheng-shu-xu-lie-lcof/)  /  [LeetCode中国](https://leetcode-cn.com/articles/he-wei-sde-lian-xu-zheng-shu-xu-lie-lcof/)

[回到目录](../README.md)