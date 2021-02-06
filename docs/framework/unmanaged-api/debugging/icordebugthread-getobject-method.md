---
description: '詳細については、次のページを参照してください:: いい Thread:: GetObject メソッド'
title: ICorDebugThread::GetObject メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetObject
helpviewer_keywords:
- GetObject method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetObject method [.NET Framework debugging]
ms.assetid: 1590febe-96c2-4046-97db-d81d81d67e01
topic_type:
- apiref
ms.openlocfilehash: db5760be0ef4230b2dccec9d1836ea0eee56f231
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658949"
---
# <a name="icordebugthreadgetobject-method"></a><span data-ttu-id="0402e-103">ICorDebugThread::GetObject メソッド</span><span class="sxs-lookup"><span data-stu-id="0402e-103">ICorDebugThread::GetObject Method</span></span>

<span data-ttu-id="0402e-104">共通言語ランタイム (CLR) スレッドへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="0402e-104">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0402e-105">構文</span><span class="sxs-lookup"><span data-stu-id="0402e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0402e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0402e-106">Parameters</span></span>  

 `ppObject`  
 <span data-ttu-id="0402e-107">入出力CLR スレッドを表す ICorDebugValue インターフェイスオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0402e-107">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0402e-108">要件</span><span class="sxs-lookup"><span data-stu-id="0402e-108">Requirements</span></span>  

 <span data-ttu-id="0402e-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0402e-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0402e-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0402e-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0402e-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0402e-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0402e-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0402e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0402e-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="0402e-113">See also</span></span>

- <xref:System.Threading.Thread>
