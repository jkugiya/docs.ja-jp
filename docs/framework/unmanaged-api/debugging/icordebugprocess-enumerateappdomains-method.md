---
description: '詳細については、次を参照してください: EnumerateAppDomains Method:: メソッド'
title: ICorDebugProcess::EnumerateAppDomains メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.EnumerateAppDomains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::EnumerateAppDomains
helpviewer_keywords:
- ICorDebugProcess::EnumerateAppDomains method [.NET Framework debugging]
- EnumerateAppDomains method [.NET Framework debugging]
ms.assetid: d508981f-e2b2-445b-a649-69951c22702d
topic_type:
- apiref
ms.openlocfilehash: d212fafe7ae1355ba69e07b88c3b96119371fe43
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691524"
---
# <a name="icordebugprocessenumerateappdomains-method"></a><span data-ttu-id="8ddce-103">ICorDebugProcess::EnumerateAppDomains メソッド</span><span class="sxs-lookup"><span data-stu-id="8ddce-103">ICorDebugProcess::EnumerateAppDomains Method</span></span>

<span data-ttu-id="8ddce-104">このプロセス内のすべてのアプリケーションドメインを列挙します。</span><span class="sxs-lookup"><span data-stu-id="8ddce-104">Enumerates all the application domains in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ddce-105">構文</span><span class="sxs-lookup"><span data-stu-id="8ddce-105">Syntax</span></span>  
  
``` cpp
HRESULT EnumerateAppDomains(  
    [out] ICorDebugAppDomainEnum **ppAppDomains);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ddce-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8ddce-106">Parameters</span></span>  

 `ppAppDomains`  
 <span data-ttu-id="8ddce-107">入出力このプロセス内のアプリケーションドメインの列挙子である [ICorDebugAppDomainEnum](icordebugappdomainenum-interface.md) のアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8ddce-107">[out] A pointer to the address of an [ICorDebugAppDomainEnum](icordebugappdomainenum-interface.md) that is an enumerator for the application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ddce-108">解説</span><span class="sxs-lookup"><span data-stu-id="8ddce-108">Remarks</span></span>  

 <span data-ttu-id="8ddce-109">このメソッド [は、によって](icordebugmanagedcallback-createprocess-method.md) 使用できます。</span><span class="sxs-lookup"><span data-stu-id="8ddce-109">This method can be used before the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ddce-110">要件</span><span class="sxs-lookup"><span data-stu-id="8ddce-110">Requirements</span></span>  

 <span data-ttu-id="8ddce-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ddce-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ddce-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8ddce-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8ddce-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ddce-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ddce-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ddce-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
