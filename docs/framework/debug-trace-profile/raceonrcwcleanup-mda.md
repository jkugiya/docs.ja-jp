---
title: raceOnRCWCleanup MDA
description: raceOnRCWCleanup マネージド デバッグ アシスタント (MDA) について確認します。これは、RCW が .NET 内の別のスレッド上または解放中のスレッド スタック上で使用されている場合にアクティブ化されます。
ms.date: 03/30/2017
helpviewer_keywords:
- RCW
- managed debugging assistants (MDAs), RCWs
- race on RCW cleanup
- MDAs (managed debugging assistants), RCWs
- RaceOnRCWCleanup MDA
- runtime callable wrappers
ms.assetid: bee1e9b1-50a8-4c89-9cd9-7dd6b2458187
ms.openlocfilehash: 393c5ea44108445a9a1a9d16e7d1d192eced5740
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96271448"
---
# <a name="raceonrcwcleanup-mda"></a><span data-ttu-id="38b1f-103">raceOnRCWCleanup MDA</span><span class="sxs-lookup"><span data-stu-id="38b1f-103">raceOnRCWCleanup MDA</span></span>

<span data-ttu-id="38b1f-104"><xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> メソッドなどのコマンドを使用して [ランタイム呼び出し可能ラッパー](../../standard/native-interop/runtime-callable-wrapper.md) (RCW: Runtime Callable Wrapper) を解放する呼び出しがなされた時点でその RCW が使用中であることを共通言語ランタイム (CLR: Common Language Runtime) が検出すると、`raceOnRCWCleanup` マネージド デバッグ アシスタント (MDA: Managed Debugging Assistant) がアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="38b1f-104">The `raceOnRCWCleanup` managed debugging assistant (MDA) is activated when the common language runtime (CLR) detects that a [Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) is in use when a call to release it is made using a command such as the <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="38b1f-105">現象</span><span class="sxs-lookup"><span data-stu-id="38b1f-105">Symptoms</span></span>  

 <span data-ttu-id="38b1f-106"><xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> メソッド、または類似メソッドを使用して RCW が解放中または解放後に、アクセス違反またはメモリ破損が発生します。</span><span class="sxs-lookup"><span data-stu-id="38b1f-106">Access violations or memory corruption during or after freeing an RCW using <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> or a similar method.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="38b1f-107">原因</span><span class="sxs-lookup"><span data-stu-id="38b1f-107">Cause</span></span>  

 <span data-ttu-id="38b1f-108">別のスレッドまたは解放中のスレッド スタックで、RCW が使用中です。</span><span class="sxs-lookup"><span data-stu-id="38b1f-108">The RCW is in use on another thread or on the freeing thread stack.</span></span>  <span data-ttu-id="38b1f-109">使用中の RCW は解放できません。</span><span class="sxs-lookup"><span data-stu-id="38b1f-109">An RCW that is in use cannot be released.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="38b1f-110">解決方法</span><span class="sxs-lookup"><span data-stu-id="38b1f-110">Resolution</span></span>  

 <span data-ttu-id="38b1f-111">現在のスレッドまたは他のスレッドで使用中の可能性がある RCW は、解放しないでください。</span><span class="sxs-lookup"><span data-stu-id="38b1f-111">Do not free an RCW that could be in use either in the current or in other threads.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="38b1f-112">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="38b1f-112">Effect on the Runtime</span></span>  

 <span data-ttu-id="38b1f-113">この MDA は CLR に影響しません。</span><span class="sxs-lookup"><span data-stu-id="38b1f-113">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="38b1f-114">出力</span><span class="sxs-lookup"><span data-stu-id="38b1f-114">Output</span></span>  

 <span data-ttu-id="38b1f-115">エラーを説明するメッセージです。</span><span class="sxs-lookup"><span data-stu-id="38b1f-115">A message describing the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="38b1f-116">構成</span><span class="sxs-lookup"><span data-stu-id="38b1f-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <raceOnRCWCleanup/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="38b1f-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="38b1f-117">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="38b1f-118">マネージド デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="38b1f-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="38b1f-119">相互運用マーシャリング</span><span class="sxs-lookup"><span data-stu-id="38b1f-119">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
