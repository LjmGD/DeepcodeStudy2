# 349.两个数组的交集

```java
class Solution {
    public int[] intersection(int[] nums1, int[] nums2) {
         HashSet<Integer> n1 = new HashSet<>();
        HashSet<Integer> n2 = new HashSet<>();
        for (int i = 0; i < nums1.length; i++) {
            n1.add(nums1[i]);
        }
        for (int i = 0; i < nums2.length; i++) {
            n2.add(nums2[i]);
        }
        n1.retainAll(n2);
        int[] res = new int[n1.size()];
        int j = 0;
        Iterator<Integer> iterator = n1.iterator();
        while (iterator.hasNext()) {
            Integer next =  iterator.next();
            res[j++] = next;
        }
        return res;

    }
}
```

# 88.合并两个有序数组

```java
class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int[] res = new int[m+n];
        int i1=0,i2=0;
        int j = 0;
        while(i1 < m || i2 < n){
            if (i1 == m){
                j = nums2[i2++];
            }else if (i2 == n){
                j = nums1[i1++];
            }else if (nums1[i1] > nums2[i2]){
                j = nums2[i2++];
            }else {
                j = nums1[i1++];
            }
            res[i1+i2-1] = j;
        }
        for (int i = 0; i < res.length; i++) {
            nums1[i] = res[i];
        }
    }
}
```

# 234.回文链表

ListNode自定义的单链表结构，以next指向下一个节点

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
class Solution {
    public boolean isPalindrome(ListNode head) {
        List<Integer> vals = new ArrayList<Integer>();

        // 将链表的值复制到数组中
        ListNode currentNode = head;
        while (currentNode != null) {
            vals.add(currentNode.val);
            currentNode = currentNode.next;
        }
        int i = 0;
        int j = vals.size() - 1;
        while(i < j){
            if(!vals.get(i).equals(vals.get(j))){
                return false;
            }
            i++;
            j--;
        }
         return true;
    }
}
```

