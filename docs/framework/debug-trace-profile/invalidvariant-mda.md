---
title: invalidVariant MDA
description: invalidVariant マネージド デバッグ アシスタントについて確認します。これは、ネイティブ/アンマネージドからマネージ ドコードへの呼び出しで無効な VARIANT が検出された場合に呼び出されます。
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid variant
- VARIANT type errors
- InvalidVariant MDA
- invalid VARIANT types
- managed debugging assistants (MDAs), invalid variant
ms.assetid: d273e070-d1b1-4a53-a9c7-7af837b04a3d
ms.openlocfilehash: f0667a54e950ead27000eb6b93ebd547dea1cfb0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96281301"
---
# <a name="invalidvariant-mda"></a><span data-ttu-id="a24f6-103">invalidVariant MDA</span><span class="sxs-lookup"><span data-stu-id="a24f6-103">invalidVariant MDA</span></span>

<span data-ttu-id="a24f6-104">`invalidVariant` マネージド デバッグ アシスタント (MDA: Managed Debugging Assistant) は、ネイティブ コードまたはアンマネージド コードからマネージド コードへの呼び出し時に、無効な `VARIANT` 構造体が見つかるとアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="a24f6-104">The `invalidVariant` managed debugging assistant (MDA) is activated when an invalid `VARIANT` structure is encountered during a call from native or unmanaged code to managed code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="a24f6-105">現象</span><span class="sxs-lookup"><span data-stu-id="a24f6-105">Symptoms</span></span>  

 <span data-ttu-id="a24f6-106">`VARIANT` からオブジェクトへのマーシャリングを含む、ネイティブ コードとマネージド コードの間の遷移中に、予期しない動作が発生します。</span><span class="sxs-lookup"><span data-stu-id="a24f6-106">Unexpected behavior during a transition between native and managed code involving the marshaling of a `VARIANT` to an object.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="a24f6-107">原因</span><span class="sxs-lookup"><span data-stu-id="a24f6-107">Cause</span></span>  

 <span data-ttu-id="a24f6-108">ネイティブ コードが、不適切な `VARIANT` 構造体をマネージド コードに渡しています。</span><span class="sxs-lookup"><span data-stu-id="a24f6-108">Native code is passing a malformed `VARIANT` structure to managed code.</span></span>  <span data-ttu-id="a24f6-109">ランタイムは、この `VARIANT` をオブジェクトにマーシャリングしようとし、`VARIANT` が有効でない場合に MDA がアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="a24f6-109">The runtime attempts to marshal this `VARIANT` to an object and activates the MDA if the `VARIANT` is not valid.</span></span> <span data-ttu-id="a24f6-110">無効な `VARIANT` には、`VARTYPE` VT_EMPTY &#124; VT_BYREF の `VARIANT` や、`VARTYPE` VT_VARIANT の `VARIANT` などがあります。</span><span class="sxs-lookup"><span data-stu-id="a24f6-110">Examples of invalid `VARIANT`S include a `VARIANT` with `VARTYPE` VT_EMPTY &#124; VT_BYREF or a `VARIANT` with `VARTYPE` VT_VARIANT.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="a24f6-111">解決方法</span><span class="sxs-lookup"><span data-stu-id="a24f6-111">Resolution</span></span>  

 <span data-ttu-id="a24f6-112">`VARIANT` を渡すネイティブ コードまたはアンマネージ コードでは、`VARIANT` の形式と初期化が正しいことを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a24f6-112">The native or unmanaged code passing the `VARIANT` must ensure that the `VARIANT` is correctly formed and initialized.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="a24f6-113">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="a24f6-113">Effect on the Runtime</span></span>  

 <span data-ttu-id="a24f6-114">この MDA は、ランタイムの動作への影響はありません。</span><span class="sxs-lookup"><span data-stu-id="a24f6-114">The MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="a24f6-115">出力</span><span class="sxs-lookup"><span data-stu-id="a24f6-115">Output</span></span>  

 <span data-ttu-id="a24f6-116">無効な `VARIANT` がアンマネージド モジュールによりマネージド コードに渡されたことを、ランタイムが検出したことを示す MDA メッセージです。</span><span class="sxs-lookup"><span data-stu-id="a24f6-116">An MDA message indicating that the runtime detected an invalid `VARIANT` passed to managed code by an unmanaged module.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="a24f6-117">構成</span><span class="sxs-lookup"><span data-stu-id="a24f6-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidVariant />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a24f6-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="a24f6-118">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="a24f6-119">マネージド デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="a24f6-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="a24f6-120">相互運用マーシャリング</span><span class="sxs-lookup"><span data-stu-id="a24f6-120">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
