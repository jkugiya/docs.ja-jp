---
title: invalidIUnknown MDA
description: invalidIUnknown マネージド デバッグ アシスタント (MDA) について確認します。これは、ネイティブ コードからマネージド コードに無効な IUnknown ポインターが渡されたときにアクティブになります。
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid IUnknown pointer
- InvalidIUnknown MDA
- invalid IUnknown pointers
- IUnknown pointers
- managed debugging assistants (MDAs), invalid IUnknown pointer
ms.assetid: c7924771-a16b-40fe-b337-ce51dcdf6a12
ms.openlocfilehash: 8e7ca6c9c43c4f507d235c879498b2e831c6eba9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272541"
---
# <a name="invalidiunknown-mda"></a><span data-ttu-id="5c9b9-103">invalidIUnknown MDA</span><span class="sxs-lookup"><span data-stu-id="5c9b9-103">invalidIUnknown MDA</span></span>

<span data-ttu-id="5c9b9-104">`invalidIUnknown` マネージド デバッグ アシスタント (MDA: Managed Debugging Assistant) は、無効な `IUnknown` ポインターがネイティブ コードからマネージド コードに渡されるとアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="5c9b9-104">The `invalidIUnknown` managed debugging assistant (MDA) is activated when an invalid `IUnknown` pointer is passed to managed code from native code.</span></span> <span data-ttu-id="5c9b9-105">`IUnknown` インターフェイスが照会されたときに、`IUnknown` は、成功したことを返すことができませんでした。</span><span class="sxs-lookup"><span data-stu-id="5c9b9-105">The `IUnknown` fails to return success when queried for the `IUnknown` interface.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="5c9b9-106">現象</span><span class="sxs-lookup"><span data-stu-id="5c9b9-106">Symptoms</span></span>  

 <span data-ttu-id="5c9b9-107">引数のマーシャリング中に COM インターフェイス ポインターをマーシャリングすると、予期しないエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="5c9b9-107">An unexpected error occurs when marshaling a COM interface pointer during argument marshaling.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="5c9b9-108">原因</span><span class="sxs-lookup"><span data-stu-id="5c9b9-108">Cause</span></span>  

 <span data-ttu-id="5c9b9-109">CLR に渡された COM インターフェイスで、`QueryInterface` の実装が正しくありません。</span><span class="sxs-lookup"><span data-stu-id="5c9b9-109">An incorrect `QueryInterface` implementation on the COM interface passed to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="5c9b9-110">解決方法</span><span class="sxs-lookup"><span data-stu-id="5c9b9-110">Resolution</span></span>  

 <span data-ttu-id="5c9b9-111">`QueryInterface` の実装を修正します。</span><span class="sxs-lookup"><span data-stu-id="5c9b9-111">Correct the `QueryInterface` implementation.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="5c9b9-112">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="5c9b9-112">Effect on the Runtime</span></span>  

 <span data-ttu-id="5c9b9-113">この MDA は CLR に影響しません。</span><span class="sxs-lookup"><span data-stu-id="5c9b9-113">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="5c9b9-114">出力</span><span class="sxs-lookup"><span data-stu-id="5c9b9-114">Output</span></span>  

 <span data-ttu-id="5c9b9-115">エラーの説明。</span><span class="sxs-lookup"><span data-stu-id="5c9b9-115">The description of the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="5c9b9-116">構成</span><span class="sxs-lookup"><span data-stu-id="5c9b9-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidIUnknown />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5c9b9-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="5c9b9-117">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="5c9b9-118">マネージド デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="5c9b9-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="5c9b9-119">相互運用マーシャリング</span><span class="sxs-lookup"><span data-stu-id="5c9b9-119">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
