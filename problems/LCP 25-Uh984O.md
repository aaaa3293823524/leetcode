# LCP 25. Uh984O | 古董键盘

## Question description

<!--If you want to use the English description, use  instead-->
小扣在秋日市集购买了一个古董键盘。由于古董键盘年久失修，键盘上只有 26 个字母 **a~z** 可以按下，且每个字母最多仅能被按 `k` 次。

小扣随机按了 `n` 次按键，请返回小扣总共有可能按出多少种内容。由于数字较大，最终答案需要对 1000000007 (1e9 + 7) 取模。


**示例 1：**
>输入：`k = 1, n = 1`
> 
>输出：`26`
> 
>解释：由于只能按一次按键，所有可能的字符串为 "a", "b", ... "z" 

**示例 2：**
>输入：`k = 1, n = 2`
> 
>输出：`650`
> 
>解释：由于只能按两次按键，且每个键最多只能按一次，所有可能的字符串（按字典序排序）为 "ab", "ac", ... "zy" 

**提示：**
- `1 <= k <= 5`
- `1 <= n <= 26*k`
 





## Solution

Language: **java**  /  Runtime: 262 ms

```java
import java.util.HashMap;
import java.util.Map;

class Solution {
    Map<Integer, Long> maps = new HashMap<>();

    public int keyboard(int k, int n) {
        int[] dp = new int[k + 1];
        dp[k] = 26;
        return (int) (dfs(dp, n, k) % 1000000007);
    }

    
    private long dfs(int[] map, int n, int limit) {
        int state = getState(map);
        if (!maps.containsKey(state)) {
            long res = 0;
            if (n == 1) {
                for (int i = 1; i <= limit; i++) {
                    res += map[i];
                }
            } else {
                for (int i = 1; i <= limit; i++) {
                    if (map[i] != 0) {
                        map[i]--;
                        map[i - 1]++;

                        res += (map[i] + 1) * dfs(map, n - 1, limit);
                        res %= 1000000007;

                        // 回溯
                        map[i]++;
                        map[i - 1]--;
                    }
                }
            }
            maps.put(state, res);
            return res;
        }
        return maps.get(state);
    }

    public int getState(int[] map) {
        int cur = 0;
        for (int i = 1; i < map.length; i++) {
            cur *= 27;
            cur += map[i];
        }
        return cur;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/Uh984O/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/Uh984O/description/)

Solution: [LeetCode](https://leetcode.com/articles/Uh984O/)  /  [LeetCode中国](https://leetcode-cn.com/articles/Uh984O/)

[回到目录](../README.md)