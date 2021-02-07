---
description: '詳細については、次を参照してください: いいね:: EnumerateSteppers メソッド'
title: ICorDebugAppDomain::EnumerateSteppers メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.EnumerateSteppers
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::EnumerateSteppers
helpviewer_keywords:
- ICorDebugAppDomain::EnumerateSteppers method [.NET Framework debugging]
- EnumerateSteppers method [.NET Framework debugging]
ms.assetid: 3f3c4503-570e-44c1-ae6a-a3c6b840c732
topic_type:
- apiref
ms.openlocfilehash: a9c7f8b1486522b4740ec18c575c9876512b7d8c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754252"
---
# <a name="icordebugappdomainenumeratesteppers-method"></a><span data-ttu-id="039fb-103">ICorDebugAppDomain::EnumerateSteppers メソッド</span><span class="sxs-lookup"><span data-stu-id="039fb-103">ICorDebugAppDomain::EnumerateSteppers Method</span></span>

<span data-ttu-id="039fb-104">アプリケーションドメイン内のすべてのアクティブな steppers の列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="039fb-104">Gets an enumerator for all active steppers in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="039fb-105">構文</span><span class="sxs-lookup"><span data-stu-id="039fb-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateSteppers (  
    [out] ICorDebugStepperEnum   **ppSteppers  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="039fb-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="039fb-106">Parameters</span></span>  

 `ppSteppers`  
 <span data-ttu-id="039fb-107">入出力アプリケーションドメイン内のすべてのアクティブな steppers の列挙子である、ツールオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="039fb-107">[out] A pointer to the address of an ICorDebugStepperEnum object that is the enumerator for all active steppers in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="039fb-108">要件</span><span class="sxs-lookup"><span data-stu-id="039fb-108">Requirements</span></span>  

 <span data-ttu-id="039fb-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="039fb-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="039fb-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="039fb-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="039fb-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="039fb-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="039fb-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="039fb-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
