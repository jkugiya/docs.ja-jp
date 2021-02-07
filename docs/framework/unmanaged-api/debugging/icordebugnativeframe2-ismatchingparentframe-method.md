---
description: '詳細について: ICorDebugNativeFrame2:: IsMatchingParentFrame メソッド'
title: ICorDebugNativeFrame2::IsMatchingParentFrame メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2.IsMatchingParentFrame Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2::IsMatchingParentFrame
helpviewer_keywords:
- IsMatchingParentFrame method [.NET Framework debugging]
- ICorDebugNativeFrame2::IsMatchingParentFrame method [.NET Framework debugging]
ms.assetid: d2ca20db-df22-4528-a0dd-a09ea62c8998
topic_type:
- apiref
ms.openlocfilehash: 6dff1cb7f5205ad742ac4b886f72938dd28bd88f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722205"
---
# <a name="icordebugnativeframe2ismatchingparentframe-method"></a><span data-ttu-id="9f629-103">ICorDebugNativeFrame2::IsMatchingParentFrame メソッド</span><span class="sxs-lookup"><span data-stu-id="9f629-103">ICorDebugNativeFrame2::IsMatchingParentFrame Method</span></span>

<span data-ttu-id="9f629-104">指定したフレームが現在のフレームの親であるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="9f629-104">Determines whether the specified frame is the parent of the current frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f629-105">構文</span><span class="sxs-lookup"><span data-stu-id="9f629-105">Syntax</span></span>  
  
```cpp  
HRESULT IsMatchingParentFrame([in] ICorDebugNativeFrame2  
                                      *pPotentialParentFrame,  
                              [out] BOOL *pIsParent);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f629-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9f629-106">Parameters</span></span>  

 `pPotentialParentFrame`  
 <span data-ttu-id="9f629-107">から親ステータスとして評価するフレームオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9f629-107">[in] A pointer to the frame object that you want to evaluate for parent status.</span></span>  
  
 `pIsParent`  
 <span data-ttu-id="9f629-108">[出力] `true``pPotentialParentFrame`が現在のフレームの親である場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="9f629-108">[out] `true` if `pPotentialParentFrame` is the current frame’s parent; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9f629-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="9f629-109">Return Value</span></span>  

 <span data-ttu-id="9f629-110">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="9f629-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="9f629-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9f629-111">HRESULT</span></span>|<span data-ttu-id="9f629-112">説明</span><span class="sxs-lookup"><span data-stu-id="9f629-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9f629-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="9f629-113">S_OK</span></span>|<span data-ttu-id="9f629-114">親の状態が正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="9f629-114">The parent status was successfully returned.</span></span>|  
|<span data-ttu-id="9f629-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9f629-115">E_FAIL</span></span>|<span data-ttu-id="9f629-116">親の状態を返すことができませんでした。</span><span class="sxs-lookup"><span data-stu-id="9f629-116">The parent status could not be returned.</span></span>|  
|<span data-ttu-id="9f629-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="9f629-117">E_INVALIDARG</span></span>|<span data-ttu-id="9f629-118">`pPotentialParentFrame` または `pIsParent` が null です。</span><span class="sxs-lookup"><span data-stu-id="9f629-118">`pPotentialParentFrame` or `pIsParent` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="9f629-119">例外</span><span class="sxs-lookup"><span data-stu-id="9f629-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f629-120">解説</span><span class="sxs-lookup"><span data-stu-id="9f629-120">Remarks</span></span>  

 <span data-ttu-id="9f629-121">`IsMatchingParentFrame``true`メソッドに渡すフレームオブジェクトが、メソッドが呼び出されたフレームオブジェクトの親である場合、を返します。</span><span class="sxs-lookup"><span data-stu-id="9f629-121">`IsMatchingParentFrame` returns `true` if the frame object you pass to the method is the parent of the frame object on which the method was called.</span></span> <span data-ttu-id="9f629-122">指定したフレームの子ではないフレームに対してメソッドを呼び出すと、エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="9f629-122">If you call the method on a frame that is not a child of the specified frame, it returns an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f629-123">要件</span><span class="sxs-lookup"><span data-stu-id="9f629-123">Requirements</span></span>  

 <span data-ttu-id="9f629-124">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9f629-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f629-125">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9f629-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9f629-126">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9f629-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9f629-127">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f629-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f629-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="9f629-128">See also</span></span>

- [<span data-ttu-id="9f629-129">ICorDebugNativeFrame2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9f629-129">ICorDebugNativeFrame2 Interface</span></span>](icordebugnativeframe2-interface.md)
- [<span data-ttu-id="9f629-130">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="9f629-130">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="9f629-131">デバッグ</span><span class="sxs-lookup"><span data-stu-id="9f629-131">Debugging</span></span>](index.md)
