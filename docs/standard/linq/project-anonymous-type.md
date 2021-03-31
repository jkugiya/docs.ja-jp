---
title: 匿名型を射影する方法 - LINQ to XML
description: 射影で使用するためだけに型を作成するのではなく、匿名型に射影することができます。 この記事では、C# と Visual Basic の例を示します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 5cb9be13-5ac4-4373-a034-b3520a5b2dec
ms.openlocfilehash: ef0b1c642db055c8c5d4f2275b02119d8ebee8f0
ms.sourcegitcommit: 6d1ae17e60384f3b5953ca7b45ac859ec6d4c3a0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2020
ms.locfileid: "103412176"
---
# <a name="how-to-project-an-anonymous-type-linq-to-xml"></a>匿名型を射影する方法 (LINQ to XML)

場合によっては、新しい型にクエリを射影する必要があることもありますが、このクエリは新しい型にのみ使用されることになります。 型を作成するのではなく、匿名型に射影することができます。 匿名型を使用すると、あらかじめ明示的に型を定義することなく、一連の読み取り専用プロパティをオブジェクトにカプセル化できるので便利です。 `select` 句で匿名型のオブジェクトを作成するクエリを記述した場合、クエリからその型の <xref:System.Collections.IEnumerable> が返されます。

次の例は、`Amount` と `Message` という 2 つのプロパティで初期化される匿名型のオブジェクトの作成を示しています。

```csharp
var v = new { Amount = 108, Message = "Hello" };
```

```vb
Dim v = New With { .Amount = 108, .Message = "Hello" };
```

各プロパティの型はコンパイラにより推測されます。 型の名前はコンパイラによって生成され、ソース コード レベルでは使用できません。

匿名型の詳細については、次を参照してください。

- [匿名型 (C# プログラミング ガイド)](../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
- [匿名型 (Visual Basic)](../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)

## <a name="example-project-an-anonymous-type-by-creating-objects-in-the-select-clause"></a>例: `select` 句でオブジェクトを作成して匿名型を射影する

この例では、`select` 句で匿名型を射影しています。 さらに、`var` を使用して `IEnumerable` オブジェクトを作成しています。 `foreach` ループ内では、繰り返し変数が、クエリ式で作成された匿名型のインスタンスになります。

この例では、XML ドキュメント「[サンプル XML ファイル : 顧客と注文](sample-xml-file-customers-orders.md)」を使用します。

```csharp
XElement custOrd = XElement.Load("CustomersOrders.xml");
var custList =
    from el in custOrd.Element("Customers").Elements("Customer")
    select new {
        CustomerID = (string)el.Attribute("CustomerID"),
        CompanyName = (string)el.Element("CompanyName"),
        ContactName = (string)el.Element("ContactName")
    };
foreach (var cust in custList)
    Console.WriteLine("{0}:{1}:{2}", cust.CustomerID, cust.CompanyName, cust.ContactName);
```

```vb
Dim custOrd As XElement = XElement.Load("CustomersOrders.xml")
Dim custList = _
    From el In custOrd.<Customers>.<Customer> _
    Select New With { _
        .CustomerID = el.@<CustomerID>, _
        .CompanyName = el.<CompanyName>.Value, _
        .ContactName = el.<ContactName>.Value _
    }
For Each cust In custList
    Console.WriteLine("{0}:{1}:{2}", cust.CustomerID, cust.CompanyName, cust.ContactName)
Next
```

この例を実行すると、次の出力が生成されます。

```output
GREAL:Great Lakes Food Market:Howard Snyder
HUNGC:Hungry Coyote Import Store:Yoshi Latimer
LAZYK:Lazy K Kountry Store:John Steel
LETSS:Let's Stop N Shop:Jaime Yorres
```

## <a name="see-also"></a>関連項目

- [匿名型 (C# プログラミング ガイド)](../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
- [匿名型 (Visual Basic)](../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
