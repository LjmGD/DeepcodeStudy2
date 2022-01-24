# 13.罗马数字转整数

```java
class Solution {
    public int romanToInt(String s) {//IV
    Map<Character, Integer> map = new HashMap<Character, Integer>() {{
        put('I', 1);
        put('V', 5);
        put('X', 10);
        put('L', 50);
        put('C', 100);
        put('D', 500);
        put('M', 1000);
    }};
        int n = s.length();
        int ans = 0;
        for (int i = 0; i < n; i++) {
            int value = map.get(s.charAt(i));
            if (i < n - 1 && value < map.get(s.charAt(i + 1)))  {
                ans -= value;
            } else {
                ans += value;
            }
        }
        return ans;
}
}
```

# 58.最后一个单词的长度

```java
class Solution {
    public int lengthOfLastWord(String s) {
        int n = s.length();
        int count = 0;
        for (int i = 0; i <n ; i++) {
            if (s.charAt(i) == ' '){
                for (int j = i; j <n ; j++) {
                    if (s.charAt(j) != ' ') {
                        count = 0;
                    }
                }
            }else {
                count++;
            }
        }
        return  count;
    }
}
class Solution {
    public int lengthOfLastWord(String s) {
        int index = s.length() - 1;
        while (s.charAt(index) == ' ') {
            index--;
        }
        int wordLength = 0;
        while (index >= 0 && s.charAt(index) != ' ') {
            wordLength++;
            index--;
        }
        return wordLength;
    }
}

```

# 14.最长公共前缀

```java
class Solution {
    public String longestCommonPrefix(String[] strs) {
        if(strs.length == 0) 
            return "";
        String ans = strs[0];
        for(int i =1;i<strs.length;i++) {
            int j=0;
            for(;j<ans.length() && j < strs[i].length();j++) {
                if(ans.charAt(j) != strs[i].charAt(j))
                    break;
            }
            ans = ans.substring(0, j);//返回一个字符串，该字符串是此字符串的子字符串。
            if(ans.equals(""))
                return ans;
        }
        return ans;
    }
}
//但用["we","flow","flight"]就无法选出，不过官方通过了
```

