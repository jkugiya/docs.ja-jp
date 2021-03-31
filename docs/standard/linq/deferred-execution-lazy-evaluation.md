---
title: 遅延実行とレイジー評価 - LINQ to XML
description: 遅延実行の長所と要件、およびクエリと軸を操作してそれを実装する方法について説明します。
ms.date: 07/20/2015
ms.assetid: 8683d1b4-b7ec-407b-be12-906ebe958a09
ms.openlocfilehash: 21b1c7b7d54e7f787919f1e1601fc36bc8c1caff
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103411953"
---
# <a name="deferred-execution-and-lazy-evaluation-linq-to-xml"></a>遅延実行とレイジー評価 (LINQ to XML)

クエリと軸の操作は、多くの場合、遅延実行を使用するように実装されています。 この記事では、遅延実行の要件と利点、および実装に関する注意点について説明します。

## <a name="deferred-execution"></a>遅延実行

遅延実行とは、"*具体*" 値が実際に必要となるまで、式の評価を遅らせることを意味します。 大きなデータ コレクションの操作が必要な場合、特に連結されたクエリや操作が含まれているプログラムでは、遅延実行によってパフォーマンスが大幅に向上することがあります。 最も効果的なケースでは、遅延実行を使用することによって、ソース コレクションの繰り返し処理を 1 度行うだけで済むようになります。

LINQ テクノロジでは、コア <xref:System.Linq?displayProperty=nameWithType> クラスのメンバーにおいても、<xref:System.Xml.Linq.Extensions?displayProperty=nameWithType> などのさまざまな LINQ 名前空間の拡張メソッドにおいても、遅延実行が広く利用されています。

C# 言語では、反復子ブロック内で [yield (C# リファレンス)](../../csharp/language-reference/keywords/yield.md) キーワード (`yield-return` ステートメントの形式) を使用することにより、遅延実行が直接サポートされます。 このような反復子は <xref:System.Collections.IEnumerator> 型または <xref:System.Collections.Generic.IEnumerator%601> 型 (または派生型) のコレクションを返します。

## <a name="eager-vs-lazy-evaluation"></a>集中評価とレイジー評価

遅延実行を実装するメソッドを記述するときは、レイジー評価と集中評価のどちらを使用してメソッドを実装するかについても決定する必要があります。

- "*レイジー評価*" では、反復子を呼び出すたびに、ソース コレクションの 1 つの要素が処理されます。 これが、一般的な反復子の実装方法です。
- "*集中評価*" では、反復子への最初の呼び出しの結果として、コレクション全体が処理されます。 ソース コレクションの一時的なコピーが必要になる場合もあります。 たとえば <xref:System.Linq.Enumerable.OrderBy%2A> メソッドでは、最初の要素を返す前に、コレクション全体を並べ替える必要があります。

通常は、レイジー評価を使用するとパフォーマンスが向上します。コレクション評価時のオーバーヘッド処理が均等に分散され、一時データの使用が最小限に抑えられるためです。 もちろん、操作によっては、中間結果を具体化するより他に方法がない場合もあります。

C# と Visual Basic で遅延実行をプログラミングする例については、「[遅延実行の例](deferred-execution-example.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [チュートリアル: C# のクエリの連結](chain-queries-example.md)
- [概念と用語 (関数型変換)](concepts-terminology-functional-transformation.md)
- [集計操作 (C#)](../../csharp/programming-guide/concepts/linq/aggregation-operations.md)
- [集計操作 (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)
- [yield (C# リファレンス)](../../csharp/language-reference/keywords/yield.md)
