---
title: クエリの連結の例 (C#) - LINQ to XML
description: 2 つのクエリ (どちらのクエリも遅延実行とレイジー評価を使用している) を連結した場合の結果について説明します。
ms.date: 07/20/2015
ms.assetid: abbca162-d95e-43af-b92c-e46e6aa2540e
ms.openlocfilehash: c0bbab9061b98eda15523f8a8e64e997bde8b307
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412047"
---
# <a name="chain-queries-example-c-linq-to-xml"></a>クエリの連結の例 (C#) (LINQ to XML)

この例は[遅延実行の例](deferred-execution-example.md)に基づいており、2 つのクエリ (どちらのクエリも遅延実行とレイジー評価を使用している) を連結した場合の結果を示します。

## <a name="example-add-a-second-extension-method-that-uses-yield-return-to-defer-execution"></a>例: `yield return` を使用して実行を延期する 2 番目の拡張メソッドを追加する

この例では、拡張メソッドをもう 1 つ導入します。この `AppendString` という拡張メソッドは、指定された文字列をソース コレクションのすべての文字列に追加して変更された文字列を生成します。

```csharp
public static class LocalExtensions
{
    public static IEnumerable<string>
      ConvertCollectionToUpperCase(this IEnumerable<string> source)
    {
        foreach (string str in source)
        {
            Console.WriteLine("ToUpper: source >{0}<", str);
            yield return str.ToUpper();
        }
    }

    public static IEnumerable<string>
      AppendString(this IEnumerable<string> source, string stringToAppend)
    {
        foreach (string str in source)
        {
            Console.WriteLine("AppendString: source >{0}<", str);
            yield return str + stringToAppend;
        }
    }
}

class Program
{
    static void Main(string[] args)
    {
        string[] stringArray = { "abc", "def", "ghi" };

        IEnumerable<string> q1 =
            from s in stringArray.ConvertCollectionToUpperCase()
            select s;

        IEnumerable<string> q2 =
            from s in q1.AppendString("!!!")
            select s;

        foreach (string str in q2)
        {
            Console.WriteLine("Main: str >{0}<", str);
            Console.WriteLine();
        }
    }
}
```

 この例を実行すると、次の出力が生成されます。

```output
ToUpper: source >abc<
AppendString: source >ABC<
Main: str >ABC!!!<

ToUpper: source >def<
AppendString: source >DEF<
Main: str >DEF!!!<

ToUpper: source >ghi<
AppendString: source >GHI<
Main: str >GHI!!!<
```

この例では、各拡張メソッドがソース コレクションのアイテムごとに 1 つずつ実行されることを確認できます。

この例からわかることは、コレクションを生成するクエリを連結しても中間コレクションは具体化されないということです。 代わりに、各アイテムが一方のレイジー メソッドから次のメソッドに渡されます。 この場合のメモリ使用量は、まず文字列の 1 つの配列を取得し、次に大文字に変換した文字列の 2 つ目の配列を作成し、最後に各文字列に感嘆符を追加した文字列の 3 つ目の配列を作成する方法と比べると、はるかに少なくなります。

このチュートリアルの次の記事では、中間結果の具体化について説明します。

- [中間結果の具体化 (C#)](intermediate-materialization.md)

## <a name="see-also"></a>関連項目

- [遅延実行とレイジー評価](deferred-execution-lazy-evaluation.md)
