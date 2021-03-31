---
title: 概念と用語 (関数型変換) - LINQ to XML
description: 純粋関数型変換の概念と用語について説明します。
ms.date: 07/20/2015
ms.assetid: 03defb3a-7e17-4ab1-8efa-4dd66621e860
ms.openlocfilehash: 0ecdbdf88ee9f868143f466222fa06f0ccf641d8
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "103412202"
---
# <a name="concepts-and-terminology-functional-transformation-linq-to-xml"></a>概念と用語 (関数型変換) (LINQ to XML)

この記事では、純粋関数型変換の概念と用語について説明します。 データを変換する場合に関数型変換の方法を使用すると、多くの場合、従来の命令型のプログラミングよりも迅速にプログラミングでき、さまざまな表現を使用できる、デバッグや保守の容易なコードを生成できます。

このセクションの記事は、関数型プログラミングのすべてを説明するのではなく、 簡単に XML を別の形に変換するいくつかの関数型プログラミングの機能を紹介することを目的としています。

## <a name="what-is-pure-functional-transformation"></a>純粋関数型変換とは

"*純粋関数型変換*" では、"*純粋関数*" と呼ばれる一連の関数により、一連の構造化データを元の形式から別の形式に変換する方法が定義されます。 "純粋" という語は、それらの関数が "*構成可能*" であることを示します。そのためには、次が必要です。

- "*自己完結している*"。このため、プログラムの他の部分との結び付きや相互依存を気にせずに、関数を自由に並べ替えることができます。 純粋変換では、その環境を考慮する必要はなく、また環境に対して影響を与えることもありません。 つまり、変換で使用される関数には "*副作用*" がありません。
- "*ステートレス*"。このため、同じ関数または関数のセットを同じ入力に対して実行すると、常に同じ出力が得られます。 純粋変換には、以前に使用されたときの情報は保持されません。

> [!IMPORTANT]
> このチュートリアルの以降では、"純粋関数" という用語を、特定の言語機能ではなくプログラミング方法を指す広い意味で使用します。
>
> 純粋関数は、C# ではメソッドとして、Visual Basic では関数として実装する必要があります。
>
> 純粋関数を C++ の純粋仮想メソッドとは混同しないでください。 純粋仮想メソッドとは、そのメソッドを含むクラスが抽象クラスであり、メソッドの本体が提供されないことを指します。

### <a name="functional-programming"></a>関数型プログラミング

"*関数型プログラミング*" とは、純粋関数型変換を直接サポートするプログラミング方法です。

これまで、ML、Scheme、Haskell、F# などの汎用関数型プログラミング言語に対する関心は、主に学術的な分野に限られていました。 C# や Visual Basic では常に純粋関数型変換を記述することが可能でしたが、その難しさから、ほとんどのプログラマにとっては魅力的な選択肢になりませんでした。 しかし、これらの言語の最近のバージョンでは、ラムダ式や型の推定などの新しい言語構成要素により、関数型プログラミングがより簡単で生産性の高いものとなっています。

関数型プログラミングの詳細については、「[関数型プログラミングと命令型プログラミング](functional-vs-imperative-programming.md)」を参照してください。

#### <a name="domain-specific-functional-programming-languages"></a>ドメイン固有の関数型プログラミング言語

一般的な関数型プログラミング言語が広く採用されていないのに対し、一部のドメイン固有の関数型プログラミング言語はそれよりも成功しています。 たとえば、多くの Web ページの外観の決定に利用されているカスケード スタイル シート (CSS) や、XML データ操作に広く利用されている XSLT(Extensible Stylesheet Language Transformations) スタイル シートです。 XSLT について詳しくは、「[XSLT 変換](../data/xml/xslt-transformations.md)」を参照してください。

## <a name="terminology"></a>用語

次に、関数型変換に関連するいくつかの用語を定義します。

高階 (ファーストクラス) 関数 \
プログラム オブジェクトとして扱うことのできる関数です。 たとえば、他の関数に渡したり、他の関数から返したりすることができます。 C# や Visual Basic では、高階関数をサポートする言語機能として、デリゲートやラムダ式があります。 高階関数を記述するには、デリゲートを受け取る引数を 1 つ以上宣言し、通常はラムダ式を使用して呼び出します。 標準クエリ演算子の多くは高階関数です。

詳細については、「[標準クエリ演算子の概要 (C#)](../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)」および「[標準クエリ演算子の概要 (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)」を参照してください。

ラムダ式 \
基本的には、デリゲート型が必要とされる場所で使用できるインラインの匿名関数です。 これはラムダ式の簡単な定義ですが、このチュートリアルの目的には十分です。

詳細については、[ラムダ式 (C# プログラミング ガイド)](../../csharp/language-reference/operators/lambda-expressions.md) に関するページおよび「[ラムダ式 (Visual Basic)](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)」を参照してください。

コレクション \
データの構造化されたセットです。コレクション内のデータは同じ型であるのが一般的です。 コレクションで LINQ との互換性を確保するには、<xref:System.Collections.IEnumerable> インターフェイスか <xref:System.Linq.IQueryable> インターフェイス (または対応するジェネリック インターフェイスである <xref:System.Collections.Generic.IEnumerator%601> か <xref:System.Linq.IQueryable%601>) を実装する必要があります。

タプル (匿名型) \
タプルは数学的概念で、それぞれが特定の型を持つオブジェクトの有限のシーケンスを意味します。 順序付きリストとも呼ばれます。 匿名型は、この概念の言語実装です。匿名型を使用すると、名前のないクラス型を宣言し、同時にその型のオブジェクトをインスタンス化することができます。

詳細については、「[匿名型 (C# プログラミング ガイド)](../../csharp/programming-guide/classes-and-structs/anonymous-types.md)」および「[匿名型 (Visual Basic)](../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)」を参照してください。

型推論 (暗黙の型指定) \
明示的な型宣言がない場合に変数の型を特定するコンパイラの機能です。

詳細については、「[暗黙的に型指定されるローカル変数 (C# プログラミング ガイド)](../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)」および「[ローカル型の推論 (Visual Basic)](../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)」を参照してください。

遅延実行とレイジー評価 \
解決された値が実際に必要となるまで式の評価を遅らせることを意味します。 遅延実行はコレクションでサポートされています。

C# の詳細については、「[LINQ クエリの概要 (C#)](../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)」および [LINQ to XML における遅延実行とレイジー評価 (C#)](./deferred-execution-lazy-evaluation.md) に関するページを参照してください。

Visual Basic の詳細については、「[基本的なクエリ操作 (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md)」および [LINQ to XML における遅延実行とレイジー評価 (Visual Basic)](./deferred-execution-lazy-evaluation.md) に関するページを参照してください。

これらの言語機能は、このセクション全体にわたってサンプル コードで使用されています。

## <a name="see-also"></a>関連項目

- [純粋関数型変換の概要](introduction-pure-functional-transformations.md)
- [関数型プログラミングと命令型プログラミング](functional-vs-imperative-programming.md)
