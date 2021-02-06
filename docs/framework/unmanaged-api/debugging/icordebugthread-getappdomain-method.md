---
description: '詳細については、次のページを参照してください: いい Thread:: GetAppDomain メソッド'
title: ICorDebugThread::GetAppDomain メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetAppDomain
helpviewer_keywords:
- GetAppDomain method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetAppDomain method [.NET Framework debugging]
ms.assetid: 415b3d34-8b35-4b60-a318-140646cc83f8
topic_type:
- apiref
ms.openlocfilehash: 416ab80fa08786fb5e95776b164723317fa59ca6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659206"
---
# <a name="icordebugthreadgetappdomain-method"></a><span data-ttu-id="b0077-103">ICorDebugThread::GetAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="b0077-103">ICorDebugThread::GetAppDomain Method</span></span>

<span data-ttu-id="b0077-104">このスレッドが現在実行されているアプリケーションドメインへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="b0077-104">Gets an interface pointer to the application domain in which this ICorDebugThread is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0077-105">構文</span><span class="sxs-lookup"><span data-stu-id="b0077-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0077-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b0077-106">Parameters</span></span>  

 `ppAppDomain`  
 <span data-ttu-id="b0077-107">入出力このスレッドが現在実行されているアプリケーションドメインを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b0077-107">[out] A pointer to an ICorDebugAppDomain object that represents the application domain in which this thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0077-108">要件</span><span class="sxs-lookup"><span data-stu-id="b0077-108">Requirements</span></span>  

 <span data-ttu-id="b0077-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0077-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0077-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b0077-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b0077-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0077-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0077-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0077-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
