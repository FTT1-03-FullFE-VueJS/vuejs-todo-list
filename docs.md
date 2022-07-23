## 1. Create new
- tạo mới 1 todo.
- clear input data.
- hidden form.
- changed text of toggle form.

Quy tắc
1 Không được thay đổi giá trị của props.
2 Chỉ có thể thay đổi giá trị của state.


## 2. Delele item
- Bắt sự kiện click delete button
- Emit id của todo mà mình muốn xóa ra ngoài state
- Tìm trong todos có todo nào trùm với id mình muốn xóa không
- Nếu có thì xóa nó đi
- Nếu không thì thông báo "Todo is not defind"
- Cải thiện
    + 1: Confirm trước khi delete
    + 2: Message để hiện thị khi không còn todo nào nữa.

## 3. Update item
- Bắt sự kiện click update button
- Emit id của todo mà mình muốn update ra ngoài state
- Tìm trong todos có todo nào trùm với id mình muốn update không
- Nếu có thì
    + Open form
    + Đổi text của button submit từ "Create new" thành "Update"
    + Truyền title của todo đã chọn vào trong input
- Xử lý update todos
- Nếu không thì thông báo "Todo is not defind"
