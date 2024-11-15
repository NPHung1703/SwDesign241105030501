# Subsystem context diagrams
Một số hệ thống con: BankSystem, PrintService, ProjectManagementDatabase subsystems.

  - Hệ thống con: BankSystem
    
![](https://www.planttext.com/api/plantuml/png/l59BJiCm4Dtx52El0FK3swYAgbAGs22adi1nfX3LiIFFM10XJiQ28t459arQsW9Rl1ZRC-_DUnhxy_rZJcmYfzefsbGUOY1KrXaYU31j3CvT1y_TZX5cCxk_vFch0bdJQHE3HIA1r-XPlQc1VxSmVhDgYR4MPkKPuzfOt161e_6qndYRV4bdnjgGFD-dki2OmOfZvHz7OEekcy4ofCBXg2SPorNmIyCe1Odd6In2S6Zyj_gHEAM2-hEOVMdp7Fx5mqtTkD0Y3gCH8n8hxlK5zNF2ut5-DBSCT28ahGwJ7UWOinskE29uhlX9_z7ur4xNl2d5k_G_hNNueSk13C7ms5X2qUvr1eI-qbkUlfnCBlHlSZks2CxHbzsl-m800F__0m00)
  - Giải thích:

    1.PayrollController: Là thành phần điều khiển (controller) có trách nhiệm thực thi phương thức processPayment, bắt đầu quá trình thanh toán lương.

    2.IBankSystem: Đây là một giao diện (interface) định nghĩa phương thức transferFunds, nhận các tham số gồm accountNumber, amount, và transactionDate, trả về giá trị Boolean để xác nhận việc chuyển khoản có         thành công hay không.

    3.BankSystem: Là một proxy (đại diện) cho hệ thống ngân hàng thực tế. Nó triển khai giao diện IBankSystem và thực hiện phương thức transferFunds. PayrollController tương tác gián tiếp với hệ thống ngân hàng        qua IBankSystem, giúp hệ thống có thể thay đổi mà không ảnh hưởng đến các thành phần khác.

    4.EmployeePayment: Là một thực thể (entity) đại diện cho dữ liệu thanh toán của nhân viên, như thông tin về số tiền cần thanh toán. PayrollController cập nhật trạng thái của EmployeePayment khi thực hiện           thanh toán.

    5.PayrollSystem: Là thành phần xử lý chính trong hệ thống, có mối quan hệ một-nhiều với EmployeePayment, nghĩa là một hệ thống lương có thể xử lý nhiều thanh toán cho nhân viên khác nhau.
  - Hệ thống con PrintService
    
![](https://www.planttext.com/api/plantuml/png/j59BJiCm4Dtx52El0FK3swYAAc3JNQMUm766Ok7OmJC6MOYJiU18N04dQQX8OLblHZFpFgCdVtryhebLuDXOGK_6GV24Gbj515kLWhVspZlkAWPOhVHFKvRm9Y2_vJBWSqJYZ2ThMl4k3WARRJ2ETnXUZCPCpWs61wMnB0Sgj1tWmBl0fhK-8Mxg0dQSD_iPaB8gf0BkVQmipg36Ecestj4ukopWrdkBoXsD9xuKAqh4s9pTTr3CbkZOSEepojlJ9EVpSX9F0J8IaXI_nnrmYkjpL9e9NWq_od_ansCoGGTKt6cFCtaZUuoyNYokvAa13GbX3LNwIt_AFrhjqUNRUhCrkhhxLzy0003__mC0)
  - Giải thích:

    1.PayrollController: Đây là thành phần điều khiển (controller), có trách nhiệm thực thi phương thức requestPayslip, bắt đầu quy trình tạo phiếu lương.

    2.IPintService: Là một giao diện (interface) định nghĩa phương thức printPayslip, nhận các tham số gồm employeeId, salary, và deductions, trả về giá trị Boolean để xác nhận việc in phiếu lương có thành công        hay không. PayrollController sẽ sử dụng giao diện này để in phiếu lương cho nhân viên.

    3.PrintService: Là một hệ thống con thực thi giao diện IPrintService và thực hiện phương thức printPayslip. Nó đóng vai trò là dịch vụ in ấn thực tế tương tác với hệ thống để in phiếu lương cho nhân viên.

    4.Payslip: Là một thực thể (entity) đại diện cho phiếu lương của nhân viên, bao gồm thông tin về lương, các khoản khấu trừ, v.v. PayrollController sẽ tạo ra phiếu lương này khi xử lý yêu cầu.
  - Hệ thống con ProhectManagementDatabase subsystems

![](https://www.planttext.com/api/plantuml/png/r5FBJiCm4BpdArOv0Q8jvwYAAYWIFI1Lui25ozPPqX37ZhoEK8NuCWvy4h-0RP8GzH5n9PSaipEUcTZv-lXSi4LZcqf6N1OAZ6QAX4HcMEFEQ2bljBB-JWRcSz6_f2cyHU2ksImdUrlLKk-8raQ_aB1BjDWEcpf3s-5tkZ4SlKUjmwg5xr5XJXMf8DmWaxCgb2NpZ89w9t160uCpQarNMG8FrXGgFqzWFm4S1ZWYl8JwXp24jfxyg4r93bpgPYF96LnhBGdLRulJ9Vv3R1UoXxfTF8Rrz2S_EpmRaqawjfy9n0qJnz48noynka8u4YWimsjXj_6957qBfq0XY8FlEDTDlLc86JwyK-mtZw-cquiuoDh7RkADc8jS_Karp6TTdTAf5gGo_mz-0m00__y30000)
  - Giải thích:

    
  
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
