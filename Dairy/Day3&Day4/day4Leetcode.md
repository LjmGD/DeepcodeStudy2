# 21.合并两个有序链表

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
 /*list1.val>list2.val mergeTwoLists() 
 */
class Solution {
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        if(list1 == null){
            return list2;
        }else if(list2 == null){
            return list1;
        }else if(list1.val > list2.val){
            list2.next = mergeTwoLists(list1 , list2.next);
            return list2;//谁小返回谁
        }else {//包含两种情况，两数相等时，next下一个list1,list2都一样
            list1.next = mergeTwoLists(list1.next , list2);
            return list1;
        }
    }
}
```

# 28.实现strStr()

```java
class Solution {
    public int strStr(String haystack, String needle) {
        for (int i = 0; i + needle.length() <= haystack.length(); i++) {
//i + needle.length() <= haystack.length() 防止 haystack.charAt(i+j)越界           
            boolean flag = true;
            for (int j = 0; j < needle.length(); j++) {
                if(haystack.charAt(i+j) != needle.charAt(j)){
                    flag = false;
                    break;
                }
                }
            if(flag == true) {
                return i;
            }
        }
        return -1;
    }
}
```

# 66.加一

```java
class Solution {
    public int[] plusOne(int[] digits) {
        for(int i = digits.length - 1;i >= 0;i--){
            if(digits[i] == 9){
                digits[i] = 0;
            }else{
                digits[i] += 1;
                return digits;
            }
        }
        // digits 中所有的元素都为9
        int[] ans = new int[digits.length + 1];
        ans[0] = 1;
        return ans;
    }
}
```

