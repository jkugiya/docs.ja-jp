---
description: 詳細については、次の説明
title: は、次のメソッドを実行します。
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHomeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHomeEnum::Next
helpviewer_keywords:
- ICorDebugVariableHomeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: eb9ea96c-5b58-4655-8104-094fc8b393b8
topic_type:
- apiref
ms.openlocfilehash: 0aa0174e67bceaa724ddfeadc2560d12e112b859
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790608"
---
# <a name="icordebugvariablehomeenumnext-method"></a><span data-ttu-id="08ab3-103">は、次のメソッドを実行します。</span><span class="sxs-lookup"><span data-stu-id="08ab3-103">ICorDebugVariableHomeEnum::Next Method</span></span>

<span data-ttu-id="08ab3-104">関数内のローカル変数および引数に関する情報を格納している指定された数の表示変数 [home](icordebugvariablehome-interface.md) インスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="08ab3-104">Gets the specified number of [ICorDebugVariableHome](icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08ab3-105">構文</span><span class="sxs-lookup"><span data-stu-id="08ab3-105">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] ICorDebugVariableHome *homes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08ab3-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="08ab3-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="08ab3-107">[in] 取得するオブジェクトの数。</span><span class="sxs-lookup"><span data-stu-id="08ab3-107">[in] The number of objects to be retrieved.</span></span>  
  
 `homes`  
 <span data-ttu-id="08ab3-108">ポインターの配列。各ポインターは、関数のローカル変数または引数に関する情報を提供 [する、の各オブジェクトを](icordebugvariablehome-interface.md) 参照します。</span><span class="sxs-lookup"><span data-stu-id="08ab3-108">An array of pointers, each of which points to a [ICorDebugVariableHome](icordebugvariablehome-interface.md) object that provides information about  a local variable or argument of a function.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="08ab3-109">入出力実際にオブジェクトで返されたインスタンスの数。</span><span class="sxs-lookup"><span data-stu-id="08ab3-109">[out] The number of instances actually returned in objects.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="08ab3-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="08ab3-110">Return Value</span></span>  

 <span data-ttu-id="08ab3-111">メソッドは、次の値を返します。</span><span class="sxs-lookup"><span data-stu-id="08ab3-111">The method returns the following values.</span></span>  
  
|<span data-ttu-id="08ab3-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="08ab3-112">HRESULT</span></span>|<span data-ttu-id="08ab3-113">説明</span><span class="sxs-lookup"><span data-stu-id="08ab3-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="08ab3-114">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="08ab3-114">The method completed successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="08ab3-115">に反映された実際のインスタンス数 `pceltFetched` が、要求されたインスタンスの数より少なくなっています。</span><span class="sxs-lookup"><span data-stu-id="08ab3-115">The actual number of instances retrieved, as reflected in `pceltFetched`, is less than the number of instances requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08ab3-116">解説</span><span class="sxs-lookup"><span data-stu-id="08ab3-116">Remarks</span></span>  

 <span data-ttu-id="08ab3-117">[次](icordebugvariablehomeenum-next-method.md)のメソッドは、 `celt` 列挙子の現在位置を起点として、最大オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="08ab3-117">The [ICorDebugVariableHomeEnum::Next](icordebugvariablehomeenum-next-method.md) method retrieves a maximum of  `celt` objects starting at the current position of the enumerator.</span></span> <span data-ttu-id="08ab3-118">メソッドから制御が戻るときに、 `pceltFetched` 取得したオブジェクトの実際の数を格納します。</span><span class="sxs-lookup"><span data-stu-id="08ab3-118">When the method returns, `pceltFetched` contains the actual number of objects retrieved.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08ab3-119">要件</span><span class="sxs-lookup"><span data-stu-id="08ab3-119">Requirements</span></span>  

 <span data-ttu-id="08ab3-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08ab3-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08ab3-121">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="08ab3-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="08ab3-122">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="08ab3-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08ab3-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08ab3-123">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08ab3-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="08ab3-124">See also</span></span>

- [<span data-ttu-id="08ab3-125">ICorDebugVariableHomeEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="08ab3-125">ICorDebugVariableHomeEnum Interface</span></span>](icordebugvariablehomeenum-interface.md)
- [<span data-ttu-id="08ab3-126">ICorDebugVariableHome インターフェイス</span><span class="sxs-lookup"><span data-stu-id="08ab3-126">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
