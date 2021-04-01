---
title: LINQ to XML イベント - LINQ to XML
description: XML イベントを使用して XML ツリーへの変更を監視する方法について説明します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: ce7de951-cba7-4870-9962-733eb01cd680
ms.openlocfilehash: 755aa1a449e873a2c4f5b17d4df3eee7ecfa9969
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412024"
---
# <a name="linq-to-xml-events-linq-to-xml"></a><span data-ttu-id="13293-103">LINQ to XML イベント (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="13293-103">LINQ to XML Events (LINQ to XML)</span></span>

<span data-ttu-id="13293-104">LINQ to XML イベントを使用すると、XML ツリーが変更されるときに通知を受けることができます。</span><span class="sxs-lookup"><span data-stu-id="13293-104">LINQ to XML events enable you to be notified when an XML tree is altered.</span></span>

<span data-ttu-id="13293-105">イベントは、任意の <xref:System.Xml.Linq.XObject> の任意のインスタンスに追加できます。</span><span class="sxs-lookup"><span data-stu-id="13293-105">You can add events to any instance of any <xref:System.Xml.Linq.XObject>.</span></span> <span data-ttu-id="13293-106">イベント ハンドラーは、その <xref:System.Xml.Linq.XObject> およびその任意の子孫に対する変更のイベントを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="13293-106">The event handler will then receive events for modifications to that <xref:System.Xml.Linq.XObject> and any of its descendants.</span></span> <span data-ttu-id="13293-107">たとえば、イベント ハンドラーをツリーのルートに追加して、そのツリーに対するすべての変更をイベント ハンドラーから処理できます。</span><span class="sxs-lookup"><span data-stu-id="13293-107">For example, you can add an event handler to the root of the tree, and handle all modifications to the tree from that event handler.</span></span>

<span data-ttu-id="13293-108">LINQ to XML イベントの例については、<xref:System.Xml.Linq.XObject.Changing> と <xref:System.Xml.Linq.XObject.Changed> のそれぞれに関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="13293-108">For examples of LINQ to XML events, see <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed>.</span></span>

## <a name="types-and-events"></a><span data-ttu-id="13293-109">型とイベント</span><span class="sxs-lookup"><span data-stu-id="13293-109">Types and events</span></span>

<span data-ttu-id="13293-110">イベントを使用する場合は、次の型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="13293-110">You use the following types when working with events:</span></span>

|<span data-ttu-id="13293-111">種類</span><span class="sxs-lookup"><span data-stu-id="13293-111">Type</span></span>|<span data-ttu-id="13293-112">説明</span><span class="sxs-lookup"><span data-stu-id="13293-112">Description</span></span>|
|----------|-----------------|
|<xref:System.Xml.Linq.XObjectChange>|<span data-ttu-id="13293-113"><xref:System.Xml.Linq.XObject> に対してイベントが生成されるときのイベントの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="13293-113">Specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|<span data-ttu-id="13293-114"><xref:System.Xml.Linq.XObject.Changing> イベントおよび <xref:System.Xml.Linq.XObject.Changed> イベントのデータを提供します。</span><span class="sxs-lookup"><span data-stu-id="13293-114">Provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>|

<span data-ttu-id="13293-115">XML ツリーを変更するときに次のイベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="13293-115">The following events are raised when you modify an XML tree:</span></span>

|<span data-ttu-id="13293-116">Event</span><span class="sxs-lookup"><span data-stu-id="13293-116">Event</span></span>|<span data-ttu-id="13293-117">説明</span><span class="sxs-lookup"><span data-stu-id="13293-117">Description</span></span>|
|-----------|-----------------|
|<xref:System.Xml.Linq.XObject.Changing>|<span data-ttu-id="13293-118"><xref:System.Xml.Linq.XObject> またはその子孫のいずれかが変更される直前に発生します。</span><span class="sxs-lookup"><span data-stu-id="13293-118">Occurs just before this <xref:System.Xml.Linq.XObject> or any of its descendants is going to change.</span></span>|
|<xref:System.Xml.Linq.XObject.Changed>|<span data-ttu-id="13293-119"><xref:System.Xml.Linq.XObject> またはその子孫のいずれかが変更されたときに発生します。</span><span class="sxs-lookup"><span data-stu-id="13293-119">Occurs when an <xref:System.Xml.Linq.XObject> has changed or any of its descendants have changed.</span></span>|

## <a name="example-use-events-to-maintain-a-proper-total-when-items-are-changed"></a><span data-ttu-id="13293-120">例: 項目が変更されたときにイベントを使用して、適切な合計を維持する</span><span class="sxs-lookup"><span data-stu-id="13293-120">Example: Use events to maintain a proper total when items are changed</span></span>

<span data-ttu-id="13293-121">XML ツリー内の集計情報を維持する場合に、イベントは便利です。</span><span class="sxs-lookup"><span data-stu-id="13293-121">Events are useful when you want to maintain some aggregate information in an XML tree.</span></span> <span data-ttu-id="13293-122">たとえば、請求書の品目の合計である請求合計を維持する場合などです。</span><span class="sxs-lookup"><span data-stu-id="13293-122">For example, you may want to maintain an invoice total that's the sum of the line items of the invoice.</span></span> <span data-ttu-id="13293-123">この例では、イベントを使用して、複合要素の `Items` の下にあるすべての子要素の合計を維持します。</span><span class="sxs-lookup"><span data-stu-id="13293-123">This example uses events to maintain the total of all of the child elements under the complex element `Items`.</span></span>

```csharp
XElement root = new XElement("Root",
    new XElement("Total", "0"),
    new XElement("Items")
);
XElement total = root.Element("Total");
XElement items = root.Element("Items");
items.Changed += (object sender, XObjectChangeEventArgs cea) =>
{
    switch (cea.ObjectChange)
    {
        case XObjectChange.Add:
            if (sender is XElement)
                total.Value = ((int)total + (int)(XElement)sender).ToString();
            if (sender is XText)
                total.Value = ((int)total + (int)((XText)sender).Parent).ToString();
            break;
        case XObjectChange.Remove:
            if (sender is XElement)
                total.Value = ((int)total - (int)(XElement)sender).ToString();
            if (sender is XText)
                total.Value = ((int)total - Int32.Parse(((XText)sender).Value)).ToString();
            break;
    }
    Console.WriteLine("Changed {0} {1}",
      sender.GetType().ToString(), cea.ObjectChange.ToString());
};
items.SetElementValue("Item1", 25);
items.SetElementValue("Item2", 50);
items.SetElementValue("Item2", 75);
items.SetElementValue("Item3", 133);
items.SetElementValue("Item1", null);
items.SetElementValue("Item4", 100);
Console.WriteLine("Total:{0}", (int)total);
Console.WriteLine(root);
```

```vb
Module Module1
    Dim WithEvents items As XElement = Nothing
    Dim total As XElement = Nothing
    Dim root As XElement = _
            <Root>
                <Total>0</Total>
                <Items></Items>
            </Root>

    Private Sub XObjectChanged( _
            ByVal sender As Object, _
            ByVal cea As XObjectChangeEventArgs) _
            Handles items.Changed
        Select Case cea.ObjectChange
            Case XObjectChange.Add
                If sender.GetType() Is GetType(XElement) Then
                    total.Value = CStr(CInt(total.Value) + _
                            CInt((DirectCast(sender, XElement)).Value))
                End If
                If sender.GetType() Is GetType(XText) Then
                    total.Value = CStr(CInt(total.Value) + _
                            CInt((DirectCast(sender, XText)).Value))
                End If
            Case XObjectChange.Remove
                If sender.GetType() Is GetType(XElement) Then
                    total.Value = CStr(CInt(total.Value) - _
                            CInt((DirectCast(sender, XElement)).Value))
                End If
                If sender.GetType() Is GetType(XText) Then
                    total.Value = CStr(CInt(total.Value) - _
                            CInt((DirectCast(sender, XText)).Value))
                End If
        End Select
        Console.WriteLine("Changed {0} {1}", _
                            sender.GetType().ToString(), _
                            cea.ObjectChange.ToString())
    End Sub

    Sub Main()
        total = root.<Total>(0)
        items = root.<Items>(0)
        items.SetElementValue("Item1", 25)
        items.SetElementValue("Item2", 50)
        items.SetElementValue("Item2", 75)
        items.SetElementValue("Item3", 133)
        items.SetElementValue("Item1", Nothing)
        items.SetElementValue("Item4", 100)
        Console.WriteLine("Total:{0}", CInt(total))
        Console.WriteLine(root)
    End Sub
End Module
```

<span data-ttu-id="13293-124">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="13293-124">This example produces the following output:</span></span>

```output
Changed System.Xml.Linq.XElement Add
Changed System.Xml.Linq.XElement Add
Changed System.Xml.Linq.XText Remove
Changed System.Xml.Linq.XText Add
Changed System.Xml.Linq.XElement Add
Changed System.Xml.Linq.XElement Remove
Changed System.Xml.Linq.XElement Add
Total:308
<Root>
  <Total>308</Total>
  <Items>
    <Item2>75</Item2>
    <Item3>133</Item3>
    <Item4>100</Item4>
  </Items>
</Root>
```
