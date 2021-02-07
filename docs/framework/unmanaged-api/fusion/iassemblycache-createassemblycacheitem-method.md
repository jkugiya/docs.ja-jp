---
description: '詳細については、次を参照してください: IAssemblyCache:: CreateAssemblyCacheItem メソッド'
title: IAssemblyCache::CreateAssemblyCacheItem メソッド
ms.date: 03/30/2017
api_name:
- IAssemblyCache.CreateAssemblyCacheItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::CreateAssemblyCacheItem
helpviewer_keywords:
- IAssemblyCache::CreateAssemblyCacheItem method [.NET Framework fusion]
- CreateAssemblyCacheItem method [.NET Framework fusion]
ms.assetid: 017a7ba5-aaaf-44e2-9cbe-ceebef259df0
topic_type:
- apiref
ms.openlocfilehash: 3377901d358bcf643ce0d30336c1c0cd8089e50c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760980"
---
# <a name="iassemblycachecreateassemblycacheitem-method"></a><span data-ttu-id="9e928-103">IAssemblyCache::CreateAssemblyCacheItem メソッド</span><span class="sxs-lookup"><span data-stu-id="9e928-103">IAssemblyCache::CreateAssemblyCacheItem Method</span></span>

<span data-ttu-id="9e928-104">新しい [Iassemblycacheitem](iassemblycacheitem-interface.md) オブジェクトへの参照を取得します。</span><span class="sxs-lookup"><span data-stu-id="9e928-104">Gets a reference to a new [IAssemblyCacheItem](iassemblycacheitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e928-105">構文</span><span class="sxs-lookup"><span data-stu-id="9e928-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyCacheItem (  
    [in]  DWORD dwFlags,  
    [in]  PVOID pvReserved,  
    [out] IAssemblyCacheItem **ppAsmItem,  
    [in, optional] LPCWSTR pszAssemblyName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e928-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9e928-106">Parameters</span></span>  

 `dwFlags`  
 <span data-ttu-id="9e928-107">からFusion に定義されているフラグ。</span><span class="sxs-lookup"><span data-stu-id="9e928-107">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="9e928-108">サポートされている値を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9e928-108">The following values are supported:</span></span>  
  
- <span data-ttu-id="9e928-109">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span><span class="sxs-lookup"><span data-stu-id="9e928-109">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span></span>  
  
- <span data-ttu-id="9e928-110">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span><span class="sxs-lookup"><span data-stu-id="9e928-110">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="9e928-111">[入力] 将来の機能拡張に備えて予約されています。</span><span class="sxs-lookup"><span data-stu-id="9e928-111">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="9e928-112">`pvReserved` null 参照である必要があります。</span><span class="sxs-lookup"><span data-stu-id="9e928-112">`pvReserved` must be a null reference.</span></span>  
  
 `ppAsmItem`  
 <span data-ttu-id="9e928-113">入出力返された `IAssemblyCacheItem` ポインター。</span><span class="sxs-lookup"><span data-stu-id="9e928-113">[out] The returned `IAssemblyCacheItem` pointer.</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="9e928-114">[in、optional]正規化が解除、コンマ区切りの `name=value` ペア。</span><span class="sxs-lookup"><span data-stu-id="9e928-114">[in, optional] Uncanonicalized, comma-separated `name=value` pairs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e928-115">要件</span><span class="sxs-lookup"><span data-stu-id="9e928-115">Requirements</span></span>  

 <span data-ttu-id="9e928-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e928-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e928-117">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="9e928-117">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="9e928-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e928-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e928-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="9e928-119">See also</span></span>

- [<span data-ttu-id="9e928-120">IAssemblyCache インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9e928-120">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
- [<span data-ttu-id="9e928-121">IAssemblyCacheItem インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9e928-121">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
