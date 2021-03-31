---
title: 新しい型を射影する方法 - LINQ to XML
description: クエリでは、一般的な型以外の型の IEnumerable を返すことができます。 この記事では、1 つの例を挙げ、その方法を示します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 48145cf9-1e0b-4e73-bbfd-28fc04800dc4
ms.openlocfilehash: a0ce8d9e5199b290dc759c191c4db7a37ddc9a55
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "103412130"
---
# <a name="how-to-project-a-new-type-linq-to-xml"></a><span data-ttu-id="09f57-104">新しい型を射影する方法 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="09f57-104">How to project a new type (LINQ to XML)</span></span>

<span data-ttu-id="09f57-105">このセクションにあるその他の例では、<xref:System.Collections.Generic.IEnumerable%601> の <xref:System.Xml.Linq.XElement>、<xref:System.Collections.Generic.IEnumerable%601> の `string`、および <xref:System.Collections.Generic.IEnumerable%601> の `int` として結果を返すクエリを示しています。</span><span class="sxs-lookup"><span data-stu-id="09f57-105">Other examples in this section have shown queries that return results as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> of `string`, and <xref:System.Collections.Generic.IEnumerable%601> of `int`.</span></span> <span data-ttu-id="09f57-106">これらは一般的な戻り値の型ですが、すべてのシナリオに適切であるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="09f57-106">These are common result types, but they're not appropriate for every scenario.</span></span> <span data-ttu-id="09f57-107">多くの場合、クエリを使用して、別の型の <xref:System.Collections.Generic.IEnumerable%601> を返すようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="09f57-107">In many cases, you'll want your queries to return an <xref:System.Collections.Generic.IEnumerable%601> of some other type.</span></span>

## <a name="example-define-a-new-type-and-have-the-select-statement-create-an-instance-of-the-type"></a><span data-ttu-id="09f57-108">例: 新しい型を定義し、`select` ステートメントにその型のインスタンスを作成させる</span><span class="sxs-lookup"><span data-stu-id="09f57-108">Example: Define a new type and have the `select` statement create an instance of the type</span></span>

<span data-ttu-id="09f57-109">この例では、`select` 句でオブジェクトをインスタンス化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="09f57-109">This example shows how to instantiate objects in the `select` clause.</span></span> <span data-ttu-id="09f57-110">コードではまず、コンストラクターを呼び出して新しいクラスを定義し、次に、式が新しいクラスの新しいインスタンスになるように `select` ステートメントを変更します。</span><span class="sxs-lookup"><span data-stu-id="09f57-110">The code first invokes a constructor to define a new class, and then modifies the `select` statement so that the expression is a new instance of the new class.</span></span> <span data-ttu-id="09f57-111">この例では、XML ドキュメント「[サンプル XML ファイル: 一般的な購買発注書](sample-xml-file-typical-purchase-order.md)」を使用します。</span><span class="sxs-lookup"><span data-stu-id="09f57-111">The example uses XML document [Sample XML file: Typical purchase order](sample-xml-file-typical-purchase-order.md).</span></span>

```csharp
class NameQty
{
    public string name;
    public int qty;
    public NameQty(string n, int q)
    {
        name = n;
        qty = q;
    }
};

class Program {
    public static void Main()
    {
        XElement po = XElement.Load("PurchaseOrder.xml");

        IEnumerable<NameQty> nqList =
            from n in po.Descendants("Item")
            select new NameQty(
                    (string)n.Element("ProductName"),
                    (int)n.Element("Quantity")
                );

        foreach (NameQty n in nqList)
            Console.WriteLine(n.name + ":" + n.qty);
    }
}
```

```vb
Public Class NameQty
    Public name As String
    Public qty As Integer
    Public Sub New(ByVal n As String, ByVal q As Integer)
        name = n
        qty = q
    End Sub
End Class

Public Class Program
    Shared Sub Main()
        Dim po As XElement = XElement.Load("PurchaseOrder.xml")

        Dim nqList As IEnumerable(Of NameQty) = _
            From n In po...<Item> _
            Select New NameQty( _
                n.<ProductName>.Value, CInt(n.<Quantity>.Value))

        For Each n As NameQty In nqList
            Console.WriteLine(n.name & ":" & n.qty)
        Next
    End Sub
End Class
```

<span data-ttu-id="09f57-112">この例では、「[単一の子要素を取得する方法](retrieve-single-child-element.md)」という記事で説明している <xref:System.Xml.Linq.XContainer.Element%2A> メソッドを使用しています。</span><span class="sxs-lookup"><span data-stu-id="09f57-112">This example uses the <xref:System.Xml.Linq.XContainer.Element%2A> method that was introduced in the [How to retrieve a single child element](retrieve-single-child-element.md) article.</span></span> <span data-ttu-id="09f57-113">また、キャストを使用して、<xref:System.Xml.Linq.XContainer.Element%2A> メソッドによって返された要素の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="09f57-113">It also uses casts to retrieve the values of the elements that are returned by the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span>

<span data-ttu-id="09f57-114">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="09f57-114">This example produces the following output:</span></span>

```output
Lawnmower:1
Baby Monitor:2
```

## <a name="see-also"></a><span data-ttu-id="09f57-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="09f57-115">See also</span></span>

- [<span data-ttu-id="09f57-116">プロジェクションと変換 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="09f57-116">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](./work-dictionaries-linq-xml.md)
