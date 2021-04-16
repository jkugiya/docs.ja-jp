---
title: 'リソースの管理: use キーワード'
description: リソースの初期化と解放を制御できる F# キーワード 'use' および 'using' 関数について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 5e0838401bee02050343b2f6dcc646a8dc8b4dc0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627255"
---
# <a name="resource-management-the-use-keyword"></a>リソースの管理: use キーワード

このトピックでは、リソースの初期化と解放を制御できるキーワード `use` および `using` 関数について説明します。

## <a name="resources"></a>リソース

*"リソース"* という用語は、さまざまな形で使用されます。 リソースは、アプリケーションで使用される文字列やグラフィックスなどのデータを指す場合がありますが、このコンテキストでは、 *"リソース"* は、グラフィックス デバイス コンテキスト、ファイル ハンドル、ネットワークとデータベース接続、待機ハンドルなどの同時実行オブジェクトなど、ソフトウェアまたはオペレーティング システムのリソースを指します。 これらのリソースのアプリケーションでの使用には、オペレーティング システムまたは他のリソース プロバイダーからリソースを取得し、その後、リソースをプールに解放することにより、別のアプリケーションに提供できるようにすることが含まれます。 アプリケーションでリソースが共通プールに解放されないと、問題が発生します。

## <a name="managing-resources"></a>リソースの管理

アプリケーションでリソースを効率的かつ確実に管理するには、リソースを迅速かつ予測可能な方法で解放する必要があります。 .NET Framework を使用すると `System.IDisposable` インターフェイスが提供され、行いやすくなります。 `System.IDisposable` を実装する型には、リソースを正しく解放する `System.IDisposable.Dispose` メソッドがあります。 適切に作成されたアプリケーションを使用すると、制限されているリソースを保持するオブジェクトが不要になったときに `System.IDisposable.Dispose` が迅速かつ確実に呼び出されます。 幸いなことに、ほとんどの .NET 言語では、これを容易にするためのサポートが提供されており、F# も例外ではありません。 破棄パターンをサポートする便利な言語構成要素として、`use` バインディングと `using` 関数の 2 つがあります。

## <a name="use-binding"></a>use バインディング

`use` キーワードには、`let` バインディングのそれと似た以下の形式のものがあります。

use *value* = *expression*

これは `let` バインディングと同じ機能を提供しますが、値がスコープ外になったときに `Dispose` への呼び出しを値に追加します。 コンパイラにより値に null チェックが挿入されるため、値が `null` の場合、`Dispose` への呼び出しは試行されないことにご注意ください。

次の例は、`use` キーワードを使用してファイルを自動的に閉じる方法を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6301.fs)]

> [!NOTE]
> `use` は、コンピュテーション式で使用することができます。その場合は、`use` 式のカスタマイズされたバージョンを使用します。 詳細については、「[シーケンス](sequences.md)」、「[非同期ワークフロー](asynchronous-workflows.md)」、「[コンピュテーション式](computation-expressions.md)」を参照してください。

## <a name="using-function"></a>using 関数

`using` 関数の形式は次のとおりです。

`using` (*expression1*) *function-or-lambda*

`using` 式では、*expression1* により、破棄する必要のあるオブジェクトが作成されます。 *expression1* (破棄する必要のあるオブジェクト) の結果は、*function-or-lambda* に対する引数 *value* になります。これは、*expression1* によって生成された値と一致する型の残りの 1 つの引数を予期する関数、またはその型の引数を予期するラムダ式のいずれかになります。 関数の実行が終了すると、ランタイムにより `Dispose` が呼び出され、リソースが解放されます (値が `null` の場合を除きます。この場合、Dispose への呼び出しは試行されません)。

次の例は、ラムダ式を含む `using` 式を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6302.fs)]

次の例は、関数を含む `using` 式を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6303.fs)]

関数は、いくつかの引数が既に適用されている関数である可能性があることに注意してください。 次のコード例はこの処理方法を示しています。 文字列 `XYZ` を含むファイルが作成されます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6304.fs)]

`using` 関数と `use` バインディングは、同じことを実現するためのほぼ同じ手法です。 `using` キーワードを使用すると、`Dispose` が呼び出されるタイミングをより細かく制御できます。 `using` を使用すると、関数またはラムダ式の末尾で `Dispose` が呼び出されます。`use` キーワードを使用すると、含まれているコード ブロックの末尾で `Dispose` が呼び出されます。 一般に、`using` 関数ではなく、`use` を使用することをお勧めします。

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
