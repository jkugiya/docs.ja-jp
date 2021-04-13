---
title: reportAvOnComRelease MDA
description: reportAvOnComRelease マネージド デバッグ アシスタント (MDA) について確認します。これは、.NET 内でのアクセス違反とメモリの破損によってアクティブ化される可能性があります。
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), reference counting errors
- exceptions, reference counting errors
- ReportAvOnComRelease MDA
- COM release access violations
- user reference counting errors
- managed debugging assistants (MDAs), reference counting errors
- report access violation on Com release
- reference counting errors
ms.assetid: a2b86b63-08b2-4943-b344-3c2cf46ccd31
ms.openlocfilehash: c5047aa4005cdaa9ae6aabe8dcd7ee838ee13f58
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267118"
---
# <a name="reportavoncomrelease-mda"></a><span data-ttu-id="151b1-103">reportAvOnComRelease MDA</span><span class="sxs-lookup"><span data-stu-id="151b1-103">reportAvOnComRelease MDA</span></span>

<span data-ttu-id="151b1-104">COM 相互運用を実行していて、COM の生呼び出しと組み合わせた `reportAvOnComRelease` または <xref:System.Runtime.InteropServices.Marshal.Release%2A> メソッドを使用しているときに、ユーザー参照カウントのエラーが原因で例外がスローされると、<xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> マネージド デバッグ アシスタント (MDA) がアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="151b1-104">The `reportAvOnComRelease` managed debugging assistant (MDA) is activated when exceptions are thrown due to user reference counting errors while performing COM interop and using the <xref:System.Runtime.InteropServices.Marshal.Release%2A> or <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> method combined with raw COM calls.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="151b1-105">現象</span><span class="sxs-lookup"><span data-stu-id="151b1-105">Symptoms</span></span>  

 <span data-ttu-id="151b1-106">アクセス違反およびメモリ破損が発生します。</span><span class="sxs-lookup"><span data-stu-id="151b1-106">Access violations and memory corruption.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="151b1-107">原因</span><span class="sxs-lookup"><span data-stu-id="151b1-107">Cause</span></span>  

 <span data-ttu-id="151b1-108">COM 相互運用を実行していて、生の COM 呼び出しと組み合わせた <xref:System.Runtime.InteropServices.Marshal.Release%2A> または <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> メソッドを使用しているときに、ユーザー参照カウントのエラーが原因で例外がスローされることがあります。</span><span class="sxs-lookup"><span data-stu-id="151b1-108">Occasionally, an exception is thrown due to user reference counting errors while performing COM interop and using the <xref:System.Runtime.InteropServices.Marshal.Release%2A> or <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> method combined with raw COM calls.</span></span> <span data-ttu-id="151b1-109">通常、この例外は破棄されます。これは、破棄しないと CLR でアクセス違反が発生し、ダウンしてしまうためです。</span><span class="sxs-lookup"><span data-stu-id="151b1-109">Normally, this exception is discarded because not doing so would cause an access violation in the CLR, bringing it down.</span></span> <span data-ttu-id="151b1-110">このアシスタントが有効な場合は、そのような例外を単に破棄するのではなく、検出して報告できます。</span><span class="sxs-lookup"><span data-stu-id="151b1-110">When this assistant is enabled, such exceptions can be detected and reported instead of being simply discarded.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="151b1-111">解決方法</span><span class="sxs-lookup"><span data-stu-id="151b1-111">Resolution</span></span>  

 <span data-ttu-id="151b1-112">参照カウントのコードを調べてエラーを探します。また、オブジェクトのネイティブ クライアントに参照カウントのエラーがないかどうかも調べます。</span><span class="sxs-lookup"><span data-stu-id="151b1-112">Examine your reference counting code and search for errors as well as examining the native clients of your object for reference counting errors.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="151b1-113">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="151b1-113">Effect on the Runtime</span></span>  

 <span data-ttu-id="151b1-114">2 つのモードを利用できます。</span><span class="sxs-lookup"><span data-stu-id="151b1-114">Two modes are available.</span></span> <span data-ttu-id="151b1-115">`allowAv` 属性が `true` の場合、アシスタントは、ランタイムがアクセス違反を破棄しないようにします。</span><span class="sxs-lookup"><span data-stu-id="151b1-115">If the `allowAv` attribute is `true`, the assistant prevents the runtime from discarding the access violation.</span></span> <span data-ttu-id="151b1-116">`allowAv` が `false` の場合 (既定)、ランタイムはアクセス違反を破棄しますが、例外がスローされて破棄されたことを通知する警告メッセージがユーザーに報告されます。</span><span class="sxs-lookup"><span data-stu-id="151b1-116">If `allowAv` is `false`, which is the default, the runtime discards the access violation, but a warning message is reported to the user to indicate that an exception was thrown and discarded.</span></span>  
  
## <a name="output"></a><span data-ttu-id="151b1-117">出力</span><span class="sxs-lookup"><span data-stu-id="151b1-117">Output</span></span>  

 <span data-ttu-id="151b1-118">可能な場合、出力には COM インターフェイス ポインターの元の vtable が含まれます。</span><span class="sxs-lookup"><span data-stu-id="151b1-118">If possible, the output contains the COM interface pointer's original vtable.</span></span> <span data-ttu-id="151b1-119">それ以外の場合は、情報メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="151b1-119">Otherwise, an informational message is displayed.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="151b1-120">構成</span><span class="sxs-lookup"><span data-stu-id="151b1-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reportAvOnComRelease />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="151b1-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="151b1-121">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="151b1-122">マネージド デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="151b1-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="151b1-123">相互運用マーシャリング</span><span class="sxs-lookup"><span data-stu-id="151b1-123">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
