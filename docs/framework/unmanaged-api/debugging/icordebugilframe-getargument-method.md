---
description: '詳細については、次のページを参照してください: GetArgument メソッド'
title: ICorDebugILFrame::GetArgument メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetArgument
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetArgument
helpviewer_keywords:
- GetArgument method [.NET Framework debugging]
- ICorDebugILFrame::GetArgument method [.NET Framework debugging]
ms.assetid: 4e2fd423-f643-4c27-ba5f-41b5ebc3b416
topic_type:
- apiref
ms.openlocfilehash: c845f3c07502f3b1ce564833ee6ef98e3305463f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650509"
---
# <a name="icordebugilframegetargument-method"></a><span data-ttu-id="9c657-103">ICorDebugILFrame::GetArgument メソッド</span><span class="sxs-lookup"><span data-stu-id="9c657-103">ICorDebugILFrame::GetArgument Method</span></span>

<span data-ttu-id="9c657-104">この MSIL (Microsoft 中間言語) スタックフレーム内の指定された引数の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="9c657-104">Gets the value of the specified argument in this Microsoft intermediate language (MSIL) stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c657-105">構文</span><span class="sxs-lookup"><span data-stu-id="9c657-105">Syntax</span></span>  
  
```cpp  
HRESULT GetArgument (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c657-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9c657-106">Parameters</span></span>  

 `dwIndex`  
 <span data-ttu-id="9c657-107">からこの MSIL スタックフレーム内の引数のインデックス。</span><span class="sxs-lookup"><span data-stu-id="9c657-107">[in] The index of the argument in this MSIL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="9c657-108">[out] 取得した値を表す ICorDebugValue オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9c657-108">[out] A pointer to the address of an ICorDebugValue object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c657-109">解説</span><span class="sxs-lookup"><span data-stu-id="9c657-109">Remarks</span></span>  

 <span data-ttu-id="9c657-110">メソッドは、 `GetArgument` MSIL スタックフレーム内または just-in-time (JIT) コンパイルフレームで使用できます。</span><span class="sxs-lookup"><span data-stu-id="9c657-110">The `GetArgument` method can be used either in an MSIL stack frame or in a just-in-time (JIT) compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c657-111">要件</span><span class="sxs-lookup"><span data-stu-id="9c657-111">Requirements</span></span>  

 <span data-ttu-id="9c657-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c657-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c657-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9c657-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9c657-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9c657-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9c657-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c657-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
