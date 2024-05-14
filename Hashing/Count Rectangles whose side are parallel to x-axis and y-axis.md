
https://www.scaler.com/academy/mentee-dashboard/class/34564/assignment/problems/4759/?navref=cl_pb_nv_tb




```
T.C::O(N^2)
S.C::O(n)

APPROACH::
Fixed two point (x1,y1) and (x2,y2) and if (x1 != x2 && y1 != y2) then we get
 recatngles which is parallel to x-axis and y-axis only when 3rd and 4th points are (x1,y2) and (x2,y1) 
respectively.

```
```

int Solution::solve(vector<int> &A, vector<int> &B) {
    // used set to store all points,used to check if a particular points exists or
    // not
    int size = A.size();
    // edge case when points is less than 3
    if(size < 4)return 0;
    // unordered_set<string>st;
    map<pair<int,int>,int>mp;
    // for(int i = 0; i < size; i++){
    //     string points = to_string(A[i]) + "@" + to_string(B[i]);
    //     st.insert(points);
    // }
    for(int i = 0; i < size; i++){
        mp[{A[i],B[i]}]++;
    }
    long count = 0;
    
    //Fixed two points and search for 3 points
    for(int i = 0; i < size; i++){
        for(int j = i + 1; j < size; j++){
            int x1 = A[i];
            int y1 = B[i];
            int x2 = A[j];
            int y2 = B[j];
            if(x1 != x2 && y1 != y2){
            // string temp1 = to_string(x1) + "@" + to_string(y2);
            // string temp2 = to_string(x2) + "@" + to_string(y1);

            // if(st.find(temp1) != st.end() && st.find(temp2) != st.end()){
            //     count = (count + 1);
            // }
            if(mp[{x1,y2}] != 0 && mp[{x2,y1}] != 0){
                count++;
            }
            }
        }
    }
    // edge case:
    // SUPPOSE THERE ARE FOUR POINTS A,B,C,D then if we find a reactnagle 
    // as ABCD .Suppose we find a recatngle for A then we also get a recatngle for 
    //C .so end divide by 2
    return count/2;
}



```
