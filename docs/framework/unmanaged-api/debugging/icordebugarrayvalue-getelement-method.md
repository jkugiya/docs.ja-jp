---
description: '詳細について: ICorDebugArrayValue:: GetElement メソッド'
title: ICorDebugArrayValue::GetElement メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetElement
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetElement
helpviewer_keywords:
- GetElement method [.NET Framework debugging]
- ICorDebugArrayValue::GetElement method [.NET Framework debugging]
ms.assetid: 7ac3cba5-c282-402e-b7ef-b46634f5176b
topic_type:
- apiref
ms.openlocfilehash: dfae074b78735934d1e71b13ce01c24741a5f2ed
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723063"
---
# <a name="icordebugarrayvaluegetelement-method"></a><span data-ttu-id="b56db-103">ICorDebugArrayValue::GetElement メソッド</span><span class="sxs-lookup"><span data-stu-id="b56db-103">ICorDebugArrayValue::GetElement Method</span></span>

<span data-ttu-id="b56db-104">指定された配列要素の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="b56db-104">Gets the value of the given array element.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b56db-105">構文</span><span class="sxs-lookup"><span data-stu-id="b56db-105">Syntax</span></span>  
  
```cpp  
HRESULT GetElement (  
    [in]  ULONG32          cdim,  
    [in, size_is(cdim), length_is(cdim)]
         ULONG32           indices[],  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b56db-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b56db-106">Parameters</span></span>  

 `cdim`  
 <span data-ttu-id="b56db-107">からこのオブジェクトの次元数 `ICorDebugArrayValue` 。</span><span class="sxs-lookup"><span data-stu-id="b56db-107">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="b56db-108">この値は、 `indices` 配列のサイズがオブジェクトの次元数と同じであるため、配列のサイズでも `ICorDebugArrayValue` あります。</span><span class="sxs-lookup"><span data-stu-id="b56db-108">This value is also the size of the `indices` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indices`  
 <span data-ttu-id="b56db-109">からインデックス値の配列。それぞれがオブジェクトのディメンション内の位置を指定し `ICorDebugArrayValue` ます。</span><span class="sxs-lookup"><span data-stu-id="b56db-109">[in] An array of index values, each of which specifies a position within a dimension of the `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="b56db-110">この値は null にしないでください。</span><span class="sxs-lookup"><span data-stu-id="b56db-110">This value must not be null.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="b56db-111">入出力指定した要素の値を表す ICorDebugValue オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b56db-111">[out] A pointer to the address of an ICorDebugValue object that represents the value of the specified element.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b56db-112">要件</span><span class="sxs-lookup"><span data-stu-id="b56db-112">Requirements</span></span>  

 <span data-ttu-id="b56db-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b56db-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b56db-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b56db-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b56db-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b56db-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b56db-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b56db-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
