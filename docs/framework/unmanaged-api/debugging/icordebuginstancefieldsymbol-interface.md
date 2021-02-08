---
description: '詳細については、次の情報を参照してください: いいでしょう。シンボルインターフェイス'
title: ICorDebugInstanceFieldSymbol インターフェイス
ms.date: 03/30/2017
ms.assetid: a4a8f259-b83a-4425-ae8b-72b067dbc0d9
ms.openlocfilehash: aa47c858ec5b4b0d04b851357fe81c0fc9b2e30a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791133"
---
# <a name="icordebuginstancefieldsymbol-interface"></a><span data-ttu-id="f9c8c-103">ICorDebugInstanceFieldSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f9c8c-103">ICorDebugInstanceFieldSymbol Interface</span></span>

<span data-ttu-id="f9c8c-104">インスタンス フィールドのデバッグ シンボル情報を表します。</span><span class="sxs-lookup"><span data-stu-id="f9c8c-104">Represents the debug symbol information for an instance field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f9c8c-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="f9c8c-105">Methods</span></span>  
  
|<span data-ttu-id="f9c8c-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="f9c8c-106">Method</span></span>|<span data-ttu-id="f9c8c-107">説明</span><span class="sxs-lookup"><span data-stu-id="f9c8c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f9c8c-108">GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="f9c8c-108">GetName Method</span></span>](icordebuginstancefieldsymbol-getname-method.md)|<span data-ttu-id="f9c8c-109">インスタンス フィールドの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="f9c8c-109">Gets the name of the instance field.</span></span>|  
|[<span data-ttu-id="f9c8c-110">GetOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="f9c8c-110">GetOffset Method</span></span>](icordebuginstancefieldsymbol-getoffset-method.md)|<span data-ttu-id="f9c8c-111">このインスタンス フィールドの親クラスにおける、このインスタンス フィールドのオフセット (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="f9c8c-111">Gets the offset in bytes of this instance field in its parent class.</span></span>|  
|[<span data-ttu-id="f9c8c-112">GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="f9c8c-112">GetSize Method</span></span>](icordebuginstancefieldsymbol-getsize-method.md)|<span data-ttu-id="f9c8c-113">インスタンス フィールドのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="f9c8c-113">Gets the size in bytes of the instance field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9c8c-114">解説</span><span class="sxs-lookup"><span data-stu-id="f9c8c-114">Remarks</span></span>  

 <span data-ttu-id="f9c8c-115">`ICorDebugInstanceFieldSymbol` インターフェイスは、インスタンス フィールドのデバッグ シンボル情報を取得するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="f9c8c-115">The `ICorDebugInstanceFieldSymbol` interface is used to retrieve the debug symbol information for an instance field.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f9c8c-116">このインターフェイスは .NET ネイティブでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="f9c8c-116">This interface is available with .NET Native only.</span></span> <span data-ttu-id="f9c8c-117">.NET ネイティブの外部で ICorDebug シナリオについてこのインターフェイスを実装する場合は、共通言語ランタイムはこのインターフェイスを無視します。</span><span class="sxs-lookup"><span data-stu-id="f9c8c-117">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9c8c-118">要件</span><span class="sxs-lookup"><span data-stu-id="f9c8c-118">Requirements</span></span>  

 <span data-ttu-id="f9c8c-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f9c8c-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9c8c-120">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f9c8c-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f9c8c-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f9c8c-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9c8c-122">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9c8c-122">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9c8c-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="f9c8c-123">See also</span></span>

- [<span data-ttu-id="f9c8c-124">ICorDebugStaticFieldSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f9c8c-124">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="f9c8c-125">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="f9c8c-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="f9c8c-126">デバッグ</span><span class="sxs-lookup"><span data-stu-id="f9c8c-126">Debugging</span></span>](index.md)
