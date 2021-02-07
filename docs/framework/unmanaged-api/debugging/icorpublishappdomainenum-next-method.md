---
description: '詳細情報: ICorPublishAppDomainEnum:: Next メソッド'
title: ICorPublishAppDomainEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomainEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomainEnum::Next
helpviewer_keywords:
- Next method, ICorPublishAppDomainEnum interface [.NET Framework debugging]
- ICorPublishAppDomainEnum::Next method [.NET Framework debugging]
ms.assetid: ad37cd10-0339-4d08-9b0e-4b3428bb4dc3
topic_type:
- apiref
ms.openlocfilehash: 8e8255aa2326c6f0678132f5735d6cdf504dcbd0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721724"
---
# <a name="icorpublishappdomainenumnext-method"></a><span data-ttu-id="7019a-103">ICorPublishAppDomainEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="7019a-103">ICorPublishAppDomainEnum::Next Method</span></span>

<span data-ttu-id="7019a-104">現在プロセスに存在する、指定した数のアプリケーションドメインを、現在の位置から取得します。</span><span class="sxs-lookup"><span data-stu-id="7019a-104">Gets the specified number of application domains that currently exist in the process, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7019a-105">構文</span><span class="sxs-lookup"><span data-stu-id="7019a-105">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]
        ICorPublishAppDomain **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7019a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7019a-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="7019a-107">から取得する要素の数。</span><span class="sxs-lookup"><span data-stu-id="7019a-107">[in] The number of elements to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="7019a-108">入出力取得された [ICorPublishAppDomain](icorpublishappdomain-interface.md) オブジェクトの配列へのポインター。各オブジェクトは、アプリケーションドメインを表します。</span><span class="sxs-lookup"><span data-stu-id="7019a-108">[out] A pointer to the array of retrieved [ICorPublishAppDomain](icorpublishappdomain-interface.md) objects, each of which represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="7019a-109">入出力実際に返されたアプリケーションドメインの数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="7019a-109">[out] Pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="7019a-110">が1の場合、この値は null `celt` になります。</span><span class="sxs-lookup"><span data-stu-id="7019a-110">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7019a-111">要件</span><span class="sxs-lookup"><span data-stu-id="7019a-111">Requirements</span></span>  

 <span data-ttu-id="7019a-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7019a-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7019a-113">**ヘッダー:** CorPub .idl、CorPub .h</span><span class="sxs-lookup"><span data-stu-id="7019a-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="7019a-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7019a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7019a-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7019a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7019a-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="7019a-116">See also</span></span>

- [<span data-ttu-id="7019a-117">ICorPublishAppDomainEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7019a-117">ICorPublishAppDomainEnum Interface</span></span>](icorpublishappdomainenum-interface.md)
