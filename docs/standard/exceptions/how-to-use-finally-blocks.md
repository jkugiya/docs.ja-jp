---
description: '詳細情報: finally ブロックを使用する方法'
title: '方法: finally ブロックを使用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, try/catch blocks
- exceptions, finally blocks
- try/catch blocks
- finally blocks
- ArgumentOutOfRangeException class
ms.assetid: 4b9c0137-04af-4468-91d1-b9014df8ddd2
ms.openlocfilehash: 0c296e5cba8e3f4f50005a6178886a116f6e7bac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99629605"
---
# <a name="how-to-use-finally-blocks"></a>finally ブロックを使用する方法

例外が発生すると、実行が停止され、コントロールが適切な例外ハンドラーに付与されます。 これは、多くの場合、実行されるはずのコード行がバイパスされることを意味します。 ファイルを閉じるなどのいくつかのリソースのクリーンアップは、例外がスローされた場合でも実行する必要があります。 これを行うために、`finally` ブロックを使用することができます。 `finally` ブロックは、例外がスローされるかどうかに関係なく、常に実行されます。

次のコード例では、`try`/`catch` ブロックを使用して <xref:System.ArgumentOutOfRangeException> をキャッチします。 `Main` メソッドは 2 つの配列を作成し、一方の配列をもう一方にコピーすることを試みます。 アクションが、<xref:System.ArgumentOutOfRangeException> を生成し、エラーは、コンソールに書き込まれます。 `finally` ブロックは、コピー操作の結果に関係なく実行されます。

[!code-cpp[CodeTryCatchFinallyExample#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CPP/source2.cpp#3)]
[!code-csharp[CodeTryCatchFinallyExample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CS/source2.cs#3)]
[!code-vb[CodeTryCatchFinallyExample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeTryCatchFinallyExample/VB/source2.vb#3)]  

## <a name="see-also"></a>関連項目

- [例外](index.md)
