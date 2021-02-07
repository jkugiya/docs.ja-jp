---
description: '詳細情報: ICorDebugNativeFrame2:: IsChild メソッド'
title: ICorDebugNativeFrame2::IsChild メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2.IsChild Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2::IsChild
helpviewer_keywords:
- IsChild method [.NET Framework debugging]
- ICorDebugNativeFrame2::IsChild method [.NET Framework debugging]
ms.assetid: 9e2aae09-49cb-4fbd-81e5-e29cd864a88b
topic_type:
- apiref
ms.openlocfilehash: 7c698c5a49ee445b4ba9c591c96f700f86a86c32
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722296"
---
# <a name="icordebugnativeframe2ischild-method"></a><span data-ttu-id="73f4a-103">ICorDebugNativeFrame2::IsChild メソッド</span><span class="sxs-lookup"><span data-stu-id="73f4a-103">ICorDebugNativeFrame2::IsChild Method</span></span>

<span data-ttu-id="73f4a-104">現在のフレームが子フレームであるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="73f4a-104">Determines whether the current frame is a child frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73f4a-105">構文</span><span class="sxs-lookup"><span data-stu-id="73f4a-105">Syntax</span></span>  
  
```cpp  
HRESULT IsChild([out] BOOL * pIsChild);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73f4a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="73f4a-106">Parameters</span></span>  

 `pIsChild`  
 <span data-ttu-id="73f4a-107">入出力現在のフレームが子フレームであるかどうかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="73f4a-107">[out] A Boolean value that specifies whether the current frame is a child frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="73f4a-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="73f4a-108">Return Value</span></span>  

 <span data-ttu-id="73f4a-109">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="73f4a-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="73f4a-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="73f4a-110">HRESULT</span></span>|<span data-ttu-id="73f4a-111">説明</span><span class="sxs-lookup"><span data-stu-id="73f4a-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="73f4a-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="73f4a-112">S_OK</span></span>|<span data-ttu-id="73f4a-113">子の状態が正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="73f4a-113">The child status was successfully returned.</span></span>|  
|<span data-ttu-id="73f4a-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="73f4a-114">E_FAIL</span></span>|<span data-ttu-id="73f4a-115">子の状態を返すことができませんでした。</span><span class="sxs-lookup"><span data-stu-id="73f4a-115">The child status could not be returned.</span></span>|  
|<span data-ttu-id="73f4a-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="73f4a-116">E_INVALIDARG</span></span>|<span data-ttu-id="73f4a-117">`pIsChild` が null です。</span><span class="sxs-lookup"><span data-stu-id="73f4a-117">`pIsChild` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="73f4a-118">例外</span><span class="sxs-lookup"><span data-stu-id="73f4a-118">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73f4a-119">解説</span><span class="sxs-lookup"><span data-stu-id="73f4a-119">Remarks</span></span>  

 <span data-ttu-id="73f4a-120">メソッドを `IsChild` `true` 呼び出す frame オブジェクトが別のフレームの子である場合、メソッドはを返します。</span><span class="sxs-lookup"><span data-stu-id="73f4a-120">The `IsChild` method returns `true` if the frame object on which you call the method is a child of another frame.</span></span> <span data-ttu-id="73f4a-121">この場合は、 [IsMatchingParentFrame](icordebugnativeframe2-ismatchingparentframe-method.md) メソッドを使用して、フレームが親であるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="73f4a-121">If this is the case, use the [IsMatchingParentFrame](icordebugnativeframe2-ismatchingparentframe-method.md) method to check whether a frame is its parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73f4a-122">要件</span><span class="sxs-lookup"><span data-stu-id="73f4a-122">Requirements</span></span>  

 <span data-ttu-id="73f4a-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="73f4a-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73f4a-124">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="73f4a-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73f4a-125">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73f4a-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73f4a-126">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73f4a-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73f4a-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="73f4a-127">See also</span></span>

- [<span data-ttu-id="73f4a-128">ICorDebugNativeFrame2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="73f4a-128">ICorDebugNativeFrame2 Interface</span></span>](icordebugnativeframe2-interface.md)
- [<span data-ttu-id="73f4a-129">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="73f4a-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="73f4a-130">デバッグ</span><span class="sxs-lookup"><span data-stu-id="73f4a-130">Debugging</span></span>](index.md)
