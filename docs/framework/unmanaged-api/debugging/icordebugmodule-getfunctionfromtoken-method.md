---
description: '詳細情報: ヘルプモジュール:: GetFunctionFromToken メソッド'
title: ICorDebugModule::GetFunctionFromToken メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetFunctionFromToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetFunctionFromToken
helpviewer_keywords:
- GetFunctionFromToken method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetFunctionFromToken method [.NET Framework debugging]
ms.assetid: 6fe12194-4ef7-43c1-9570-ade35ccf127a
topic_type:
- apiref
ms.openlocfilehash: d6da43441f3774cff44a6f867c3ccf2a8581ebab
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691654"
---
# <a name="icordebugmodulegetfunctionfromtoken-method"></a><span data-ttu-id="5fe28-103">ICorDebugModule::GetFunctionFromToken メソッド</span><span class="sxs-lookup"><span data-stu-id="5fe28-103">ICorDebugModule::GetFunctionFromToken Method</span></span>

<span data-ttu-id="5fe28-104">メタデータトークンによって指定された関数を取得します。</span><span class="sxs-lookup"><span data-stu-id="5fe28-104">Gets the function that is specified by the metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fe28-105">構文</span><span class="sxs-lookup"><span data-stu-id="5fe28-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromToken(  
    [in] mdMethodDef methodDef,  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5fe28-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5fe28-106">Parameters</span></span>  

 `methodDef`  
 <span data-ttu-id="5fe28-107">から `mdMethodDef` 関数のメタデータを参照するメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="5fe28-107">[in] A `mdMethodDef` metadata token that references the function's metadata.</span></span>  
  
 `ppFunction`  
 <span data-ttu-id="5fe28-108">入出力関数を表す、のオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5fe28-108">[out] A pointer to the address of a ICorDebugFunction interface object that represents the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5fe28-109">解説</span><span class="sxs-lookup"><span data-stu-id="5fe28-109">Remarks</span></span>  

 <span data-ttu-id="5fe28-110">渡された `GetFunctionFromToken` 値 `methodDef` が Microsoft 中間言語 (MSIL) メソッドを参照していない場合、メソッドは CORDBG_E_FUNCTION_NOT_IL HRESULT を返します。</span><span class="sxs-lookup"><span data-stu-id="5fe28-110">The `GetFunctionFromToken` method returns a CORDBG_E_FUNCTION_NOT_IL HRESULT if the value passed in `methodDef` does not refer to a Microsoft intermediate language (MSIL) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fe28-111">要件</span><span class="sxs-lookup"><span data-stu-id="5fe28-111">Requirements</span></span>  

 <span data-ttu-id="5fe28-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5fe28-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fe28-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5fe28-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5fe28-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5fe28-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5fe28-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fe28-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
