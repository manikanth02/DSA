##

https://www.scaler.com/academy/mentee-dashboard/class/34567/assignment/problems/161/?navref=cl_pb_nv_tb

```
//   idea-1 -     BRUTE FORCE APPROACH::

// T.C::O(N^3)
// s.c::O(N)

#include<bits/stdc++.h>
using namespace std;
int main() {
    string s = "hiuhucuhehuieihiuireieherfurfirggruurgieruiur";
    int n = s.size();
    int maxm = 1;
    for(int i = 0; i < n; i++){
        for(int j = i; j < n; j++){
            unordered_set<char>st;
            for(int k = i;k <= j;k++){
                st.insert(s[k]);
            }
            if(st.size() == j - i + 1){
                maxm = max(maxm, j - i + 1);
            }
        }
    }
    cout<<"Length of the longest substring which have not repeating characters  :  "<<maxm<<"\n";
    return 0;
}


```


```

//    idea2  -  BETTER 

// T.C::O(N^2)
// s.c::O(N)

//APPROACH:: We take each elements as starting points of substring and calculate maxm lengths

#include<bits/stdc++.h>
using namespace std;
int main() {
    string s = "hiuhucuhehuieihiuireieherfurfirggruurgieruiur";
    int n = s.size();
    int maxm = 1;
    for(int i = 0; i < n; i++){
        unordered_set<char>st;
        for(int j = i; j < n; j++){
            if(st.find(s[j]) == st.end()){
                st.insert(s[j]);
            }else{
                break;
            }
        }
        int sizeOfSet = st.size();
        maxm = max(maxm,sizeOfSet);
    }
    cout<<"Length of the longest substring which have not repeating characters  :  "<<maxm<<"\n";
    return 0;
}


```


```
idea3 - binary search + sliding windows

Approach:: length have minm length = 1 and maxm length = s.size();
and check for length = left + (right - left)/2

and check function is basically to check whether is there any subarray of length mid(k) which have all distinct characters


T.C::O(NlogN)
s.c::O(n)




```


//idea-4  OPTIMAL APPROACH
// T.C::O(N)
// S.C::O(N)

// TWO POINTERS WITH HASHSET
int Solution::lengthOfLongestSubstring(string A) {

    int i = 0;
    int j = 0;
    int ans = 0;
    int size = A.size();
    unordered_set<char>st;

    while(j < size){
        if(st.find(A[j]) == st.end() ){
            st.insert(A[j]);
            int length = st.size();
            ans = max(ans,length);
            j++;
        }else{
            st.erase(A[i]);
            i++;
        }
    }
    return ans;   
}

```


























