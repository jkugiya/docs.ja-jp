---
description: 詳細については、「ICorDebugLoadedModule インターフェイス」を参照してください。
title: ICorDebugLoadedModule インターフェイス
ms.date: 03/30/2017
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
ms.openlocfilehash: 6a1b466a9d2d7781fad7ac2bc8c24f0b2a5c23e0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801229"
---
# <a name="icordebugloadedmodule-interface"></a><span data-ttu-id="a8273-103">ICorDebugLoadedModule インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a8273-103">ICorDebugLoadedModule Interface</span></span>

<span data-ttu-id="a8273-104">読み込まれたモジュールについての情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="a8273-104">Provides information about a loaded module.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a8273-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="a8273-105">Methods</span></span>  
  
|<span data-ttu-id="a8273-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="a8273-106">Method</span></span>|<span data-ttu-id="a8273-107">説明</span><span class="sxs-lookup"><span data-stu-id="a8273-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a8273-108">GetBaseAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="a8273-108">GetBaseAddress Method</span></span>](icordebugloadedmodule-getbaseaddress-method.md)|<span data-ttu-id="a8273-109">読み込まれたモジュールのベース アドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="a8273-109">Gets the base address of the loaded module.</span></span>|  
|[<span data-ttu-id="a8273-110">GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="a8273-110">GetName Method</span></span>](icordebugloadedmodule-getname-method.md)|<span data-ttu-id="a8273-111">読み込まれたモジュールの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="a8273-111">Gets the name of the loaded module.</span></span>|  
|[<span data-ttu-id="a8273-112">GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="a8273-112">GetSize Method</span></span>](icordebugloadedmodule-getsize-method.md)|<span data-ttu-id="a8273-113">読み込まれたモジュールのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="a8273-113">Gets the size in bytes of the loaded module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8273-114">解説</span><span class="sxs-lookup"><span data-stu-id="a8273-114">Remarks</span></span>  

 <span data-ttu-id="a8273-115">`ICorDebugLoadedModule` インターフェイスはデバッガーによって実装され、CLR デバッグ インターフェイスが、デバッガーから読み込まれたモジュールに関する情報を取得するために使用します。</span><span class="sxs-lookup"><span data-stu-id="a8273-115">The `ICorDebugLoadedModule` interface is implemented by a debugger and is used by the CLR debugging interfaces to get information about the loaded module from the debugger.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a8273-116">このインターフェイスは .NET ネイティブでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="a8273-116">This interface is available with .NET Native only.</span></span> <span data-ttu-id="a8273-117">.NET ネイティブの外部で ICorDebug シナリオについてこのインターフェイスを実装する場合は、共通言語ランタイムはこのインターフェイスを無視します。</span><span class="sxs-lookup"><span data-stu-id="a8273-117">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8273-118">要件</span><span class="sxs-lookup"><span data-stu-id="a8273-118">Requirements</span></span>  

 <span data-ttu-id="a8273-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8273-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8273-120">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a8273-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a8273-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a8273-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8273-122">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8273-122">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8273-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="a8273-123">See also</span></span>

- [<span data-ttu-id="a8273-124">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="a8273-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="a8273-125">デバッグ</span><span class="sxs-lookup"><span data-stu-id="a8273-125">Debugging</span></span>](index.md)
