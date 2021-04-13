---
title: illegalPrepareConstrainedRegion MDA
description: illegalPrepareConstrainedRegion マネージド デバッグ アシスタントについて確認します。これは、PrepareConstrainedRegions 呼び出しの後に try ステートメントが続かない場合に呼び出されます。
ms.date: 03/30/2017
helpviewer_keywords:
- PrepareConstrainedRegions method
- managed debugging assistants (MDAs), illegal PrepareConstrainedRegions
- try/catch exception handling, managed debugging assistants
- IllegalPrepareConstrainedRegions MDA
- MDAs (managed debugging assistants), illegal PrepareConstrainedRegions
ms.assetid: 2f9b5031-f910-4e01-a196-f89eab313eaf
ms.openlocfilehash: 7cbf04e8605ccf18e89882dd09b96cc7c59330c9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272788"
---
# <a name="illegalprepareconstrainedregion-mda"></a><span data-ttu-id="e0b27-103">illegalPrepareConstrainedRegion MDA</span><span class="sxs-lookup"><span data-stu-id="e0b27-103">illegalPrepareConstrainedRegion MDA</span></span>

<span data-ttu-id="e0b27-104">`illegalPrepareConstrainedRegion` マネージド デバッグ アシスタント (MDA) は、<xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> メソッドの呼び出しが、例外ハンドラーの `try` ステートメントの直前にない場合にアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="e0b27-104">The `illegalPrepareConstrainedRegion` managed debugging assistant (MDA) is activated when a <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> method call does not immediately precede the `try` statement of the exception handler.</span></span> <span data-ttu-id="e0b27-105">この制限は、MSIL レベルであり、呼び出しと `try` の間でコメントなどのコードを生成しないソースの使用が許可されます。</span><span class="sxs-lookup"><span data-stu-id="e0b27-105">This restriction is at the MSIL level, so it is permissible to have non-code-generating source between the call and the `try`, such as comments.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="e0b27-106">現象</span><span class="sxs-lookup"><span data-stu-id="e0b27-106">Symptoms</span></span>  

 <span data-ttu-id="e0b27-107">そのように扱われず、単純な例外処理ブロック (`finally` または `catch`) として扱われる制約された実行領域 (CER)。</span><span class="sxs-lookup"><span data-stu-id="e0b27-107">A constrained execution region (CER) that is never treated as such, but as a simple exception handling block (`finally` or `catch`).</span></span> <span data-ttu-id="e0b27-108">その結果、メモリ不足の状態やスレッドの中止のときには領域は実行されません。</span><span class="sxs-lookup"><span data-stu-id="e0b27-108">As a consequence, the region does not run in the event of an out-of-memory condition or a thread abort.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="e0b27-109">原因</span><span class="sxs-lookup"><span data-stu-id="e0b27-109">Cause</span></span>  

 <span data-ttu-id="e0b27-110">CER の準備パターンが正しく実行されません。</span><span class="sxs-lookup"><span data-stu-id="e0b27-110">The preparation pattern for a CER is not followed correctly.</span></span>  <span data-ttu-id="e0b27-111">エラー イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="e0b27-111">This is an error event.</span></span> <span data-ttu-id="e0b27-112">`catch`/`finally`/`fault`/`filter` ブロックで CER の導入として例外ハンドラーをマークするために使用される <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> メソッドの呼び出しを `try` ステートメントの直前に使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e0b27-112">The <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method call used to mark exception handlers as introducing a CER in their `catch`/`finally`/`fault`/`filter` blocks must be used immediately before the `try` statement.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="e0b27-113">解決方法</span><span class="sxs-lookup"><span data-stu-id="e0b27-113">Resolution</span></span>  

 <span data-ttu-id="e0b27-114">`try`ステートメントの直前に <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> の呼び出しがあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e0b27-114">Ensure that the call to <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> happens immediately before the `try` statement.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="e0b27-115">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="e0b27-115">Effect on the Runtime</span></span>  

 <span data-ttu-id="e0b27-116">この MDA は CLR に影響しません。</span><span class="sxs-lookup"><span data-stu-id="e0b27-116">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="e0b27-117">出力</span><span class="sxs-lookup"><span data-stu-id="e0b27-117">Output</span></span>  

 <span data-ttu-id="e0b27-118">MDA は、<xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> メソッドの呼び出し元の名前、MSIL のオフセット、および呼び出しが try ブロックの先頭の直前にないことを示すメッセージを表示します。</span><span class="sxs-lookup"><span data-stu-id="e0b27-118">The MDA displays the name of the method calling the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method, the MSIL offset, and a message indicating the call does not immediately precede the beginning of the try block.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="e0b27-119">構成</span><span class="sxs-lookup"><span data-stu-id="e0b27-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="e0b27-120">例</span><span class="sxs-lookup"><span data-stu-id="e0b27-120">Example</span></span>  

 <span data-ttu-id="e0b27-121">次のコード例では、この MDA のアクティブ化の原因となるパターンを示します。</span><span class="sxs-lookup"><span data-stu-id="e0b27-121">The following code example demonstrates the pattern that causes this MDA to be activated.</span></span>  
  
```csharp
void MethodWithInvalidPCR()  
{  
    RuntimeHelpers.PrepareConstrainedRegions();  
    Object o = new Object();  
    try  
    {  
        …  
    }  
    finally  
    {  
        …  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="e0b27-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="e0b27-122">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>
- [<span data-ttu-id="e0b27-123">マネージド デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="e0b27-123">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="e0b27-124">相互運用マーシャリング</span><span class="sxs-lookup"><span data-stu-id="e0b27-124">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
