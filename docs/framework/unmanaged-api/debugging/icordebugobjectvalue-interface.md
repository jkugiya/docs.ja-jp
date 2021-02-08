---
description: '詳細については、次の情報を参照してください: の値インターフェイス'
title: ICorDebugObjectValue インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue
helpviewer_keywords:
- ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 937de6a0-6fbf-4ddc-80ea-a6217b73e62b
topic_type:
- apiref
ms.openlocfilehash: a2af438bbb4c2f56eb1a72151e339b6b0a978eec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794772"
---
# <a name="icordebugobjectvalue-interface"></a><span data-ttu-id="3b6f9-103">ICorDebugObjectValue インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3b6f9-103">ICorDebugObjectValue Interface</span></span>

<span data-ttu-id="3b6f9-104">オブジェクトを含む値を表す "ICorDebugValue" のサブクラス。</span><span class="sxs-lookup"><span data-stu-id="3b6f9-104">A subclass of "ICorDebugValue" that represents a value that contains an object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3b6f9-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="3b6f9-105">Methods</span></span>  
  
|<span data-ttu-id="3b6f9-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="3b6f9-106">Method</span></span>|<span data-ttu-id="3b6f9-107">説明</span><span class="sxs-lookup"><span data-stu-id="3b6f9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3b6f9-108">GetClass メソッド</span><span class="sxs-lookup"><span data-stu-id="3b6f9-108">GetClass Method</span></span>](icordebugobjectvalue-getclass-method.md)|<span data-ttu-id="3b6f9-109"><xref:System.Type>このが参照するオブジェクトの共通言語ランタイム (CLR) へのインターフェイスポインターを取得し `ICorDebugObjectValue` ます。</span><span class="sxs-lookup"><span data-stu-id="3b6f9-109">Gets an interface pointer to the common language runtime (CLR) <xref:System.Type> of the object that this `ICorDebugObjectValue` references.</span></span>|  
|[<span data-ttu-id="3b6f9-110">GetContext メソッド</span><span class="sxs-lookup"><span data-stu-id="3b6f9-110">GetContext Method</span></span>](icordebugobjectvalue-getcontext-method.md)|<span data-ttu-id="3b6f9-111">実装されていません。</span><span class="sxs-lookup"><span data-stu-id="3b6f9-111">Not implemented.</span></span>|  
|[<span data-ttu-id="3b6f9-112">GetFieldValue メソッド</span><span class="sxs-lookup"><span data-stu-id="3b6f9-112">GetFieldValue Method</span></span>](icordebugobjectvalue-getfieldvalue-method.md)|<span data-ttu-id="3b6f9-113">指定したクラスの指定したフィールドの値を表す、 [ICorDebugValue](icordebugvalue-interface.md) へのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="3b6f9-113">Gets an interface pointer to an [ICorDebugValue](icordebugvalue-interface.md) that represents the value of the specified field of the specified class.</span></span>|  
|[<span data-ttu-id="3b6f9-114">GetManagedCopy メソッド</span><span class="sxs-lookup"><span data-stu-id="3b6f9-114">GetManagedCopy Method</span></span>](icordebugobjectvalue-getmanagedcopy-method.md)|<span data-ttu-id="3b6f9-115">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="3b6f9-115">Obsolete.</span></span> <span data-ttu-id="3b6f9-116">このメソッドは呼び出さないでください。</span><span class="sxs-lookup"><span data-stu-id="3b6f9-116">Do not call this method.</span></span>|  
|[<span data-ttu-id="3b6f9-117">GetVirtualMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="3b6f9-117">GetVirtualMethod Method</span></span>](icordebugobjectvalue-getvirtualmethod-method.md)|<span data-ttu-id="3b6f9-118">実装されていません。</span><span class="sxs-lookup"><span data-stu-id="3b6f9-118">Not implemented.</span></span>|  
|[<span data-ttu-id="3b6f9-119">IsValueClass メソッド</span><span class="sxs-lookup"><span data-stu-id="3b6f9-119">IsValueClass Method</span></span>](icordebugobjectvalue-isvalueclass-method.md)|<span data-ttu-id="3b6f9-120">このによって参照されるオブジェクトが値型かどうかを示す値を取得し `ICorDebugObjectValue` ます。</span><span class="sxs-lookup"><span data-stu-id="3b6f9-120">Gets a value that indicates whether the object referenced by this `ICorDebugObjectValue` is a value type.</span></span>|  
|[<span data-ttu-id="3b6f9-121">SetFromManagedCopy メソッド</span><span class="sxs-lookup"><span data-stu-id="3b6f9-121">SetFromManagedCopy Method</span></span>](icordebugobjectvalue-setfrommanagedcopy-method.md)|<span data-ttu-id="3b6f9-122">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="3b6f9-122">Obsolete.</span></span> <span data-ttu-id="3b6f9-123">このメソッドは呼び出さないでください。</span><span class="sxs-lookup"><span data-stu-id="3b6f9-123">Do not call this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b6f9-124">解説</span><span class="sxs-lookup"><span data-stu-id="3b6f9-124">Remarks</span></span>  

 <span data-ttu-id="3b6f9-125">は、 `ICorDebugObjectValue` デバッグ中のプロセスが続行されるまで有効なままです。</span><span class="sxs-lookup"><span data-stu-id="3b6f9-125">An `ICorDebugObjectValue` remains valid until the process being debugged is continued.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3b6f9-126">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="3b6f9-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b6f9-127">要件</span><span class="sxs-lookup"><span data-stu-id="3b6f9-127">Requirements</span></span>  

 <span data-ttu-id="3b6f9-128">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3b6f9-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b6f9-129">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3b6f9-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3b6f9-130">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3b6f9-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3b6f9-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b6f9-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b6f9-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="3b6f9-132">See also</span></span>

- [<span data-ttu-id="3b6f9-133">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="3b6f9-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
