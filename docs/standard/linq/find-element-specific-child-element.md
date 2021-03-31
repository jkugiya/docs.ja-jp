---
title: 特定の子要素を持つ要素を検索する方法 - LINQ to XML
description: 子要素に特定の値が含まれる要素を検索する
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 00cf5555-374e-4369-bf93-7bd2e7f21db3
ms.openlocfilehash: 2f97f920ce09222858a0a51eb52ffe0d58dba960
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/16/2020
ms.locfileid: "103412158"
---
# <a name="how-to-find-an-element-with-a-specific-child-element-linq-to-xml"></a>特定の子要素を持つ要素を検索する方法 (LINQ to XML)

この記事では、子要素に特定の値が含まれる要素を検索する方法を紹介します。

## <a name="example-find-an-element-whose-child-element-has-a-specific-value"></a>例: 子要素に特定の値が含まれる要素を検索する

この例では、`CommandLine` 子要素に "Examp2.EXE" という値が含まれる `Test` 要素が検索されます。 この例では、XML ドキュメント「[サンプル XML ファイル: テスト構成](sample-xml-file-test-configuration.md)」を使用します。

```csharp
XElement root = XElement.Load("TestConfig.xml");
IEnumerable<XElement> tests =
    from el in root.Elements("Test")
    where (string)el.Element("CommandLine") == "Examp2.EXE"
    select el;
foreach (XElement el in tests)
    Console.WriteLine((string)el.Attribute("TestId"));
```

```vb
Dim root As XElement = XElement.Load("TestConfig.xml")
Dim tests As IEnumerable(Of XElement) = _
    From el In root.<Test> _
    Where el.<CommandLine>.Value = "Examp2.EXE" _
    Select el
For Each el as XElement In tests
    Console.WriteLine(el.@TestId)
Next
```

この例を実行すると、次の出力が生成されます。

```output
0002
0006
```

このコードの Visual Basic 版では、[XML 子軸プロパティ](../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)、[XML 属性軸プロパティ](../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)、[XML 値プロパティ](../../visual-basic/language-reference/xml-axis/xml-value-property.md)が使用されることに注意してください。

## <a name="example-find-when-the-xml-is-in-a-namespace"></a>例: ある名前空間に XML が属する場合に検索する

次の例のクエリは前のものと同じですが、ある名前空間にある XML が対象になっています。 この例では、XML ドキュメント「[サンプル XML ファイル:名前空間内のテスト構成](sample-xml-file-test-configuration-namespace.md)」を使用します。

詳細については、「[名前空間の概要](namespaces-overview.md)」を参照してください。

```csharp
XElement root = XElement.Load("TestConfigInNamespace.xml");
XNamespace ad = "http://www.adatum.com";
IEnumerable<XElement> tests =
    from el in root.Elements(ad + "Test")
    where (string)el.Element(ad + "CommandLine") == "Examp2.EXE"
    select el;
foreach (XElement el in tests)
    Console.WriteLine((string)el.Attribute("TestId"));
```

```vb
Imports <xmlns='http://www.adatum.com'>

Module Module1
    Sub Main()
        Dim root As XElement = XElement.Load("TestConfigInNamespace.xml")
        Dim tests As IEnumerable(Of XElement) = _
            From el In root.<Test> _
            Where el.<CommandLine>.Value = "Examp2.EXE" _
            Select el
        For Each el As XElement In tests
            Console.WriteLine(el.@TestId)
        Next
    End Sub
End Module
```

この例を実行すると、次の出力が生成されます。

```output
0002
0006
```

## <a name="see-also"></a>関連項目

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [標準クエリ演算子の概要](../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [射影操作](../../csharp/programming-guide/concepts/linq/projection-operations.md)
