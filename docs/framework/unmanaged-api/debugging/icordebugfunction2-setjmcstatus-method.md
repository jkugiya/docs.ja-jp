---
description: '詳細について: ICorDebugFunction2:: SetJMCStatus メソッド'
title: ICorDebugFunction2::SetJMCStatus メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::SetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 22c27b01-2869-4214-b840-5921f7c874fc
topic_type:
- apiref
ms.openlocfilehash: d2df9d47808b0220a91bd344e7600f8d16eccdb4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692187"
---
# <a name="icordebugfunction2setjmcstatus-method"></a><span data-ttu-id="7fce6-103">ICorDebugFunction2::SetJMCStatus メソッド</span><span class="sxs-lookup"><span data-stu-id="7fce6-103">ICorDebugFunction2::SetJMCStatus Method</span></span>

<span data-ttu-id="7fce6-104">この ICorDebugFunction2 によって表される関数をステップ実行マイコードのみにマークします。</span><span class="sxs-lookup"><span data-stu-id="7fce6-104">Marks the function represented by this ICorDebugFunction2 for Just My Code stepping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fce6-105">構文</span><span class="sxs-lookup"><span data-stu-id="7fce6-105">Syntax</span></span>  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7fce6-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7fce6-106">Parameters</span></span>  

 `bIsJustMyCode`  
 <span data-ttu-id="7fce6-107">から関数を `true` ユーザーコードとしてマークする場合はに設定します。それ以外の場合はに設定 `false` します。</span><span class="sxs-lookup"><span data-stu-id="7fce6-107">[in] Set to `true` to mark the function as user code; otherwise, set to `false`.</span></span>  
  
## <a name="return-values"></a><span data-ttu-id="7fce6-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="7fce6-108">Return Values</span></span>  
  
|<span data-ttu-id="7fce6-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7fce6-109">HRESULT</span></span>|<span data-ttu-id="7fce6-110">説明</span><span class="sxs-lookup"><span data-stu-id="7fce6-110">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="7fce6-111">関数は正常にマークされました。</span><span class="sxs-lookup"><span data-stu-id="7fce6-111">The function was successfully marked.</span></span>|  
|`CORDBG_E_FUNCTION_NOT_DEBUGGABLE`|<span data-ttu-id="7fce6-112">デバッグできないため、関数をユーザーコードとしてマークできませんでした。</span><span class="sxs-lookup"><span data-stu-id="7fce6-112">The function could not be marked as user code because it cannot be debugged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7fce6-113">解説</span><span class="sxs-lookup"><span data-stu-id="7fce6-113">Remarks</span></span>  

 <span data-ttu-id="7fce6-114">マイコードのみステッパは、非ユーザーコードをスキップします。</span><span class="sxs-lookup"><span data-stu-id="7fce6-114">A Just My Code stepper will skip non-user code.</span></span> <span data-ttu-id="7fce6-115">ユーザーコードは、デバッグ可能なコードのサブセットである必要があります。</span><span class="sxs-lookup"><span data-stu-id="7fce6-115">User code must be a subset of debuggable code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7fce6-116">要件</span><span class="sxs-lookup"><span data-stu-id="7fce6-116">Requirements</span></span>  

 <span data-ttu-id="7fce6-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7fce6-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fce6-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7fce6-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7fce6-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7fce6-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7fce6-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7fce6-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
