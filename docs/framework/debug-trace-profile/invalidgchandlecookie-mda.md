---
title: invalidGCHandleCookie MDA
description: invalidGCHandleCookie マネージド デバッグ アシスタント (MDA) について確認します。これは、無効な IntPtr Cookie から GCHandle への変換が試行されたときにアクティブになります。
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid cookies
- cookies, invalid
- managed debugging assistants (MDAs), invalid cookies
- InvalidGCHandleCookie MDA
- invalid cookies
ms.assetid: 613ad742-3c11-401d-a6b3-893ceb8de4f8
ms.openlocfilehash: 36806498445da78c8d9dd5c51c1903b253a39da0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272606"
---
# <a name="invalidgchandlecookie-mda"></a><span data-ttu-id="d564d-103">invalidGCHandleCookie MDA</span><span class="sxs-lookup"><span data-stu-id="d564d-103">invalidGCHandleCookie MDA</span></span>

<span data-ttu-id="d564d-104">`invalidGCHandleCookie` マネージド デバッグ アシスタント (MDA) は、無効な <xref:System.IntPtr> Cookie から <xref:System.Runtime.InteropServices.GCHandle> への変換が試行されたときにアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="d564d-104">The `invalidGCHandleCookie` managed debugging assistant (MDA) is activated when a conversion from an invalid <xref:System.IntPtr> cookie to a <xref:System.Runtime.InteropServices.GCHandle> is attempted.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="d564d-105">現象</span><span class="sxs-lookup"><span data-stu-id="d564d-105">Symptoms</span></span>  

 <span data-ttu-id="d564d-106"><xref:System.Runtime.InteropServices.GCHandle> の使用または <xref:System.IntPtr> からの取得を試みているときのアクセス違反やメモリ破損などの定義されていない動作。</span><span class="sxs-lookup"><span data-stu-id="d564d-106">Undefined behavior such as access violations and memory corruption while attempting to use or retrieve a <xref:System.Runtime.InteropServices.GCHandle> from an <xref:System.IntPtr>.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="d564d-107">原因</span><span class="sxs-lookup"><span data-stu-id="d564d-107">Cause</span></span>  

 <span data-ttu-id="d564d-108">Cookie が <xref:System.Runtime.InteropServices.GCHandle> から最初に作成されていないために無効になっている可能性があります。既に解放されている <xref:System.Runtime.InteropServices.GCHandle> が異なるアプリケーション ドメイン内で <xref:System.Runtime.InteropServices.GCHandle> の Cookie になっているか、<xref:System.Runtime.InteropServices.GCHandle> としてネイティブ コードにマーシャリングされても、<xref:System.IntPtr> として CLR に再び渡され、キャストが試行されたことを表します。</span><span class="sxs-lookup"><span data-stu-id="d564d-108">The cookie is probably invalid because it was not originally created from a <xref:System.Runtime.InteropServices.GCHandle>, represents a <xref:System.Runtime.InteropServices.GCHandle> that has already been freed, is a cookie to a <xref:System.Runtime.InteropServices.GCHandle> in a different application domain, or was marshaled to native code as a <xref:System.Runtime.InteropServices.GCHandle> but passed back into the CLR as an <xref:System.IntPtr>, where a cast was attempted.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="d564d-109">解決方法</span><span class="sxs-lookup"><span data-stu-id="d564d-109">Resolution</span></span>  

 <span data-ttu-id="d564d-110"><xref:System.Runtime.InteropServices.GCHandle> の有効な <xref:System.IntPtr> Cookie を指定します。</span><span class="sxs-lookup"><span data-stu-id="d564d-110">Specify a valid <xref:System.IntPtr> cookie for the <xref:System.Runtime.InteropServices.GCHandle>.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="d564d-111">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="d564d-111">Effect on the Runtime</span></span>  

 <span data-ttu-id="d564d-112">この MDA が有効になっているときには、返される Cookie の値が MDA が有効になっていないときに返される値と異なるので、デバッガはルートをオブジェクトまでトレースできなくなります。</span><span class="sxs-lookup"><span data-stu-id="d564d-112">When this MDA is enabled, the debugger is no longer able to trace the roots back to their objects because the cookie values passed back are different from the ones returned when the MDA is not enabled.</span></span>  
  
## <a name="output"></a><span data-ttu-id="d564d-113">出力</span><span class="sxs-lookup"><span data-stu-id="d564d-113">Output</span></span>  

 <span data-ttu-id="d564d-114">無効な <xref:System.IntPtr> Cookie 値が報告されます。</span><span class="sxs-lookup"><span data-stu-id="d564d-114">The invalid <xref:System.IntPtr> cookie value is reported.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="d564d-115">構成</span><span class="sxs-lookup"><span data-stu-id="d564d-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidGCHandleCookie />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d564d-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="d564d-116">See also</span></span>

- <xref:System.Runtime.InteropServices.GCHandle.FromIntPtr%2A>
- <xref:System.Runtime.InteropServices.GCHandle>
- [<span data-ttu-id="d564d-117">マネージド デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="d564d-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
