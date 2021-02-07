---
description: '詳細情報: IAssemblyCacheItem:: Commit メソッド'
title: IAssemblyCacheItem::Commit メソッド
ms.date: 03/30/2017
api_name:
- IAssemblyCacheItem.Commit
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem::Commit
helpviewer_keywords:
- IAssemblyCacheItem::Commit method [.NET Framework fusion]
- Commit method, IAssemblyCacheItem interface [.NET Framework fusion]
ms.assetid: c2321f17-f46f-4815-ae41-b28678753613
topic_type:
- apiref
ms.openlocfilehash: bd73bb9099090089e52d52009cfef309b33adc53
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760856"
---
# <a name="iassemblycacheitemcommit-method"></a><span data-ttu-id="125e9-103">IAssemblyCacheItem::Commit メソッド</span><span class="sxs-lookup"><span data-stu-id="125e9-103">IAssemblyCacheItem::Commit Method</span></span>

<span data-ttu-id="125e9-104">キャッシュされたアセンブリ参照をメモリにコミットします。</span><span class="sxs-lookup"><span data-stu-id="125e9-104">Commits the cached assembly reference to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="125e9-105">構文</span><span class="sxs-lookup"><span data-stu-id="125e9-105">Syntax</span></span>  
  
```cpp  
HRESULT Commit (  
    [in] DWORD dwFlags,
    [out, optional] ULONG *pulDisposition  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="125e9-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="125e9-106">Parameters</span></span>  

 `dwFlags`  
 <span data-ttu-id="125e9-107">からFusion に定義されているフラグ。</span><span class="sxs-lookup"><span data-stu-id="125e9-107">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pulDisposition`  
 <span data-ttu-id="125e9-108">[out、省略可能]操作の結果を示す値です。</span><span class="sxs-lookup"><span data-stu-id="125e9-108">[out, optional] A value that indicates the result of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="125e9-109">要件</span><span class="sxs-lookup"><span data-stu-id="125e9-109">Requirements</span></span>  

 <span data-ttu-id="125e9-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="125e9-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="125e9-111">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="125e9-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="125e9-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="125e9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="125e9-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="125e9-113">See also</span></span>

- [<span data-ttu-id="125e9-114">IAssemblyCacheItem インターフェイス</span><span class="sxs-lookup"><span data-stu-id="125e9-114">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
