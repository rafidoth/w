# UVa 441 - Lotto

```cpp
#include<bits/stdc++.h> 
using namespace std;
typedef long long int lli;
#define MOD 1000000007
int k;
vector<int> arr;

int r = 6;
vector<int> sel;
void ncr(int curr){
    if((int)sel.size() == r){
        for(int i =0; i<(int)sel.size();i++){
            if(i!=0) cout << " ";
            cout << sel[i];
        }
        cout << endl;
        return;
    }

    for(int i = curr; i<k;i++){
        sel.push_back(arr[i]);
        ncr(i+1);
        sel.pop_back();
    }
}


int main(){
    #ifndef ONLINE_JUDGE
      freopen("input.txt", "r", stdin);
      freopen("output.txt", "w", stdout);
    #endif

    ios_base::sync_with_stdio(0);
    cin.tie(0);
    int t = 0;
    while(cin>> k){
        if(k==0) break;
        vector<int> v(k);
        for(int i =0;i<k;i++){
            cin >> v[i];
        }
        arr = v;
        t++;
        if(t!=1) cout << endl;
        ncr(0);
    }

}



```