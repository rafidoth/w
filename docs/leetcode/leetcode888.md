# 888 Fair Candy Swap


## Naive Approach

For each element of `aliceSizes` array look into `bobSizes` and check if any one combination makes the both sum equals.


### Code 
```
for each x of aliceSizes[]
    for each y of bobSizes[]
        if aliceSum - y + x == bobSum -x +y
            return x and y
```

```
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


