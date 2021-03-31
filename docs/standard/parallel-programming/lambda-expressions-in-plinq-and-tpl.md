---
description: '詳細情報: PLINQ および TPL のラムダ式'
title: PLINQ および TPL のラムダ式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Func delegate, creating with lambda expression
- Action delegate, creating with lambda expression
- lambda expressions, with Action and Func
ms.assetid: 645b2c17-29d0-4ffa-8684-430743cc2f2d
ms.openlocfilehash: 86ecfca0e9866a08b4f4bb40d15b74257ec4540e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798031"
---
# <a name="lambda-expressions-in-plinq-and-tpl"></a>PLINQ および TPL のラムダ式

タスク並列ライブラリ (TPL) には、入力パラメーターとしてデリゲートの <xref:System.Func%601?displayProperty=nameWithType> または <xref:System.Action?displayProperty=nameWithType> ファミリのいずれかを受け取る多くのメソッドが含まれます。 これらのデリゲートを使用して、並列ループ、タスク、またはクエリにカスタムのプログラム ロジックを渡します。 TPL と PLINQ のコード例では、ラムダ式を使用して、インライン コード ブロックとしてこれらのデリゲートのインスタンスを作成します。 このトピックでは、Func および Action について簡単に紹介し、タスク並列ライブラリと PLINQ でラムダ式を使用する方法を示します。

> [!NOTE]
> 一般的なデリゲートの詳細については、「[デリゲート](../../csharp/programming-guide/delegates/index.md)」と「[デリゲート](../../visual-basic/programming-guide/language-features/delegates/index.md)」を参照してください。 C# と Visual Basic のラムダ式の詳細については、それぞれ「[ラムダ式](../../csharp/language-reference/operators/lambda-expressions.md)」と「[ラムダ式](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)」を参照してください。

## <a name="func-delegate"></a>Func デリゲート

`Func` デリゲートは、値を返すメソッドをカプセル化します。 `Func` シグネチャでは、末尾または最も右の型パラメーターが常に戻り値の型を指定します。 コンパイラ エラーの一般的な原因の 1 つは、2 つの入力パラメーターを <xref:System.Func%602?displayProperty=nameWithType> に渡そうとしていることです。この型は、実際には 1 つの入力パラメーターのみを受け取ります。 .NET では、17 のバージョンの `Func` が定義されています (<xref:System.Func%601?displayProperty=nameWithType>、<xref:System.Func%602?displayProperty=nameWithType>、<xref:System.Func%603?displayProperty=nameWithType> ... <xref:System.Func%6017?displayProperty=nameWithType>)。

## <a name="action-delegate"></a>Action デリゲート

<xref:System.Action?displayProperty=nameWithType> デリゲートは、値を返さないメソッド (Visual Basic では Sub) をカプセル化します。 `Action` 型シグネチャでは、型パラメーターは、入力パラメーターのみを表します。 `Func` と同じように、.NET では、型パラメーターを持たないバージョンから 16 の型パラメーターを持つバージョンまでの 17 のバージョンの `Action` が定義されています。

## <a name="example"></a>例

<xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> メソッドの次の例は、ラムダ式を使用して、Func および Action の両方のデリゲートを表す方法を示しています。

[!code-csharp[System.Threading.Tasks.Parallel#02](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.parallel/cs/parallelforeach.cs#02)]
[!code-vb[System.Threading.Tasks.Parallel#02](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.parallel/vb/parallelforeach.vb#02)]

## <a name="see-also"></a>関連項目

- [並列プログラミング](index.md)
