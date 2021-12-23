# 211. design-add-and-search-words-data-structure | 添加与搜索单词 - 数据结构设计

## Question description

<!--If you want to use the English description, use <p>Design a data structure that supports adding new words and finding if a string matches any previously added string.</p>

<p>Implement the <code>WordDictionary</code> class:</p>

<ul>
	<li><code>WordDictionary()</code>&nbsp;Initializes the object.</li>
	<li><code>void addWord(word)</code> Adds <code>word</code> to the data structure, it can be matched later.</li>
	<li><code>bool search(word)</code>&nbsp;Returns <code>true</code> if there is any string in the data structure that matches <code>word</code>&nbsp;or <code>false</code> otherwise. <code>word</code> may contain dots <code>&#39;.&#39;</code> where dots can be matched with any letter.</li>
</ul>

<p>&nbsp;</p>
<p><strong>Example:</strong></p>

<pre>
<strong>Input</strong>
[&quot;WordDictionary&quot;,&quot;addWord&quot;,&quot;addWord&quot;,&quot;addWord&quot;,&quot;search&quot;,&quot;search&quot;,&quot;search&quot;,&quot;search&quot;]
[[],[&quot;bad&quot;],[&quot;dad&quot;],[&quot;mad&quot;],[&quot;pad&quot;],[&quot;bad&quot;],[&quot;.ad&quot;],[&quot;b..&quot;]]
<strong>Output</strong>
[null,null,null,null,false,true,true,true]

<strong>Explanation</strong>
WordDictionary wordDictionary = new WordDictionary();
wordDictionary.addWord(&quot;bad&quot;);
wordDictionary.addWord(&quot;dad&quot;);
wordDictionary.addWord(&quot;mad&quot;);
wordDictionary.search(&quot;pad&quot;); // return False
wordDictionary.search(&quot;bad&quot;); // return True
wordDictionary.search(&quot;.ad&quot;); // return True
wordDictionary.search(&quot;b..&quot;); // return True
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= word.length &lt;= 500</code></li>
	<li><code>word</code> in <code>addWord</code> consists lower-case English letters.</li>
	<li><code>word</code> in <code>search</code> consist of&nbsp; <code>&#39;.&#39;</code> or lower-case English letters.</li>
	<li>At most <code>50000</code>&nbsp;calls will be made to <code>addWord</code>&nbsp;and <code>search</code>.</li>
</ul>
 instead-->
<p>请你设计一个数据结构，支持 添加新单词 和 查找字符串是否与任何先前添加的字符串匹配 。</p>

<p>实现词典类 <code>WordDictionary</code> ：</p>

<ul>
	<li><code>WordDictionary()</code> 初始化词典对象</li>
	<li><code>void addWord(word)</code> 将 <code>word</code> 添加到数据结构中，之后可以对它进行匹配</li>
	<li><code>bool search(word)</code> 如果数据结构中存在字符串与 <code>word</code> 匹配，则返回 <code>true</code> ；否则，返回  <code>false</code> 。<code>word</code> 中可能包含一些 <code>'.'</code> ，每个 <code>.</code> 都可以表示任何一个字母。</li>
</ul>

<p> </p>

<p><strong>示例：</strong></p>

<pre>
<strong>输入：</strong>
["WordDictionary","addWord","addWord","addWord","search","search","search","search"]
[[],["bad"],["dad"],["mad"],["pad"],["bad"],[".ad"],["b.."]]
<strong>输出：</strong>
[null,null,null,null,false,true,true,true]

<strong>解释：</strong>
WordDictionary wordDictionary = new WordDictionary();
wordDictionary.addWord("bad");
wordDictionary.addWord("dad");
wordDictionary.addWord("mad");
wordDictionary.search("pad"); // return False
wordDictionary.search("bad"); // return True
wordDictionary.search(".ad"); // return True
wordDictionary.search("b.."); // return True
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= word.length <= 500</code></li>
	<li><code>addWord</code> 中的 <code>word</code> 由小写英文字母组成</li>
	<li><code>search</code> 中的 <code>word</code> 由 '.' 或小写英文字母组成</li>
	<li>最多调用 <code>50000</code> 次 <code>addWord</code> 和 <code>search</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 47 ms

```java
class Trie {

    Trie[] children;
    boolean isEnd;
    public Trie() { // 初始化

        children = new Trie[26];
        isEnd = false;
    }
}
class WordDictionary {

    Trie root;
    public WordDictionary() {

        root = new Trie(); // 初始化
    }
    
    public void addWord(String word) { // 将 word 添加到数据结构中，之后可以对它进行匹配

        Trie node = this.root;
        int n = word.length();
        for (int i=0;i<n;i++) {

            if (node.children[word.charAt(i) - 'a'] == null) {

                node.children[word.charAt(i) - 'a'] = new Trie();
            }
            node = node.children[word.charAt(i) - 'a'];
        }
        node.isEnd = true;
    }
    
    public boolean search(String word) {

        return searchWord(word, this.root);
    }

    public boolean searchWord(String word, Trie root) { // 递归

        Trie node = root;
        int n = word.length();
        for (int i=0;i<n;i++) {

            char c = word.charAt(i);
            if (c != '.' && node.children[c - 'a'] == null) return false;
            if (c == '.') { // 如果是 '.'，则对该节点所有不为空的节点进行深度搜索

                for (int j=0;j<26;j++) { // 继续遍历 node.children[26]

                    // 如果存在下一个字母，则从下一个字母开始再继续做检查
                    if (node.children[j] != null) {

                        if (searchWord(word.substring(i + 1), node.children[j])) {

                            return true;
                        }
                    }
                }
                return false;
            }
            node = node.children[c - 'a'];
        }
        return node.isEnd;
    }
}

```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/design-add-and-search-words-data-structure/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/design-add-and-search-words-data-structure/description/)

Solution: [LeetCode](https://leetcode.com/articles/design-add-and-search-words-data-structure/)  /  [LeetCode中国](https://leetcode-cn.com/articles/design-add-and-search-words-data-structure/)

[回到目录](../README.md)