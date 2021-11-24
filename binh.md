**Iterator** 
- Là một mẫu thiết kế hành vi cho phép duyệt tuần tự thông qua một cấu trúc dữ liệu phức tạp mà không để lộ các chi tiết bên trong của nó. Ý tưởng chính của mẫu Iterator là trích xuất hành vi truyền tải của một tập hợp thành một đối tượng riêng biệt được gọi là trình vòng lặp.
- Ví dụ như trình vòng lặp hồ sơ mạng xã hội,  mẫu Iterator được sử dụng để duyệt qua các hồ sơ có trong một bộ sưu tập mạng xã hội từ xa mà không để lộ bất kỳ chi tiết giao tiếp nào với phía client.
- VD trong project (https://github.com/abishekaditya/DesignPatterns/blob/master/IteratorPattern/Client.cs).

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
    .
    
    - So sánh
    + khá giống nhau vì nó không để lộ các thuộc tính có bên trong class.
    
  ** Mediator**
  -làm giảm sự ghép nối giữa các thành phần của chương trình bằng cách làm cho chúng giao tiếp gián tiếp, thông qua một đối tượng trung gian đặc biệt.
  - ví dụ rất nhiều phần tử GUI hợp tác với sự trợ giúp của người trung gian nhưng không phụ thuộc vào nhau.
  - VD trong project (https://github.com/abishekaditya/DesignPatterns/blob/master/MediatorPattern/Customer.cs).
  
   class Customer : Colleague
    {
        public Customer(Mediator mediator) : base(mediator) { }

        public override void Notify(string message)
        {
            Console.WriteLine($"Message to customer: {message}");
        }
    }
    .
    
    - so sánh : về cơ bản thì giống với cách sử dụng trong phần lý thuyết nhưng khác nhau ở chỗ trong phần này thì lớp Customer không kế thừa lớp Mediator mà sử dụng một đối tượng Mediator. 
    
    **Memento**
    - cho phép tạo ảnh chụp nhanh trạng thái của một đối tượng và khôi phục nó trong tương lai.
    - không làm ảnh hưởng đến cấu trúc bên trong của đối tượng mà nó làm việc cùng, cũng như dữ liệu được lưu giữ bên trong ảnh chụp nhanh.
    - trong project không sử dụng mẫu này.
    
    **Observer **
    - cho phép một số đối tượng thông báo cho các đối tượng khác về những thay đổi trong trạng thái của chúng.
    - cung cấp một cách để đăng ký và hủy đăng ký cho bất kỳ đối tượng nào triển khai giao diện người đăng ký.
    - VD trong project(https://github.com/abishekaditya/DesignPatterns/blob/master/ObserverPattern/WeatherSupplier.cs)
    - so sánh: cơ bản thì giống nhau, chỉ khác ở cách xử lý sự kiện
    
    **State**
    - là một mẫu thiết kế hành vi cho phép một đối tượng thay đổi hành vi khi trạng thái bên trong của nó thay đổi.
    - State pattern gợi ý nên tạo các lớp mới cho tất cả các trạng thái có thể có của một đối tượng và trích xuất tất cả các hành vi dành riêng cho trạng thái vào các lớp này.
    - VD trong project(https://github.com/abishekaditya/DesignPatterns/blob/master/StatePattern/GumballMachine.cs).
    
     public void InsertQuarter()
        {
            State.InsertQuarter();
        }

        public void EjectQuarter()
        {
            State.EjectQuarter();
        }

        public void TurnCrank()
        {
            State.TurnCrank();
            State.Dispense();
        }

        public void ReleaseBall()
        {
            Console.WriteLine("A ball comes rolling down");
            if (Count == 0) return;
            Count--;
        }
    }
    
    - So sánh : giống với cách sử dụng trong lý thuyết.
    
   **Strategy**
    - là một mẫu thiết kế biến một tập hợp các hành vi thành các đối tượng và làm cho chúng có thể hoán đổi cho nhau bên trong đối tượng ngữ cảnh ban đầu.
    - Strategy pattern gợi ý rằng nên chọn một lớp thực hiện điều gì đó cụ thể theo nhiều cách khác nhau và trích xuất tất cả các thuật toán này thành các lớp riêng biệt.
    - VP trong project (https://github.com/abishekaditya/DesignPatterns/blob/master/StrategyPattern/QuackSqueak.cs).
    
     class QuackSqueak : IQuackBehaviour
     {
        public void Quack()
        {
            Console.WriteLine("Squeeeak");
        }
     }
    - So sánh : giống với cách sử dụng trong lý thuyết.
    
    **Template Method**
    - là một mẫu thiết kế cho phép bạn xác định khung của một thuật toán trong một lớp cơ sở và để các lớp con ghi đè các bước mà không thay đổi cấu trúc của thuật toán tổng thể.
    - Template Method khá phổ biến trong các khung công tác Java. Các nhà phát triển thường sử dụng nó để cung cấp cho người dùng khung một phương tiện đơn giản để mở rộng chức năng tiêu chuẩn bằng cách sử dụng tính năng kế thừa.
    - VD trong project (https://github.com/abishekaditya/DesignPatterns/blob/master/TemplatePattern/Comparable/Person.cs)
    - So sánh: giống với cách sử dụng trong lý thuyết do thuật toán trong lớp Person không làm thay đổi cấu trúc của thuật toán tổng thể mà chỉ đối chiếu đối tượng đầu vào với đối tượng Person.
    **Visitor**
    - là một mẫu thiết kế hành vi cho phép thêm các hành vi mới vào hệ thống phân cấp lớp hiện có mà không thay đổi bất kỳ mã hiện có nào.
    - Visitor pattern không phải là một mẫu quá phổ biến vì tính phức tạp và khả năng áp dụng hẹp của nó.
    - VD trong project (https://github.com/abishekaditya/DesignPatterns/blob/master/VisitorPattern/LivingRoomVisitor.cs).
    
     public class LivingRoomVisitor : IUnitVisitor
    {
        public void VisitApartment(Apartment apartment)
        {
        }

        public void VisitStudio(Studio studio)
        {
        }

        public void VisitBedroom(Bedroom bedroom)
        {
        }

        public void VisitLivingRoom(LivingRoom livingRoom)
        {
            Console.WriteLine("This is the living room");
        }
    }
    - So sánh: khá giống nhau về cách sử dụng, vì các phương thức được thêm vào trong class không làm thay đổi hành vi của các đoạn code trước đó 


     
    
