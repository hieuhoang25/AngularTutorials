# Angular Framework
## 1.Get Started
1. Tao project Angular
```java
ng new lab1
```
2. Build and thực thi project Angular
```java
ng serve
```
3. Cấu truc file và folder
- node_modules: folder chứa các modules của Angular
- src : folder chứa source code project
- .browserslistrc: các version browser tương thích với project
- .editorconfig : cấu hình VS Code.
- .gitignore : khai báo các file sẽ bỏ qua khi đưa lên github
- angular.json : nơi cấu hình Angular CLI
- karma.config.js : cấu hình chạy các testing (kiểm thử)
- package.json: chứa thông tin các thư viện cần trong project
- src/app : chưa code chính của project
- src/app/app.component.html: là file view chưa code html và dữ liệu show cho người dùng
- src/app/app.component.ts : là file component chính, chứa các hàm và biến để thao tác
- src/app/app.component.css : chứa định dạng css cho app.component.html
- src/app/app.modules.ts: nơi nhúng các module dùng trong project
- src/app/app-routing.module.ts: nơi định nghĩa các route trong project

## Sử dụng component trong angular
1. Giới thiệu về component trong angular
==> Mỗi ứng dụng Angular là một tập hợp nhiều component, bởi vậy sử dụng component rất quan trọng. Khi tạo mới 1 project, Angular CLI đã tạo sẵn cho bạn 1 component gốc có tên là AppComponent (đặt trong folder src/app), sau đó thì bạn có thể tạo các component cn khác trong ứng dụng web của mình.
==> Một component trong Angular bao gồm 3 thứ: template, class và metadata. Template còn gọi là view = nơi bạn code html và hiển thị dữ liệu (trong class). Class là file .ts viết băng typescript - nơi định nghĩa các hàm, khai báo và gán giá trị cho các biến, thực hiện xử lý, tính toán... Còn metadata là nơi khai báo các thông tin bổ sung cho component.
![alt](https://longnv.name.vn/wp-content/uploads/2022/05/image-6.png)
![alt](https://longnv.name.vn/wp-content/uploads/2022/05/image-7.png)
==> AppComponent là component gốc, các component tạo ra sau là con AppComponent này.Bạn có thể tạo nhiều component cho ứng dụng minh như Component Đăng nhập , Đăng ký, Sản phầm bán chạy, Chi tiết sản phẩm, Bình luận, Liên hệ , Giới thiệu,... tùy nhu cầu. Trong mỗi component, file.ts là file coding chính.
2. Tạo component trong angular
==> Để tạo 1 component trong angular, bạn dùng lệnh như sau:
```java
ng g c [-t][-s] <Tên Component>
```
Lệnh sẽ thực hiện các việc sau:
- Tạo 1 folder con trong app dể chứa component
- lệnh cũng tạo file <tên-component>.component.ts, đây là file class, là nơi chứa code chính của Angular
- File có tên <tên-component>.component.html, đây là file template của component, còn gọi là view, nơi bạn sẽ code html và hiện dữ liệu
- File có tên <ten-component>.component.css, đây là file chứa các định dạng css cho các tag trong file view
- File dụng cho mục đích test cũng đc tạo có tên dile là <tên-component>.component.spec.ts
- Thêm 1 dùng import và khai báo cho componnet mới tạo trong file src/app/app.module.ts
Các option của lệnh;
- -t(-inline-template) : không tọa file html, dùng template ngay trong componet
- -s(-inline-stype) : không tạo file css, sử dụng css trực tiệp trong componet
3. Hiện component angular ra trong web
Để hiện nội dung component đã tạo, viết tag theo tên select trong file .ts của component Vi du:
Trong app.component.html (hoặc trong file view nào đó), code sau là để hiện thông ti trong component sản phẩm bán chạt đã tọa ở trên
```html
<app-san-pham-ban-chay><app-san-pham-ban-chay>

```
4. Xóa component angular
==> Để xóa component đã tạo, bạn thực hiện thủ công bằng cách xóa folder component, sau đó mở file app.modules.ts rồi xóa lệnh import component + xóa tên component trong phần declaration.
5. Các chỉ thị thường dùng trong view Angular
==> *ngIf, *ngFor, *ngSwitch,... giúp hiển thị dữ liệu trong view
6. Component lồng nhau
Trong mỗi ứng dụng angular, bạn sẽ phải tạo nhiều component để thực hiện các yêu cầu về nghiệp vụ, như component san phẩm chạy, sản phẩm hot, chi tiết sản phẩm, bình luận, giỏ hàng, đăng ký,... 
- Tạo component dangnhap : 
```java
ng g c dangnhap
```
- Thực hiện view con
```java
<!-- dangnhap.component.html-->
<div class="formdangnhap text-white">
<p><label>Email</label><input type="email" class="form-control"> </p>
<p><label>Pass</label><input type="password" class="form-control"> </p>
<p><button class="bg-info p-2 border-0">Đăng nhập</button></p>
</div>
```
- Nhúng view con vào
```java
<!-- app.component.html-->
<app-dangnhap></app-dangnhap>
```
7. Truyền dữ liệu giữa các component
Có 2 cách để truyền dữ liệu giữa các conponent:
- Cha -> Con : @Input -> dùng để nhận giá trị ngoài truyền từ cha vào con
- Con -> Cha : @Output -> dùng để bắn giá trị từ con ra component cha mỗi khi có sự kiện gì đó (tùy bạn code) xảy ra tring view on. Truong @Output bạn sử dụng đối tượng Event Emitter để thực hiện chuyễn dữ liệu.
8. Vòng đời của component trong Angular
==> Vòng đời (lifecycle) của component tính từ lúc nó được tạo, đến lúc cuôi đời là component bị hủy. Angular có chức năng cho phép bạn thực thi các hàm của mình để thực hiện những can thiệp trong vòng đời của từng component
- ngOnchanges : có 1 tham số kiểu SimpleChange, thông qua tham số này, bạn có thể truy xuất giá trị mới, giá trị vũ trc và sau thay đổi
- ngOnInit:nó chạy sau hàm contructor và hàm ngOnchange(lần đầu). Trong hàm này có thể thuocj ư hiện các công việc dùng khi componenet khởi tạo, như án giá trị khởi đầu cho các biến, gọi api, ghi log, khởi tạo form... 
- ngDoCheck: hàm này sẽ chạy mỗi component phát hiện ra có sự thay đổi dữ liệu ở component. Hàm ngDoCheck() thực thi ngay sau hàm ngOnchanges() và ngOnInit()
- ngAfterContentInit: hàm ngAfterContentInit thì nó sẽ chạy (1 lần) sau khi nội dung component đã được xây dựng thành công trong DOM, tức nội dụng component đã nạp vào trang web lần đầu tiên thành công.
- ngAfterContentChecked: hàm ngAfterContentChecked thì nó sẽ chạy mỗi lần Angular dò thấy có sự thay đổi trong targets DOM content
- ngAfterViewInit: chạy khi component và các component con của nó được khởi tạo thành công. chỉ gọi được 1 lần sau khi ngConttentChecked
- ngAfterViewCheck: chạy sau khi Angular dò thất có sự thây đổi trong view của component cha và các view component con
- ngOnDestroy: nó được gọi chạy 1 lần duy nhất trước khi component bị hủy bởi Angular. Dùng hàm nếu cần để hủy connection, unsubrive , các các biến trong stored...
![alt](https://longnv.name.vn/wp-content/uploads/2022/05/image-29.png)
![alt](https://longnv.name.vn/wp-content/uploads/2022/05/image-30.png)
## 3. Data Binding Trong Angular
==>là tính năng có sẵn trong Angular giúp gắn 1 biến với 1 vị trí nào đó trong view,
==>Có nhiều cách binding trong Angular, như expression, property,event, two-way
==> Chúng diễn ra 1 chiều từ component ra DOM, hoặc 1 chiều từ DOM và componenet, hoặc cả 2 chiều. Khi ứng dụng thực thi, chức năng Data Binding của Angular sẽ chuyễn thông tin một cách tự động.
![alt](https://longnv.name.vn/wp-content/uploads/2022/05/image-20.png)
1. Bind dữ liệu từ component ra view
==> Là cách gắn 1 biến hay biểu thưc ra 1 vị trí nào đó trong view.
```java
{{ten_bien/bieu_thuc}}
```
```java
<!-- app.component.html -->
<p>Tên sách: <b>{{tensach}}</b> </p>
<p>Giá: <b>{{giasach}}</b></p> <hr>
<div id="thongtin">
  <p>Họ tên: {{sinhvien.hoten}}</p>
  <p>Ngày sinh: {{sinhvien.ngaysinh}}</p>
  <p>Điểm: {{sinhvien.diem}}</p>
</div>
```
```java
//app.component.ts
export class AppComponent {
  tensach="Nói với tuổi 20";
  giasach = 25000;  
  sinhvien = {
    hoten:'Mai Anh Tới',
    ngaysinh:'2004-3-24',
    diem: 8
  } 
}
```
2. Bind dữ liệu từ component ra thuộc tính của tag HTML
==> Đây là cách bind kiểu property. Với cách này, Angular sẽ đưa giá trị của biến/biểu thưc vào 1 thuộc tính của tagHTML. Ví dụ đưa vào các thuộc tính như value, src, href, class, style.color, style.background-color,...
```html
<tag [thuoctinhHTML] = "TenBien"></tag>
```
```java
<p> 
  <a [href]="linkHocWeb.url" > {{linkHocWeb.ten}} </a> <br>
  <a [href]="linkHocWeb.url" target="tlw">
    <img [src]="linkHocWeb.logo" width="80">
  </a>
</p>
```
```java
//app.component.ts
export class AppComponent {  
  tensach="Nói với tuổi 20"; giasach = 25000;
  sinhvien = {hoten:'Mai Anh Tới', ngaysinh:'2004-3-24',diem: 8} 
  linkHocWeb = {
    url:'https://longnv.name.vn',
    ten:'Thầy Long Web',
    logo:'https://longnv.name.vn/wp-content/uploads/2019/09/logo3.png'
  }
}
```
3. Bind sự kiện trong DOM với hàm trong component
Đầy là cách event bind, tức là gắn sự kiện của tag với 1 hàm nào đó trong component. Khi  sự kiên xảy ra thì hàm sẽ chay.
```java
<tag (tenSuKien) = "tenHam([input])">
```
```java
<p>
Số lượng sách: <input (keyup)="xuly($event)"> . 
Tiền: {{thanhtien}}
</p>
```
 (keyup)  là sự kiện buông phím trong tag input, khi đó hàm xuly trong component sẽ được gọi.
```java
//app.component.ts
export class AppComponent {  
  tensach="Nói với tuổi 20"; giasach = 25000;
  sinhvien = {hoten:'Mai Anh Tới', ngaysinh:'2004-3-24',diem: 8} 
  linkHocWeb = {
    url:'https://longnv.name.vn', ten:'Thầy Long Web',
    logo:'https://longnv.name.vn/wp-content/uploads/2019/09/logo3.png'
  }
  thanhtien:number=0;
  xuly(ev:any){
    var t: HTMLInputElement = ev.target;
    var sl = Number(t.value);   
    this.thanhtien = this.giasach* sl;
  }
}
```
## 4. Định dạng dữ liệu vơi Angular Pipe
1. Định dạng string
==> Các biến kiểu string khi hiển thị trong view có thể điều chỉnh lại. Gồm dạng chữ hoa, chữ thường, hoặc chữ hoa đầu mỗi từ.
Syntax: 
```java
{{ tênbiến | uppercase}} hoặc {{ tênbiến | lowercase}} hoặc
{{ tênbiến |  titlecase}}
```
```java
<div id="thongtin">
  <p>Họ tên: {{sinhvien.hoten | uppercase}}</p>
  <p>Ngày sinh: {{sinhvien.ngaysinh}}</p>
  <p>Điểm: {{sinhvien.diem}}</p>
</div>
```
```java
//app.component.ts
export class AppComponent {
  sinhvien = {
    hoten:'Mai Anh Tới', 
    ngaysinh:'2004-3-24',
    diem: 8
  }  
}
```
[StringPipe](https://angular.io/api/common/UpperCasePipe)
2. Định dạng biến kiểu ngày giờ
==> Các biến có kiểu ngày giờ hiển thị trong view có thể định dạng theo format mong muốn:
Syntax:
```java
{{ TênBiến | date: format }} 
```
```java
<div id="thongtin">
  <p>Họ tên: {{sinhvien.hoten | uppercase}}</p>
  <p>Ngày sinh: {{sinhvien.ngaysinh | date:'dd/MM/Y'}}</p>
  <p>Điểm: {{sinhvien.diem}}</p>
</div>
```
[DatePipe](https://angular.io/api/common/DatePipe)
3. Định dạng số 
==> Các biến số có thể định dạng theo format thân thiện với người xem. Như định số các số lẻ, các số trong phần nguyên, phần lẻ...
Syntax:
```java
{{ tênbiến|number [ : digitsInfo [ : locale ] ] }}
```
```java
<p>
  Số lượng sách: <input (keyup)="xuly($event)"> . 
  Tiền: {{thanhtien | number: '1.0-0'}}
</p>
```
```java
//app.component.ts
export class AppComponent {  
  tensach="Nói với tuổi 20"; giasach = 25000;
  sinhvien = {hoten:'Mai Anh Tới', ngaysinh:'2004-3-24',diem: 8} 
  linkHocWeb = {
    url:'https://longnv.name.vn', ten:'Thầy Long Web',
    logo:'https://longnv.name.vn/wp-content/uploads/2019/09/logo3.png'
  }
  thanhtien:number=0;
  xuly(ev:any){
    var t: HTMLInputElement = ev.target;
    var sl = Number(t.value);   
    this.thanhtien = this.giasach* sl;
  }
}
```
[Tiền tệ](https://angular.io/api?query=pipe)
## 5. Các chỉ thị thường dùng trong angular
1. Chỉ thị *ngIf trong angular
==> Sử dụng chỉ thị *ngIf bằng cách ghi *ngIf = "Điều kiện" trong 1 tag của view sẽ giúp tạo/không tạo tag đó trong DOM tùy ý theo điều kiện dúng sai hay sai.
```java
<!-- app.component.html -->
<p> Phái: 
   <span *ngIf="phai==true">Nam</span> 
   <span *ngIf="phai==false">Nữ</span> </p>
<p> Kết quả: 
   <span *ngIf="diem>=5">Đậu</span> 
   <span *ngIf="diem<5">Rớt</span> 
</p>
```
```java
//app.component.ts
export class AppComponent {
  diem= 7;
  phai=true;
}
```
2. Chỉ thị *ngFor trong angular
==> Sử dụng chỉ thị *ngFor trong 1 tag của view sẽ giúp tạo ra tag đó nhiều lần trong DOM.
```java
<!-- app.component.html -->
<select>
    <option *ngFor="let t of thu"> {{t}} </option>
</select>
```
```java
export class AppComponent {
  thu=['Thứ 2','Thứ 3','Thứ 4','Thứ 5','Thứ 6','Thứ 7','Chủ nhật'];
}
```
3. CHỉ thị ngSwitch 
==> Đây là chỉ thị rẽ nhánh, tương đương nhiều lệnh *ngIf
```java
<p [ngSwitch]="true">Xếp loại:
        <b *ngSwitchCase="diem>=9">Giỏi</b>
        <b *ngSwitchCase="9>diem && diem>=7">Khá</b>
        <b *ngSwitchCase="7>diem && diem>=5">Trung bình</b>
        <b *ngSwitchDefault>Yếu</b>
</p>
```
4. ngStyle
5. ngClass


