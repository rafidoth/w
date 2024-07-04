# Uva 10344 - 23 out of 5


```cpp
#include<bits/stdc++.h> 
using namespace std;
typedef long long int lli;
#define MOD 1000000007


vector<int> arr(5);

int calc(int v1, int v2,int i ){
    if(i==0) return v1+v2; else if(i==1) return v1-v2;
    else return v1*v2;
}

bool func(vector<int> seq ){
   int f = false;
   for(int x =0; x<3;x++){
       for(int y =0; y<3;y++){
           for(int z = 0; z<3;z++){
               for(int a =0; a<3;a++){
                   //cout << x << y << z << a ;
                   int res = calc(seq[0], seq[1],x) ;
                   res = calc(res, seq[2],y);
                   res = calc(res, seq[3],z);
                   res = calc(res, seq[4],a);
                  // cout << "res = "<< res <<endl;
                   if(res == 23) {
                       //for(int m : seq) cout << m << " ";
                       //cout <<endl;
                       //cout << x<< y << z<< a<<" " << res << endl;
                       f = true;
                       break;
                   }
               }
               if(f) break;
           }
           if(f) break;
       }
       if(f) break;
   } 
   if(f) return true;
   else return false;
}

vector<int> sel;
bool vTaken[10];
bool f = false;
void value_permutation(){
    if(f) return;
    if((int)sel.size() == 5){
        bool ans = func(sel);
        if(ans){
            //for(int x : sel) cout << x << " ";
            //cout<<endl;
            f = true;
        } 
        return;
    }
    for(int i = 0; i< 5;i++){
        if(!vTaken[i]){
            sel.push_back(arr[i]);
            vTaken[i] = true;
            value_permutation();
            sel.pop_back();
            vTaken[i] = false;
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
    int t = 0;
    while(cin >> arr[0]){
        int s = 0;
        for(int i = 1; i<5;i++){
            cin >> arr[i];
            s+= arr[i];
        }
        if(s== 0) break;
        t++;
        //cout << "test case" <<t<<endl;
        f = false;
        value_permutation(); 
        if(f) cout << "Possible" <<endl; 
        else cout << "Impossible" <<endl;
    }
}



```