```cpp
#include<bits/stdc++.h> 
using namespace std;
typedef long long int lli;
#define MOD 110000000007
#define debug(...) fprintf(stderr, __VA_ARGS__), fflush(stderr)


int N;

bool taken[20];
string sel =  "";
// 10! = 3528800
bool f= false;
vector<string> pre;
void func(){
    if((int)sel.size() == 5){
        pre.push_back(sel);
        return;
    }
    for(int i = 0; i<=9;i++){
        if(!taken[i]){
            char x = i+48;
            sel +=x;
            taken[i] = true;
            func();
            sel.pop_back();
            taken[i] = false;
        }
    }
}


int main(){
    #ifndef ONLINE_JUDGE
      freopen("input.txt", "r", stdin);
      freopen("output.txt", "w", stdout);
    #endif
    clock_t z = clock();
    ios_base::sync_with_stdio(0);
    cin.tie(0);
    func();
    while(cin >> N){
        if(N==0) break;

        for(string x : pre){
            string num2  = x; 
            long long int b = 0;
            bool check[10];
            for(char y : num2){
               b*=10; 
               int m = (int(y)-48);
               b+= m;
               check[m] = true;
            }
            long long int a = N*b;
            long long int cp = a;
            while(cp!=0){
                int l = cp %10;
                cp/=10;
                if(check[l] == true){
                    break;
                }else{
                    check[l] = true;
                }
            }
            int cnt =0;
            for(bool z : check) if(z) cnt++;
            if(cnt==10) cout << b << "/ "<< a<<endl;
            
        }
    }
    debug("Total Time: %.3f\n", (double)(clock() - z) / CLOCKS_PER_SEC);
}



```