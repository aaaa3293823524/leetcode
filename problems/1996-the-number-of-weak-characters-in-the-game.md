# 1996. the-number-of-weak-characters-in-the-game | 游戏中弱角色的数量

## Question description

<!--If you want to use the English description, use <p>You are playing a game that contains multiple characters, and each of the characters has <strong>two</strong> main properties: <strong>attack</strong> and <strong>defense</strong>. You are given a 2D integer array <code>properties</code> where <code>properties[i] = [attack<sub>i</sub>, defense<sub>i</sub>]</code> represents the properties of the <code>i<sup>th</sup></code> character in the game.</p>

<p>A character is said to be <strong>weak</strong> if any other character has <strong>both</strong> attack and defense levels <strong>strictly greater</strong> than this character&#39;s attack and defense levels. More formally, a character <code>i</code> is said to be <strong>weak</strong> if there exists another character <code>j</code> where <code>attack<sub>j</sub> &gt; attack<sub>i</sub></code> and <code>defense<sub>j</sub> &gt; defense<sub>i</sub></code>.</p>

<p>Return <em>the number of <strong>weak</strong> characters</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> properties = [[5,5],[6,3],[3,6]]
<strong>Output:</strong> 0
<strong>Explanation:</strong> No character has strictly greater attack and defense than the other.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> properties = [[2,2],[3,3]]
<strong>Output:</strong> 1
<strong>Explanation:</strong> The first character is weak because the second character has a strictly greater attack and defense.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> properties = [[1,5],[10,4],[4,3]]
<strong>Output:</strong> 1
<strong>Explanation:</strong> The third character is weak because the second character has a strictly greater attack and defense.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>2 &lt;= properties.length &lt;= 10<sup>5</sup></code></li>
	<li><code>properties[i].length == 2</code></li>
	<li><code>1 &lt;= attack<sub>i</sub>, defense<sub>i</sub> &lt;= 10<sup>5</sup></code></li>
</ul>
 instead-->
<p>你正在参加一个多角色游戏，每个角色都有两个主要属性：<strong>攻击</strong> 和 <strong>防御</strong> 。给你一个二维整数数组 <code>properties</code> ，其中 <code>properties[i] = [attack<sub>i</sub>, defense<sub>i</sub>]</code> 表示游戏中第 <code>i</code> 个角色的属性。</p>

<p>如果存在一个其他角色的攻击和防御等级 <strong>都严格高于</strong> 该角色的攻击和防御等级，则认为该角色为 <strong>弱角色</strong> 。更正式地，如果认为角色 <code>i</code> <strong>弱于</strong> 存在的另一个角色 <code>j</code> ，那么 <code>attack<sub>j</sub> &gt; attack<sub>i</sub></code> 且 <code>defense<sub>j</sub> &gt; defense<sub>i</sub></code> 。</p>

<p>返回 <strong>弱角色</strong> 的数量。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>properties = [[5,5],[6,3],[3,6]]
<strong>输出：</strong>0
<strong>解释：</strong>不存在攻击和防御都严格高于其他角色的角色。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>properties = [[2,2],[3,3]]
<strong>输出：</strong>1
<strong>解释：</strong>第一个角色是弱角色，因为第二个角色的攻击和防御严格大于该角色。
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>properties = [[1,5],[10,4],[4,3]]
<strong>输出：</strong>1
<strong>解释：</strong>第三个角色是弱角色，因为第二个角色的攻击和防御严格大于该角色。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>2 &lt;= properties.length &lt;= 10<sup>5</sup></code></li>
	<li><code>properties[i].length == 2</code></li>
	<li><code>1 &lt;= attack<sub>i</sub>, defense<sub>i</sub> &lt;= 10<sup>5</sup></code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 101 ms

```java
class Solution {
    public int numberOfWeakCharacters(int[][] properties) {
        List<int[]>list=new ArrayList<int[]>();
        for(int i=0;i<properties.length;i++) {
            list.add(properties[i]);
        }
        Collections.sort(list,new Comparator<int[]>() {

            @Override
            public int compare(int[] o1, int[] o2) {
                // TODO Auto-generated method stub
                return o1[0]!=o2[0]?o1[0]-o2[0]:o2[1]-o1[1];
            }
            
        });
        // for(int i=0;i<properties.length;i++) {
        //     System.out.println(list.get(i)[0]+":"+list.get(i)[1]);
        // }
        //        获取长度
        int len=properties.length;
//        弱对手数量
        int people=0;
        int defense=-1;
//        for循环遍历数组,由于已经排序好了,我们只要比较防御的大小就可以知道前面的数是不是弱角色
        for(int i=len-1;i>=0;i--) {//这里从后往前遍历,因为要获取最大的防御值
            int[] left=list.get(i);//properties[i];
            //System.out.println(left[0]+"***"+left[1]);
//            定义一个defense,为了获取右边的最大防御值
            
//            如果右边的防御值大于左边的防御值，那么左边肯定是弱对手
            //System.out.println(defense+"->"+left[1]);
            if (defense>left[1]) {
                people++;
            }
//            然后获取右边最大防御值
            //System.out.println("ss");
            //System.out.println(defense+"---"+left[1]);
            defense=Math.max(defense, left[1]);
            //System.out.println("tt");
        }
        return people;


    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/the-number-of-weak-characters-in-the-game/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/the-number-of-weak-characters-in-the-game/description/)

Solution: [LeetCode](https://leetcode.com/articles/the-number-of-weak-characters-in-the-game/)  /  [LeetCode中国](https://leetcode-cn.com/articles/the-number-of-weak-characters-in-the-game/)

[回到目录](../README.md)