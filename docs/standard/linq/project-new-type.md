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
# <a name="how-to-project-a-new-type-linq-to-xml"></a>新しい型を射影する方法 (LINQ to XML)

このセクションにあるその他の例では、<xref:System.Collections.Generic.IEnumerable%601> の <xref:System.Xml.Linq.XElement>、<xref:System.Collections.Generic.IEnumerable%601> の `string`、および <xref:System.Collections.Generic.IEnumerable%601> の `int` として結果を返すクエリを示しています。 これらは一般的な戻り値の型ですが、すべてのシナリオに適切であるとは限りません。 多くの場合、クエリを使用して、別の型の <xref:System.Collections.Generic.IEnumerable%601> を返すようにする必要があります。

## <a name="example-define-a-new-type-and-have-the-select-statement-create-an-instance-of-the-type"></a>例: 新しい型を定義し、`select` ステートメントにその型のインスタンスを作成させる

この例では、`select` 句でオブジェクトをインスタンス化する方法を示します。 コードではまず、コンストラクターを呼び出して新しいクラスを定義し、次に、式が新しいクラスの新しいインスタンスになるように `select` ステートメントを変更します。 この例では、XML ドキュメント「[サンプル XML ファイル: 一般的な購買発注書](sample-xml-file-typical-purchase-order.md)」を使用します。

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

この例では、「[単一の子要素を取得する方法](retrieve-single-child-element.md)」という記事で説明している <xref:System.Xml.Linq.XContainer.Element%2A> メソッドを使用しています。 また、キャストを使用して、<xref:System.Xml.Linq.XContainer.Element%2A> メソッドによって返された要素の値を取得します。

この例を実行すると、次の出力が生成されます。

```output
Lawnmower:1
Baby Monitor:2
```

## <a name="see-also"></a>関連項目

- [プロジェクションと変換 (LINQ to XML) (Visual Basic)](./work-dictionaries-linq-xml.md)
