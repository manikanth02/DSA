###Two pointers Template

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
    int k = 4;
    while(i < size && j < size){
        sum += A[j];
        while(sum > k){
            sum -= A[i];
            i++;
        }
        count += (j - i + 1);
        j++;
    }
    cout<<count<<"\n";
    return 0;
}
```
