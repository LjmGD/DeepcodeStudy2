# 1332.删除回文子序列  

```java
class Solution {//不是回文返回2，是回文返回1
    public int removePalindromeSub(String s) {
        int n = s.length();
        int i = 0,j=n-1;
        while(i < j){
            if(s.charAt(i) != s.charAt(j)){
                return 2;
            }
            i++;
            j--;
        }
        return 1;
    }
}
```

## 3.无重复字符的最长字串

```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
       int n=s.length(),res =0;
       Map<Character,Integer> map = new HashMap<>();
       for(int end = 0,start = 0;end < n;end++){
           char a = s.charAt(end);
           if(map.containsKey(a)){
               start = Math.max(map.get(a),start);
           }
           res = Math.max(res,end-start +1);
           map.put(s.charAt(end),end+1);
       }
       return res;
    }
}
```

# 141.环形链表

```java
/**
 * Definition for singly-linked list.
 * class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public boolean hasCycle(ListNode head) {
        Set<ListNode> set = new HashSet<>();
        while(head != null){
            if(!set.add(head)){//如果没有在哈希表中则加入
                return true;
            }
            head = head.next;
        }
        return false;
    }
}
```

