---
title: pInvokeLog MDA
description: pInvokeLog マネージド デバッグ アシスタント (MDA) について説明します。これは、.NET 内で実行中に使用される一意のプラットフォーム呼び出しシグネチャごとにアクティブになります。
ms.date: 03/30/2017
helpviewer_keywords:
- signatures, platform invoke
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- platform invoke log
- PInvokeLog MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: b830444a-5003-49fe-b89b-b8bee22f7b1a
ms.openlocfilehash: b8cb4805663a2b28a133f98503730199af695c4f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96271461"
---
# <a name="pinvokelog-mda"></a><span data-ttu-id="2c1b7-103">pInvokeLog MDA</span><span class="sxs-lookup"><span data-stu-id="2c1b7-103">pInvokeLog MDA</span></span>

<span data-ttu-id="2c1b7-104">`pInvokeLog` マネージド デバッグ アシスタント (MDA) は、実行中に使用される一意のプラットフォーム呼び出しシグネチャごとにアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="2c1b7-104">The `pInvokeLog` managed debugging assistant (MDA) is activated for each unique platform invoke signature used during execution.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="2c1b7-105">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="2c1b7-105">Effect on the Runtime</span></span>  

 <span data-ttu-id="2c1b7-106">この MDA は CLR に影響しません。</span><span class="sxs-lookup"><span data-stu-id="2c1b7-106">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="2c1b7-107">出力</span><span class="sxs-lookup"><span data-stu-id="2c1b7-107">Output</span></span>  

 <span data-ttu-id="2c1b7-108">実行中に使用されるプラットフォーム呼び出しシグネチャを示すメッセージ。</span><span class="sxs-lookup"><span data-stu-id="2c1b7-108">A message indicating the platform invoke signature used during execution.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="2c1b7-109">構成</span><span class="sxs-lookup"><span data-stu-id="2c1b7-109">Configuration</span></span>  

 <span data-ttu-id="2c1b7-110">各 match 要素で、プラットフォーム呼び出しが行われる .dll ファイルがフィルター処理されます。</span><span class="sxs-lookup"><span data-stu-id="2c1b7-110">Each match element filters the .dll files to which platform invoke calls are made.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <pInvokeLog>  
      <filter>  
        <match dllName="user32.dll"/>  
        <match dllName="kernel32.dll"/>  
      </filter>  
    </pInvokeLog>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2c1b7-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="2c1b7-111">See also</span></span>

- [<span data-ttu-id="2c1b7-112">マネージド デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="2c1b7-112">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="2c1b7-113">アンマネージ DLL 関数の処理</span><span class="sxs-lookup"><span data-stu-id="2c1b7-113">Consuming Unmanaged DLL Functions</span></span>](../interop/consuming-unmanaged-dll-functions.md)
