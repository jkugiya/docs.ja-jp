---
description: '詳細について: ICLRMetaHost:: EnumerateInstalledRuntimes メソッド'
title: ICLRMetaHost::EnumerateInstalledRuntimes メソッド
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.EnumerateInstalledRuntimes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::EnumerateInstalledRuntimes
helpviewer_keywords:
- ICLRMetaHost::EnumerateInstalledRuntimes method [.NET Framework hosting]
- EnumerateInstalledRuntimes method [.NET Framework hosting]
ms.assetid: 9e359384-0d3d-451c-807e-5d7fcebf2be7
topic_type:
- apiref
ms.openlocfilehash: a1c2fe46a64339e013df0f65dc073d183036a0fb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689197"
---
# <a name="iclrmetahostenumerateinstalledruntimes-method"></a><span data-ttu-id="56fc8-103">ICLRMetaHost::EnumerateInstalledRuntimes メソッド</span><span class="sxs-lookup"><span data-stu-id="56fc8-103">ICLRMetaHost::EnumerateInstalledRuntimes Method</span></span>

<span data-ttu-id="56fc8-104">コンピューターにインストールされている共通言語ランタイム (CLR) の各バージョンの有効な [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) インターフェイスを含む列挙を返します。</span><span class="sxs-lookup"><span data-stu-id="56fc8-104">Returns an enumeration that contains a valid [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface for each version of the common language runtime (CLR) that is installed on a computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56fc8-105">構文</span><span class="sxs-lookup"><span data-stu-id="56fc8-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateInstalledRuntimes (  
    [out, retval] IEnumUnknown **ppEnumerator);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56fc8-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="56fc8-106">Parameters</span></span>  

 `ppEnumerator`  
 <span data-ttu-id="56fc8-107">入出力コンピューターにインストールされている CLR の各バージョンに対応する [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) インターフェイスの列挙体。</span><span class="sxs-lookup"><span data-stu-id="56fc8-107">[out] An enumeration of [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interfaces corresponding to each version of the CLR that is installed on the computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="56fc8-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="56fc8-108">Return Value</span></span>  

 <span data-ttu-id="56fc8-109">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="56fc8-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="56fc8-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="56fc8-110">HRESULT</span></span>|<span data-ttu-id="56fc8-111">説明</span><span class="sxs-lookup"><span data-stu-id="56fc8-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="56fc8-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="56fc8-112">S_OK</span></span>|<span data-ttu-id="56fc8-113">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="56fc8-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="56fc8-114">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="56fc8-114">E_POINTER</span></span>|<span data-ttu-id="56fc8-115">`ppEnumerator` が null です。</span><span class="sxs-lookup"><span data-stu-id="56fc8-115">`ppEnumerator` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="56fc8-116">要件</span><span class="sxs-lookup"><span data-stu-id="56fc8-116">Requirements</span></span>  

 <span data-ttu-id="56fc8-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="56fc8-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56fc8-118">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="56fc8-118">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="56fc8-119">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="56fc8-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="56fc8-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56fc8-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56fc8-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="56fc8-121">See also</span></span>

- [<span data-ttu-id="56fc8-122">ICLRMetaHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="56fc8-122">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="56fc8-123">ホスティング</span><span class="sxs-lookup"><span data-stu-id="56fc8-123">Hosting</span></span>](index.md)
