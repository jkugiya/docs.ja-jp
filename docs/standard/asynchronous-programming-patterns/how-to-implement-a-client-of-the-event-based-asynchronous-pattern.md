---
description: '詳細情報: イベントベースの非同期パターンのクライアントを実装する方法'
title: '方法: イベントベースの非同期パターンのクライアントを実装する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET], asynchronous features
- components [.NET], asynchronous
- AsyncOperation class
- threading [Windows Forms], asynchronous features
- AsyncCompletedEventArgs class
ms.assetid: 21a858c1-3c99-4904-86ee-0d17b49804fa
ms.openlocfilehash: 819f756c9d2b4250bc64d97810ac8c40e52d3bbf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99703082"
---
# <a name="how-to-implement-a-client-of-the-event-based-asynchronous-pattern"></a><span data-ttu-id="1b86b-103">方法: イベントベースの非同期パターンのクライアントを実装する</span><span class="sxs-lookup"><span data-stu-id="1b86b-103">How to: Implement a Client of the Event-based Asynchronous Pattern</span></span>

<span data-ttu-id="1b86b-104">次のコード例では、[イベント ベースの非同期パターンの概要](event-based-asynchronous-pattern-overview.md)ページに記載されている方法でコンポーネントを使用しています。</span><span class="sxs-lookup"><span data-stu-id="1b86b-104">The following code example demonstrates how to use a component that adheres to the [Event-based Asynchronous Pattern Overview](event-based-asynchronous-pattern-overview.md).</span></span> <span data-ttu-id="1b86b-105">この例のフォームでは、「[方法 : イベントベースの非同期パターンをサポートするコンポーネントを実装する](component-that-supports-the-event-based-asynchronous-pattern.md)」に説明がある `PrimeNumberCalculator` コンポーネントが使用されています。</span><span class="sxs-lookup"><span data-stu-id="1b86b-105">The form for this example uses the `PrimeNumberCalculator` component described in [How to: Implement a Component That Supports the Event-based Asynchronous Pattern](component-that-supports-the-event-based-asynchronous-pattern.md).</span></span>  
  
 <span data-ttu-id="1b86b-106">この例を使用するプロジェクトを実行すると、"Prime Number Calculator" とグリッドと共に、**[Start New Task]\(新しいタスクの開始\)** と **[キャンセル]** という 2 つのボタンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1b86b-106">When you run a project that uses this example, you will see a "Prime Number Calculator" form with a grid and two buttons: **Start New Task** and **Cancel**.</span></span> <span data-ttu-id="1b86b-107">**[Start New Task]\(新しいタスクの開始\)** ボタンは数回連続でクリックできます。クリックのたびに、非同期操作は計算を開始し、無作為に生成されたテスト用の数字が素数かどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="1b86b-107">You can click the **Start New Task** button several times in succession, and for each click, an asynchronous operation will begin a computation to determine if a randomly generated test number is prime.</span></span> <span data-ttu-id="1b86b-108">フォームには進捗と増分が定期的に表示されます。</span><span class="sxs-lookup"><span data-stu-id="1b86b-108">The form will periodically display progress and incremental results.</span></span> <span data-ttu-id="1b86b-109">各操作には一意のタスク ID が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="1b86b-109">Each operation is assigned a unique task ID.</span></span> <span data-ttu-id="1b86b-110">計算結果は **[結果]** 列に表示されます。テスト用の数字が素数ではない場合、**Composite** というラベルが付き、その最初の除数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1b86b-110">The result of the computation is displayed in the **Result** column; if the test number is not prime, it is labeled as **Composite,** and its first divisor is displayed.</span></span>  
  
 <span data-ttu-id="1b86b-111">保留中の操作は **[キャンセル]** ボタンでキャンセルできます。</span><span class="sxs-lookup"><span data-stu-id="1b86b-111">Any pending operation can be canceled with the **Cancel** button.</span></span> <span data-ttu-id="1b86b-112">複数選択が可能です。</span><span class="sxs-lookup"><span data-stu-id="1b86b-112">Multiple selections can be made.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1b86b-113">ほとんどの数値は素数になりません。</span><span class="sxs-lookup"><span data-stu-id="1b86b-113">Most numbers will not be prime.</span></span> <span data-ttu-id="1b86b-114">操作を数回完了しても素数が出てこない場合、さらに多くのタスクを開始してください。いずれは素数が見つかります。</span><span class="sxs-lookup"><span data-stu-id="1b86b-114">If you have not found a prime number after several completed operations, simply start more tasks, and eventually you will find some prime numbers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b86b-115">例</span><span class="sxs-lookup"><span data-stu-id="1b86b-115">Example</span></span>  

 [!code-csharp[System.ComponentModel.AsyncOperationManager#10](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/primenumbercalculatormain.cs#10)]
 [!code-vb[System.ComponentModel.AsyncOperationManager#10](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/primenumbercalculatormain.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="1b86b-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="1b86b-116">See also</span></span>

- <xref:System.ComponentModel.AsyncOperation>
- <xref:System.ComponentModel.AsyncOperationManager>
- <xref:System.Windows.Forms.WindowsFormsSynchronizationContext>
