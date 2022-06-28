### [3.无重复字符的最长子串](https://leetcode-cn.com/problems/longest-substring-without-repeating-characters/)

#### 解法一：滑动窗口

```
设立左指针a和右指针b

b指针向右侧滑动{

	对每个A[b]判断是否在之前的数组中出现过;

		如果出现，指针a指向出现过的位置的下一个位置;

	更新右指针和最大长度;

}
```

```c++
class Solution
{
public:
    	int lengthOfLogestSubstring(string s){
            int start(0), end(0), length(0), result(0);
            int sSize = int(s.size());
            while (end < sSize){
                char tmpChar = s[end];
                for (int index = start; index < end; index++){
                    if (tmpChar == s[index]){
                        start = index + 1;
                        length = end - start;
                        break;   
                    }
                }
                end++;
                length++;
                result = max(result, length);
            }
            return result;
        }
};
```

