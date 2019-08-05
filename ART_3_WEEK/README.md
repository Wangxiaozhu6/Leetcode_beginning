# Algorithm
## 1.旋转数组
给定一个数组，将数组中的元素向右移动 k 个位置，其中 k 是非负数。
```示例 1:    
输入: [1,2,3,4,5,6,7] 和 k = 3    
输出: [5,6,7,1,2,3,4]    
解释:    
向右旋转 1 步: [7,1,2,3,4,5,6]    
向右旋转 2 步: [6,7,1,2,3,4,5]     
向右旋转 3 步: [5,6,7,1,2,3,4]     
示例 2:     
输入: [-1,-100,3,99] 和 k = 2         
输出: [3,99,-1,-100]        
解释:         
向右旋转 1 步: [99,-1,-100,3]     
向右旋转 2 步: [3,99,-1,-100]         
说明:         
尽可能想出更多的解决方案，至少有三种不同的方法可以解决这个问题。
要求使用空间复杂度为 O(1) 的 原地 算法。
```
提交代码：
```c++
class Solution {
public:
    void rotate(vector<int>& nums, int k) {
        if(k>nums.size())
            k=k%nums.size();
        //if(k==0||nums.size()<2)
         //   return nums;
        reverse(nums.begin(),nums.begin()+nums.size()-k);
        reverse(nums.begin()+nums.size()-k,nums.end());
        reverse(nums.begin(),nums.end());
  //      return nums;
    }
};
```
## 2.存在重复
```给定一个整数数组，判断是否存在重复元素。
如果任何值在数组中出现至少两次，函数返回 true。如果数组中每个元素都不相同，则返回 false。
示例 1:       
输入: [1,2,3,1]         
输出: true         
示例 2:          
输入: [1,2,3,4]    
输出: false       
示例 3:    
输入: [1,1,1,3,3,4,3,2,4,2]    
输出: true    
```
自己提交的代码：
```c++
class Solution {
public:
    bool containsDuplicate(vector<int>& nums) {
        vector<int> temp;
        for(int i=0;i<nums.size();i++)
            temp.push_back(nums[i]);
        auto unique_end=unique(nums.begin(),nums.end());
        nums.erase(unique_end,nums.end());
        if(temp.size()!=nums.size())
            return true;
        else
            return false;
        
    }
};
```
（<font color=#FF0000> 样例[1,2,3,1]总是出现逻辑判断错误 </font>）存在一点问题，暂未查找到。正在解决当中

---
```c++
class Solution {
public:
    bool containsDuplicate(vector<int>& nums) {
        set<int> values;
        for (auto num : nums) {
            values.insert(num);
        }
        return nums.size() != values.size();
    }
};
//这里用到了STL标准库中对set()无重复特性的使用，简易、恰到好处。
```
---
```c++
class Solution {
public:
    /**
     * @param nums: the given array
     * @return: if any value appears at least twice in the array
     */
    bool containsDuplicate(vector<int> &nums) {
        // Write your code here
        unordered_set<int> dict;
        for(int num : nums) {
            if(dict.find(num) == dict.end())
                dict.insert(num);
            else
                return true;
        }
        return false;
    }
};
//用到了无序容器set，通过find()语句``(dict.find(num) == dict.end()``判断是否会添加重复元素。
```
## 3.找出只有一个的元素
```
给定一个非空整数数组，除了某个元素只出现一次以外，其余每个元素均出现两次。找出那个只出现了一次的元素。    
说明：
你的算法应该具有线性时间复杂度。 你可以不使用额外空间来实现吗？
示例 1:
输入: [2,2,1]
输出: 1
示例 2:
输入: [4,1,2,1,2]
输出: 4
```
```c++
//根据消化的强大异或功能表现出来：
class Solution {
public:
    int singleNumber(vector<int>& nums) {
        
        int result=0;
        for(int i:nums)
            result^=i;
        return result;
        
    }
};
//哈希集这种思路也值得借鉴！

若第一次出现，插入哈希集；
第二次出现，冲哈希集内删除；
最后剩下的就是那个只出现一次的数字。
class Solution {
public:
    int singleNumber(vector<int>& nums) {
        unordered_set<int> bobo;
        int ans;
        for(auto i : nums){
            if(bobo.count(i))   bobo.erase(i);
            else    bobo.insert(i);
        }
        for(auto j : bobo)  ans = j;
        return ans;
    }
};

```
## 4.两个数组的交集 II
给定两个数组，编写一个函数来计算它们的交集。
示例 1:
输入: nums1 = [1,2,2,1], nums2 = [2,2]
输出: [2,2]
示例 2:
输入: nums1 = [4,9,5], nums2 = [9,4,9,8,4]
输出: [4,9]
```c++
class Solution {
public:
    vector<int> intersect(vector<int>& nums1, vector<int>& nums2) {
        
        vector<int>bobo;
        vector<int>::iterator it;
        for(auto i=0;i<nums1.size();i++)
        {             
            it=find(nums2.begin(),nums2.end(),nums1[i]);
            
            if(it!=nums2.end())
            {      
                bobo.push_back(nums1[i]);                                                                                                                                                 
                nums2.erase(it);
        }
        }
        
         return bobo;
    
}};
```
# Share
# Review
[How To Ask Questions The Smart Way](http://www.catb.org/~esr/faqs/smart-questions.html#writewell)文章比较长，还未读完。       
中文书籍《提问是一门艺术》，之前有浏览过书名，但没深入了解。此篇文章更像是《提问的艺术》Geek版；文章介绍的非常详细，从如何仔细挑选自己领域的论坛，提问思考的方式，该如何可以训练自己的思维，如何正确的使用开源平台等等。    节选一些自己收获到的一些知识：    
提问之前，搜寻论坛、Web、手册、FAQ、检测和实验数据、身边同学、开源平台。         
/。所要搜寻的答案质量会取决于你提问的角度和深度。在做哪怕一点细微小事，如果自己还有没找到问题，继续坚持自己思考，不过大脑的提问所得到的受益甚小/
真正能解决问题的人是不看或者不想浪费时间在这些没过脑的提问上面。
文中提出了一个让我眼前一亮的方法：使用有意义、具体的语言来描述标题。“object - deviation”，字面反过来是对象-偏差（即是差异），“对象”部分指定什么东西或一组东西有问题，“偏差”部分描述与预期行为的偏差；这样显著的提高了提问的效率，而且描述问题清晰。     
同样，在开源平台上永远不要一味地做一位索取者。是虽然你的问题，error or warning 已经有太多的类似问题无需再次开帖，但是通过自己的亲身实践去解决一些力所能及的提问同样也能实现自己的价值，帮助他人提高自己。
# Tip
```
在敲打C++primer习题时出现。在输入流作为for语句的判断条件时，如何使之停止？    
windows按ctrl + z，linux按ctrl + d
```
