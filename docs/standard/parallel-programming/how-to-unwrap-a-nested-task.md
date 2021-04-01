---
description: '詳細情報: 入れ子のタスクのラップを解除する方法'
title: 方法:入れ子のタスクのラップを解除する
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to unwrap nested tasks
ms.assetid: a0769dd2-0f6d-48ca-8418-a9d39de7f450
ms.openlocfilehash: 0b9380d82e2b61fe371cfe56a849403212853074
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701691"
---
# <a name="how-to-unwrap-a-nested-task"></a><span data-ttu-id="ae77b-103">方法:入れ子のタスクのラップを解除する</span><span class="sxs-lookup"><span data-stu-id="ae77b-103">How to: Unwrap a Nested Task</span></span>

<span data-ttu-id="ae77b-104">以下の例に示すように、メソッドからタスクを返して、そのタスクで待機またはそのタスクから続行することができます。</span><span class="sxs-lookup"><span data-stu-id="ae77b-104">You can return a task from a method, and then wait on or continue from that task, as shown in the following example:</span></span>  
  
 [!code-csharp[TPL_Unwrap#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#01)]
 [!code-vb[TPL_Unwrap#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#01)]  
  
 <span data-ttu-id="ae77b-105">前の例では、<xref:System.Threading.Tasks.Task%601.Result%2A> プロパティは `string` 型 (Visual Basic では `String`) です。</span><span class="sxs-lookup"><span data-stu-id="ae77b-105">In the previous example, the <xref:System.Threading.Tasks.Task%601.Result%2A> property is of type `string` (`String` in Visual Basic).</span></span>  
  
 <span data-ttu-id="ae77b-106">ただし、一部のシナリオでは、あるタスクを別のタスク内で作成してから、入れ子のタスクを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="ae77b-106">However, in some scenarios, you might want to create a task within another task, and then return the nested task.</span></span> <span data-ttu-id="ae77b-107">その場合、外側のタスクの `TResult` は、それ自体がタスクとなります。</span><span class="sxs-lookup"><span data-stu-id="ae77b-107">In this case, the `TResult` of the enclosing task is itself a task.</span></span> <span data-ttu-id="ae77b-108">次の例では、Result プロパティは、C# の場合は `Task<Task<string>>`、Visual Basic の場合は `Task(Of Task(Of String))` になります。</span><span class="sxs-lookup"><span data-stu-id="ae77b-108">In the following example, the Result property is a `Task<Task<string>>` in C# or `Task(Of Task(Of String))` in Visual Basic.</span></span>  
  
 [!code-csharp[TPL_Unwrap#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#02)]
 [!code-vb[TPL_Unwrap#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#02)]  
  
 <span data-ttu-id="ae77b-109">外側のタスクのラップを解除し、元のタスクとその <xref:System.Threading.Tasks.Task%601.Result%2A> プロパティを取得するようにコードを作成できますが、例外を処理して、キャンセル要求も処理する必要があるため、そのようなコードを作成するのは簡単ではありません。</span><span class="sxs-lookup"><span data-stu-id="ae77b-109">Although it is possible to write code to unwrap the outer task and retrieve the original task and its <xref:System.Threading.Tasks.Task%601.Result%2A> property, such code is not easy to write because you must handle exceptions and also cancellation requests.</span></span> <span data-ttu-id="ae77b-110">このような場合は、以下の例に示すように、<xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> 拡張メソッドのいずれかを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ae77b-110">In this situation, we recommend that you use one of the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension methods, as shown in the following example.</span></span>  
  
 [!code-csharp[TPL_UnWrap#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#03)]
 [!code-vb[TPL_UnWrap#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#03)]  
  
 <span data-ttu-id="ae77b-111"><xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> メソッドを使用して、`Task<Task>` または `Task<Task<TResult>>` (Visual Basic では `Task(Of Task)` または `Task(Of Task(Of TResult))`) を `Task` または `Task<TResult>` (Visual Basic では `Task(Of TResult)`) に変換することができます。</span><span class="sxs-lookup"><span data-stu-id="ae77b-111">The <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> methods can be used to transform any `Task<Task>` or `Task<Task<TResult>>` (`Task(Of Task)` or `Task(Of Task(Of TResult))` in Visual Basic) to a `Task` or `Task<TResult>` (`Task(Of TResult)` in Visual Basic).</span></span> <span data-ttu-id="ae77b-112">新しいタスクは完全に内側の入れ子のタスクを表し、キャンセル状態とすべての例外を含みます。</span><span class="sxs-lookup"><span data-stu-id="ae77b-112">The new task fully represents the inner nested task, and includes cancellation state and all exceptions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae77b-113">例</span><span class="sxs-lookup"><span data-stu-id="ae77b-113">Example</span></span>  

 <span data-ttu-id="ae77b-114"><xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> 拡張メソッドの使用方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="ae77b-114">The following example demonstrates how to use the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension methods.</span></span>  
  
 [!code-csharp[TPL_UnWrap#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#04)]
 [!code-vb[TPL_UnWrap#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippet04.vb#04)]  
  
## <a name="see-also"></a><span data-ttu-id="ae77b-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="ae77b-115">See also</span></span>

- <xref:System.Threading.Tasks.TaskExtensions?displayProperty=nameWithType>
- [<span data-ttu-id="ae77b-116">タスク ベースの非同期プログラミング</span><span class="sxs-lookup"><span data-stu-id="ae77b-116">Task-based Asynchronous Programming</span></span>](task-based-asynchronous-programming.md)
