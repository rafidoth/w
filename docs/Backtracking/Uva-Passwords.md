# UVa 628 - Passwords

```cpp
#include<bits/stdc++.h> 
using namespace std;
typedef long long int lli;
#define MOD 1000000007

int N;
vector<string> words;
vector<string> sel;
void f(int curr,string rule){
    if(sel.size() ==  rule.size()) {
        for(string p : sel) cout << p ;
        cout <<endl;
        return;
    }
    if(rule[curr] == '#') {
        for(int i= 0;i<N;i++){
            sel.push_back(words[i]);
            f(curr+1,rule);
            sel.pop_back();
        }
    } else{
        for(int i = 0 ;i <10; i++){
            char x = char(i+48);
            string str = "";
            str+= x;
            sel.push_back(str);
            f(curr+1,rule);
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
    while(cin >> N){
        cout << "--" << endl;
        words.clear(); 
        for(int i =0 ; i<N;i++){
           string s; 
           cin >> s;
           words.push_back(s);
        }
        int k ;
        cin >> k;
        for(int i =0; i<k;i++){
            string rule;
            cin >> rule;
            f(0,rule);
        }


    }

}



```