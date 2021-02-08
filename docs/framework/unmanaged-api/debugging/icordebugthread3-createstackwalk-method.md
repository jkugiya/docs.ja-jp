---
description: '詳細について: ICorDebugThread3:: CreateStackWalk メソッド'
title: ICorDebugThread3::CreateStackWalk メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread3.CreateStackWalk Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3::CreateStackWalk
helpviewer_keywords:
- CreateStackWalk method [.NET Framework debugging]
- ICorDebugThread3::CreateStackWalk method [.NET Framework debugging]
ms.assetid: c55e35d9-f9aa-4268-94b5-dce44c61acf2
topic_type:
- apiref
ms.openlocfilehash: b36252160dbad14ca1bee0674b6d042072a36359
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800995"
---
# <a name="icordebugthread3createstackwalk-method"></a><span data-ttu-id="023ce-103">ICorDebugThread3::CreateStackWalk メソッド</span><span class="sxs-lookup"><span data-stu-id="023ce-103">ICorDebugThread3::CreateStackWalk Method</span></span>

<span data-ttu-id="023ce-104">スタックをアンワインドするスレッドに対し [て、このオブジェクトを](icordebugstackwalk-interface.md) 作成します。</span><span class="sxs-lookup"><span data-stu-id="023ce-104">Creates an [ICorDebugStackWalk](icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="023ce-105">構文</span><span class="sxs-lookup"><span data-stu-id="023ce-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateStackWalk([out] ICorDebugStackWalk **ppStackWalk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="023ce-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="023ce-106">Parameters</span></span>  

 `ppStackWalk`  
 <span data-ttu-id="023ce-107">入出力スタックをアンワインドするスレッド [の、説明オブジェクトの](icordebugstackwalk-interface.md) アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="023ce-107">[out] A pointer to address of the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="023ce-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="023ce-108">Return Value</span></span>  

 <span data-ttu-id="023ce-109">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="023ce-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="023ce-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="023ce-110">HRESULT</span></span>|<span data-ttu-id="023ce-111">説明</span><span class="sxs-lookup"><span data-stu-id="023ce-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="023ce-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="023ce-112">S_OK</span></span>|<span data-ttu-id="023ce-113">`ICorDebugStackWalk`オブジェクトが正常に作成されました。</span><span class="sxs-lookup"><span data-stu-id="023ce-113">The `ICorDebugStackWalk` object was successfully created.</span></span>|  
|<span data-ttu-id="023ce-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="023ce-114">E_FAIL</span></span>|<span data-ttu-id="023ce-115">オブジェクトは作成され `ICorDebugStackWalk` ませんでした。</span><span class="sxs-lookup"><span data-stu-id="023ce-115">The `ICorDebugStackWalk` object was not created.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="023ce-116">例外</span><span class="sxs-lookup"><span data-stu-id="023ce-116">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="023ce-117">解説</span><span class="sxs-lookup"><span data-stu-id="023ce-117">Remarks</span></span>  

 <span data-ttu-id="023ce-118">メソッドが `CreateStackWalk` 成功すると、返された `ICorDebugStackWalk` オブジェクトのコンテキストがスレッドの現在のコンテキストに設定されます。</span><span class="sxs-lookup"><span data-stu-id="023ce-118">If the `CreateStackWalk` method succeeds, the returned `ICorDebugStackWalk` object's context is set to the thread's current context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="023ce-119">要件</span><span class="sxs-lookup"><span data-stu-id="023ce-119">Requirements</span></span>  

 <span data-ttu-id="023ce-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="023ce-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="023ce-121">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="023ce-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="023ce-122">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="023ce-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="023ce-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="023ce-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="023ce-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="023ce-124">See also</span></span>

- [<span data-ttu-id="023ce-125">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="023ce-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="023ce-126">デバッグ</span><span class="sxs-lookup"><span data-stu-id="023ce-126">Debugging</span></span>](index.md)
