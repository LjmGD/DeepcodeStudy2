# 83.删除排序链表中的重复元素

```java
class Solution {
    public ListNode deleteDuplicates(ListNode head) {
        if (head == null) {
            return head;
        }
        ListNode res = head;
        while(res.next != null){
            if(res.val == res.next.val){
                res.next = res.next.next;//直接将next指向下一个节点
            }else{
                res = res.next;
            }
            
        }
        return head;
    }
}
```

# 382.链表随机节点

```java

class Solution {
    List<Integer> list;
    Random random;//定义全局变量

    public Solution(ListNode head) {
        list = new ArrayList<Integer>();
        while (head != null) {//用ArrayList来存储数据，方便后面的调用random方法
            list.add(head.val);
            head = head.next;
        }
        random = new Random();
    }

    public int getRandom() {
        return list.get(random.nextInt(list.size()));//nextInt返回下一个随机数
    }
}
```

# 1185.一周中的第几天

```java
class Solution {
    public String dayOfTheWeek(int day, int month, int year) {
        String[] week = {"Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday"};
        int[] monthDays = {31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30};
        int sum = 0;
        for (int i = 1971; i < year; i++) {
            if (judge(i))
                sum += 366;
            else
                sum += 365;
        }//计算年之前的天数

        for (int i = 0; i < month - 1; i++) {
            sum += monthDays[i];
        }//计算剩余月的天数

        if (month > 2 && judge(year))
            sum += 1 + day;
        else
            sum += day;//判断剩余的月份是否大于2

        int more = day + 3;
        return week[more % 7];//因为1971年12月31日为星期四，加三筹到星期一再取余7
    }

    public boolean judge(int year)//判断是否为闰年
    {
        return (year % 400 == 0) || (year % 4 == 0 && year % 100 != 0);
    }
}class Solution {
    public String dayOfTheWeek(int day, int month, int year) {
        String[] week = {"Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday"};
        int[] monthDays = {31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30};
        int sum = 0;
        //计算输入年之前的天数 
        for(int i = 1971; i < year; i++)
        {
            if(is_leap(i))
                sum += 366;
            else
                sum += 365;
        }
        //计算输入月之前的天数
        for(int i = 0; i < month-1; i++)
        {
            sum += monthDays[i];
        }
        //注意大于2月的情况才需要考虑是否要额外加1
        if(month > 2 && is_leap(year))
            sum += 1 + day;
        else
            sum += day;
        //天数 由于对应的是周四 
        int temp = sum%7;
        //最终结果在+3 就可以得到是一周的第几天了 
        return week[(temp+3)%7];
    }
    //判断是否是闰年
    public boolean is_leap(int year)//判断闰年
    {
        return (year % 400 == 0) || (year % 4 == 0 && year % 100 != 0);
    }
}
```

