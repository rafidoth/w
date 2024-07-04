# Leetcode - N Queen Problem
```cpp
#include<bits/stdc++.h> 
using namespace std;
typedef long long int lli;
#define MOD 1000000007

using vi = vector<int>;
vi sel;
vector<vi> ans;
bool taken[10];
int N;
// row check -> sel arr index
// col check -> permutation
// diag. check -> 
void notsofun(){
   if((int)sel.size() == N){
       /*
       for(int x : sel) cout <<  x << " ";
       cout << endl;
       */
        ans.push_back(sel);
       return;
   }

   for(int i = 0;i<N;i++){
       if(!taken[i]){
           int p = sel.size();
           // diagonal check
           if(p>0){
               bool flag = false;
               for(int h=0;h<p;h++) {
                   int r1 = h;
                   int c1 = sel[h];
                   int r2 = p; 
                   int c2 = i;
                   if(abs(r1-r2) == abs(c1-c2)){
                       flag = true;
                       break;
                   }
               }
               if(flag){
                   continue;
               }
           }     
           sel.push_back(i);
           taken[i] = true;
           notsofun();
           sel.pop_back();
           taken[i] = false;
       }
   }
}


vector<vector<string>> solveNQueens(int n) {
    N = n;
    notsofun();
    vector<vector<string>> etai_ans;
    int m =ans.size(); 
    for(int i = 0 ; i<m;i++){
        vector<int> curr = ans[i];
        vector<string> board;
        for(int p = 0;p<n;p++){
            string line= "";
            for(int q = 0;q<n;q++){
                if(curr[p]==q) line+='Q';
                else line+= '.';
            }
            board.push_back(line);
        }
        etai_ans.push_back(board);
    }
    return etai_ans;
    
}


int main(){
    #ifndef ONLINE_JUDGE
      freopen("input.txt", "r", stdin);
      freopen("output.txt", "w", stdout);
    #endif

    ios_base::sync_with_stdio(0);
    cin.tie(0);
    vector<vector<string>> a = solveNQueens(5);
    for(int i = 0;i<(int)a.size();i++){
        for(string x : a[i]) cout << x << endl;
        cout <<endl;
    }
}


```