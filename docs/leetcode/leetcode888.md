# 888 Fair Candy Swap


## Naive Approach

For each element of `aliceSizes` array look into `bobSizes` and check if any one combination makes the both sum equals.


```
for each x of aliceSizes[]
    for each y of bobSizes[]
        if aliceSum - y + x == bobSum -x +y
            return x and y
```
C++ code
```cpp
vector<int> fairCandySwapNaive(vector<int>& aliceSizes, vector<int>& bobSizes) {
    int aliceSum = 0;
    for(int x : aliceSizes) aliceSum+= x;
    int bobSum= 0;
    for(int x : bobSizes) bobSum+= x;
    vector<int> answer;
    
    for (int i = 0; i <(int) aliceSizes.size(); ++i) {
        int aTemp = aliceSizes[i];
        for (int m = 0; m <(int) bobSizes.size(); ++m) {
            int bTemp = bobSizes[m];
            int newAliceSum = aliceSum - aTemp + bTemp;
            int newBobSum = bobSum - bTemp + aTemp;
            if (newAliceSum == newBobSum) {
                answer.push_back(aTemp);
                answer.push_back(bTemp);
                return answer;
            }
        }
    }
    return answer;
}
```


## Binary Search Optimization Scope

We need to find out the pair of numbers to exchange and make both the sum equals.
In the naive approach we were trying every combinations to exchange which is time
consuming and that makes the naive approach of O(n^2) Time Complexity. 

Now, the equal sum will be between their current sum and that is actually their
average number by that I meant `newEqualSum = (aliceInitialSum + bobInitialSum)/2`. 

If we take an example <br>
`aliceSizes = [3,4,5,9]` `aliceInitialSum = 21` <br>
`bobSizes = [7,2,6]` `bobInitialSum = 15`
<br>

so for this case the new sum should be (21+15)/2 = 18<br>
Let's see from Bob's perspective,<br>
To make the sum 18 what does Bob can do? <br>
<br>
Bob says "I have 7 and without 7 I have sum (15-7)=8. so if I exchange 7 I need (18-8)=10. 
Alice have 10?"
Alice searched and didn't get 10
Now again, 
Bob says "I have 2 and without 2 I have sum (15-2)=13. so if I exchange 2 I need (18-13)=5. 
Alice have 5?"
yes Alice got 5 and its the answer.

<br>
So, for every element of bob we can get what's the other element which should be exchanged.
and thus we can search that other element in alice's array. Here for searching 
we can use binary search to take less time. 
Therefore, the time complexity is O(nlogn)

```

for each x in bob's array
    bobEle = x
    aliceEle = (theirEqualSum - (bobSum - bobEle))
    if binsearch(aliceArray, aliceEle) == true then 
        answer will be aliceEle and bobEle
```

C++ code
```cpp
vector<int> fairCandySwap(vector<int>& aliceSizes, vector<int>& bobSizes){

    int asum = 0;
    for(int x : aliceSizes) asum += x;
    int bsum = 0;
    for(int x : bobSizes) bsum += x;

    vector<int> answer;

    int n = bobSizes.size();
    sort(aliceSizes.begin(), aliceSizes.end());
    for(int i =0;i<n;i++){
        int b = bobSizes[i];
        int target = ((asum+bsum)/2 ) - ( bsum - b);
        bool foundTarget = binsearch(aliceSizes,target);
        if(foundTarget){
            answer.push_back(target);
            answer.push_back(b);
            return answer;
        }
    }
    return answer;
}

```


