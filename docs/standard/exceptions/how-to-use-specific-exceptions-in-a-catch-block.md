---
description: '詳細情報: catch ブロックで特定の例外を使用する方法'
title: '方法: catch ブロックで特定の例外を使用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, try/catch blocks
- try/catch blocks
- catch blocks
ms.assetid: 12af9ff3-8587-4f31-90cf-6c2244e0fdae
ms.openlocfilehash: 5eb2a753af05c10b722cc7e41b5bb13f45fdef9a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775865"
---
# <a name="how-to-use-specific-exceptions-in-a-catch-block"></a>catch ブロックで特定の例外を使用する方法

一般的には、基本的な `catch` ステートメントを使用するよりも、特定の種類の例外をキャッチするプログラミング手法を勧めします。

例外が発生すると、スタックに渡され、各 catch ブロックが処理する機会を与えられます。 catch ステートメントの順序が重要です。 一般的な例外 catch ブロックまたはコンパイラがエラーを発行する前に、特定の例外を対象とした catch ブロックを配置します。 適切な catch ブロックは、例外の種類を catch ブロックで指定された例外の名前に一致させることで決まります。 特定の catch ブロックがない場合は、汎用 catch ブロック (ある場合) によってキャッチされます。

次のコード例では、`try`/`catch` ブロックを使用して <xref:System.InvalidCastException> をキャッチします。 サンプルでは、1 つのプロパティ、従業員レベル (`Emlevel`) を使用して、`Employee` と呼ばれるクラスを作成します。 メソッド `PromoteEmployee` は、オブジェクトを受け取って、従業員レベルをインクリメントします。 <xref:System.DateTime> インスタンスが `PromoteEmployee` メソッドに渡されたとき、<xref:System.InvalidCastException> が発生します。

[!code-cpp[CatchException#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception1.cpp#2)]
[!code-csharp[CatchException#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception1.cs#2)]
[!code-vb[CatchException#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception1.vb#2)]

## <a name="see-also"></a>関連項目

- [例外](index.md)
