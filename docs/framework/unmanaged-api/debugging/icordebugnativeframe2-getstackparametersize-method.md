---
description: '詳細について: ICorDebugNativeFrame2:: GetStackParameterSize メソッド'
title: ICorDebugNativeFrame2::GetStackParameterSize メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2.GetStackParameterSize Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2::GetStackParameterSize
helpviewer_keywords:
- ICorDebugNativeFrame2::GetStackParameterSize method [.NET Framework debugging]
- GetStackParameterSize method [.NET Framework debugging]
ms.assetid: f6a449c8-a941-43ba-9a90-c98b29ae3c36
topic_type:
- apiref
ms.openlocfilehash: 08a17ced0be75737c1c49aa3f9bb42b13bbe8aa0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722335"
---
# <a name="icordebugnativeframe2getstackparametersize-method"></a><span data-ttu-id="06fb4-103">ICorDebugNativeFrame2::GetStackParameterSize メソッド</span><span class="sxs-lookup"><span data-stu-id="06fb4-103">ICorDebugNativeFrame2::GetStackParameterSize Method</span></span>

<span data-ttu-id="06fb4-104">X86 オペレーティングシステムのスタックのパラメーターの累積サイズを返します。</span><span class="sxs-lookup"><span data-stu-id="06fb4-104">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06fb4-105">構文</span><span class="sxs-lookup"><span data-stu-id="06fb4-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStackParameterSize([out] ULONG32 * pSize)  
```  
  
## <a name="parameters"></a><span data-ttu-id="06fb4-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="06fb4-106">Parameters</span></span>  

 `pSize`  
 <span data-ttu-id="06fb4-107">入出力スタック上のパラメーターの累積サイズへのポインター。</span><span class="sxs-lookup"><span data-stu-id="06fb4-107">[out] A pointer to the cumulative size of the parameters on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="06fb4-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="06fb4-108">Return Value</span></span>  

 <span data-ttu-id="06fb4-109">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="06fb4-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="06fb4-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="06fb4-110">HRESULT</span></span>|<span data-ttu-id="06fb4-111">説明</span><span class="sxs-lookup"><span data-stu-id="06fb4-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="06fb4-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="06fb4-112">S_OK</span></span>|<span data-ttu-id="06fb4-113">スタックサイズが正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="06fb4-113">The stack size was successfully returned.</span></span>|  
|<span data-ttu-id="06fb4-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="06fb4-114">S_FALSE</span></span>|<span data-ttu-id="06fb4-115">`GetStackParameterSize` は、x86 以外のプラットフォームで呼び出されました。</span><span class="sxs-lookup"><span data-stu-id="06fb4-115">`GetStackParameterSize` was called on a non-x86 platform.</span></span>|  
|<span data-ttu-id="06fb4-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="06fb4-116">E_FAIL</span></span>|<span data-ttu-id="06fb4-117">`The size of the parameters could not be returned`.</span><span class="sxs-lookup"><span data-stu-id="06fb4-117">`The size of the parameters could not be returned`.</span></span>|  
|<span data-ttu-id="06fb4-118">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="06fb4-118">E_INVALIDARG</span></span>|<span data-ttu-id="06fb4-119">`pSize` が `null` です。</span><span class="sxs-lookup"><span data-stu-id="06fb4-119">`pSize` Is `null`.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="06fb4-120">例外</span><span class="sxs-lookup"><span data-stu-id="06fb4-120">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06fb4-121">解説</span><span class="sxs-lookup"><span data-stu-id="06fb4-121">Remarks</span></span>  

 <span data-ttu-id="06fb4-122">この [方法では、スタック](icordebugstackwalk-interface.md) にプッシュされるパラメーターのスタックポインターは調整されません。</span><span class="sxs-lookup"><span data-stu-id="06fb4-122">The [ICorDebugStackWalk](icordebugstackwalk-interface.md) methods do not adjust the stack pointer for parameters that are pushed on the stack.</span></span> <span data-ttu-id="06fb4-123">代わりに、によって返される値を使用して、スタックポインターを調整してネイティブアンワインダーをシード処理することができます。これにより、 `GetStackParameterSize` パラメーターが調整されます。</span><span class="sxs-lookup"><span data-stu-id="06fb4-123">Instead, you can use the value returned by `GetStackParameterSize` to adjust the stack pointer to seed a native unwinder, which does adjust for the parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06fb4-124">要件</span><span class="sxs-lookup"><span data-stu-id="06fb4-124">Requirements</span></span>  

 <span data-ttu-id="06fb4-125">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="06fb4-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06fb4-126">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="06fb4-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="06fb4-127">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="06fb4-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06fb4-128">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06fb4-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06fb4-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="06fb4-129">See also</span></span>

- [<span data-ttu-id="06fb4-130">ICorDebugNativeFrame2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="06fb4-130">ICorDebugNativeFrame2 Interface</span></span>](icordebugnativeframe2-interface.md)
- [<span data-ttu-id="06fb4-131">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="06fb4-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="06fb4-132">デバッグ</span><span class="sxs-lookup"><span data-stu-id="06fb4-132">Debugging</span></span>](index.md)
