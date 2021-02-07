---
description: '詳細について: ICorPublishProcess:: GetProcessID メソッド'
title: ICorPublishProcess::GetProcessID メソッド
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.GetProcessID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::GetProcessID
helpviewer_keywords:
- ICorPublishProcess::GetProcessID method [.NET Framework debugging]
- GetProcessID method [.NET Framework debugging]
ms.assetid: f31185e0-f01d-463a-b392-42163e39bfe9
topic_type:
- apiref
ms.openlocfilehash: f959a49330e0ef4ade2a878acfd287657b5086ec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728822"
---
# <a name="icorpublishprocessgetprocessid-method"></a><span data-ttu-id="ea7cb-103">ICorPublishProcess::GetProcessID メソッド</span><span class="sxs-lookup"><span data-stu-id="ea7cb-103">ICorPublishProcess::GetProcessID Method</span></span>

<span data-ttu-id="ea7cb-104">このプロセスのオペレーティングシステム識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="ea7cb-104">Gets the operating system identifier for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea7cb-105">構文</span><span class="sxs-lookup"><span data-stu-id="ea7cb-105">Syntax</span></span>  
  
```cpp  
HRESULT GetProcessID (  
    [out] unsigned   *pid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea7cb-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ea7cb-106">Parameters</span></span>  

 `pid`  
 <span data-ttu-id="ea7cb-107">入出力この [ICorPublishProcess](icorpublishprocess-interface.md) オブジェクトによって表されるプロセスの識別子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ea7cb-107">[out] A pointer to the identifier of the process represented by this [ICorPublishProcess](icorpublishprocess-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea7cb-108">要件</span><span class="sxs-lookup"><span data-stu-id="ea7cb-108">Requirements</span></span>  

 <span data-ttu-id="ea7cb-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea7cb-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea7cb-110">**ヘッダー:** CorPub .idl、CorPub .h</span><span class="sxs-lookup"><span data-stu-id="ea7cb-110">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="ea7cb-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ea7cb-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea7cb-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea7cb-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea7cb-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="ea7cb-113">See also</span></span>

- [<span data-ttu-id="ea7cb-114">ICorPublishProcess インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ea7cb-114">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)
