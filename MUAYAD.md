<%@ Page Language="vb" AutoEventWireup="false" CodeBehind="WebForm4.aspx.vb" Inherits="WebApplication5.YAZAN.WebForm4"  %>


<!DOCTYPE html>

<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
    <title>العملاء</title>
    <!-- Add your Bootstrap and jQuery CDN links here -->
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" />
    <script src="https://code.jquery.com/jquery-3.6.4.min.js"></script>
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/js/bootstrap.min.js"></script>
    
   
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #f8f9fa;
            margin: 20px;
        }

        .container {
            max-width: 1200px;
        }

        h2 {
            color: #007bff;
        }

        table {
            width: 100%;
            margin-top: 20px;
            border-collapse: collapse;
        }

        table, th, td {
            border: 1px solid #dee2e6;
        }

        th, td {
            padding: 15px;
            text-align: center;
        }

        th {
            background-color: #007bff;
            color: #fff;
        }
    </style>
</head>
<body>
    <form id="form2" runat="server" action="./WebForm4">
    <asp:ScriptManager ID="ScriptManager1" runat="server"></asp:ScriptManager>
        <ContentTemplate>
        <div class="container">
            <h2>شاشة العملاء</h2>
         <asp:Button ID="btnOpenModal" runat="server" Text="اضافة عميل جديد" CssClass="btn btn-primary" OnClientClick="OpenModal(); return false;" OnClick="btnSave_Click" />
        <asp:GridView ID="GridView1" runat="server" CssClass="table mt-4" AutoGenerateColumns="False">
        <Columns>
            <asp:BoundField DataField="ID" HeaderText="ID العميل" />
            <asp:BoundField DataField="Date" HeaderText="تاريخ الإدخال" />
            <asp:BoundField DataField="ACCOUNT" HeaderText="رقم الحساب" />
            <asp:BoundField DataField="Customer" HeaderText="اسم العميل" />
            <asp:BoundField DataField="CUS_KIND" HeaderText="شركة أو فرد" />
            <asp:BoundField DataField="ADDRESSES" HeaderText="العنوان" />
            <asp:BoundField DataField="EMAIL" HeaderText="البريد الإلكتروني" />
            <asp:BoundField DataField="TEL" HeaderText="رقم الهاتف" />
            <asp:BoundField DataField="CUS_TYPE" HeaderText="نوع العميل" />
            <asp:BoundField DataField="NATIONALITY" HeaderText="الجنسية" />
            <asp:BoundField DataField="SALES" HeaderText="الموظف المسؤول" />
        </Columns>
       </asp:GridView>
     </div>
        <div class="modal fade" id="simpleModal" tabindex="-1" role="dialog" aria-labelledby="simpleModalLabel" aria-hidden="TRUE">
            <div class="modal-dialog" role="document">
                <div class="modal-content">
                    <div class="modal-header">
                        <h5 class="modal-title" id="simpleModalLabel">Modal Title</h5>
                    </div>
                    <div class="modal-body">
                        <div class="form-group">
                            <label for="customerId">ID العميل:</label>
                            <asp:TextBox ID="customerId" runat="server" CssClass="form-control"></asp:TextBox>
                        </div>
                        <div class="form-group">
                        <label for="entryDate">تاريخ الإدخال:</label>
                        <asp:TextBox ID="Date12" runat="server" CssClass="form-control" TextMode="Date"></asp:TextBox>
                    </div>
                    <div class="form-group">
                        <label for="AccountNumber">رقم الحساب:</label>
                        <asp:TextBox ID="ACCOUNT" runat="server" CssClass="form-control"></asp:TextBox>
                    </div>
                    <div class="form-group">
                        <label for="CustomerName">اسم العميل:</label>
                        <asp:TextBox ID="customer" runat="server" CssClass="form-control"></asp:TextBox>
                    </div>
                    <div class="form-group">
                        <label for="companyType">شركة أو فرد:</label>
                        <asp:DropDownList ID="CUS_KIND" runat="server" CssClass="form-control">
                        </asp:DropDownList>
                    </div>
                    <div class="form-group">
                        <label for="address">العنوان:</label>
                        <asp:TextBox ID="ADDRESSES" runat="server" CssClass="form-control"></asp:TextBox>
                    </div>
                    <div class="form-group">
                        <label for="email">البريد الإلكتروني:</label>
                        <asp:TextBox ID="EMAIL" runat="server" CssClass="form-control" TextMode="Email"></asp:TextBox>
                    </div>
                    <div class="form-group">
                        <label for="phoneNumber">رقم الهاتف:</label>
                        <asp:TextBox ID="TEL" runat="server" CssClass="form-control"></asp:TextBox>
                    </div>
                        
                    <div class="form-group">
                        <label for="customerType">نوع العميل:</label>
                <asp:DropDownList ID="CUS_TYPE" runat="server" CssClass="form-control" AutoPostBack="True"  OnSelectedIndexChanged="CUS_TYPE_SelectedIndexChanged"  >

                    </asp:DropDownList>
                    </div>
                         
                    <div class="form-group">
                        <label for="NATIONALITY">الجنسية:</label>
                        <asp:DropDownList ID="NATIONALITY" runat="server" CssClass="form-control">
                        </asp:DropDownList>
                    </div>
                    <div class="form-group">
                        <label for="responsibleEmployee">الموظف المسؤول:</label>
                        <asp:TextBox ID="SALES" runat="server" CssClass="form-control"></asp:TextBox>
                    </div>
                    <div class="form-group">
                        <label for="ACCOUNTSOURS">ACCOUNT SOURS:</label>
                        <asp:TextBox ID="TextBox1" runat="server" CssClass="form-control"></asp:TextBox>
                    </div>
                    <div class="form-group">
                        <label for="ACCOUNTTYPE">ACCOUNT TYPE:</label>
                        <asp:TextBox ID="TextBox2" runat="server" CssClass="form-control"></asp:TextBox>
                    </div>
                    </div>
                    <div class="modal-footer">
                        <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
                        <asp:Button ID="btnSave" runat="server" Text="Save changes" OnClick="btnSave_Click"/>
                    </div>
                </div>
            </div>
        </div>
    
    <script>
        function OpenModal() {
            $('#simpleModal').modal('show');
        }
    </script>
       </ContentTemplate>
   </form>
</body>
</html>
