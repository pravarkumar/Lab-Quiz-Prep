<img width="492" height="629" alt="Screenshot 2026-09-20 at 10 50 33 AM" src="https://github.com/user-attachments/assets/a6ef8d1d-3a2f-4d3c-94a7-5c42c1141bdd" />


We need to solve this Question in O(N + M) time and the O(M) space.One method is PQ but then the time complexity is higher .
Use the follwing method if constraints on the elemtn size are small :

Soln1)





"kth element" hints towards the use of heap data structrue 


Soln 2)
O(N log K) time and O(N)

    class Solution {
    public:
    int findKthLargest(vector<int>& nums, int k) {
        int mn=INT_MAX;
        int mx=INT_MIN;
        int n=nums.size();
        for(int i=0;i<n;i++){
            mn=min(mn,nums[i]);
            mx=max(mx,nums[i]);
        }
        
        vector<int> count(mx-mn+1);

        for(int i=0;i<n;i++){
            count[nums[i]-mn]++;
        }

        int seen=0;
        for(int i=mx-mn;i>-1;i--){
            seen+=count[i];
            if(seen>=k){
                return i+mn;
            }
        }
        return -1;
    }
    };


<img width="465" height="270" alt="Screenshot 2026-09-20 at 10 58 56 AM" src="https://github.com/user-attachments/assets/8c295379-b252-4210-ac0a-91226d64412d" />





