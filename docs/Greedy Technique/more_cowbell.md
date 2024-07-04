# CF More Cowbell
Problem Link : https://codeforces.com/problemset/problem/604/B

```cpp
#include<bits/stdc++.h> 
using namespace std;
typedef long long int lli;
#define MOD 1000000007



int main(){
    ios_base::sync_with_stdio(0);
    cin.tie(0);
    int n,k;
    cin >> n >> k;
    vector<int> arr(n);
    for(int i =0;i<n;i++) cin  >> arr[i];
    if(k>=n){
        cout << arr[n-1] <<endl;
        return 0;
    }
    int z = n;
    if(n%k == 0) z = n/k;
    else z = (n/k) +1;
    for(int i =0;i<(z*k-n);i++) arr.push_back(0);
    sort(arr.begin(),arr.end());
    int new_size = z*k;
    int ans = 0;
    for(int i = 0 ; i <new_size/2;i++){
        ans = max(ans, arr[i] + arr[new_size-i-1]);
    }
    cout << ans << endl;
}


```