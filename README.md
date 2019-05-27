**我的代码**

```cpp
class Solution {
public:
    vector<int> printMatrix(vector<vector<int> > matrix) {
        vector <int> result;
        int rows = matrix.size();//有多少行
        int cols = matrix[0].size();//有多少列
        int top =0;
        int bottom =rows-1;
        int left =0;
        int right = cols-1;
        //循环截止的判定条件
        while(top<=bottom && left<=right){
        for(int i=left;i<=right;i++){
            result.push_back(matrix[top][i]);
            top++;
        }
        for(int i=top;i<=bottom;i++){
            result.push_back(matrix[i][right]);
            right--;
        }
        for(int i=right;i>=left;i--){
            result.push_back(matrix[bottom][i]);
            bottom--;
        }
        for(int i=bottom;i>=top;i--){
            result.push_back(matrix[i][left]);
            left++;
        }
        }
        return result;
    }
};
```

**别人的答案**

```cpp
class Solution {
public:
    vector<int> printMatrix(vector<vector<int> > matrix) {
        int rows = matrix.size();            //行数
        int cols = matrix[0].size();        //列数
        vector<int> result;
        
        if(rows == 0 && cols == 0){
            return result;
        }
        int left = 0, right = cols - 1, top = 0, bottom = rows - 1;
        
        while(left <= right && top <= bottom){
            //从左到右
            for(int i = left; i <= right; ++i){
                result.push_back(matrix[top][i]);
            }
            //从上到下
            for(int i = top + 1; i <= bottom; ++i){
                result.push_back(matrix[i][right]);
            }
            //从右到左
            if(top != bottom){
                for(int i = right - 1; i >= left; --i){
                    result.push_back(matrix[bottom][i]);
                }
            }
            //从下到上
            if(left != right){
                for(int i = bottom - 1; i > top; --i){
                    result.push_back(matrix[i][left]);
                }
            }
            left++, top++, right--, bottom--;
        }
        return result;
    }
};
```
