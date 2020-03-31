

# 560 (Medium)
Given an array of integers and an integer k, you need to find the total number of continuous subarrays whose sum equals to k.

        Idea:
        If the cumulative sum upto two indices, saying i and j is at a difference of k 
        i.e. sum[i] - sum[j] = sum[i] − sum[j]=k, the sum of elements lying between indices i and j is k.

        Steps:
        1. make use of a hashmap mapmap which is used to store the cumulative sum upto all the indices possible 
        along with the number of times the same sum occurs. 
        We store the data in the form: (sum_i, no. of occurrences of  sum_i).
        2. traverse over the array nums and keep on finding the cumulative sum. Every time we encounter a new sum, 
        we make a new entry in the hashmap corresponding to that sum. 
        3. if the same sum occurs again, we increment the count corresponding to that sum in the hashmap. 
        4. further, for every sum encountered, we also determine the number of times the sum-k has occured already, 
        since it will determine the number of times a subarray of sum-k has occured upto the current index. 
        We increment the count by the same amount.
        5. after the complete array has been traversed, the count gives the required result.

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
        # time:o(n)
        # space:o(n)
        
        
        
        
        
        # other ways
         def subarraySum(nums,k):
              count=0
                for start in range(len(nums)):
                    for end in range(start+1,len(nums)+1):
                        sums=sum(nums[start:end])
                        if sums==k:
                            count+=1
                return count  
         # time:o(n^3)
         # space:o(1)
         
          def subarraySum(nums,k):   
                count=0
                sums=[0]*(len(nums)+1)
                for i in range(1,len(nums)+1):
                    sums[i]=sums[i-1]+nums[i-1]
                for start in range(len(nums)):
                    for end in range(start+1,len(nums)+1):
                        if sums[end]-sums[start]==k:
                            count+=1
                return count
         # time:o(n^2)
         # space:o(n)
         
           def subarraySum(nums,k):
                count=0
                for start in range(len(nums)):
                    sums=0
                    for end in range(start,len(nums)):
                        sums+=nums[end]
                        if sums==k:
                            count+=1
                return count
         # time:o(n^2)
         # space:o(1)


