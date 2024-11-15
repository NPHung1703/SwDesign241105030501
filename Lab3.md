# Subsystem context diagrams
Một số hệ thống con: BankSystem, PrintService, ProjectManagementDatabase subsystems.

  - Hệ thống con: BankSystem
    
![](https://www.planttext.com/api/plantuml/png/l59BJiCm4Dtx52El0FK3swYAgbAGs22adi1nfX3LiIFFM10XJiQ28t459arQsW9Rl1ZRC-_DUnhxy_rZJcmYfzefsbGUOY1KrXaYU31j3CvT1y_TZX5cCxk_vFch0bdJQHE3HIA1r-XPlQc1VxSmVhDgYR4MPkKPuzfOt161e_6qndYRV4bdnjgGFD-dki2OmOfZvHz7OEekcy4ofCBXg2SPorNmIyCe1Odd6In2S6Zyj_gHEAM2-hEOVMdp7Fx5mqtTkD0Y3gCH8n8hxlK5zNF2ut5-DBSCT28ahGwJ7UWOinskE29uhlX9_z7ur4xNl2d5k_G_hNNueSk13C7ms5X2qUvr1eI-qbkUlfnCBlHlSZks2CxHbzsl-m800F__0m00)
  - Giải thích:
    
    Đây là một biểu đồ UML cho hệ thống quản lý lương, trong đó các thành phần tương tác với nhau để thực hiện quy trình thanh toán lương qua hệ thống ngân hàng. 

    Hệ thống này bao gồm các thành phần chính như sau:

    1.PayrollController:

      + Đây là thành phần controller có chức năng chính là thực hiện phương thức processPayment.
      + PayrollController sử dụng interface IBankSystem để xử lý các giao dịch liên quan đến ngân hàng.
        
    2.IBankSystem (Interface):

      + Đây là một interface cho hệ thống ngân hàng, cung cấp phương thức transferFunds với các tham số:
        
        accountNumber (kiểu String): Số tài khoản ngân hàng.
        
        amount (kiểu Double): Số tiền giao dịch.
        
        transactionDate (kiểu Date): Ngày thực hiện giao dịch.
      + Phương thức transferFunds trả về kết quả kiểu Boolean để xác định giao dịch thành công hay thất bại.
      + PayrollController sử dụng IBankSystem để thực hiện chuyển khoản cho nhân viên.
        
    3.BankSystem (Subsystem Proxy):

      + Đây là hệ thống con thực sự thực hiện giao dịch ngân hàng và đóng vai trò như một proxy.
      + BankSystem cũng có phương thức transferFunds tương tự như trong IBankSystem.
      + IBankSystem tương tác với BankSystem để thực hiện các giao dịch thực tế.
        
    4.EmployeePayment (Entity):

      + Đây là entity đại diện cho thông tin thanh toán của nhân viên.
      + PayrollController cập nhật thông tin của EmployeePayment trong quá trình xử lý thanh toán.
      + EmployeePayment được PayrollSystem xử lý.

    5.PayrollSystem:

      + Đây là hệ thống quản lý bảng lương của nhân viên.
      + PayrollSystem có mối quan hệ 0..* với EmployeePayment, nghĩa là PayrollSystem có thể xử lý nhiều thông tin thanh toán của nhân viên hoặc không có thông tin nào.
      + PayrollSystem có mối quan hệ "processes" với EmployeePayment, thực hiện xử lý các thông tin thanh toán.
   
- Hệ thống con: PrintService
    
![](https://www.planttext.com/api/plantuml/png/j59BJiCm4Dtx52El0FK3swYAAc3JNQMUm766Ok7OmJC6MOYJiU18N04dQQX8OLblHZFpFgCdVtryhebLuDXOGK_6GV24Gbj515kLWhVspZlkAWPOhVHFKvRm9Y2_vJBWSqJYZ2ThMl4k3WARRJ2ETnXUZCPCpWs61wMnB0Sgj1tWmBl0fhK-8Mxg0dQSD_iPaB8gf0BkVQmipg36Ecestj4ukopWrdkBoXsD9xuKAqh4s9pTTr3CbkZOSEepojlJ9EVpSX9F0J8IaXI_nnrmYkjpL9e9NWq_od_ansCoGGTKt6cFCtaZUuoyNYokvAa13GbX3LNwIt_AFrhjqUNRUhCrkhhxLzy0003__mC0)
  - Giải thích:

    Đây là một biểu đồ UML cho hệ thống in phiếu lương, mô tả các thành phần liên quan và mối quan hệ giữa chúng trong quá trình tạo và in phiếu lương.

    Hệ thống này bao gồm các thành phần chính như sau:

    1.PayrollController:

      + Đây là thành phần controller có nhiệm vụ xử lý yêu cầu requestPayslip.
      + PayrollController sử dụng interface IPrintService để in phiếu lương (payslip).
        
    2.IPrintService (Interface):

      + Đây là một interface cho dịch vụ in ấn, cung cấp phương thức printPayslip với các tham số:
        
        employeeId (kiểu String): Mã định danh của nhân viên.
        
        salary (kiểu Double): Mức lương của nhân viên.

        deductions (kiểu Double): Số tiền trừ vào lương.
        
      + Phương thức printPayslip trả về kiểu Boolean để xác định quá trình in có thành công hay không.
      + PayrollController sử dụng IPrintService để thực hiện in phiếu lương cho nhân viên.
        
    3.PrintService (Subsystem):

      + Đây là hệ thống con thực hiện chức năng in ấn thực tế và đóng vai trò như một subsystem.
      + PrintService có phương thức printPayslip tương tự như trong IPrintService.
      + IPrintService tương tác với PrintService để thực hiện chức năng in ấn.
        
    4.Payslip (Entity):

      + Đây là entity đại diện cho phiếu lương của nhân viên.
      + PayrollController tạo và tạo ra đối tượng Payslip trong quá trình xử lý yêu cầu in phiếu lương.
      + Payslip có mối quan hệ 0..* với PrintService, nghĩa là một phiếu lương có thể được in nhiều lần hoặc không in lần nào.

  - Hệ thống con ProhectManagementDatabase subsystems

![](https://www.planttext.com/api/plantuml/png/r5FBJiCm4BpdArOv0Q8jvwYAAYWIFI1Lui25ozPPqX37ZhoEK8NuCWvy4h-0RP8GzH5n9PSaipEUcTZv-lXSi4LZcqf6N1OAZ6QAX4HcMEFEQ2bljBB-JWRcSz6_f2cyHU2ksImdUrlLKk-8raQ_aB1BjDWEcpf3s-5tkZ4SlKUjmwg5xr5XJXMf8DmWaxCgb2NpZ89w9t160uCpQarNMG8FrXGgFqzWFm4S1ZWYl8JwXp24jfxyg4r93bpgPYF96LnhBGdLRulJ9Vv3R1UoXxfTF8Rrz2S_EpmRaqawjfy9n0qJnz48noynka8u4YWimsjXj_6957qBfq0XY8FlEDTDlLc86JwyK-mtZw-cquiuoDh7RkADc8jS_Karp6TTdTAf5gGo_mz-0m00__y30000)
  - Giải thích:

    Đây là một biểu đồ UML mô tả hệ thống quản lý dự án cho nhân viên, thể hiện các thành phần chính và mối quan hệ giữa chúng trong việc truy xuất và cập nhật dữ liệu dự án của nhân viên.
    
    Hệ thống này bao gồm các thành phần chính như sau:

    1.Subsystem (Hệ thống con):

      + PayrollController: Là bộ điều khiển chính (controller) của hệ thống, có trách nhiệm quản lý các chức năng liên quan đến bảng lương. Nó thực hiện các chức năng như getEmployeeProjectData (lấy dữ liệu dự          án của nhân viên) và updateProjectHours (cập nhật giờ làm việc của nhân viên trong dự án).
        
    2.Interface (Giao diện hệ thống con):

      + IProjectManagementDatabase: Là giao diện chính giữa bộ điều khiển PayrollController và cơ sở dữ liệu quản lý dự án. Giao diện này định nghĩa các chức năng:
        
        getProjectData(employeeId: String): ProjectData: Lấy dữ liệu dự án cho một nhân viên cụ thể dựa trên ID của họ.
        
        updateProjectHours(employeeId: String, projectId: String, hoursWorked: Double): Boolean: Cập nhật giờ làm việc của nhân viên cho một dự án cụ thể.
        
    3.Các lớp khác trong hệ thống:

      + EmployeePayment: Lớp này được cập nhật thông qua hệ thống IProjectManagementDatabase, có thể liên quan đến việc tính toán tiền lương dựa trên giờ làm việc.
      + EmployeeProject: Lớp này đại diện cho mối quan hệ giữa Employee (nhân viên) và Project (dự án). Một nhân viên có thể tham gia vào nhiều dự án (mối quan hệ 0..* giữa Employee và Project), và một dự án            cũng có thể có nhiều nhân viên tham gia.
      + Employee: Đại diện cho nhân viên trong hệ thống.
      + Project: Đại diện cho dự án trong hệ thống.
        
    4.Interaction (Tương tác):

      + PayrollController: Sử dụng giao diện IProjectManagementDatabase để truy cập vào dữ liệu dự án, cập nhật giờ làm việc và các thông tin khác.
      + EmployeePayment: Được cập nhật thông qua các dữ liệu từ ProjectManagementDatabase.
      + ProjectManagementDatabase: Là cơ sở dữ liệu quản lý dự án, tương tác với các chức năng trong giao diện IProjectManagementDatabase.

    
  
# Analysis class to design element map
|  Analysis Class | Design Element |  
|-----------------|----------------|
| LoginForm | LoginForm|
| MaintainTimecardForm | MainEmployeeForm |
| TimecardController | TimecardController |
| PayrollController | PayrollController |
| PayCheck | PayCheck |
| BankService | BankService |
| SystemClockInterface | SystemCLockInterface |
| PayrollController | PayrollControllerImpl |
| Employee | EmployeeEntity |
| Timecard | TimecardEntity |
| Payroll | PayrollProcessor |
| BankTransaction | BankTransactionProcessor |
| PaymentUI | PaymentUIComponent |
| PrintService | PrintServiceProcessor |

# Design element to owning package map
|  Design Element | "Owning" Package |  
|-----------------|----------------|
| LoginForm | Middleware::Security::GUIFramwork |
| MainEmployeeForm | Applications::Employee Activities |
| TimecardController | Applications::Employee Activities |
| SystemClockInterface | Applications::Payroll |
| PayrollController | Applications: Payroll |
| PayCheck | Business Services::Payroll Artifacts |
| BankService | Business::Banking |
| EmployeeEntity | Data Access::Employee Management |
| TimecardEntity | Data Access::Employee Management |
| PayrollProcessor | Business Services::Payroll Processing |
| BankTransactionProcessor | Business Services::Banking |
| PaymentUIComponent | Middleware::User Interface Components |
| PaymentUIComponent | Middleware::Print Services |

# Architectural layers and their dependencies

![](https://www.planttext.com/api/plantuml/png/T991JiCm44NtFiN86rQz04Ae9M9NfAhb0iOP9LOSsvfnMaM8ax7WI5o1kBHA6gVUUF7_pFT_yk_tpvgZejYrLd1Z791d528etQWAGMv2i4QhQBo3hUgH97mA68wsYXbsgYTlRU5TJ3VIH7itBMf5vQBusWRhUyG3qj5e55-Jp9UEZSF1T14N8tVazU3nT2iLDUhckZH_oqBSatmpPMdnf6YMjEbYZIvUwkTBjxwgZAjouT1pnBQmNZSfwG7sQCyxk3Q1uGFZ2T61JJnPP0nXjNhEQi8Zo8wHfSYvdWTc5KV_3FLr-vJKQCvYatiHH9fHev269xtlTWZaZwP4XZYyLufRXlUAM5yn-83qJr4AiKPNfZ_x1m00__y30000)
