---
description: '詳細については、次を参照してください: いい Thread:: GetProcess メソッド'
title: ICorDebugThread::GetProcess メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetProcess
helpviewer_keywords:
- ICorDebugThread::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 163816e7-0739-4566-b3df-cd256be8b8a4
topic_type:
- apiref
ms.openlocfilehash: dac5da30b343ebd17c1b1ebdd6d4cfa38b78f0bd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658938"
---
# <a name="icordebugthreadgetprocess-method"></a><span data-ttu-id="641ff-103">ICorDebugThread::GetProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="641ff-103">ICorDebugThread::GetProcess Method</span></span>

<span data-ttu-id="641ff-104">このコンポーネントがパートを形成するプロセスへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="641ff-104">Gets an interface pointer to the process of which this ICorDebugThread forms a part.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="641ff-105">構文</span><span class="sxs-lookup"><span data-stu-id="641ff-105">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="641ff-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="641ff-106">Parameters</span></span>  

 `ppProcess`  
 <span data-ttu-id="641ff-107">入出力プロセスを表す、のプロセスインターフェイスオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="641ff-107">[out] A pointer to the address of an ICorDebugProcess interface object that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="641ff-108">要件</span><span class="sxs-lookup"><span data-stu-id="641ff-108">Requirements</span></span>  

 <span data-ttu-id="641ff-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="641ff-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="641ff-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="641ff-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="641ff-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="641ff-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="641ff-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="641ff-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
