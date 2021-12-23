# 691. stickers-to-spell-word | 贴纸拼词

## Question description

<!--If you want to use the English description, use <p>We are given <code>n</code> different types of <code>stickers</code>. Each sticker has a lowercase English word on it.</p>

<p>You would like to spell out the given string <code>target</code> by cutting individual letters from your collection of stickers and rearranging them. You can use each sticker more than once if you want, and you have infinite quantities of each sticker.</p>

<p>Return <em>the minimum number of stickers that you need to spell out </em><code>target</code>. If the task is impossible, return <code>-1</code>.</p>

<p><strong>Note:</strong> In all test cases, all words were chosen randomly from the <code>1000</code> most common US English words, and <code>target</code> was chosen as a concatenation of two random words.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> stickers = [&quot;with&quot;,&quot;example&quot;,&quot;science&quot;], target = &quot;thehat&quot;
<strong>Output:</strong> 3
<strong>Explanation:</strong>
We can use 2 &quot;with&quot; stickers, and 1 &quot;example&quot; sticker.
After cutting and rearrange the letters of those stickers, we can form the target &quot;thehat&quot;.
Also, this is the minimum number of stickers necessary to form the target string.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> stickers = [&quot;notice&quot;,&quot;possible&quot;], target = &quot;basicbasic&quot;
<strong>Output:</strong> -1
Explanation:
We cannot form the target &quot;basicbasic&quot; from cutting letters from the given stickers.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == stickers.length</code></li>
	<li><code>1 &lt;= n &lt;= 50</code></li>
	<li><code>1 &lt;= stickers[i].length &lt;= 10</code></li>
	<li><code>1 &lt;= target &lt;= 15</code></li>
	<li><code>stickers[i]</code> and <code>target</code> consist of lowercase English letters.</li>
</ul>
 instead-->
<p>我们给出了 N 种不同类型的贴纸。每个贴纸上都有一个小写的英文单词。</p>

<p>你希望从自己的贴纸集合中裁剪单个字母并重新排列它们，从而拼写出给定的目标字符串 <code>target</code>。</p>

<p>如果你愿意的话，你可以不止一次地使用每一张贴纸，而且每一张贴纸的数量都是无限的。</p>

<p>拼出目标&nbsp;<code>target</code> 所需的最小贴纸数量是多少？如果任务不可能，则返回 -1。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<p>输入：</p>

<pre>[&quot;with&quot;, &quot;example&quot;, &quot;science&quot;], &quot;thehat&quot;
</pre>

<p>输出：</p>

<pre>3
</pre>

<p>解释：</p>

<pre>我们可以使用 2 个 &quot;with&quot; 贴纸，和 1 个 &quot;example&quot; 贴纸。
把贴纸上的字母剪下来并重新排列后，就可以形成目标 &ldquo;thehat&ldquo; 了。
此外，这是形成目标字符串所需的最小贴纸数量。
</pre>

<p><strong>示例 2：</strong></p>

<p>输入：</p>

<pre>[&quot;notice&quot;, &quot;possible&quot;], &quot;basicbasic&quot;
</pre>

<p>输出：</p>

<pre>-1
</pre>

<p>解释：</p>

<pre>我们不能通过剪切给定贴纸的字母来形成目标&ldquo;basicbasic&rdquo;。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>stickers</code> 长度范围是&nbsp;<code>[1, 50]</code>。</li>
	<li><code>stickers</code> 由小写英文单词组成（不带撇号）。</li>
	<li><code>target</code> 的长度在&nbsp;<code>[1, 15]</code>&nbsp;范围内，由小写字母组成。</li>
	<li>在所有的测试案例中，所有的单词都是从 1000 个最常见的美国英语单词中随机选取的，目标是两个随机单词的串联。</li>
	<li>时间限制可能比平时更具挑战性。预计 50 个贴纸的测试案例平均可在35ms内解决。</li>
</ul>

<p>&nbsp;</p>




## Solution

Language: **java**  /  Runtime: 16 ms

```java
class Solution {
    public static int minStickers(String[] stickers, String target) {
        // 过滤判断：如果target中存在贴纸集中没有的字母，直接返回-1
        if (existLetterNotInStickers(stickers, target)) return -1;

        int[][] stickerMap = new int[stickers.length][26]; // stickerMap[i]：表示第i号贴纸stickers[i] 
        // 将贴纸集转换成字母频率表示，放入stickerMap
        for (int i = 0; i < stickers.length; i++) {
            for (char c : stickers[i].toCharArray()) {
                stickerMap[i][c-'a']++;
            }
        }
        // 记忆化搜索 target -> 最少贴纸数
        HashMap<String, Integer> memo = new HashMap<>(); 
        return minStickers(stickerMap, target, memo);
    }

    // stickerMap：贴纸集
    // target：rest target，要搞定的剩余目标
    // 返回搞定target所需要的最少贴纸数
    private static int minStickers(int[][] stickerMap, String target, HashMap<String, Integer> memo) {
        if (memo.containsKey(target)) return memo.get(target);

        if (target.length() == 0) {
            memo.put("", 0);
            return 0;
        }

        char[] targetLetters = target.toCharArray(); // target
        int[] targetWord = new int[26]; // 以字母频率方式表示target
        for (char c : targetLetters) {
            targetWord[c-'a']++;
        }
        int minCount = Integer.MAX_VALUE;

        // 枚举第1张使用哪种贴纸
        for (int i = 0; i < stickerMap.length; i++) {
            int[] sticker = stickerMap[i]; // 决定使用i号贴纸
            // 能否使用这种贴纸？
            // 如果这种贴纸是"aaabbb"，而target是"xyz"，使用这种贴纸啥也搞定不了，递归下去就是死循环
            // 如果使用这种贴纸，target中至少得有一种字母在这种贴纸中，如果target中的字母在sticker中都不存在，搞定个锤子
            if (notContainAnyLetter(sticker, targetLetters)) continue;
            
            // 计算使用这张贴纸后，新的target是啥
            // 26种字母依次处理，得到每种字母处理后的字母频率表targetWord
            StringBuilder sb = new StringBuilder();
            for (int j = 0; j < 26; j++) {
                // 如果目标中包含这种字母，使用1张贴纸后，计算这种字母还剩多少个
                int restCount = targetWord[j];
                if (targetWord[j] != 0) {
                    restCount = targetWord[j] > sticker[j] ? targetWord[j] - sticker[j] : 0;
                }
                // 将字母频率转成String：将这种字母添加到StringBuilder
                for (int k = 0; k < restCount; k++) {
                    sb.append((char)(j+'a'));
                }
            }
            String restTarget = sb.toString(); // 使用完第1张贴纸后，剩余目标
            int next = minStickers(stickerMap, restTarget, memo); // 【递归】后续需要的贴纸数量
            if (next != -1) minCount = Math.min(minCount, next + 1); // 后续过程有效，当前这种方案（使用i号贴纸作为第1张），是一种有效方案
        }

        int ans = minCount == Integer.MAX_VALUE ? -1 : minCount;
        memo.put(target, ans);
        return ans;
    }

    // 【贪心优化】
    // 如果target中的字母在sticker中都不存在，返回true
    // 如果target中至少存在一种字母在sticker中，返回false
    private static boolean notContainAnyLetter(int[] sticker, char[] target) {
        // 方法1：暴力枚举target中的每个字符，判断是否在sticker中存在
        // 200+ ms，击败30%
        // for (char c : target) {
        //     if (sticker[c-'a'] != 0) return false;
        // }
        // return true;

        // 方法2：贪心：因为最终是要搞定所有字母的，而题目最终的答案其实与顺序无关
        // 这里其实只需要to check target中的任意一个字符即可，不妨设为target[0]。
        // 18 ms，击败 97%
        char toCheckLetter = target[0];
        return sticker[toCheckLetter-'a'] == 0;
    }

    // 判断target中是否含有贴纸集stickers中没有的字母，如果存在，返回true
    private static boolean existLetterNotInStickers(String[] stickers, String target) {
        int[] stickersLetters = new int[26];
        for (String sticker : stickers) {
            for (char letter : sticker.toCharArray()) {
                stickersLetters[letter-'a']++;
            }
        }
        for (char letter : target.toCharArray()) {
            if (stickersLetters[letter-'a'] == 0) return true;
        }
        return false;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/stickers-to-spell-word/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/stickers-to-spell-word/description/)

Solution: [LeetCode](https://leetcode.com/articles/stickers-to-spell-word/)  /  [LeetCode中国](https://leetcode-cn.com/articles/stickers-to-spell-word/)

[回到目录](../README.md)