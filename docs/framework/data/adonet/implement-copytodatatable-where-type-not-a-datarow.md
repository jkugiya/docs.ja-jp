---
description: '詳細情報: 方法:ジェネリック型 T が DataRow ではない CopyToDataTable<T> を実装する'
title: '方法: ジェネリック型 T が DataRow ではない CopyToDataTable<T> を実装する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b27b52cf-6172-485f-a75c-70ff9c5a2bd4
ms.openlocfilehash: 742e4f0a4854cbb1a37a5401abc628cd4d239b26
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723804"
---
# <a name="how-to-implement-copytodatatablet-where-the-generic-type-t-is-not-a-datarow"></a><span data-ttu-id="1fa98-103">方法: ジェネリック型 T が DataRow ではない CopyToDataTable\<T> を実装する</span><span class="sxs-lookup"><span data-stu-id="1fa98-103">How to: Implement CopyToDataTable\<T> Where the Generic Type T Is Not a DataRow</span></span>

<span data-ttu-id="1fa98-104">データ バインドには、しばしば <xref:System.Data.DataTable> オブジェクトが使用されます。</span><span class="sxs-lookup"><span data-stu-id="1fa98-104">The <xref:System.Data.DataTable> object is often used for data binding.</span></span> <span data-ttu-id="1fa98-105"><xref:System.Data.DataTableExtensions.CopyToDataTable%2A> メソッドは、クエリの結果を受け取り、そのデータを <xref:System.Data.DataTable> にコピーします。これをデータ バインディングに利用できます。</span><span class="sxs-lookup"><span data-stu-id="1fa98-105">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method takes the results of a query and copies the data into a <xref:System.Data.DataTable>, which can then be used for data binding.</span></span> <span data-ttu-id="1fa98-106">ただし、<xref:System.Data.DataTableExtensions.CopyToDataTable%2A> メソッドは、ジェネリック パラメーター <xref:System.Collections.Generic.IEnumerable%601> が `T` 型である <xref:System.Data.DataRow> ソースに対してのみ作用します。</span><span class="sxs-lookup"><span data-stu-id="1fa98-106">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> methods, however, only operate on an <xref:System.Collections.Generic.IEnumerable%601> source where the generic parameter `T` is of type <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="1fa98-107">有用ではありますが、一連のスカラー型、匿名型を射影するクエリ、またはテーブルの結合を実行するクエリからは、テーブルを作成できません。</span><span class="sxs-lookup"><span data-stu-id="1fa98-107">Although this is useful, it does not allow tables to be created from a sequence of scalar types, from queries that project anonymous types, or from queries that perform table joins.</span></span>  
  
 <span data-ttu-id="1fa98-108">このトピックでは、`CopyToDataTable<T>` 型以外のジェネリック パラメーター `T` を受け取る 2 つのカスタム <xref:System.Data.DataRow> 拡張メソッドを実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1fa98-108">This topic describes how to implement two custom `CopyToDataTable<T>` extension methods that accept a generic parameter `T` of a type other than <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="1fa98-109"><xref:System.Data.DataTable> ソースから <xref:System.Collections.Generic.IEnumerable%601> を作成するロジックは、`ObjectShredder<T>` クラスに存在し、オーバーロードされた 2 つの `CopyToDataTable<T>` 拡張メソッドにラップされています。</span><span class="sxs-lookup"><span data-stu-id="1fa98-109">The logic to create a <xref:System.Data.DataTable> from an <xref:System.Collections.Generic.IEnumerable%601> source is contained in the `ObjectShredder<T>` class, which is then wrapped in two overloaded `CopyToDataTable<T>` extension methods.</span></span> <span data-ttu-id="1fa98-110">`Shred` クラスの `ObjectShredder<T>` メソッドは、データが格納された <xref:System.Data.DataTable> を返し、<xref:System.Collections.Generic.IEnumerable%601> ソース、<xref:System.Data.DataTable>、および <xref:System.Data.LoadOption> 列挙型の 3 つの入力パラメーターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="1fa98-110">The `Shred` method of the `ObjectShredder<T>` class returns the filled <xref:System.Data.DataTable> and accepts three input parameters: an <xref:System.Collections.Generic.IEnumerable%601> source, a <xref:System.Data.DataTable>, and a <xref:System.Data.LoadOption> enumeration.</span></span> <span data-ttu-id="1fa98-111">返される <xref:System.Data.DataTable> の最初のスキーマは、`T` 型のスキーマに基づきます。</span><span class="sxs-lookup"><span data-stu-id="1fa98-111">The initial schema of the returned <xref:System.Data.DataTable> is based on the schema of the type `T`.</span></span> <span data-ttu-id="1fa98-112">既存のテーブルを入力として指定する場合は、そのスキーマが、`T` 型のスキーマと矛盾がないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1fa98-112">If an existing table is provided as input, the schema must be consistent with the schema of the type `T`.</span></span> <span data-ttu-id="1fa98-113">返されたテーブルでは、`T` 型のパブリック プロパティおよびパブリック フィールドが、それぞれ <xref:System.Data.DataColumn> に変換されます。</span><span class="sxs-lookup"><span data-stu-id="1fa98-113">Each public property and field of the type `T` is converted to a <xref:System.Data.DataColumn> in the returned table.</span></span> <span data-ttu-id="1fa98-114">`T` から派生した型がソース シーケンスに含まれている場合は、返されるテーブルのスキーマが、あらゆる追加パブリック プロパティまたは追加パブリック フィールドに展開されます。</span><span class="sxs-lookup"><span data-stu-id="1fa98-114">If the source sequence contains a type derived from `T`, the returned table schema is expanded for any additional public properties or fields.</span></span>  
  
 <span data-ttu-id="1fa98-115">カスタム `CopyToDataTable<T>` メソッドの使用例については、[クエリから DataTable を作成する](creating-a-datatable-from-a-query-linq-to-dataset.md)方法に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1fa98-115">For examples of using the custom `CopyToDataTable<T>` methods, see [Creating a DataTable From a Query](creating-a-datatable-from-a-query-linq-to-dataset.md).</span></span>  
  
### <a name="to-implement-the-custom-copytodatatablet-methods-in-your-application"></a><span data-ttu-id="1fa98-116">カスタム CopyToDataTable\<T> メソッドをアプリケーションに実装するには</span><span class="sxs-lookup"><span data-stu-id="1fa98-116">To implement the custom CopyToDataTable\<T> methods in your application</span></span>  
  
1. <span data-ttu-id="1fa98-117">`ObjectShredder<T>` クラスを実装して、<xref:System.Data.DataTable> ソースから <xref:System.Collections.Generic.IEnumerable%601> を作成します。</span><span class="sxs-lookup"><span data-stu-id="1fa98-117">Implement the `ObjectShredder<T>` class to create a <xref:System.Data.DataTable> from an <xref:System.Collections.Generic.IEnumerable%601> source:</span></span>  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#objectshredderclass)]
     [!code-vb[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#objectshredderclass)]  

    <span data-ttu-id="1fa98-118">上の例は、`DataColumn` のプロパティとフィールドが Null 許容値型ではないことを前提としています。</span><span class="sxs-lookup"><span data-stu-id="1fa98-118">The preceding example assumes that the properties and fields of the `DataColumn` are not nullable value types.</span></span> <span data-ttu-id="1fa98-119">Null 許容値型のプロパティとフィールドを処理するには、次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="1fa98-119">To handle properties and fields with nullable value types, use the following code:</span></span>

    ```csharp
    // Nullable-aware code for properties.
    DataColumn dc = table.Columns.Contains(p.Name) ? table.Columns[p.Name] : table.Columns.Add(p.Name, Nullable.GetUnderlyingType(p.PropertyType) ?? p.PropertyType);

    // Nullable-aware code for fields.
    DataColumn dc = table.Columns.Contains(f.Name) ? table.Columns[f.Name] : table.Columns.Add(f.Name, Nullable.GetUnderlyingType(f.FieldType) ?? f.FieldType);
    ```

2. <span data-ttu-id="1fa98-120">カスタム `CopyToDataTable<T>` 拡張メソッドをクラスに実装します。</span><span class="sxs-lookup"><span data-stu-id="1fa98-120">Implement the custom `CopyToDataTable<T>` extension methods in a class:</span></span>  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#customcopytodatatablemethods)]
     [!code-vb[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#customcopytodatatablemethods)]  
  
3. <span data-ttu-id="1fa98-121">`ObjectShredder<T>` クラスおよび `CopyToDataTable<T>` 拡張メソッドをアプリケーションに追加します。</span><span class="sxs-lookup"><span data-stu-id="1fa98-121">Add the `ObjectShredder<T>` class and `CopyToDataTable<T>` extension methods to your application.</span></span>  
  
```vb  
Module Module1  
    Sub Main()  
        ' Your application code using CopyToDataTable<T>.  
    End Sub  
End Module  
  
Public Module CustomLINQtoDataSetMethods  
…  
End Module  
  
Public Class ObjectShredder(Of T)  
…  
End Class
```
  
```csharp
class Program  
{  
    static void Main(string[] args)  
    {  
        // Your application code using CopyToDataTable<T>.  
    }  
}  
public static class CustomLINQtoDataSetMethods  
{  
…  
}  
public class ObjectShredder<T>  
{  
…  
}  
```
  
## <a name="see-also"></a><span data-ttu-id="1fa98-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="1fa98-122">See also</span></span>

- [<span data-ttu-id="1fa98-123">クエリによる DataTable の作成</span><span class="sxs-lookup"><span data-stu-id="1fa98-123">Creating a DataTable From a Query</span></span>](creating-a-datatable-from-a-query-linq-to-dataset.md)
- [<span data-ttu-id="1fa98-124">プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="1fa98-124">Programming Guide</span></span>](programming-guide-linq-to-dataset.md)
