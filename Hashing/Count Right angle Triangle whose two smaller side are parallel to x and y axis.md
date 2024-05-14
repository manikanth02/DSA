https://www.scaler.com/academy/mentee-dashboard/class/34564/assignment/problems/4719/submissions?navref=cl_pb_nv_tb

```
BETTER
T.C::O(N^2)
S.C::O(N)


int mod = 1e9 + 7;

// T.C:: O(N^2)
// S.C::O(N)
int Solution::solve(vector<int> &A, vector<int> &B) {
    // used set to store all points,used to check if a particular points exists or
    // not
    int size = A.size();
    // edge case when points is less than 3
    if(size < 3)return 0;
    unordered_set<string>st;
    for(int i = 0; i < size; i++){
        string points = to_string(A[i]) + "@" + to_string(B[i]);
        st.insert(points);
    }
    long count = 0;
    
    //Fixed two points and search for 3 points
    for(int i = 0; i < size; i++){
        for(int j = i + 1; j < size; j++){

            int x1 = A[i];
            int y1 = B[i];

            int x2 = A[j];
            int y2 = B[j];

            // we must pick two points such that line joining two points not be parallel to x-asis
            //or y-axis becaues then we can't decide our third points
            if(x1 != x2 && y1 != y2){
            string temp1 = to_string(x1) + "@" + to_string(y2);
            string temp2 = to_string(x2) + "@" + to_string(y1);

            if(st.find(temp1) != st.end()){
                count = (count + 1)%mod;
            }
            if(st.find(temp2) != st.end()){
                count = (count + 1)%mod;
            }
            }
        }
    }
    return count;

}
```


```

// T.C:: O(N)
// S.C::O(N)
//OPTIMAL APPROACH

int mod = 1e9 + 7;

int Solution::solve(vector<int> &A, vector<int> &B) {
    int size = A.size();
    if(size < 3)return 0;
    unordered_map<int,int>mp1,mp2;
    for(auto x: A){
        mp1[x]++;
    }
    for(auto y: B){
        mp2[y]++;
    }
    long count = 0;
    for(int i = 0; i < size; i++){
        long count1 = mp1[A[i]];
        long count2 = mp2[B[i]];

        count += ((count1 - 1)*(count2 - 1))%mod;
    }
    return count;
}

// Approach::The intuition is that we set one point and check 
// 1.count1 = no of points equal to y-axis 
// 2.count2 = no of points equal to x-axis

// ans += ((count1 - 1)*(count2 - 1))




// 1,3,5,5,1
// 3,3,3,1,1
// mp1 =[
//     1:2,
//     3:1,
//     5:2,
// ]

// mp2 =[
//     3:3,
//     1:2,
// ]


```
