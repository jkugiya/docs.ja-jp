---
description: '詳細については、次のページを参照してください: GetSlotIndex メソッド'
title: 'いい変数 Home:: GetSlotIndex メソッド'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetSlotIndex
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetSlotIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetSlotIndex method [.NET Framework debugging]
- GetSlotIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 966da50d-5665-4fff-bf7b-1c72bbadd9a4
topic_type:
- apiref
ms.openlocfilehash: 7f6ee01c2bfcee4c78f8463a7cefac1f90a3295f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790647"
---
# <a name="icordebugvariablehomegetslotindex-method"></a><span data-ttu-id="fc0a7-103">いい変数 Home:: GetSlotIndex メソッド</span><span class="sxs-lookup"><span data-stu-id="fc0a7-103">ICorDebugVariableHome::GetSlotIndex Method</span></span>

<span data-ttu-id="fc0a7-104">ローカル変数のマネージドスロットインデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="fc0a7-104">Gets the managed slot-index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc0a7-105">構文</span><span class="sxs-lookup"><span data-stu-id="fc0a7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSlotIndex(  
    [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc0a7-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fc0a7-106">Parameters</span></span>  

 `pSlotIndex`  
 <span data-ttu-id="fc0a7-107">入出力ローカル変数のスロットインデックスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="fc0a7-107">[out] A pointer to the slot-index of a local variable.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fc0a7-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="fc0a7-108">Return Value</span></span>  

 <span data-ttu-id="fc0a7-109">メソッドは、次の値を返します。</span><span class="sxs-lookup"><span data-stu-id="fc0a7-109">The method returns the following values.</span></span>  
  
|<span data-ttu-id="fc0a7-110">値</span><span class="sxs-lookup"><span data-stu-id="fc0a7-110">Value</span></span>|<span data-ttu-id="fc0a7-111">説明</span><span class="sxs-lookup"><span data-stu-id="fc0a7-111">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="fc0a7-112">メソッド呼び出しによって、でスロットインデックス値が返されました `pSlotIndex` 。</span><span class="sxs-lookup"><span data-stu-id="fc0a7-112">The method call returned a slot-index value in `pSlotIndex`.</span></span>|  
|`E_FAIL`|<span data-ttu-id="fc0a7-113">現在のは、 [関数の引数](icordebugvariablehome-interface.md) を表します。</span><span class="sxs-lookup"><span data-stu-id="fc0a7-113">The current [ICorDebugVariableHome](icordebugvariablehome-interface.md) instance represents a function argument.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc0a7-114">解説</span><span class="sxs-lookup"><span data-stu-id="fc0a7-114">Remarks</span></span>  

 <span data-ttu-id="fc0a7-115">このローカル変数のメタデータを取得するために、スロットインデックスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="fc0a7-115">The slot-index can be used to retrieve the metadata for this local variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc0a7-116">要件</span><span class="sxs-lookup"><span data-stu-id="fc0a7-116">Requirements</span></span>  

 <span data-ttu-id="fc0a7-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fc0a7-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc0a7-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fc0a7-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fc0a7-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc0a7-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc0a7-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc0a7-120">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc0a7-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="fc0a7-121">See also</span></span>

- [<span data-ttu-id="fc0a7-122">ICorDebugVariableHome インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fc0a7-122">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
