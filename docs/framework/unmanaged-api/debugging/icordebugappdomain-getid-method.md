---
description: '詳細については、次を参照してください: いいね:: GetId メソッド'
title: ICorDebugAppDomain::GetId メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetId
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetId
helpviewer_keywords:
- GetId method, ICorDebugAppDomain interface [.NET Framework debugging]
- ICorDebugAppDomain::GetId method [.NET Framework debugging]
ms.assetid: 32c27576-71fa-42ee-8230-67b92913ea08
topic_type:
- apiref
ms.openlocfilehash: ea660aa08e93e4ce2d97f1e7ae05b261db91118f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772467"
---
# <a name="icordebugappdomaingetid-method"></a><span data-ttu-id="47c36-103">ICorDebugAppDomain::GetId メソッド</span><span class="sxs-lookup"><span data-stu-id="47c36-103">ICorDebugAppDomain::GetId Method</span></span>

<span data-ttu-id="47c36-104">アプリケーションドメインの一意の識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="47c36-104">Gets the unique identifier of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47c36-105">構文</span><span class="sxs-lookup"><span data-stu-id="47c36-105">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] ULONG32   *pId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="47c36-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="47c36-106">Parameters</span></span>  

 `pId`  
 <span data-ttu-id="47c36-107">入出力アプリケーションドメインの一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="47c36-107">[out] The unique identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47c36-108">解説</span><span class="sxs-lookup"><span data-stu-id="47c36-108">Remarks</span></span>  

 <span data-ttu-id="47c36-109">アプリケーションドメインの識別子は、含まれているプロセス内で一意です。</span><span class="sxs-lookup"><span data-stu-id="47c36-109">The identifier for the application domain is unique within the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47c36-110">要件</span><span class="sxs-lookup"><span data-stu-id="47c36-110">Requirements</span></span>  

 <span data-ttu-id="47c36-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47c36-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47c36-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="47c36-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="47c36-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="47c36-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="47c36-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47c36-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
