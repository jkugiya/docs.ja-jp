---
title: invalidFunctionPointerInDelegate MDA
description: invalidFunctionPointerInDelegate マネージド デバッグ アシスタント (MDA) について確認します。これは、デリゲートを作成するために無効な関数ポインターが渡された場合に呼び出されます。
ms.date: 03/30/2017
helpviewer_keywords:
- invalidFunctionPointerInDelegate MDA
- managed debugging assistants (MDAs), invalid function pointer to delegates
- MDAs (managed debugging assistants), invalid function pointer to delegates
- function pointers, invalid
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
- invalid function pointers
ms.assetid: 99ae44f1-783e-49a9-9009-24f54bbd0f09
ms.openlocfilehash: 8072d35a45cb1e0590aa5533210d0e0f86913164
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272619"
---
# <a name="invalidfunctionpointerindelegate-mda"></a><span data-ttu-id="d3f1c-103">invalidFunctionPointerInDelegate MDA</span><span class="sxs-lookup"><span data-stu-id="d3f1c-103">invalidFunctionPointerInDelegate MDA</span></span>

<span data-ttu-id="d3f1c-104">ネイティブ関数ポインターに対するデリゲートを作成するときに、無効な関数ポインターが渡されると、`invalidFunctionPointerInDelegate` マネージド デバッグ アシスタント (MDA) がアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="d3f1c-104">The `invalidFunctionPointerInDelegate` managed debugging assistant (MDA) is activated when an invalid function pointer is passed in to construct a delegate over a native function pointer.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="d3f1c-105">現象</span><span class="sxs-lookup"><span data-stu-id="d3f1c-105">Symptoms</span></span>  

 <span data-ttu-id="d3f1c-106">関数ポインターでデリゲートを使用すると、アクセス違反または予期しないメモリの破損が発生します。</span><span class="sxs-lookup"><span data-stu-id="d3f1c-106">Access violations or unexpected memory corruption when using a delegate over a function pointer.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="d3f1c-107">原因</span><span class="sxs-lookup"><span data-stu-id="d3f1c-107">Cause</span></span>  

 <span data-ttu-id="d3f1c-108">無効な関数ポインターが指定されました。</span><span class="sxs-lookup"><span data-stu-id="d3f1c-108">An invalid function pointer was specified.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="d3f1c-109">解決方法</span><span class="sxs-lookup"><span data-stu-id="d3f1c-109">Resolution</span></span>  

 <span data-ttu-id="d3f1c-110">有効な関数ポインターを指定します。</span><span class="sxs-lookup"><span data-stu-id="d3f1c-110">Specify a valid function pointer</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="d3f1c-111">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="d3f1c-111">Effect on the Runtime</span></span>  

 <span data-ttu-id="d3f1c-112">この MDA は CLR に影響しません。</span><span class="sxs-lookup"><span data-stu-id="d3f1c-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="d3f1c-113">出力</span><span class="sxs-lookup"><span data-stu-id="d3f1c-113">Output</span></span>  

 <span data-ttu-id="d3f1c-114">無効な関数ポインター。</span><span class="sxs-lookup"><span data-stu-id="d3f1c-114">The invalid function pointer.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="d3f1c-115">構成</span><span class="sxs-lookup"><span data-stu-id="d3f1c-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidFunctionPointerInDelegate />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d3f1c-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="d3f1c-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="d3f1c-117">マネージド デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="d3f1c-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="d3f1c-118">相互運用マーシャリング</span><span class="sxs-lookup"><span data-stu-id="d3f1c-118">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
