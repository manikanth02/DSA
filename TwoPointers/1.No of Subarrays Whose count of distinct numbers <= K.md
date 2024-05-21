No of Subarrays Whose count of distinct numbers <= K

```
#include <bits/stdc++.h>
using namespace std;
int main() {
    vector<int>A = {2,1,1,5,8};
    int i = 0;
    int j = 0;
    int count = 0;
    int sum = 0;
    int size = A.size();
    int k = 2;
    unordered_map<int,int>mp;
    while(i < size && j < size){
        mp[A[j]]++;
        while(mp.size() > k){
            mp[A[i]]--;
            if(mp[A[i]] == 0){
                mp.erase(A[i]);
            }
            i++;
        }
        count += (j - i + 1);
        j++;
    }
    cout<<count<<"\n";
    return 0;
}


```
