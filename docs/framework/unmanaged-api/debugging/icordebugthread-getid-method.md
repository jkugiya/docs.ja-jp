---
description: '詳細については、次を参照してください: GetID メソッド'
title: ICorDebugThread::GetID メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetID
helpviewer_keywords:
- ICorDebugThread::GetID method [.NET Framework debugging]
- GetID method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: f1de4584-92df-42f3-9da4-fca03a1c6821
topic_type:
- apiref
ms.openlocfilehash: d089201527da67299b64cdf074bdd331f22375a1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659089"
---
# <a name="icordebugthreadgetid-method"></a><span data-ttu-id="8c142-103">ICorDebugThread::GetID メソッド</span><span class="sxs-lookup"><span data-stu-id="8c142-103">ICorDebugThread::GetID Method</span></span>

<span data-ttu-id="8c142-104">このコンポーネントのアクティブな部分の現在のオペレーティングシステム識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="8c142-104">Gets the current operating system identifier of the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c142-105">構文</span><span class="sxs-lookup"><span data-stu-id="8c142-105">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] DWORD *pdwThreadId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c142-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8c142-106">Parameters</span></span>  

 `pdwThreadId`  
 <span data-ttu-id="8c142-107">入出力スレッドの識別子。</span><span class="sxs-lookup"><span data-stu-id="8c142-107">[out] The identifier of the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c142-108">解説</span><span class="sxs-lookup"><span data-stu-id="8c142-108">Remarks</span></span>  

 <span data-ttu-id="8c142-109">オペレーティングシステムの識別子は、プロセスの実行中に変更される可能性があり、スレッドのさまざまな部分に対して異なる値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="8c142-109">The operating system identifier can potentially change during execution of a process, and can be a different value for different parts of the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c142-110">要件</span><span class="sxs-lookup"><span data-stu-id="8c142-110">Requirements</span></span>  

 <span data-ttu-id="8c142-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c142-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c142-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8c142-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8c142-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c142-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c142-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c142-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
