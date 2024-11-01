## Bài toán
Cho số tự nhiên N. Hãy tìm số nguyên dương X nhỏ nhất được tạo thành bởi các chữ số 8 và 0 sao cho X chia hết cho N.

### Ví dụ
- Với N = 5, số X = 80 là số nhỏ nhất thỏa mãn điều kiện.

### Ràng buộc
- T ≤ 100, N ≤ 200

### Input
- 6
- 61
- 79
- 45
= 129
- 5
- 176

###  Ouput
- 800808
- 80080088
- 8888888880
- 800800008
- 80
- 880


### Ý tưởng
Để tìm số nhỏ nhất X chỉ bao gồm các chữ số 8 và 0 và chia hết cho N:
1. Sử dụng BFS (tìm kiếm theo chiều rộng) để tìm các số có dạng này.
2. Bắt đầu từ số nhỏ nhất là 8, rồi lần lượt thêm các chữ số 0 hoặc 8 để tạo ra số mới.
3. Kiểm tra điều kiện chia hết cho N, nếu tìm được số chia hết thì dừng lại và in kết quả.

```cpp
int main(){
    FileIO();
    queue<long long > q;
    vector<long long> v;
    q.push(8);
    v.push_back(8);

    while (true){
        long long top = q.front(); q.pop();
        if (top > 1e18) break;
        v.push_back(top);
        q.push(top * 10);
        q.push(top * 10 + 8);
    }
    int t; cin >> t;
    while (t--){
        int n; cin >> n;
        for (long long x : v){
            if (x % n == 0){
                cout << x << endl;
                break;
            }
        }
    }
}
```
