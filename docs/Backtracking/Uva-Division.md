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
    // clock_t z = clock();
    ios_base::sync_with_stdio(0);
    cin.tie(0);
    func();
    int t = 0;

    while(cin >> N){
        if(N==0) break;
        t++;    
        if(t!=1) cout << endl;
        bool q = false;
        for(string x : pre){
            string num2  = x; 
            long long int b = 0;
            set<char> chk;
            for(char y : num2){
               b*=10; 
               int m = (int(y)-48);
               b+= m;
               chk.insert(y);
            }
            long long int a = N*b;
            long long int cp = a;
            int u = 0;
            while(cp!=0){
                u++;
                if(u>5) break;
                int l = cp %10;
                cp/=10;
                chk.insert(char(l+48));
            }
            if(u>5) continue;
            int cnt = chk.size();
            if(cnt==10){
                 q = true;
                 if(x[0]=='0') cout << a <<" / 0"<<b <<" = "<< N<<endl;
                 else cout << a << " / "<< b<< " = " << N<<endl;
            }
            
        }
        if(!q) cout << "There are no solutions for " << N << "." << endl;
    }
    //debug("Total Time: %.3f\n", (double)(clock() - z) / CLOCKS_PER_SEC);
}




```