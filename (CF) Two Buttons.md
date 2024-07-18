Vasya đã tìm thấy một thiết bị kỳ lạ. Trên bảng điều khiển phía trước của thiết bị có: một nút màu đỏ, 
một nút màu xanh và một màn hình hiển thị một số nguyên dương. Sau khi nhấn nút màu đỏ, thiết bị nhân đôi số hiển thị. 
Sau khi nhấn nút màu xanh, thiết bị trừ một khỏi số trên màn hình. Nếu tại bất kỳ thời điểm nào số này không còn là số dương, 
thiết bị sẽ bị hỏng. Màn hình có thể hiển thị số lớn tùy ý. Ban đầu, màn hình hiển thị số n.

Bob muốn màn hình hiển thị số m. Số lần nhấn nút tối thiểu mà Bob phải thực hiện để đạt được kết quả này là bao nhiêu?

### Đầu vào:
- Một số nguyên dương n (giá trị ban đầu trên màn hình).
- Một số nguyên dương m (giá trị mong muốn trên màn hình).
### Đầu ra:
- Số lần nhấn nút tối thiểu để biến n thành m.
### Giải thích:
- Nhấn nút đỏ sẽ nhân đôi số trên màn hình.
- Nhấn nút xanh sẽ trừ một khỏi số trên màn hình.
- Cần tìm số lần nhấn nút tối thiểu để biến n thành m mà không để số trên màn hình trở thành số không dương.

### input
4 6
### output
2
### input
10 1
### output
9
### Note
- In the first example you need to push the blue button once, and then push the red button once.
- In the second example, doubling the number is unnecessary, so we need to push the blue button nine times.

```cpp
int solve(int s, int t){
    queue<pair<int,int>> Q;
    Q.push({s,0});
    set<int> se;
    se.insert(s);
    while (!Q.empty()){
        pair<int,int> x = Q.front(); Q.pop();
        if (x.first == t) return x.second;

        // x.first - 1
        if (x.first > 1 && se.count(x.first - 1) == 0){
            Q.push({x.first - 1, x.second + 1});
            se.insert(x.first - 1);
        }

        // x.first * 2
        if (x.first < t && se.count(x.first * 2) == 0){
            Q.push({x.first * 2, x.second + 1});
            se.insert(x.first * 2);
        }
    }
    return -1;
}

int main(){
    int s, t; cin >> s >> t;
    cout << solve(s,t) << endl;
    return 0;
}
```
