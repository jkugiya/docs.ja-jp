---
title: テキストから XML へのストリーミング変換を実行する方法 (C#) - LINQ to XML
description: 処理のためにテキスト ファイルをストリーミングする目的で、一度に 1 行をリリースする拡張メソッドを使用できます。 この手法では、ファイル全体を読み込んでから処理する手法に比べ、メモリ要件が少なくてすみます。
ms.date: 07/20/2015
dev_langs:
- csharp
ms.assetid: 9b3bd941-d0ff-4f2d-ae41-7c3b81d8fae6
ms.openlocfilehash: 8e0d710d7cbc6de8cc60721c211376a82b6c29fc
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103366015"
---
# <a name="how-to-perform-streaming-transformations-of-text-to-xml-in-c-linq-to-xml"></a>テキストから XML へのストリーミング変換を実行する方法 (C#) (LINQ to XML)

処理のためにテキスト ファイルをストリーミングする目的で、一度に 1 行をリリースする拡張メソッドを使用できます。 この手法では、ファイル全体を読み込んでから処理する手法に比べ、メモリ要件が少なくてすみます。

この拡張メソッドでは、`yield return` コンストラクトを使用して行を指定できます。 LINQ クエリでは、レイジーな遅延方式でストリームを処理できます。 <xref:System.Xml.Linq.XStreamingElement> を使用してストリーム出力すると、ソース テキスト ファイルのサイズにかかわらず、メモリを最小限しか使用しないテキスト ファイルから XML への変換を作成できます。

> [!NOTE]
> ソース ドキュメントから行を順番に受け取り、ファイル全体をいっせいに処理できる状況に、この手法は最適です。 ファイルを複数回処理するか処理前に並べ替える場合、ストリーミング手法のパフォーマンス上の利点が少なくなります。

## <a name="example-use-an-extension-method-to-stream-text"></a>拡張メソッドを使用し、テキストをストリーミングする例

この例では、People.txt というテキスト ファイルをそのソースとして使用しています。

```text
#This is a comment
1,Tai,Yee,Writer
2,Nikolay,Grachev,Programmer
3,David,Wright,Inventor
```

例のコードでは、拡張メソッド `Lines` によってテキストが一度に 1 行指定されます。

```csharp
public static class StreamReaderSequence
{
    public static IEnumerable<string> Lines(this StreamReader source)
    {
        if (source == null)
            throw new ArgumentNullException(nameof(source));

        string line;
        while ((line = source.ReadLine()) != null)
        {
            yield return line;
        }
    }
}

class Program
{
    static void Main(string[] args)
    {
        var sr = new StreamReader("People.txt");
        var xmlTree = new XStreamingElement("Root",
            from line in sr.Lines()
            let items = line.Split(',')
            where !line.StartsWith("#")
            select new XElement("Person",
                       new XAttribute("ID", items[0]),
                       new XElement("First", items[1]),
                       new XElement("Last", items[2]),
                       new XElement("Occupation", items[3])
                   )
        );
        Console.WriteLine(xmlTree);
        sr.Close();
    }
}
```

この例では次の出力が生成されます。

```xml
<Root>
  <Person ID="1">
    <First>Tai</First>
    <Last>Yee</Last>
    <Occupation>Writer</Occupation>
  </Person>
  <Person ID="2">
    <First>Nikolay</First>
    <Last>Grachev</Last>
    <Occupation>Programmer</Occupation>
  </Person>
  <Person ID="3">
    <First>David</First>
    <Last>Wright</Last>
    <Occupation>Inventor</Occupation>
  </Person>
</Root>
```

## <a name="see-also"></a>関連項目

- <xref:System.Xml.Linq.XStreamingElement>
