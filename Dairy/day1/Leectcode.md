# 1.两数之和

法一：

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        for (int i = 0; i < nums.length; i++) {
                for (int j = 0; j < nums.length; j++) {
                    if(nums[i] + nums[j] == target){
                        return new int[]{i,j};
                    }
                }
            }
            return null;
    }

```

# 20.有效括号

```java
class Solution {
    public boolean isValid(String s) {
       Stack<Character> stack = new Stack<>();
        HashMap<Character,Character> pairs = new HashMap<Character, Character>(){{
            put('}','{');
            put(']','[');
            put(')','(');
        }};//方便判断
        for (int i = 0; i < s.length(); i++) {
            char c = s.charAt(i);
            if (pairs.containsKey(c)){//判断是否为右半边的符号
                if (stack.isEmpty() || stack.peek() != pairs.get(c)){
                    return false;
                }//判断栈是否为空，以及栈的顶部是否可以配对
                stack.pop();//弹出顶部
            }else {
                stack.push(c);//加入栈
            }
        }
        return stack.isEmpty();//判断最后的栈是否为空
    }
}
```

# 709.转换成小写字母

```java
class Solution {
    public String toLowerCase(String s) {
        StringBuilder stringBuilder = new StringBuilder();
        for (int i = 0; i < s.length(); i++) {
            char c = s.charAt(i);
            if(c >= 65 && c <= 90){
                c += 32;
            }
            stringBuilder.append(c);
        }
        return stringBuilder.toString();
    }
}
```

