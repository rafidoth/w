# 349 Intersection of Two Arrays

It can be done with naive approach of two loops. For each element of 
nums1 is it in the nums2 too? if yes then its an answer and for 
repetitive numbers we can use `set` to get the unique values only.

This process will take O(N^2) Time Complexity.
but for the search purpose  we can use binary searching. obviously before
searching in Nums2 it should be sorted. C++ sort function takes O(NlogN)
time to sort a vector. 

```
sort(nums2) // O(nlogn)
for each x of nums1 // O(nlogn)
    if binarySearch(nums2, x) == true  
        push it to the answer set

```


```cpp
#include<bits/stdc++.h> 
using namespace std;
typedef long long int lli;
#define MOD 1000000007



bool binsearch(vector<int> arr, int target){
    int start = 0;
    int end = arr.size() -1 ;
    while(start <=end){
        int mid = (start + end) /2;
        if(arr[mid] == target) return true;
        else if (target > arr[mid]) start = mid +1;
        else end = mid -1;
    }
    return false;
}


vector<int> func(vector<int>& nums1, vector<int>& nums2){
    set<int> ans;
    sort(nums2.begin(),nums2.end());
    for(int x: nums1){
        bool found = binsearch(nums2,x) ;
        if(found) ans.insert(x);
    }
    vector<int> v;
    for(int a : ans)  v.push_back(a);
    return v;
}




int main(){
    ios_base::sync_with_stdio(0);
    cin.tie(0);
    vector<int> nums1 = {4,9,5};
    vector<int> nums2 = {9,4,9,8,4};
    vector<int> res = func(nums1,nums2);
    for(int x : res ) cout << x << " ";
    cout << endl;
}


```
