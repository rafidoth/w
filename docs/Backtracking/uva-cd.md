# UVa 624 - CD


```cpp

#include<bits/stdc++.h> 
using namespace std;
typedef long long int lli;
#define MOD 1000000007
#define debug(...) fprintf(stderr, __VA_ARGS__), fflush(stderr)


int N;
int k;
vector<int> arr;
vector<int> sel;
int sum  = 0;
int maxsum = 0;
vector<int> maxv;
void ncr(int curr){
    /*
    for(int x : sel) cout << x << " " ;
    cout<<"sum :"  << sum << endl;
    */
    if(sum == N) {
        maxv = sel;
        maxsum = sum;
        return;
    }
    if((int)sel.size() == k){
        return;
    }
    for(int i =curr; i<k;i++){
        if(sum == N ) return;
        if(sum + arr[i] >  N ) {
            continue;
        }
        sel.push_back(arr[i]);
        sum += arr[i];
        if(sum >maxsum){
            maxsum = sum;
            maxv = sel;
        }
        ncr(i+1);
        if(sum ==N) return;
        sel.pop_back();
        sum -= arr[i];
    }
}

int main(){
    #ifndef ONLINE_JUDGE
      freopen("input.txt", "r", stdin);
      freopen("output.txt", "w", stdout);
    #endif

    ios_base::sync_with_stdio(0);
    cin.tie(0);
    clock_t z = clock();
    //int t = 0;
    while(cin >> N){
    //    cout << "test case"<< ++t <<endl;
        cin >> k;
        int s = 0;
        for(int i =0;i<k;i++) {
            int x ;
            cin >> x;
            arr.push_back(x);
            s+=x;
        }
        if(s<=N){
            for(int x : arr) cout << x << " "; 
            cout << "sum:" << s <<endl;
            arr.clear();
            continue;
        }
        ncr(0);
        for(int x: maxv) cout << x << " ";
        cout << "sum:"<< maxsum<<endl;
        sum =0;
        maxsum = 0;
        sel.clear();
        arr.clear();
    }

    debug("Total Time: %.3f\n", (double)(clock() - z) / CLOCKS_PER_SEC);
}

```


