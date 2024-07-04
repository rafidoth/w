# UVA 524 - Prime Ring Problem


```cpp
#include<bits/stdc++.h> 
using namespace std;
typedef long long int lli;
#define MOD 1000000007

vector<int> primes = {2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31,37};
bool checkPrime(int n){
    for(int x : primes){
        if(x ==n) return true;
    }
    return false;
}

vector<vector<int>> ans;
vector<int> sel;
using ump = unordered_map<int,bool>;
void notfun(vector<int>arr,ump proc){
    if(sel.size()== arr.size()-1){
        if(!checkPrime(sel.back()+1)) return;
        cout << 1 ;
        for(int x : sel) cout << " " << x ;
        cout <<endl;
        return;
    }
    for(int i =1;i<(int)arr.size();i++){
        if(!proc[arr[i]]){
            int sum = arr[i]; 
            if((int)sel.size() !=0) sum += sel.back();
            else sum+=1;
            if(!checkPrime(sum)) continue;
            proc[arr[i]] = true;
            sel.push_back(arr[i]);
            notfun(arr,proc);
            proc[arr[i]]= false;
            sel.pop_back();
        }
    }
}

int main(){
    #ifndef ONLINE_JUDGE
      freopen("input.txt", "r", stdin);
      freopen("output.txt", "w", stdout);
    #endif

    ios_base::sync_with_stdio(0);
    cin.tie(0);
    int in;
    int t = 0;
    while(cin >> in){
        if(t!=0) cout << endl;
        cout << "Case " << ++t << ":" <<endl;
        vector<int> arr;
        for(int i = 1; i<=in;i++) arr.push_back(i);
        ump proc;
        notfun(arr,proc);
        ans.clear();
    }
    

}


```
