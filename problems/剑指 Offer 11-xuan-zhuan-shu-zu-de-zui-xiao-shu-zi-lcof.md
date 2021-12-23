# 剑指 Offer 11. xuan-zhuan-shu-zu-de-zui-xiao-shu-zi-lcof | 旋转数组的最小数字

## Question description

<!--If you want to use the English description, use English description is not available for the problem. Please switch to Chinese. instead-->
<p>把一个数组最开始的若干个元素搬到数组的末尾，我们称之为数组的旋转。</p>

<p>给你一个可能存在&nbsp;<strong>重复</strong>&nbsp;元素值的数组&nbsp;<code>numbers</code>&nbsp;，它原来是一个升序排列的数组，并按上述情形进行了一次旋转。请返回旋转数组的最小元素。例如，数组&nbsp;<code>[3,4,5,1,2]</code> 为 <code>[1,2,3,4,5]</code> 的一次旋转，该数组的最小值为1。&nbsp;&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>[3,4,5,1,2]
<strong>输出：</strong>1
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>[2,2,2,0,1]
<strong>输出：</strong>0
</pre>

<p>注意：本题与主站 154 题相同：<a href="https://leetcode-cn.com/problems/find-minimum-in-rotated-sorted-array-ii/">https://leetcode-cn.com/problems/find-minimum-in-rotated-sorted-array-ii/</a></p>


## Note

二分查找


## Solution

Language: **java**  /  Runtime: 0 ms

```java
class Solution {
    public int minArray(int[] numbers) {
        int l = 0;
        int r = numbers.length-1;
        int mid = (l+r)/2;
        //本就是有序数组
        if(numbers[r] > numbers[l]) return numbers[l];

        while(l <= r){
            //如果二分后的数组是有序数组，则返回最左元素，即为最小
            if(numbers[r] > numbers[l]) return numbers[l];
            //若最左小于mid元素，则最左到mid是严格递增的，那么最小元素必定在mid之后
            if(numbers[l] < numbers[mid]){
                l = mid+1;
                mid = (l+r)/2;
            }
            //若最左大于mid元素，则最小元素必定在最左到mid之间(不包括最左，因为最左已经大于mid)
            else if(numbers[l] > numbers[mid]){
                r = mid;
                l++;
                mid = (l+r)/2;
            }
            //若二者相等，则最小元素必定在l+1到r之间，因为l和mid相等，故可以去除
            else{
                l++;
                mid = (l+r)/2;
            }
        }
        return numbers[mid];
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/xuan-zhuan-shu-zu-de-zui-xiao-shu-zi-lcof/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/xuan-zhuan-shu-zu-de-zui-xiao-shu-zi-lcof/description/)

Solution: [LeetCode](https://leetcode.com/articles/xuan-zhuan-shu-zu-de-zui-xiao-shu-zi-lcof/)  /  [LeetCode中国](https://leetcode-cn.com/articles/xuan-zhuan-shu-zu-de-zui-xiao-shu-zi-lcof/)

[回到目录](../README.md)