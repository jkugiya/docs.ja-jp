---
description: '詳細について: ICorPublish:: GetProcess メソッド'
title: ICorPublish::GetProcess メソッド
ms.date: 03/30/2017
api_name:
- ICorPublish.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish::GetProcess
helpviewer_keywords:
- ICorPublish::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorPublish interface [.NET Framework debugging]
ms.assetid: c5143805-2eb7-45b8-85ed-c8fb34df1084
topic_type:
- apiref
ms.openlocfilehash: d288a772274618cc99b63a68b37e84e543957b44
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721984"
---
# <a name="icorpublishgetprocess-method"></a><span data-ttu-id="1177c-103">ICorPublish::GetProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="1177c-103">ICorPublish::GetProcess Method</span></span>

<span data-ttu-id="1177c-104">指定した識別子を持つプロセスを表す [ICorPublishProcess](icorpublishprocess-interface.md) インスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="1177c-104">Gets an [ICorPublishProcess](icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1177c-105">構文</span><span class="sxs-lookup"><span data-stu-id="1177c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess(  
    [in] unsigned              pid,
    [out] ICorPublishProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1177c-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1177c-106">Parameters</span></span>  

 `pid`  
 <span data-ttu-id="1177c-107">からプロセスの識別子。</span><span class="sxs-lookup"><span data-stu-id="1177c-107">[in] The identifier of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="1177c-108">入出力プロセスを表すインスタンスのアドレスへのポインター `ICorPublishProcess` 。</span><span class="sxs-lookup"><span data-stu-id="1177c-108">[out] A pointer to the address of an `ICorPublishProcess` instance that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1177c-109">解説</span><span class="sxs-lookup"><span data-stu-id="1177c-109">Remarks</span></span>  

 <span data-ttu-id="1177c-110">`GetProcess` プロセスが存在しない場合、または現在のユーザーがデバッグできるマネージプロセスでない場合は、失敗します。</span><span class="sxs-lookup"><span data-stu-id="1177c-110">`GetProcess` fails if the process doesn't exist, or isn't a managed process that can be debugged by the current user.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1177c-111">要件</span><span class="sxs-lookup"><span data-stu-id="1177c-111">Requirements</span></span>  

 <span data-ttu-id="1177c-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1177c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1177c-113">**ヘッダー:** CorPub .idl、CorPub .h</span><span class="sxs-lookup"><span data-stu-id="1177c-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="1177c-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1177c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1177c-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1177c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1177c-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="1177c-116">See also</span></span>

- [<span data-ttu-id="1177c-117">ICorPublish インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1177c-117">ICorPublish Interface</span></span>](icorpublish-interface.md)
