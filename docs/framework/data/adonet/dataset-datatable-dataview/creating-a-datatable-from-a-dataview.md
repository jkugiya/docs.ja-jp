---
description: '詳細情報: DataView からの DataTable の作成'
title: DataView からの DataTable の作成
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2d45cf41-d8ae-4409-af3e-a96a7e476d85
ms.openlocfilehash: 2cd1b4520cfcbeb626eea06ae2d87208339dae9a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725054"
---
# <a name="creating-a-datatable-from-a-dataview"></a><span data-ttu-id="453fb-103">DataView からの DataTable の作成</span><span class="sxs-lookup"><span data-stu-id="453fb-103">Creating a DataTable from a DataView</span></span>

<span data-ttu-id="453fb-104">データ ソースからデータを取得し、<xref:System.Data.DataTable> にデータを格納した後、再度データを取得せずに、返されたデータの並べ替え、フィルター処理、または制限の適用を行うことが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="453fb-104">Once you have retrieved data from a data source, and have filled a <xref:System.Data.DataTable> with the data, you may want to sort, filter, or otherwise limit the returned data without retrieving it again.</span></span> <span data-ttu-id="453fb-105">これを行うには、<xref:System.Data.DataView> クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="453fb-105">The <xref:System.Data.DataView> class makes this possible.</span></span> <span data-ttu-id="453fb-106">さらに、<xref:System.Data.DataView> から新しい <xref:System.Data.DataTable> を作成する必要がある場合は、<xref:System.Data.DataView.ToTable%2A> メソッドを使用して、すべての行および列、またはデータのサブセットを新しい <xref:System.Data.DataTable> にコピーできます。</span><span class="sxs-lookup"><span data-stu-id="453fb-106">In addition, if you need to create a new <xref:System.Data.DataTable> from the <xref:System.Data.DataView>, you can use the <xref:System.Data.DataView.ToTable%2A> method to copy all the rows and columns, or a subset of the data into a new <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="453fb-107"><xref:System.Data.DataView.ToTable%2A> メソッドには、次の操作を行うためのオーバーロード機能があります。</span><span class="sxs-lookup"><span data-stu-id="453fb-107">The <xref:System.Data.DataView.ToTable%2A> method provides overloads to:</span></span>  
  
- <span data-ttu-id="453fb-108"><xref:System.Data.DataTable> 内の列のサブセットである列を含む <xref:System.Data.DataView> の作成</span><span class="sxs-lookup"><span data-stu-id="453fb-108">Create a <xref:System.Data.DataTable> containing columns that are a subset of the columns in the <xref:System.Data.DataView>.</span></span>  
  
- <span data-ttu-id="453fb-109">Transact-SQL の DISTINCT キーワードと同様に、<xref:System.Data.DataView> とは異なる行のみを含む <xref:System.Data.DataTable> の作成。</span><span class="sxs-lookup"><span data-stu-id="453fb-109">Create a <xref:System.Data.DataTable> that includes only distinct rows from the <xref:System.Data.DataView>, analogously to the DISTINCT keyword in Transact-SQL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="453fb-110">例</span><span class="sxs-lookup"><span data-stu-id="453fb-110">Example</span></span>  

 <span data-ttu-id="453fb-111">次のコンソール アプリケーションの例では、**AdventureWorks** サンプル データベース内の **Person.Contact** テーブルからのデータが含まれる <xref:System.Data.DataTable> が作成されます。</span><span class="sxs-lookup"><span data-stu-id="453fb-111">The following console application example creates a <xref:System.Data.DataTable> that contains data from the **Person.Contact** table in the **AdventureWorks** sample database.</span></span> <span data-ttu-id="453fb-112">次に、<xref:System.Data.DataTable> に基づいて、並べ替えおよびフィルター処理を行った <xref:System.Data.DataView> が作成されます。</span><span class="sxs-lookup"><span data-stu-id="453fb-112">Next, the example creates a sorted and filtered <xref:System.Data.DataView> based on the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="453fb-113"><xref:System.Data.DataTable> および <xref:System.Data.DataView> の内容が表示された後、<xref:System.Data.DataView.ToTable%2A> メソッドが呼び出され、<xref:System.Data.DataView> から新しい <xref:System.Data.DataTable> が作成されて、使用可能な列のサブセットのみが選択されます。</span><span class="sxs-lookup"><span data-stu-id="453fb-113">After displaying the contents of the <xref:System.Data.DataTable> and the <xref:System.Data.DataView>, the example creates a new <xref:System.Data.DataTable> from the <xref:System.Data.DataView> by calling the <xref:System.Data.DataView.ToTable%2A> method, selecting only a subset of the available columns.</span></span> <span data-ttu-id="453fb-114">最後に、新しい <xref:System.Data.DataTable> の内容が表示されます。</span><span class="sxs-lookup"><span data-stu-id="453fb-114">Finally, the example displays the contents of the new <xref:System.Data.DataTable>.</span></span>  
  
```vb  
Private Sub DemonstrateDataView()  
    ' Retrieve a DataTable from the AdventureWorks sample database.  
    ' connectionString is assumed to be a valid connection string.  
    Dim adapter As New SqlDataAdapter( _  
       "SELECT FirstName, LastName, EmailAddress FROM Person.Contact WHERE FirstName LIKE 'Mich%'", connectionString)  
    Dim table As New DataTable  
  
    adapter.Fill(table)  
    Console.WriteLine("Original table name: " & table.TableName)  
    ' Print current table values.  
    PrintTableOrView(table, "Current Values in Table")  
  
    ' Now create a DataView based on the DataTable.  
    ' Sort and filter the data.  
    Dim view As DataView = table.DefaultView  
    view.Sort = "LastName, FirstName"  
    view.RowFilter = "LastName > 'M'"  
    PrintTableOrView(view, "Current Values in View")  
  
    ' Create a new DataTable based on the DataView,  
    ' requesting only two columns with distinct values  
    ' in the columns.  
    Dim newTable As DataTable = view.ToTable("UniqueLastNames", True, "FirstName", "LastName")  
    PrintTableOrView(newTable, "Table created from DataView")  
    Console.WriteLine("New table name: " & newTable.TableName)  
  
    Console.WriteLine("Press any key to continue.")  
    Console.ReadKey()  
    End Sub  
  
Private Sub PrintTableOrView(ByVal dv As DataView, ByVal label As String)  
    Dim sw As System.IO.StringWriter  
    Dim output As String  
    Dim table As DataTable = dv.Table  
  
    Console.WriteLine(label)  
  
    ' Loop through each row in the view.  
    For Each rowView As DataRowView In dv  
        sw = New System.IO.StringWriter  
  
        ' Loop through each column.  
        For Each col As DataColumn In table.Columns  
            ' Output the value of each column's data.  
            sw.Write(rowView(col.ColumnName).ToString() & ", ")  
        Next  
        output = sw.ToString  
        ' Trim off the trailing ", ", so the output looks correct.  
        If output.Length > 2 Then  
            output = output.Substring(0, output.Length - 2)  
        End If  
        ' Display the row in the console window.  
        Console.WriteLine(output)  
    Next  
    Console.WriteLine()  
End Sub  
  
Private Sub PrintTableOrView(ByVal table As DataTable, ByVal label As String)  
    Dim sw As System.IO.StringWriter  
    Dim output As String  
  
    Console.WriteLine(label)  
  
    ' Loop through each row in the table.  
    For Each row As DataRow In table.Rows  
        sw = New System.IO.StringWriter  
        ' Loop through each column.  
        For Each col As DataColumn In table.Columns  
            ' Output the value of each column's data.  
            sw.Write(row(col).ToString() & ", ")  
        Next  
        output = sw.ToString  
        ' Trim off the trailing ", ", so the output looks correct.  
        If output.Length > 2 Then  
            output = output.Substring(0, output.Length - 2)  
        End If  
        ' Display the row in the console window.  
        Console.WriteLine(output)  
    Next  
    Console.WriteLine()  
    End Sub  
End Module  
```  
  
```csharp  
private static void DemonstrateDataView()  
{  
// Retrieve a DataTable from the AdventureWorks sample database.  
// connectionString is assumed to be a valid connection string.  
SqlDataAdapter adapter = new SqlDataAdapter(  
    "SELECT FirstName, LastName, EmailAddress " +  
    "FROM Person.Contact WHERE FirstName LIKE 'Mich%'",
       GetConnectionString());  
DataTable table = new DataTable();  
  
adapter.Fill(table);  
Console.WriteLine("Original table name: " + table.TableName);  
// Print current table values.  
PrintTableOrView(table, "Current Values in Table");  
  
// Now create a DataView based on the DataTable.  
// Sort and filter the data.  
DataView view = table.DefaultView;  
view.Sort = "LastName, FirstName";  
view.RowFilter = "LastName > 'M'";  
PrintTableOrView(view, "Current Values in View");  
  
// Create a new DataTable based on the DataView,  
// requesting only two columns with distinct values  
// in the columns.  
DataTable newTable = view.ToTable("UniqueLastNames",  
     true, "FirstName", "LastName");  
PrintTableOrView(newTable, "Table created from DataView");  
Console.WriteLine("New table name: " + newTable.TableName);  
  
Console.WriteLine("Press any key to continue.");  
Console.ReadKey();  
}  
  
private static void PrintTableOrView(DataView dv, string label)  
{  
System.IO.StringWriter sw;  
string output;  
DataTable table = dv.Table;  
  
Console.WriteLine(label);  
  
// Loop through each row in the view.  
foreach (DataRowView rowView in dv)  
{  
    sw = new System.IO.StringWriter();  
  
    // Loop through each column.  
    foreach (DataColumn col in table.Columns)  
    {  
        // Output the value of each column's data.  
        sw.Write(rowView[col.ColumnName].ToString() + ", ");  
    }  
    output = sw.ToString();  
    // Trim off the trailing ", ", so the output looks correct.  
    if (output.Length > 2)  
    {  
        output = output.Substring(0, output.Length - 2);  
    }  
    // Display the row in the console window.  
    Console.WriteLine(output);  
}  
Console.WriteLine();  
}  
  
private static void PrintTableOrView(DataTable table, string label)  
{  
System.IO.StringWriter sw;  
string output;  
  
Console.WriteLine(label);  
  
// Loop through each row in the table.  
foreach (DataRow row in table.Rows)  
{  
    sw = new System.IO.StringWriter();  
    // Loop through each column.  
    foreach (DataColumn col in table.Columns)  
    {  
        // Output the value of each column's data.  
        sw.Write(row[col].ToString() + ", ");  
    }  
    output = sw.ToString();  
    // Trim off the trailing ", ", so the output looks correct.  
    if (output.Length > 2)  
    {  
        output = output.Substring(0, output.Length - 2);  
    }  
    // Display the row in the console window.  
    Console.WriteLine(output);  
} //  
Console.WriteLine();  
}  
```  
  
 <span data-ttu-id="453fb-115">}</span><span class="sxs-lookup"><span data-stu-id="453fb-115">}</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="453fb-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="453fb-116">See also</span></span>

- <xref:System.Data.DataView.ToTable%2A>
- [<span data-ttu-id="453fb-117">DataViews</span><span class="sxs-lookup"><span data-stu-id="453fb-117">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="453fb-118">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="453fb-118">ADO.NET Overview</span></span>](../ado-net-overview.md)
