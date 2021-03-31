---
title: 射影の型を制御する方法 - LINQ to XML
description: クエリで返されるコレクションの型を制御できます。XElements の IEnumerable にする必要はありません。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: e4db6b7e-4cc9-4c8f-af85-94acf32aa348
ms.openlocfilehash: c92258fa9501aeeee46fe664cc4436f9349ff232
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "103412152"
---
# <a name="how-to-control-the-type-of-a-projection-linq-to-xml"></a>射影の型を制御する方法 (LINQ to XML)

"*射影*" はデータ セットをフィルタリングするプロセスです。その構造を変更し、場合によってはその型を変更します。 ほとんどのクエリ式は射影を実行します。 このセクション内のクエリ式は、ほとんどが <xref:System.Xml.Linq.XElement> の <xref:System.Collections.Generic.IEnumerable%601> に評価されますが、他の型のコレクションを作成できます。 この記事では、この実行方法について説明します。

## <a name="example-define-a-new-type-and-create-a-query-that-creates-an-ienumerable-of-that-type"></a>例: 新しい型を定義し、その型の IEnumerable を作成するクエリを作成する

次の例では新しい型 `Customer` が定義され、クエリ式によって `Select` 句で新しい `Customer` オブジェクトがインスタンス化されます。 これによって、クエリ式の型が <xref:System.Collections.Generic.IEnumerable%601> の `Customer` になります。 この例では、XML ドキュメント「[サンプル XML ファイル : 顧客と注文](sample-xml-file-customers-orders.md)」を使用します。

```csharp
public class Customer
{
    private string customerID;
    public string CustomerID{ get{return customerID;} set{customerID = value;}}

    private string companyName;
    public string CompanyName{ get{return companyName;} set{companyName = value;}}

    private string contactName;
    public string ContactName { get{return contactName;} set{contactName = value;}}

    public Customer(string customerID, string companyName, string contactName)
    {
        CustomerID = customerID;
        CompanyName = companyName;
        ContactName = contactName;
    }

    public override string ToString()
    {
        return $"{this.customerID}:{this.companyName}:{this.contactName}";
    }
}

class Program
{
    static void Main(string[] args)
    {
        XElement custOrd = XElement.Load("CustomersOrders.xml");
        IEnumerable<Customer> custList =
            from el in custOrd.Element("Customers").Elements("Customer")
            select new Customer(
                (string)el.Attribute("CustomerID"),
                (string)el.Element("CompanyName"),
                (string)el.Element("ContactName")
            );
        foreach (Customer cust in custList)
            Console.WriteLine(cust);
    }


}
```

```vb
Public Class Customer
    Private customerIDValue As String
    Public Property CustomerID() As String
        Get
            Return customerIDValue
        End Get
        Set(ByVal value As String)
            customerIDValue = value
        End Set
    End Property

    Private companyNameValue As String
    Public Property CompanyName() As String
        Get
            Return companyNameValue
        End Get
        Set(ByVal value As String)
            companyNameValue = value
        End Set
    End Property

    Private contactNameValue As String
    Public Property ContactName() As String
        Get
            Return contactNameValue
        End Get
        Set(ByVal value As String)
            contactNameValue = value
        End Set
    End Property

    Public Sub New(ByVal customerID As String, _
                   ByVal companyName As String, _
                   ByVal contactName As String)
        CustomerIDValue = customerID
        CompanyNameValue = companyName
        ContactNameValue = contactName
    End Sub

    Public Overrides Function ToString() As String
        Return String.Format("{0}:{1}:{2}", Me.CustomerID, Me.CompanyName, Me.ContactName)
    End Function
End Class

Sub Main()
    Dim custOrd As XElement = XElement.Load("CustomersOrders.xml")
    Dim custList As IEnumerable(Of Customer) = _
        From el In custOrd.<Customers>.<Customer> _
        Select New Customer( _
            el.@<CustomerID>, _
            el.<CompanyName>.Value, _
            el.<ContactName>.Value _
        )
    For Each cust In custList
        Console.WriteLine(cust)
    Next
End Sub
```

この例を実行すると、次の出力が生成されます。

```output
GREAL:Great Lakes Food Market:Howard Snyder
HUNGC:Hungry Coyote Import Store:Yoshi Latimer
LAZYK:Lazy K Kountry Store:John Steel
LETSS:Let's Stop N Shop:Jaime Yorres
```

## <a name="see-also"></a>関連項目

- <xref:System.Linq.Enumerable.Select%2A>
- [プロジェクションと変換 (LINQ to XML) (Visual Basic)](./work-dictionaries-linq-xml.md)
