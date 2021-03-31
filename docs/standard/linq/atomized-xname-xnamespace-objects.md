---
title: アトミック化された XName および XNamespace オブジェクト - LINQ to XML
description: アトミック化された XName オブジェクトと XNamespace オブジェクトで名前が同じときにインスタンスを共有するしくみについて説明します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: a5b21433-b49d-415c-b00e-bcbfb0d267d7
ms.openlocfilehash: 05df7b5348fecebb7504ebb4e2623f688b6549e1
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2020
ms.locfileid: "103366034"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml"></a><span data-ttu-id="a871f-103">アトミック化された XName および XNamespace オブジェクト (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="a871f-103">Atomized XName and XNamespace objects (LINQ to XML)</span></span>

<span data-ttu-id="a871f-104"><xref:System.Xml.Linq.XName> オブジェクトと <xref:System.Xml.Linq.XNamespace> オブジェクトは "*アトミック化*" されています。つまり、同じ修飾名を含んでいる場合は、同じオブジェクトを参照します。</span><span class="sxs-lookup"><span data-stu-id="a871f-104"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> objects are *atomized*; that is, if they contain the same qualified name, they refer to the same object.</span></span> <span data-ttu-id="a871f-105">これによってクエリのパフォーマンスが向上します。これは、2 つのアトミック化された名前の等価性を比べる場合に、基になる中間言語が、2 つの参照が同じオブジェクトを指しているかどうかを判別するだけで済むためです。</span><span class="sxs-lookup"><span data-stu-id="a871f-105">This yields performance benefits for queries: when you compare two atomized names for equality, the underlying intermediate language only has to determine whether the two references point to the same object.</span></span> <span data-ttu-id="a871f-106">基になるコードは、時間のかかることがある文字列比較を行う必要がありません。</span><span class="sxs-lookup"><span data-stu-id="a871f-106">The underlying code doesn't have to do string comparisons, which would take longer.</span></span>

## <a name="atomization-semantics"></a><span data-ttu-id="a871f-107">アトミック化のセマンティクス</span><span class="sxs-lookup"><span data-stu-id="a871f-107">Atomization semantics</span></span>

<span data-ttu-id="a871f-108">アトミック化とは、2 個の <xref:System.Xml.Linq.XName> オブジェクトのローカル名が同じであり、これらのオブジェクトが同じ名前空間にある場合に、同じインスタンスを共有するという意味です。</span><span class="sxs-lookup"><span data-stu-id="a871f-108">Atomization means that if two <xref:System.Xml.Linq.XName> objects have the same local name, and they're in the same namespace, they share the same instance.</span></span> <span data-ttu-id="a871f-109">同様に、2 個の <xref:System.Xml.Linq.XNamespace> オブジェクトに同じ名前空間 URI がある場合も、これらのオブジェクトは同じインスタンスを共有します。</span><span class="sxs-lookup"><span data-stu-id="a871f-109">In the same way, if two <xref:System.Xml.Linq.XNamespace> objects have the same namespace URI, they share the same instance.</span></span>

<span data-ttu-id="a871f-110">アトミック化されたオブジェクトをクラスに対して有効にするには、クラスのコンストラクターがパブリックではなく、プライベートであることが必要です。</span><span class="sxs-lookup"><span data-stu-id="a871f-110">For a class to enable atomized objects, the constructor for the class must be private, not public.</span></span> <span data-ttu-id="a871f-111">その理由は、コンストラクターがパブリックであれば、アトミック化されていないオブジェクトを作成できるからです。</span><span class="sxs-lookup"><span data-stu-id="a871f-111">This is because if the constructor were public, you could create a non-atomized object.</span></span> <span data-ttu-id="a871f-112"><xref:System.Xml.Linq.XName> クラスと <xref:System.Xml.Linq.XNamespace> クラスは暗黙的な変換演算子を実装して、文字列を <xref:System.Xml.Linq.XName> または <xref:System.Xml.Linq.XNamespace> に変換します。</span><span class="sxs-lookup"><span data-stu-id="a871f-112">The <xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> classes implement an implicit conversion operator to convert a string into an <xref:System.Xml.Linq.XName> or <xref:System.Xml.Linq.XNamespace>.</span></span> <span data-ttu-id="a871f-113">この方法でこれらのオブジェクトのインスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="a871f-113">This is how you get an instance of these objects.</span></span> <span data-ttu-id="a871f-114">コンストラクターにはアクセスできないため、コンストラクターを使用してインスタンスを取得することはできません。</span><span class="sxs-lookup"><span data-stu-id="a871f-114">You can't get an instance by using a constructor, because the constructor is inaccessible.</span></span>

<span data-ttu-id="a871f-115"><xref:System.Xml.Linq.XName> と <xref:System.Xml.Linq.XNamespace> では、等値演算子と非等値演算子も実装されます。これらの演算子では、比較する 2 個のオブジェクトが同じインスタンスを参照しているか判断されます。</span><span class="sxs-lookup"><span data-stu-id="a871f-115"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> also implement the equality and inequality operators, which determine whether the two objects being compared are references to the same instance.</span></span>

## <a name="example-create-objects-and-show-that-identical-names-share-an-instance"></a><span data-ttu-id="a871f-116">例: オブジェクトを作成し、同じ名前でインスタンスを共有していることを示す</span><span class="sxs-lookup"><span data-stu-id="a871f-116">Example: Create objects and show that identical names share an instance</span></span>

<span data-ttu-id="a871f-117">次のコードは <xref:System.Xml.Linq.XElement> オブジェクトを作成して、同じ名前が同じインスタンスを共有することを示します。</span><span class="sxs-lookup"><span data-stu-id="a871f-117">The following code creates some <xref:System.Xml.Linq.XElement> objects and demonstrates that identical names share the same instance.</span></span>

```csharp
var r1 = new XElement("Root", "data1");
XElement r2 = XElement.Parse("<Root>data2</Root>");

if ((object)r1.Name == (object)r2.Name)
    Console.WriteLine("r1 and r2 have names that refer to the same instance.");
else
    Console.WriteLine("Different");

XName n = "Root";

if ((object)n == (object)r1.Name)
    Console.WriteLine("The name of r1 and the name in 'n' refer to the same instance.");
else
    Console.WriteLine("Different");
```

```vb
Dim r1 As New XElement("Root", "data1")
Dim r2 As XElement = XElement.Parse("<Root>data2</Root>")

If DirectCast(r1.Name, Object) = DirectCast(r2.Name, Object) Then
    Console.WriteLine("r1 and r2 have names that refer to the same instance.")
Else
    Console.WriteLine("Different")
End If

Dim n As XName = "Root"

If DirectCast(n, Object) = DirectCast(r1.Name, Object) Then
    Console.WriteLine("The name of r1 and the name in 'n' refer to the same instance.")
Else
    Console.WriteLine("Different")
End If
```

<span data-ttu-id="a871f-118">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="a871f-118">This example produces the following output:</span></span>

```output
r1 and r2 have names that refer to the same instance.
The name of r1 and the name in 'n' refer to the same instance.
```

<span data-ttu-id="a871f-119">前述のように、アトミック化されたオブジェクトの利点は、パラメーターとして <xref:System.Xml.Linq.XName> がある軸メソッドの 1 つを使用するときに、目的の要素を選択するために、軸メソッドが、2 つの名前が同じインスタンスを参照していることを判別するだけで済むことです。</span><span class="sxs-lookup"><span data-stu-id="a871f-119">As mentioned earlier, the benefit of atomized objects is that when you use one of the axis methods that take an <xref:System.Xml.Linq.XName> as a parameter, the axis method only has to determine that two names reference the same instance to select the desired elements.</span></span>

<span data-ttu-id="a871f-120">次の例では、<xref:System.Xml.Linq.XName> を <xref:System.Xml.Linq.XContainer.Descendants%2A> メソッド呼び出しに渡すので、アトミック化パターンによってパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="a871f-120">The following example passes an <xref:System.Xml.Linq.XName> to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method call, which then has better performance because of the atomization pattern.</span></span>

```csharp
var root = new XElement("Root",
    new XElement("C1", 1),
    new XElement("Z1",
        new XElement("C1", 2),
        new XElement("C1", 1)
    )
);

var query = from e in root.Descendants("C1")
            where (int)e == 1
            select e;

foreach (var z in query)
    Console.WriteLine(z);
```

```vb
Dim root As New XElement("Root", New XElement("C1", 1), New XElement("Z1", New XElement("C1", 2), New XElement("C1", 1)))

Dim query = From e In root.Descendants("C1") Where CInt(e) = 1

For Each z In query
    Console.WriteLine(z)
Next
```

<span data-ttu-id="a871f-121">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="a871f-121">This example produces the following output:</span></span>

```xml
<C1>1</C1>
<C1>1</C1>
```
