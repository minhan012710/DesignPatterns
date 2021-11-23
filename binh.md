**Iterator** 
- Là một mẫu thiết kế hành vi cho phép duyệt tuần tự thông qua một cấu trúc dữ liệu phức tạp mà không để lộ các chi tiết bên trong của nó. Ý tưởng chính của mẫu Iterator là trích xuất hành vi truyền tải của một tập hợp thành một đối tượng riêng biệt được gọi là trình vòng lặp.
- Ví dụ như trình vòng lặp hồ sơ mạng xã hội,  mẫu Iterator được sử dụng để duyệt qua các hồ sơ có trong một bộ sưu tập mạng xã hội từ xa mà không để lộ bất kỳ chi tiết giao tiếp nào với phía client.
- VD trong project (https://github.com/abishekaditya/DesignPatterns/blob/master/IteratorPattern/Client.cs)
 public class Client
    {
        private IEnumerable _breakfast;
        private IEnumerable _dinner;

        public Client(BreakfastMenu breakfast, DinnerMenu dinner)
        {
            this._breakfast = breakfast.Items;
            this._dinner = dinner.Items;
        }

        public void PrintMenu()
        {
            var breakfast = _breakfast;
            PrintMenu(breakfast);
            var dinner = _dinner;
            PrintMenu(dinner);
        }

        private void PrintMenu(IEnumerable iter)
        {
            foreach (var item in iter)
            {
                var i = (Menu)item;
                Console.WriteLine($"{i.Name}  Rs. {i.Price} {  (i.Vegetarian ? "*" : "x") } \n {i.Description} ");

            }
        }
    }
    - So sánh
    + khá giống nhau vì nó không để lộ các thuộc tính có bên trong class.
    
  ** Mediator**
  
    
