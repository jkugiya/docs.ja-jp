---
description: '詳細について: ICorDebugInternalFrame2:: Getフレームアドレスメソッド'
title: ICorDebugInternalFrame2::GetFrameAddress メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame2.GetFrameAddress Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame2::GetFrameAddress
helpviewer_keywords:
- GetFrameAddress method [.NET Framework debugging]
- ICorDebugInternalFrame2::GetFrameAddress method [.NET Framework debugging]
ms.assetid: 4ee8d058-ffc8-4967-9133-a5adfef4e518
topic_type:
- apiref
ms.openlocfilehash: bb745424680c5b9a5277badfbe2d96db46e2e3d8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791115"
---
# <a name="icordebuginternalframe2getframeaddress-method"></a><span data-ttu-id="3d260-103">ICorDebugInternalFrame2::GetFrameAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="3d260-103">ICorDebugInternalFrame2::GetFrameAddress Method</span></span>

<span data-ttu-id="3d260-104">内部フレームのスタックアドレスを返します。</span><span class="sxs-lookup"><span data-stu-id="3d260-104">Returns the stack address of the internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d260-105">構文</span><span class="sxs-lookup"><span data-stu-id="3d260-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameAddress([out] CORDB_ADDRESS *pAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d260-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3d260-106">Parameters</span></span>  

 `pAddress`  
 <span data-ttu-id="3d260-107">入出力 `CORDB_ADDRESS` 内部フレームのへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3d260-107">[out] Pointer to the `CORDB_ADDRESS` for the internal frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3d260-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="3d260-108">Return Value</span></span>  

 <span data-ttu-id="3d260-109">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="3d260-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="3d260-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3d260-110">HRESULT</span></span>|<span data-ttu-id="3d260-111">説明</span><span class="sxs-lookup"><span data-stu-id="3d260-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3d260-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="3d260-112">S_OK</span></span>|<span data-ttu-id="3d260-113">内部フレームのアドレスが正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="3d260-113">The address of the internal frame was successfully returned.</span></span>|  
|<span data-ttu-id="3d260-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3d260-114">E_FAIL</span></span>|<span data-ttu-id="3d260-115">内部フレームのアドレスを返すことができませんでした。</span><span class="sxs-lookup"><span data-stu-id="3d260-115">The address of the internal frame could not be returned.</span></span>|  
|<span data-ttu-id="3d260-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="3d260-116">E_INVALIDARG</span></span>|<span data-ttu-id="3d260-117">`pAddress` は `null` です。</span><span class="sxs-lookup"><span data-stu-id="3d260-117">`pAddress` is `null`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d260-118">解説</span><span class="sxs-lookup"><span data-stu-id="3d260-118">Remarks</span></span>  

 <span data-ttu-id="3d260-119">で返される値を使用して、 `pAddress` スタック上の他のフレームに対する内部フレームの位置を判断できます。</span><span class="sxs-lookup"><span data-stu-id="3d260-119">The value returned in `pAddress` can be used to determine the location of the internal frame relative to other frames on the stack.</span></span> <span data-ttu-id="3d260-120">IA-64 ベースのコンピューターでも、内部フレームはスタックのみに存在し、バッキングストアへの対応するポインターは存在しません。</span><span class="sxs-lookup"><span data-stu-id="3d260-120">Even on IA-64-based computers, the internal frame lives on the stack only, and there is no corresponding pointer to a backing store.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d260-121">要件</span><span class="sxs-lookup"><span data-stu-id="3d260-121">Requirements</span></span>  

 <span data-ttu-id="3d260-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3d260-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d260-123">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3d260-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3d260-124">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d260-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d260-125">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d260-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d260-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="3d260-126">See also</span></span>

- [<span data-ttu-id="3d260-127">ICorDebugInternalFrame2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3d260-127">ICorDebugInternalFrame2 Interface</span></span>](icordebuginternalframe2-interface.md)
- [<span data-ttu-id="3d260-128">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="3d260-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="3d260-129">デバッグ</span><span class="sxs-lookup"><span data-stu-id="3d260-129">Debugging</span></span>](index.md)
