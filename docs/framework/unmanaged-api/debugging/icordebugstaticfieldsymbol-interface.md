---
description: '詳細情報: 参照インターフェイス'
title: ICorDebugStaticFieldSymbol インターフェイス
ms.date: 03/30/2017
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
ms.openlocfilehash: 3aa9c98cef4cdc7edc519b06b6cf9b4b2192b4e5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794677"
---
# <a name="icordebugstaticfieldsymbol-interface"></a><span data-ttu-id="fff4f-103">ICorDebugStaticFieldSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fff4f-103">ICorDebugStaticFieldSymbol Interface</span></span>

<span data-ttu-id="fff4f-104">静的フィールドのデバッグ シンボル情報を表します。</span><span class="sxs-lookup"><span data-stu-id="fff4f-104">Represents the debug symbol information for a static field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fff4f-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="fff4f-105">Methods</span></span>  
  
|<span data-ttu-id="fff4f-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="fff4f-106">Method</span></span>|<span data-ttu-id="fff4f-107">説明</span><span class="sxs-lookup"><span data-stu-id="fff4f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fff4f-108">GetAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="fff4f-108">GetAddress Method</span></span>](icordebugstaticfieldsymbol-getaddress-method.md)|<span data-ttu-id="fff4f-109">静的フィールドのアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="fff4f-109">Gets the address of the static field.</span></span>|  
|[<span data-ttu-id="fff4f-110">GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="fff4f-110">GetName Method</span></span>](icordebugstaticfieldsymbol-getname-method.md)|<span data-ttu-id="fff4f-111">静的フィールドの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="fff4f-111">Gets the name of the static field.</span></span>|  
|[<span data-ttu-id="fff4f-112">GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="fff4f-112">GetSize Method</span></span>](icordebugstaticfieldsymbol-getsize-method.md)|<span data-ttu-id="fff4f-113">静的フィールドのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="fff4f-113">Gets the size in bytes of the static field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fff4f-114">解説</span><span class="sxs-lookup"><span data-stu-id="fff4f-114">Remarks</span></span>  

 <span data-ttu-id="fff4f-115">`ICorDebugStaticFieldSymbol` インターフェイスは、静的フィールドのデバッグ シンボル情報を取得するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="fff4f-115">The `ICorDebugStaticFieldSymbol` interface is used to retrieve the debug symbol information for a static field.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fff4f-116">このインターフェイスは .NET ネイティブでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="fff4f-116">This interface is available with .NET Native only.</span></span> <span data-ttu-id="fff4f-117">.NET ネイティブの外部で ICorDebug シナリオについてこのインターフェイスを実装する場合は、共通言語ランタイムはこのインターフェイスを無視します。</span><span class="sxs-lookup"><span data-stu-id="fff4f-117">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fff4f-118">要件</span><span class="sxs-lookup"><span data-stu-id="fff4f-118">Requirements</span></span>  

 <span data-ttu-id="fff4f-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fff4f-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fff4f-120">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fff4f-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fff4f-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fff4f-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fff4f-122">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fff4f-122">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fff4f-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="fff4f-123">See also</span></span>

- [<span data-ttu-id="fff4f-124">ICorDebugInstanceFieldSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fff4f-124">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="fff4f-125">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="fff4f-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="fff4f-126">デバッグ</span><span class="sxs-lookup"><span data-stu-id="fff4f-126">Debugging</span></span>](index.md)
