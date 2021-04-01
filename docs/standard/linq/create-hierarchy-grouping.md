---
title: グループ化を使用して階層を作成する方法 - LINQ to XML
description: 異なる要素の関連する値に基づいてデータをグループ化し、そのリレーションシップを反映した要素の下に関連要素を配置するように並べ替える方法の例を確認します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 0213d59e-5f76-438c-9cab-4bf11f7b971d
ms.openlocfilehash: cd913a2546227154fc48ee4e4ae7d007b7e926a2
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412049"
---
# <a name="how-to-create-hierarchy-using-grouping-linq-to-xml"></a><span data-ttu-id="04804-103">グループ化を使用して階層を作成する方法 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="04804-103">How to create hierarchy using grouping (LINQ to XML)</span></span>

<span data-ttu-id="04804-104">データは、異なる要素の関連する値に基づいてグループ化し、そのリレーションシップを反映した要素の下に関連要素を配置するように並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="04804-104">Data can be grouped based on related values in different elements, then reordered to place related elements together under an element that reflects the relationship.</span></span> <span data-ttu-id="04804-105">この記事では、C# と Visual Basic の例を示します。</span><span class="sxs-lookup"><span data-stu-id="04804-105">This article provides an example for C# and Visual Basic.</span></span>

## <a name="example-create-a-new-xml-document-in-which-data-is-grouped-by-category"></a><span data-ttu-id="04804-106">例: データがカテゴリ別にグループ化された新しい XML ドキュメントを作成する</span><span class="sxs-lookup"><span data-stu-id="04804-106">Example: Create a new XML document in which data is grouped by category</span></span>

<span data-ttu-id="04804-107">次の例では、データをグループ化し、そのグループ化に基づいて XML を生成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="04804-107">The following example shows how to group data, and generate XML based on the grouping.</span></span> <span data-ttu-id="04804-108">まずデータを `<Category>` 要素の値が同じものでグループ化し、次にグループ化を反映した XML 階層を含む新しい XML ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="04804-108">It first groups data by equality of value of the `<Category>` elements, then generates a new XML file in which the XML hierarchy reflects the grouping.</span></span>

<span data-ttu-id="04804-109">この例では、「[サンプル XML ファイル: 数値データ](sample-xml-file-numerical-data.md)」の XML ドキュメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="04804-109">This example uses XML document [Sample XML file: Numerical data](sample-xml-file-numerical-data.md).</span></span>

```csharp
XElement doc = XElement.Load("Data.xml");
var newData =
    new XElement("Root",
        from data in doc.Elements("Data")
        group data by (string)data.Element("Category") into groupedData
        select new XElement("Group",
            new XAttribute("ID", groupedData.Key),
            from g in groupedData
            select new XElement("Data",
                g.Element("Quantity"),
                g.Element("Price")
            )
        )
    );
Console.WriteLine(newData);
```

```vb
Dim doc As XElement = XElement.Load("Data.xml")
Dim newData As XElement = _
    <Root>
        <%= _
            From data In doc.<Data> _
            Group By category = data.<Category>(0).Value _
            Into groupedData = Group _
            Select <Group ID=<%= category %>>
                       <%= _
                           From g In groupedData _
                           Select _
                           <Data>
                               <%= g.<Quantity>(0) %>
                               <%= g.<Price>(0) %>
                           </Data> _
                       %>
                   </Group> _
        %>
    </Root>
Console.WriteLine(newData)
```

<span data-ttu-id="04804-110">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="04804-110">This example produces the following output:</span></span>

```xml
<Root>
  <Group ID="A">
    <Data>
      <Quantity>3</Quantity>
      <Price>24.50</Price>
    </Data>
    <Data>
      <Quantity>5</Quantity>
      <Price>4.95</Price>
    </Data>
    <Data>
      <Quantity>3</Quantity>
      <Price>66.00</Price>
    </Data>
    <Data>
      <Quantity>15</Quantity>
      <Price>29.00</Price>
    </Data>
  </Group>
  <Group ID="B">
    <Data>
      <Quantity>1</Quantity>
      <Price>89.99</Price>
    </Data>
    <Data>
      <Quantity>10</Quantity>
      <Price>.99</Price>
    </Data>
    <Data>
      <Quantity>8</Quantity>
      <Price>6.99</Price>
    </Data>
  </Group>
</Root>
```
