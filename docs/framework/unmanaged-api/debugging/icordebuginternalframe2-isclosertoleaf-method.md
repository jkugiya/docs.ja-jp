---
description: '詳細について: ICorDebugInternalFrame2:: IsCloserToLeaf メソッド'
title: ICorDebugInternalFrame2::IsCloserToLeaf メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame2.IsCloserToLeaf Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame2::IsCloserToLeaf
helpviewer_keywords:
- ICorDebugInternalFrame2::IsCloserToLeaf method [.NET Framework debugging]
- IsCloserToLeaf method [.NET Framework debugging]
ms.assetid: c1d3d1eb-8370-4f25-8297-3bd262b4740a
topic_type:
- apiref
ms.openlocfilehash: d773f8670f600a5bcd2a8dad7f23fe243195957c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801281"
---
# <a name="icordebuginternalframe2isclosertoleaf-method"></a><span data-ttu-id="7040f-103">ICorDebugInternalFrame2::IsCloserToLeaf メソッド</span><span class="sxs-lookup"><span data-stu-id="7040f-103">ICorDebugInternalFrame2::IsCloserToLeaf Method</span></span>

<span data-ttu-id="7040f-104">内部フレームが、指定されたのは、指定されたとしての `this` オブジェクトよりもリーフの近くにあるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="7040f-104">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7040f-105">構文</span><span class="sxs-lookup"><span data-stu-id="7040f-105">Syntax</span></span>  
  
```cpp  
HRESULT IsCloserToLeaf([in] ICorDebugFrame * pFrameToCompare,  
                       [out] BOOL * pIsCloser);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7040f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7040f-106">Parameters</span></span>  

 `pFrameToCompare`  
 <span data-ttu-id="7040f-107">から比較オブジェクトへのポインター `ICorDebugFrame` 。</span><span class="sxs-lookup"><span data-stu-id="7040f-107">[in] A pointer to the comparison `ICorDebugFrame` object.</span></span>  
  
 `pIsCloser`  
 <span data-ttu-id="7040f-108">[出力] `true``this`内部フレームがで指定されたフレームよりもリーフの近くにある場合は `pFrameToCompare` 。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="7040f-108">[out] `true` if the `this` internal frame is closer to the leaf than the frame specified by `pFrameToCompare`; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7040f-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="7040f-109">Return Value</span></span>  

 <span data-ttu-id="7040f-110">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="7040f-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="7040f-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7040f-111">HRESULT</span></span>|<span data-ttu-id="7040f-112">説明</span><span class="sxs-lookup"><span data-stu-id="7040f-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7040f-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="7040f-113">S_OK</span></span>|<span data-ttu-id="7040f-114">比較が正常に実行されました。</span><span class="sxs-lookup"><span data-stu-id="7040f-114">The comparison was successfully performed.</span></span>|  
|<span data-ttu-id="7040f-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7040f-115">E_FAIL</span></span>|<span data-ttu-id="7040f-116">比較を実行できませんでした。</span><span class="sxs-lookup"><span data-stu-id="7040f-116">The comparison could not be performed.</span></span>|  
|<span data-ttu-id="7040f-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="7040f-117">E_INVALIDARG</span></span>|<span data-ttu-id="7040f-118">`pFrameToCompare` または `pIsCloser` が null です。</span><span class="sxs-lookup"><span data-stu-id="7040f-118">`pFrameToCompare` or `pIsCloser` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7040f-119">解説</span><span class="sxs-lookup"><span data-stu-id="7040f-119">Remarks</span></span>  

 <span data-ttu-id="7040f-120">`IsCloserToLeaf` を使用すると、スタック上の他のフレームと内部フレームをインターリーブするポリシーを実装できます。</span><span class="sxs-lookup"><span data-stu-id="7040f-120">`IsCloserToLeaf` can be used to implement a policy for interleaving internal frames with other frames on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7040f-121">要件</span><span class="sxs-lookup"><span data-stu-id="7040f-121">Requirements</span></span>  

 <span data-ttu-id="7040f-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7040f-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7040f-123">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7040f-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7040f-124">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7040f-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7040f-125">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7040f-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7040f-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="7040f-126">See also</span></span>

- [<span data-ttu-id="7040f-127">ICorDebugInternalFrame2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7040f-127">ICorDebugInternalFrame2 Interface</span></span>](icordebuginternalframe2-interface.md)
- [<span data-ttu-id="7040f-128">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="7040f-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="7040f-129">デバッグ</span><span class="sxs-lookup"><span data-stu-id="7040f-129">Debugging</span></span>](index.md)
