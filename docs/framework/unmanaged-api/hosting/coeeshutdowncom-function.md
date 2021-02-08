---
description: 詳細については、「Coeesの Tdowncom 関数」を参照してください。
title: CoEEShutDownCOM 関数
ms.date: 03/30/2017
api_name:
- CoEEShutDownCOM
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoEEShutDownCOM
helpviewer_keywords:
- CoEEShutDownCOM function [.NET Framework hosting]
ms.assetid: b634cae2-632f-4737-9be4-92d0652844d7
topic_type:
- apiref
ms.openlocfilehash: 4f1ac8107c9a121ebf52ef21a5f2c9006880914f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799864"
---
# <a name="coeeshutdowncom-function"></a><span data-ttu-id="b3f9f-103">CoEEShutDownCOM 関数</span><span class="sxs-lookup"><span data-stu-id="b3f9f-103">CoEEShutDownCOM Function</span></span>

<span data-ttu-id="b3f9f-104">共通言語ランタイム (CLR) に対して、ランタイム呼び出し可能ラッパー (RCW) 内に保持されているすべてのインターフェイスポインターを強制的に解放します。</span><span class="sxs-lookup"><span data-stu-id="b3f9f-104">Forces the common language runtime (CLR) to release all interface pointers it holds inside runtime callable wrappers (RCW).</span></span> <span data-ttu-id="b3f9f-105">これにより、すべての RCW キャッシュが解放されます。</span><span class="sxs-lookup"><span data-stu-id="b3f9f-105">This has the effect of releasing all RCW caches.</span></span> <span data-ttu-id="b3f9f-106">このグローバル関数は .NET Framework 4 では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="b3f9f-106">This global function is deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="b3f9f-107">代わりに、特定のランタイムのエントリポイントを使用します。</span><span class="sxs-lookup"><span data-stu-id="b3f9f-107">Instead, use the entry point for a specific runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3f9f-108">構文</span><span class="sxs-lookup"><span data-stu-id="b3f9f-108">Syntax</span></span>  
  
```cpp  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="b3f9f-109">解説</span><span class="sxs-lookup"><span data-stu-id="b3f9f-109">Remarks</span></span>  

 <span data-ttu-id="b3f9f-110">この関数は、最初にすべての `CoEEShutDownCOM` コンテキストのすべての rcw とすべてのキャッシュを解放してから、セットアップに存在するすべての破棄通知を削除します。</span><span class="sxs-lookup"><span data-stu-id="b3f9f-110">The `CoEEShutDownCOM` function first releases all the RCWs in all contexts and in all caches, and then removes any tear-down notification existing in setup.</span></span> <span data-ttu-id="b3f9f-111">DLL のアンロードは行われません。</span><span class="sxs-lookup"><span data-stu-id="b3f9f-111">No DLL unloading occurs.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="b3f9f-112">この関数は、プロセスに読み込まれるすべてのランタイムに影響します。</span><span class="sxs-lookup"><span data-stu-id="b3f9f-112">This function affects all runtimes that are loaded into the process.</span></span>  
  
 <span data-ttu-id="b3f9f-113">.NET Framework 4 から、影響を与える特定のランタイムに対して、この関数のエントリポイントを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b3f9f-113">Beginning with the .NET Framework 4, call the entry point for this function on the specific runtime you want to affect.</span></span> <span data-ttu-id="b3f9f-114">エントリポイントを取得するには、 [ICLRRuntimeInfo:: GetProcAddress](iclrruntimeinfo-getprocaddress-method.md) メソッドを呼び出し、"Coees Tdowncom" を指定します。</span><span class="sxs-lookup"><span data-stu-id="b3f9f-114">To get the entry point, call the [ICLRRuntimeInfo::GetProcAddress](iclrruntimeinfo-getprocaddress-method.md) method and specify "CoEEShutDownCOM".</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3f9f-115">要件</span><span class="sxs-lookup"><span data-stu-id="b3f9f-115">Requirements</span></span>  

 <span data-ttu-id="b3f9f-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b3f9f-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3f9f-117">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="b3f9f-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b3f9f-118">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="b3f9f-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b3f9f-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3f9f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3f9f-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="b3f9f-120">See also</span></span>

- [<span data-ttu-id="b3f9f-121">メタデータ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="b3f9f-121">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
