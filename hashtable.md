# Leetcode - Python3

560 (Medium)
Given an array of integers and an integer k, you need to find the total number of continuous subarrays whose sum equals to k.


def subarraySum(nums,k):
    count=0
    sums=0
    dic={0:1}
    for i in range(len(nums)):
        sums+=nums[i]
        if (sums-k) in dic:
             count+=dic[sums-k]
        if sums not in dic:
             dic[sums]=1
        else:
             dic[sums]+=1
    return count
    
  
      count=0
        for start in range(len(nums)):
            for end in range(start+1,len(nums)+1):
                sums=sum(nums[start:end])
                if sums==k:
                    count+=1
        return count  
     
        count=0
        sums=[0]*(len(nums)+1)
        for i in range(1,len(nums)+1):
            sums[i]=sums[i-1]+nums[i-1]
        for start in range(len(nums)):
            for end in range(start+1,len(nums)+1):
                if sums[end]-sums[start]==k:
                    count+=1
        return count
    
        count=0
        for start in range(len(nums)):
            sums=0
            for end in range(start,len(nums)):
                sums+=nums[end]
                if sums==k:
                    count+=1
        return count
    
  
    
