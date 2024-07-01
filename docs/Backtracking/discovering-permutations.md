# Light OJ Discovering Permutations 




```cpp
#include<bits/stdc++.h> 
using namespace std;
typedef long long int lli;
#define MOD 1000000007

int cnt = 0;
vector<char> selected;
bool r = false;
void fun(vector<char> arr, unordered_map<char,bool>taken,int k){
    if(arr.size() == selected.size()){
        for(char x : selected ) cout << x;
        cout << endl;
        cnt++;
        if(cnt==k) r = true; 
        return;
    }

    for(int i : arr){
        if(!taken[i] && !r){
            taken[i] = true;
            selected.push_back(i);
            fun(arr,taken,k);
            taken[i] = false;
            selected.pop_back();
        }
    }
}  

void soln(){
    int n,k;
    cin >> n >> k;
    vector<char> a = {'A','B','C','D','E','F','G','H','I','J','K','L','M','N','O','P','Q','R','S','T','U','V','W','X','Y','Z'} ;

    vector<char> arr;
    for(int i = 0; i<n;i++) arr.push_back(a[i]);
    cnt = 0;
    r = false;
    unordered_map<char,bool> ump;
    fun(arr,ump, k);
}



int main(){
    #ifndef ONLINE_JUDGE
      freopen("input.txt", "r", stdin);
      freopen("output.txt", "w", stdout);
    #endif
    ios_base::sync_with_stdio(0);
    cin.tie(0);
    int tc;
    cin >> tc; 
    for(int i =0;i<tc;i++){
        cout << "Case "  << i+1 <<":"<<endl;
        soln();
    }
}

```
