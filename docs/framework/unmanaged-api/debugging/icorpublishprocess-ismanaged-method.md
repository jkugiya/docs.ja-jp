---
description: '詳細について: ICorPublishProcess:: IsManaged メソッド'
title: ICorPublishProcess::IsManaged メソッド
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.IsManaged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::IsManaged
helpviewer_keywords:
- IsManaged method, ICorPublishProcess interface [.NET Framework debugging]
- ICorPublishProcess::IsManaged method [.NET Framework debugging]
ms.assetid: 06b1f7cc-acdf-47a6-9d53-d9dec2424152
topic_type:
- apiref
ms.openlocfilehash: 55f620a896efd87c2f154ac68ef2db1a1b0a1ebc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790504"
---
# <a name="icorpublishprocessismanaged-method"></a><span data-ttu-id="89b84-103">ICorPublishProcess::IsManaged メソッド</span><span class="sxs-lookup"><span data-stu-id="89b84-103">ICorPublishProcess::IsManaged Method</span></span>

<span data-ttu-id="89b84-104">この [ICorPublishProcess](icorpublishprocess-interface.md) によって参照されるプロセスに、マネージコードがあることがわかっているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="89b84-104">Gets a value that indicates whether the process referenced by this [ICorPublishProcess](icorpublishprocess-interface.md) is known to have managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89b84-105">構文</span><span class="sxs-lookup"><span data-stu-id="89b84-105">Syntax</span></span>  
  
```cpp  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89b84-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="89b84-106">Parameters</span></span>  

 `pbManaged`  
 <span data-ttu-id="89b84-107">入出力プロセスにマネージコードがあるかどうかを示すブール値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="89b84-107">[out] A pointer to a Boolean value that indicates whether the process has managed code.</span></span> <span data-ttu-id="89b84-108">`true`プロセスにマネージコードがある場合は、値はです。それ以外の場合は `false` です。</span><span class="sxs-lookup"><span data-stu-id="89b84-108">The value is `true` if the process has managed code; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="89b84-109">解説</span><span class="sxs-lookup"><span data-stu-id="89b84-109">Remarks</span></span>  

 <span data-ttu-id="89b84-110">現在のバージョンのでは `ICorPublishProcess` 、マネージコードを持つプロセスのみにアクセスが許可されるため、は `IsManaged` 常にを返し `true` ます。</span><span class="sxs-lookup"><span data-stu-id="89b84-110">Since the current version of `ICorPublishProcess` allows access only to processes that have managed code, `IsManaged` always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89b84-111">要件</span><span class="sxs-lookup"><span data-stu-id="89b84-111">Requirements</span></span>  

 <span data-ttu-id="89b84-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89b84-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89b84-113">**ヘッダー:** CorPub .idl、CorPub .h</span><span class="sxs-lookup"><span data-stu-id="89b84-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="89b84-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="89b84-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89b84-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89b84-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89b84-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="89b84-116">See also</span></span>

- [<span data-ttu-id="89b84-117">ICorPublishProcess インターフェイス</span><span class="sxs-lookup"><span data-stu-id="89b84-117">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)
