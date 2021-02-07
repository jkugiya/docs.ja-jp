---
description: '詳細情報: ICorDebugValue インターフェイス'
title: ICorDebugValue インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue
helpviewer_keywords:
- ICorDebugValue interface [.NET Framework debugging]
ms.assetid: b2f7007f-c446-4b18-aed1-a25cff8aee31
topic_type:
- apiref
ms.openlocfilehash: cae8fdef5c1c49cbabc25d3d547cb5748a9eeee1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690312"
---
# <a name="icordebugvalue-interface"></a><span data-ttu-id="378e8-103">ICorDebugValue インターフェイス</span><span class="sxs-lookup"><span data-stu-id="378e8-103">ICorDebugValue Interface</span></span>

<span data-ttu-id="378e8-104">デバッグ中のプロセスの値を表します。</span><span class="sxs-lookup"><span data-stu-id="378e8-104">Represents a value in the process being debugged.</span></span> <span data-ttu-id="378e8-105">値には、読み取りまたは書き込みの値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="378e8-105">The value can be a read or a write value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="378e8-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="378e8-106">Methods</span></span>  
  
|<span data-ttu-id="378e8-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="378e8-107">Method</span></span>|<span data-ttu-id="378e8-108">説明</span><span class="sxs-lookup"><span data-stu-id="378e8-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="378e8-109">CreateBreakpoint メソッド</span><span class="sxs-lookup"><span data-stu-id="378e8-109">CreateBreakpoint Method</span></span>](icordebugvalue-createbreakpoint-method.md)|<span data-ttu-id="378e8-110">このメソッドは、現在実装されていません。</span><span class="sxs-lookup"><span data-stu-id="378e8-110">This method is not currently implemented.</span></span>|  
|[<span data-ttu-id="378e8-111">GetAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="378e8-111">GetAddress Method</span></span>](icordebugvalue-getaddress-method.md)|<span data-ttu-id="378e8-112">このオブジェクトのアドレスを取得します。このアドレスは、 `ICorDebugValue` デバッグ中のプロセスです。</span><span class="sxs-lookup"><span data-stu-id="378e8-112">Gets the address of this `ICorDebugValue` object, which is in the process of being debugged.</span></span>|  
|[<span data-ttu-id="378e8-113">GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="378e8-113">GetSize Method</span></span>](icordebugvalue-getsize-method.md)|<span data-ttu-id="378e8-114">このオブジェクトのサイズ (バイト単位) を取得し `ICorDebugValue` ます。</span><span class="sxs-lookup"><span data-stu-id="378e8-114">Gets the size, in bytes, of this `ICorDebugValue` object.</span></span>|  
|[<span data-ttu-id="378e8-115">GetType メソッド</span><span class="sxs-lookup"><span data-stu-id="378e8-115">GetType Method</span></span>](icordebugvalue-gettype-method.md)|<span data-ttu-id="378e8-116">このオブジェクトのプリミティブ型を取得し `ICorDebugValue` ます。</span><span class="sxs-lookup"><span data-stu-id="378e8-116">Gets the primitive type of this `ICorDebugValue` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="378e8-117">解説</span><span class="sxs-lookup"><span data-stu-id="378e8-117">Remarks</span></span>  

 <span data-ttu-id="378e8-118">一般に、値オブジェクトの所有権は、返されるときに渡されます。</span><span class="sxs-lookup"><span data-stu-id="378e8-118">In general, ownership of a value object is passed when it is returned.</span></span> <span data-ttu-id="378e8-119">オブジェクトの終了時に、オブジェクトからの参照を削除するのは、受信者の責任です。</span><span class="sxs-lookup"><span data-stu-id="378e8-119">The recipient is responsible for removing a reference from the object when it is finished with the object.</span></span>  
  
 <span data-ttu-id="378e8-120">値が取得された場所によっては、プロセスが再開された後も値が有効なままにならないことがあります。</span><span class="sxs-lookup"><span data-stu-id="378e8-120">Depending on where the value was retrieved from, the value may not remain valid after the process is resumed.</span></span> <span data-ttu-id="378e8-121">そのため、一般に、次のように、値は、は、「いいね [:: Continue](icordebugcontroller-continue-method.md) メソッドの呼び出し」で保持するべきではありません。</span><span class="sxs-lookup"><span data-stu-id="378e8-121">So, in general, the value shouldn't be held across a call of the [ICorDebugController::Continue](icordebugcontroller-continue-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="378e8-122">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="378e8-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="378e8-123">要件</span><span class="sxs-lookup"><span data-stu-id="378e8-123">Requirements</span></span>  

 <span data-ttu-id="378e8-124">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="378e8-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="378e8-125">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="378e8-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="378e8-126">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="378e8-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="378e8-127">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="378e8-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="378e8-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="378e8-128">See also</span></span>

- [<span data-ttu-id="378e8-129">ICorDebugValue3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="378e8-129">ICorDebugValue3 Interface</span></span>](icordebugvalue3-interface.md)
- [<span data-ttu-id="378e8-130">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="378e8-130">Debugging Interfaces</span></span>](debugging-interfaces.md)
