---
description: '詳細については、次の情報を参照してください: GetCurrentVersionNumber メソッド'
title: ICorDebugFunction::GetCurrentVersionNumber メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetCurrentVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetCurrentVersionNumber
helpviewer_keywords:
- GetCurrentVersionNumber method [.NET Framework debugging]
- ICorDebugFunction::GetCurrentVersionNumber method [.NET Framework debugging]
ms.assetid: c3af1575-cbe6-457a-bc08-c53460edcbc8
topic_type:
- apiref
ms.openlocfilehash: ccc96755ac74624a00b806e3f569f39f2d6059f5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692538"
---
# <a name="icordebugfunctiongetcurrentversionnumber-method"></a><span data-ttu-id="77d77-103">ICorDebugFunction::GetCurrentVersionNumber メソッド</span><span class="sxs-lookup"><span data-stu-id="77d77-103">ICorDebugFunction::GetCurrentVersionNumber Method</span></span>

<span data-ttu-id="77d77-104">このオブジェクトによって表される関数に対して行われた最新の編集のバージョン番号を取得します。</span><span class="sxs-lookup"><span data-stu-id="77d77-104">Gets the version number of the latest edit made to the function represented by this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77d77-105">構文</span><span class="sxs-lookup"><span data-stu-id="77d77-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentVersionNumber (  
    [out] ULONG32 *pnCurrentVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77d77-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="77d77-106">Parameters</span></span>  

 `pnCurrentVersion`  
 <span data-ttu-id="77d77-107">入出力この関数に対して行われた最新の編集のバージョン番号を表す整数値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="77d77-107">[out] A pointer to an integer value that is the version number of the latest edit made to this function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77d77-108">解説</span><span class="sxs-lookup"><span data-stu-id="77d77-108">Remarks</span></span>  

 <span data-ttu-id="77d77-109">この関数に対して行われた最新の編集のバージョン番号が、関数自体のバージョン番号よりも大きい可能性があります。</span><span class="sxs-lookup"><span data-stu-id="77d77-109">The version number of the latest edit made to this function may be greater than the version number of the function itself.</span></span> <span data-ttu-id="77d77-110">[ICorDebugFunction2:: GetVersionNumber](icordebugfunction2-getversionnumber-method.md)メソッドまたは[Code:: GetVersionNumber](icordebugcode-getversionnumber-method.md)メソッドを使用して、関数のバージョン番号を取得します。</span><span class="sxs-lookup"><span data-stu-id="77d77-110">Use either the [ICorDebugFunction2::GetVersionNumber](icordebugfunction2-getversionnumber-method.md) method or the [ICorDebugCode::GetVersionNumber](icordebugcode-getversionnumber-method.md) method to retrieve the version number of the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77d77-111">要件</span><span class="sxs-lookup"><span data-stu-id="77d77-111">Requirements</span></span>  

 <span data-ttu-id="77d77-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="77d77-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77d77-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="77d77-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="77d77-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="77d77-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77d77-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77d77-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
