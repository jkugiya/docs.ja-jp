---
description: '詳細については、次のページを参照してください: を参照'
title: ICorDebugDebugEvent インターフェイス
ms.date: 03/30/2017
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
ms.openlocfilehash: 5735be22b76e9f74847bb5138c00130f28dbfc96
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764308"
---
# <a name="icordebugdebugevent-interface"></a><span data-ttu-id="a614c-103">ICorDebugDebugEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a614c-103">ICorDebugDebugEvent Interface</span></span>

<span data-ttu-id="a614c-104">すべての `ICorDebug` デバッグ イベントを派生させる基本インターフェイスを定義します。</span><span class="sxs-lookup"><span data-stu-id="a614c-104">Defines the base interface from which all `ICorDebug` debug events derive.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a614c-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="a614c-105">Methods</span></span>  
  
|<span data-ttu-id="a614c-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="a614c-106">Method</span></span>|<span data-ttu-id="a614c-107">説明</span><span class="sxs-lookup"><span data-stu-id="a614c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a614c-108">GetEventKind メソッド</span><span class="sxs-lookup"><span data-stu-id="a614c-108">GetEventKind Method</span></span>](icordebugdebugevent-geteventkind-method.md)|<span data-ttu-id="a614c-109">この `ICorDebugDebugEvent` オブジェクトが表すイベントの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="a614c-109">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>|  
|[<span data-ttu-id="a614c-110">GetThread メソッド</span><span class="sxs-lookup"><span data-stu-id="a614c-110">GetThread Method</span></span>](icordebugdebugevent-getthread-method.md)|<span data-ttu-id="a614c-111">イベントが発生したスレッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="a614c-111">Gets the thread on which the event occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a614c-112">解説</span><span class="sxs-lookup"><span data-stu-id="a614c-112">Remarks</span></span>  

 <span data-ttu-id="a614c-113">次のインターフェイスは、`ICorDebugDebugEvent` インターフェイスから派生したものです。</span><span class="sxs-lookup"><span data-stu-id="a614c-113">The following interfaces are derived from the `ICorDebugDebugEvent` interface:</span></span>  
  
- [<span data-ttu-id="a614c-114">ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="a614c-114">ICorDebugExceptionDebugEvent</span></span>](icordebugexceptiondebugevent-interface.md)  
  
- [<span data-ttu-id="a614c-115">ICorDebugModuleDebugEvent</span><span class="sxs-lookup"><span data-stu-id="a614c-115">ICorDebugModuleDebugEvent</span></span>](icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
> <span data-ttu-id="a614c-116">このインターフェイスは .NET ネイティブでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="a614c-116">The interface is available with .NET Native only.</span></span> <span data-ttu-id="a614c-117">インターフェイス ポインターを取得するために `QueryInterface` を呼び出そうとすると、.NET ネイティブ外の ICorDebug シナリオに対して `E_NOINTERFACE` が返されます。</span><span class="sxs-lookup"><span data-stu-id="a614c-117">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a614c-118">要件</span><span class="sxs-lookup"><span data-stu-id="a614c-118">Requirements</span></span>  

 <span data-ttu-id="a614c-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a614c-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a614c-120">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a614c-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a614c-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a614c-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a614c-122">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a614c-122">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a614c-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="a614c-123">See also</span></span>

- [<span data-ttu-id="a614c-124">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="a614c-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="a614c-125">デバッグ</span><span class="sxs-lookup"><span data-stu-id="a614c-125">Debugging</span></span>](index.md)
