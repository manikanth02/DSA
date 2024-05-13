

Given an array of integers, a and a max score m . Score of a subsequence [a[i1], a[i2] ... a[ik]] is defined as i1 * k + a[i1] + i2 * k + a[i2] + ... + ik * k + a[ik]. Now, find the length of largest subsequence whose score <= m.
Example:
Input: n = 4, a = [4, 3, 2, 1], max score = 33.
Output: 3
Optimal Subsequence Indexes: [1, 2, 4]. As, score is (1 * 3 + 4) + (2 * 3 + 3) + (4 * 3 + 1) = 29 <= 33
Constriants:

1 <= n <= 2e5
1 <= a[i] <= 10000
1 <= max score <= 1e15
It is guarenteed that at least one of the elements of the array is less than max score.


```

#include <bits/stdc++.h>
using namespace std;
bool check(int k,vector<int>& A,int m){

    vector<int>B;

    for(int i = 1; i <= A.size(); i++){
        int val = A[i - 1] + (i*k);
        B.push_back(val);
    }

    sort(B.begin(),B.end());

    int i = 0;
    int sum = 0;
    while(i <= k){
        sum += A[i];
        i++;
    }
    if(sum <= m){
        return true;
    }
    return false;
}
int main() {
    vector<int> A = {4,3,2,1};
    int n = 4;
    int m = 33;
    int ans = 0;
    // for(int k = 1; k <= n; k++){
    //     if(check(k,A,m)){
    //         ans = k;
    //     }else{
    //         break;
    //     }
    // }
    int left = 1;
    int right = n;
    while(left <= right){
        int mid = left + (right-left)/2;
        if(check(mid,A,m)){
            ans = mid;
            left = mid + 1;
        }else{
            right = mid - 1;
        }
    }
    cout<<ans<<"\n";
    return 0;
}
```

