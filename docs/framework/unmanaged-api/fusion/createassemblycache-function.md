---
description: CreateAssemblyCache 関数の詳細について説明します。
title: CreateAssemblyCache 関数
ms.date: 03/30/2017
api_name:
- CreateAssemblyCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyCache
helpviewer_keywords:
- CreateAssemblyCache function [.NET Framework fusion]
ms.assetid: 348c7c8c-8578-46ae-97cf-480d6015c3c6
topic_type:
- apiref
ms.openlocfilehash: 1646e1d33401c557b13ae5c025f53aef48042004
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761162"
---
# <a name="createassemblycache-function"></a><span data-ttu-id="43644-103">CreateAssemblyCache 関数</span><span class="sxs-lookup"><span data-stu-id="43644-103">CreateAssemblyCache Function</span></span>

<span data-ttu-id="43644-104">グローバルアセンブリキャッシュを表す新しい [Iassemblycache](iassemblycache-interface.md) インスタンスへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="43644-104">Gets a pointer to a new [IAssemblyCache](iassemblycache-interface.md) instance that represents the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43644-105">構文</span><span class="sxs-lookup"><span data-stu-id="43644-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyCache (  
    [out] IAssemblyCache  **ppAsmCache,  
    [in]  DWORD           dwReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="43644-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="43644-106">Parameters</span></span>  

 `ppAsmCache`  
 <span data-ttu-id="43644-107">入出力返された `IAssemblyCache` ポインター。</span><span class="sxs-lookup"><span data-stu-id="43644-107">[out] The returned `IAssemblyCache` pointer.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="43644-108">[入力] 将来の機能拡張に備えて予約されています。</span><span class="sxs-lookup"><span data-stu-id="43644-108">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="43644-109">`dwReserved` 0 (ゼロ) にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="43644-109">`dwReserved` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43644-110">要件</span><span class="sxs-lookup"><span data-stu-id="43644-110">Requirements</span></span>  

 <span data-ttu-id="43644-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="43644-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43644-112">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="43644-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="43644-113">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="43644-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="43644-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43644-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43644-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="43644-115">See also</span></span>

- [<span data-ttu-id="43644-116">IAssemblyCache インターフェイス</span><span class="sxs-lookup"><span data-stu-id="43644-116">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
- [<span data-ttu-id="43644-117">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="43644-117">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
- [<span data-ttu-id="43644-118">グローバル アセンブリ キャッシュ</span><span class="sxs-lookup"><span data-stu-id="43644-118">Global Assembly Cache</span></span>](../../app-domains/gac.md)
