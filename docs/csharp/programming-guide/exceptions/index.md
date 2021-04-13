---
title: 例外と例外処理 - C# プログラミング ガイド
description: 例外と例外処理について説明します。 これらの C# 機能は、プログラムの実行中に発生する予期しない状況や例外的な状況に対処するのに役立ちます。
ms.date: 12/09/2020
helpviewer_keywords:
- exception handling [C#]
- exceptions [C#]
- C# language, exceptions
ms.assetid: 0001887f-4fa2-47e2-8034-2819477e2344
ms.openlocfilehash: 245299707254c7bafb4589ee8031a107921ca2a7
ms.sourcegitcommit: e7e0921d0a10f85e9cb12f8b87cc1639a6c8d3fe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2021
ms.locfileid: "107255403"
---
# <a name="exceptions-and-exception-handling-c-programming-guide"></a>例外と例外処理 (C# プログラミング ガイド)

C# 言語の例外処理機能は、プログラムの実行時に発生する予期しない状況や例外的な状況を扱うのに役立ちます。 例外処理では、キーワード `try`、`catch`、および `finally` を使用して、成功しない可能性があるアクションを試行し、適切な場合はエラーを処理して、後からリソースをクリーンアップします。 例外の発生元は、共通言語ランタイム (CLR)、.NET、サード パーティ ライブラリ、またはアプリケーション コードなどさまざまです。 例外は、`throw` キーワードを使用して作成されます。

コードが直接呼び出したメソッドではなく、呼び出し履歴の下の方にある別のメソッドによって例外がスローされることも多くあります。 例外がスローされた場合、CLR によってスタックがアンワインドされ、`catch` ブロックを持つメソッドで特定の例外の種類がないかを調べ、もしあれば最初に見つかった `catch` ブロックを実行します。 適切な `catch` ブロックが呼び出し履歴にない場合は、プロセスが終了し、ユーザーにメッセージが表示されます。

この例では、メソッドが 0 による除算をテストしてエラーをキャッチします。 例外処理せずにプログラムは終了し、"**DivideByZeroException はハンドルされませんでした。** " というエラーが表示されます。

:::code language="csharp" source="snippets/exceptions/ExceptionTest.cs" ID="ExceptionTest":::

## <a name="exceptions-overview"></a>例外の概要

例外には、次の特徴があります。

- 例外はすべて最終的に `System.Exception` から派生した種類になります。
- 例外をスローする可能性のあるステートメントの周囲で `try` ブロックを使用します。
- `try` ブロックで例外が発生すると、コントロールのフローが、呼び出し履歴内の関連付けられている最初の例外ハンドラーにジャンプします。 C# では、`catch` キーワードは例外ハンドラーの定義に使用されます。
- 特定の例外の例外ハンドラーが存在しない場合、プログラムは実行を停止し、エラー メッセージを表示します。
- 処理できない例外はキャッチしないようにして、アプリケーションを既知の状態に保ちます。 `System.Exception` をキャッチした場合は、`catch` ブロックの最後で `throw` キーワードを使用して、それを再スローします。
- `catch` ブロックで例外変数を定義した場合、それを使用して、発生した例外の種類に関する詳細を入手することができます。
- 例外は、`throw` キーワードを使用してプログラムで明示的に生成することができます。
- 例外オブジェクトには、呼び出し履歴の状態やエラーの説明など、エラーに関する詳細情報が含まれています。
- `finally` ブロック内のコードは、例外がスローされた場合でも実行されます。 `finally` ブロックを使用してリソースを解放します。たとえば、`try` ブロックで開かれたストリームまたはファイルを閉じます。
- .NET のマネージド例外は、Win32 構造化例外処理メカニズムの上に実装されます。 詳細については、「[構造化例外処理 (C/C++)](/cpp/cpp/structured-exception-handling-c-cpp)」と「[A Crash Course on the Depths of Win32 Structured Exception Handling (Win32 構造化例外処理に関する短期集中コース)」](http://bytepointer.com/resources/pietrek_crash_course_depths_of_win32_seh.htm)を参照してください。

## <a name="c-language-specification"></a>C# 言語仕様

詳細については、「[C# 言語の仕様](/dotnet/csharp/language-reference/language-specification/introduction)」の「[例外](~/_csharplang/spec/exceptions.md)」を参照してください。 言語仕様は、C# の構文と使用法に関する信頼性のある情報源です。

## <a name="see-also"></a>関連項目

- <xref:System.SystemException>
- [C# のキーワード](../../language-reference/keywords/index.md)
- [throw](../../language-reference/keywords/throw.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
- [例外](../../../standard/exceptions/index.md)
