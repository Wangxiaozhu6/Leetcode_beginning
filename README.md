# Leetcode_beginning
It's my first anwering question on leetcode,emmmm..

## algorithm_leetcode.26
Given a sorted array nums, remove the duplicates in-place such that each element appear only once and return the new length.

Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.
Example 1:

Given nums = [1,1,2],

Your function should return length = 2, with the first two elements of nums being 1 and 2 respectively.
MY code  is following:

---
```c++
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        if (nums.size()==0 )return 0;
        int index=1;
        int j=0;
        for(int i=1;i<nums.size();++i)
        {
            if(nums[j]!=nums[i])
            {
                nums[++j]=nums[i];
                index++;
            }
        }
        return index;
    }
};
```
---
不得不说自己真是菜鸡一个，不要提什么科不科班出身？你努不努力，拉出来遛遛。Leecode第一次难度级别：easy     
高手自在人间，看完讨论区懵了，一口一个卧槽/
解法一：
```c++
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        if(nums.size() == 0){
           return 0; 
        }
        for(int i=0;i<nums.size()-1;){
            if(nums[i] == nums[i+1]){
                nums.erase(nums.begin()+i+1);
            }else{
                i++;
            }
        }
        return nums.size();
    }
};```
用到了C++11特性的erase()函数，然后返回数组个数，常规做法。
erase(position);删除position处的一个字符(position是个string类型的迭代器)    
erase(pos,n); 删除从pos开始的n个字符，比如erase(0,1)就是删除第一个字符     
erase(first,last);删除从first到last之间的字符（first和last都是迭代器）   

---
     
解法二：
```c++
return distance(nums.begin(), unique(nums.begin(), nums.end()));
明白了无所不用其极是什么，把STL标准库用到了极致；
```

---

三：双指针
```c++
设置两个指针，一个慢指针i，一个快指针j，当nums[i]!=nums[j],将nums[i+1]=nums[j]。
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        if(nums.size()==0) return 0;
        int i=0;
        for(int j=1;j<nums.size();j++)
        {
            if(nums[j]!=nums[i])
            {
                i++;
                nums[i]=nums[j];
            }
        }
        return i+1;
    }
};
```
---
   记得严魏敏老师讲过双指针的用法，暂时消化不了。显摆上来，经典解法望日后吃掉。初学阶段，就先从容易开始刷，但是速度、量一定要提上来，今个儿下午吭哧了一下午，效率额还是太低了，菜是本源，一步步来吧。    
   值得高兴的，在一步步进行左耳听风打卡的同时，它逼迫自己主动去猎取未知的知识。eg.创建自己github，让自己从零到有；像写博客一样进行文字编辑（explore了Markdown，这种之前从没听说过的标记语法），以及头一次在开源平台输出自己的想法和知识，总之这很值得去做的一件事。不管有没有人去看，对自己来说也是一次进步成长的机会。
