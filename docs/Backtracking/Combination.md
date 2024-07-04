# Combination Skeleton



```cpp

int N;
int k;
vector<int> arr;
vector<int> sel;
int r= 3;
void ncr(int curr){
    if((int)sel.size() == r){
        for(int x : sel) cout << x << " ";
        cout << endl;
        return;
    }
    for(int i =curr; i<k;i++){
        sel.push_back(arr[i]);
        ncr(i+1);
        sel.pop_back();
    }
}

```