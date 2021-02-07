---
description: '詳細については、次の情報を参照してください: いい値インターフェイス'
title: ICorDebugGenericValue インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue
helpviewer_keywords:
- ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: bc14f408-b359-4c8c-ade2-888ccdf7261b
topic_type:
- apiref
ms.openlocfilehash: 7c81855849d7b72bc509d20072b96bb64f5d395a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692035"
---
# <a name="icordebuggenericvalue-interface"></a><span data-ttu-id="3ed07-103">ICorDebugGenericValue インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3ed07-103">ICorDebugGenericValue Interface</span></span>

<span data-ttu-id="3ed07-104">すべての値に適用される "ICorDebugValue" のサブクラス。</span><span class="sxs-lookup"><span data-stu-id="3ed07-104">A subclass of "ICorDebugValue" that applies to all values.</span></span> <span data-ttu-id="3ed07-105">このインターフェイスは、値に対して Get メソッドと Set メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="3ed07-105">This interface provides Get and Set methods for the value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3ed07-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="3ed07-106">Methods</span></span>  
  
|<span data-ttu-id="3ed07-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="3ed07-107">Method</span></span>|<span data-ttu-id="3ed07-108">説明</span><span class="sxs-lookup"><span data-stu-id="3ed07-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3ed07-109">GetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="3ed07-109">GetValue Method</span></span>](icordebuggenericvalue-getvalue-method.md)|<span data-ttu-id="3ed07-110">指定したバッファーに値をコピーします。</span><span class="sxs-lookup"><span data-stu-id="3ed07-110">Copies the value into the specified buffer.</span></span>|  
|[<span data-ttu-id="3ed07-111">SetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="3ed07-111">SetValue Method</span></span>](icordebuggenericvalue-setvalue-method.md)|<span data-ttu-id="3ed07-112">指定したバッファーから新しい値をコピーします。</span><span class="sxs-lookup"><span data-stu-id="3ed07-112">Copies a new value from the specified buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ed07-113">解説</span><span class="sxs-lookup"><span data-stu-id="3ed07-113">Remarks</span></span>  

 <span data-ttu-id="3ed07-114">`ICorDebugGenericValue` は、リモート処理が不可能なため、サブインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="3ed07-114">`ICorDebugGenericValue` is a sub-interface because it is non-remotable.</span></span>  
  
 <span data-ttu-id="3ed07-115">参照型の場合、値は参照の内容ではなく参照です。</span><span class="sxs-lookup"><span data-stu-id="3ed07-115">For reference types, the value is the reference rather than the contents of the reference.</span></span>  
  
 <span data-ttu-id="3ed07-116">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="3ed07-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3ed07-117">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="3ed07-117">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ed07-118">要件</span><span class="sxs-lookup"><span data-stu-id="3ed07-118">Requirements</span></span>  

 <span data-ttu-id="3ed07-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3ed07-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ed07-120">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3ed07-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3ed07-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3ed07-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3ed07-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ed07-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ed07-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="3ed07-123">See also</span></span>

- [<span data-ttu-id="3ed07-124">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="3ed07-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
