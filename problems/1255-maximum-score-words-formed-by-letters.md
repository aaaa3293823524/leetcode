﻿# 1255. maximum-score-words-formed-by-letters | 得分最高的单词集合

## Question description

<!--If you want to use the English description, use <p>Given a list of <code>words</code>, list of&nbsp; single&nbsp;<code>letters</code> (might be repeating)&nbsp;and <code>score</code>&nbsp;of every character.</p>

<p>Return the maximum score of <strong>any</strong> valid set of words formed by using the given letters (<code>words[i]</code> cannot be used two&nbsp;or more times).</p>

<p>It is not necessary to use all characters in <code>letters</code> and each letter can only be used once. Score of letters&nbsp;<code>&#39;a&#39;</code>, <code>&#39;b&#39;</code>, <code>&#39;c&#39;</code>, ... ,<code>&#39;z&#39;</code> is given by&nbsp;<code>score[0]</code>, <code>score[1]</code>, ... , <code>score[25]</code> respectively.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> words = [&quot;dog&quot;,&quot;cat&quot;,&quot;dad&quot;,&quot;good&quot;], letters = [&quot;a&quot;,&quot;a&quot;,&quot;c&quot;,&quot;d&quot;,&quot;d&quot;,&quot;d&quot;,&quot;g&quot;,&quot;o&quot;,&quot;o&quot;], score = [1,0,9,5,0,0,3,0,0,0,0,0,0,0,2,0,0,0,0,0,0,0,0,0,0,0]
<strong>Output:</strong> 23
<strong>Explanation:</strong>
Score  a=1, c=9, d=5, g=3, o=2
Given letters, we can form the words &quot;dad&quot; (5+1+5) and &quot;good&quot; (3+2+2+5) with a score of 23.
Words &quot;dad&quot; and &quot;dog&quot; only get a score of 21.</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> words = [&quot;xxxz&quot;,&quot;ax&quot;,&quot;bx&quot;,&quot;cx&quot;], letters = [&quot;z&quot;,&quot;a&quot;,&quot;b&quot;,&quot;c&quot;,&quot;x&quot;,&quot;x&quot;,&quot;x&quot;], score = [4,4,4,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,5,0,10]
<strong>Output:</strong> 27
<strong>Explanation:</strong>
Score  a=4, b=4, c=4, x=5, z=10
Given letters, we can form the words &quot;ax&quot; (4+5), &quot;bx&quot; (4+5) and &quot;cx&quot; (4+5) with a score of 27.
Word &quot;xxxz&quot; only get a score of 25.</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> words = [&quot;leetcode&quot;], letters = [&quot;l&quot;,&quot;e&quot;,&quot;t&quot;,&quot;c&quot;,&quot;o&quot;,&quot;d&quot;], score = [0,0,1,1,1,0,0,0,0,0,0,1,0,0,1,0,0,0,0,1,0,0,0,0,0,0]
<strong>Output:</strong> 0
<strong>Explanation:</strong>
Letter &quot;e&quot; can only be used once.</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= words.length &lt;= 14</code></li>
	<li><code>1 &lt;= words[i].length &lt;= 15</code></li>
	<li><code>1 &lt;= letters.length &lt;= 100</code></li>
	<li><code>letters[i].length == 1</code></li>
	<li><code>score.length ==&nbsp;26</code></li>
	<li><code>0 &lt;= score[i] &lt;= 10</code></li>
	<li><code>words[i]</code>, <code>letters[i]</code>&nbsp;contains only lower case English letters.</li>
</ul>
 instead-->
<p>你将会得到一份单词表&nbsp;<code>words</code>，一个字母表&nbsp;<code>letters</code>&nbsp;（可能会有重复字母），以及每个字母对应的得分情况表&nbsp;<code>score</code>。</p>

<p>请你帮忙计算玩家在单词拼写游戏中所能获得的「最高得分」：能够由&nbsp;<code>letters</code>&nbsp;里的字母拼写出的&nbsp;<strong>任意</strong>&nbsp;属于 <code>words</code>&nbsp;单词子集中，分数最高的单词集合的得分。</p>

<p>单词拼写游戏的规则概述如下：</p>

<ul>
	<li>玩家需要用字母表&nbsp;<code>letters</code> 里的字母来拼写单词表&nbsp;<code>words</code>&nbsp;中的单词。</li>
	<li>可以只使用字母表&nbsp;<code>letters</code> 中的部分字母，但是每个字母最多被使用一次。</li>
	<li>单词表 <code>words</code>&nbsp;中每个单词只能计分（使用）一次。</li>
	<li>根据字母得分情况表<code>score</code>，字母 <code>&#39;a&#39;</code>,&nbsp;<code>&#39;b&#39;</code>,&nbsp;<code>&#39;c&#39;</code>, ... ,&nbsp;<code>&#39;z&#39;</code> 对应的得分分别为 <code>score[0]</code>, <code>score[1]</code>,&nbsp;...,&nbsp;<code>score[25]</code>。</li>
	<li>本场游戏的「得分」是指：玩家所拼写出的单词集合里包含的所有字母的得分之和。</li>
</ul>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>words = [&quot;dog&quot;,&quot;cat&quot;,&quot;dad&quot;,&quot;good&quot;], letters = [&quot;a&quot;,&quot;a&quot;,&quot;c&quot;,&quot;d&quot;,&quot;d&quot;,&quot;d&quot;,&quot;g&quot;,&quot;o&quot;,&quot;o&quot;], score = [1,0,9,5,0,0,3,0,0,0,0,0,0,0,2,0,0,0,0,0,0,0,0,0,0,0]
<strong>输出：</strong>23
<strong>解释：</strong>
字母得分为  a=1, c=9, d=5, g=3, o=2
使用给定的字母表 letters，我们可以拼写单词 &quot;dad&quot; (5+1+5)和 &quot;good&quot; (3+2+2+5)，得分为 23 。
而单词 &quot;dad&quot; 和 &quot;dog&quot; 只能得到 21 分。</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>words = [&quot;xxxz&quot;,&quot;ax&quot;,&quot;bx&quot;,&quot;cx&quot;], letters = [&quot;z&quot;,&quot;a&quot;,&quot;b&quot;,&quot;c&quot;,&quot;x&quot;,&quot;x&quot;,&quot;x&quot;], score = [4,4,4,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,5,0,10]
<strong>输出：</strong>27
<strong>解释：</strong>
字母得分为  a=4, b=4, c=4, x=5, z=10
使用给定的字母表 letters，我们可以组成单词 &quot;ax&quot; (4+5)， &quot;bx&quot; (4+5) 和 &quot;cx&quot; (4+5) ，总得分为 27 。
单词 &quot;xxxz&quot; 的得分仅为 25 。</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>words = [&quot;leetcode&quot;], letters = [&quot;l&quot;,&quot;e&quot;,&quot;t&quot;,&quot;c&quot;,&quot;o&quot;,&quot;d&quot;], score = [0,0,1,1,1,0,0,0,0,0,0,1,0,0,1,0,0,0,0,1,0,0,0,0,0,0]
<strong>输出：</strong>0
<strong>解释：</strong>
字母 &quot;e&quot; 在字母表 letters 中只出现了一次，所以无法组成单词表 words 中的单词。</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= words.length &lt;= 14</code></li>
	<li><code>1 &lt;= words[i].length &lt;= 15</code></li>
	<li><code>1 &lt;= letters.length &lt;= 100</code></li>
	<li><code>letters[i].length == 1</code></li>
	<li><code>score.length ==&nbsp;26</code></li>
	<li><code>0 &lt;= score[i] &lt;= 10</code></li>
	<li><code>words[i]</code>&nbsp;和&nbsp;<code>letters[i]</code>&nbsp;只包含小写的英文字母。</li>
</ul>




## Solution

Language: **java**  /  Runtime: 6 ms

```java
class Solution {
    public int maxScoreWords(String[] words, char[] letters, int[] score) {
        // 状态压缩  + 动态规划
        int range = 1<<words.length;
        int dp[] = new int[range];
        int wordsNumber[][]=new int [words.length][26];
        int value[]=new int[words.length];
        int max = 0;
        // 计算每个words的价值
        // 统计每个单词需要的字符个数
        for(int i=0;i<words.length;i++){
            for(int j=0;j<words[i].length();j++){
                wordsNumber[i][words[i].charAt(j)-'a']++;
                value[i] = value[i] + score[words[i].charAt(j)-'a'];
            }  
        }
        int lettersNumber[] = new int [26];
        // 统计letters 每个字母可用的次数
        for(int i=0;i<letters.length;i++){
            lettersNumber[letters[i]-'a']++;
        }
        //初始化 dp 和 map 
        Map<Integer,int []> map = new HashMap<Integer,int []>();
        dp[0]=0;
        map.put(0,lettersNumber);
        // 用map 来记录每个状态下可用的字母数
        for(int i=1;i<range;i++){
            int temp = i - (i & (i-1));
            int index = 1;
            // 获取当时需要加入的单词在words中的下标
            while(temp!=1){
                temp = temp>>1;
                index++;
            }
            int []restNumber = Arrays.copyOf(map.get(i & (i-1)),26);
            // 判断是否可以构成该单词
            if(judge(wordsNumber[index-1],restNumber)){
                // 状态转移  dp[i] = dp[i & (i -1)] + value[index -1 ]; index为
                dp[i] = dp[i & (i-1)] +  value[index-1];
                for(int j=0;j<26;j++){
                    // 减去该单词需要消耗的字符数
                    restNumber[j] = restNumber[j]-wordsNumber[index-1][j];
                }
            }
            // 将加入 或者 不加入 后剩余单词的结果放入到map中
            map.put(i,restNumber);
            // 获取当前处理过状态的最大值
            max = Math.max(dp[i],max);
        }
        return max;
    }
    // 判断是否可以组合成该单词
    public boolean judge(int []words,int []rest){
        for(int i=0;i<26;i++){
            if(words[i]>rest[i]){
                return false;
            }
        }
        return true;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/maximum-score-words-formed-by-letters/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/maximum-score-words-formed-by-letters/description/)

Solution: [LeetCode](https://leetcode.com/articles/maximum-score-words-formed-by-letters/)  /  [LeetCode中国](https://leetcode-cn.com/articles/maximum-score-words-formed-by-letters/)

[回到目录](../README.md)