---
description: 詳細については、「ICorDebugDataTarget2 インターフェイス」を参照してください。
title: ICorDebugDataTarget2 インターフェイス
ms.date: 03/30/2017
ms.assetid: 13f11388-2f91-48d8-98d6-6a4a63cb5746
ms.openlocfilehash: 13a83ee99f0158f32f466f9ae29af3d917248f95
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710466"
---
# <a name="icordebugdatatarget2-interface"></a><span data-ttu-id="f8483-103">ICorDebugDataTarget2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f8483-103">ICorDebugDataTarget2 Interface</span></span>

<span data-ttu-id="f8483-104">によって、"の" を論理的に [拡張します](icordebugdatatarget-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="f8483-104">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md)interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f8483-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="f8483-105">Methods</span></span>  
  
|<span data-ttu-id="f8483-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="f8483-106">Method</span></span>|<span data-ttu-id="f8483-107">説明</span><span class="sxs-lookup"><span data-stu-id="f8483-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f8483-108">CreateVirtualUnwinder メソッド</span><span class="sxs-lookup"><span data-stu-id="f8483-108">CreateVirtualUnwinder Method</span></span>](icordebugdatatarget2-createvirtualunwinder-method.md)|<span data-ttu-id="f8483-109">初期コンテキストからアンワインドを開始する新しいスタック アンワインダーを作成します (これは、必ずしもスレッドのリーフではありません)。</span><span class="sxs-lookup"><span data-stu-id="f8483-109">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>|  
|[<span data-ttu-id="f8483-110">EnumerateThreadIDs メソッド</span><span class="sxs-lookup"><span data-stu-id="f8483-110">EnumerateThreadIDs Method</span></span>](icordebugdatatarget2-enumeratethreadids-method.md)|<span data-ttu-id="f8483-111">アクティブなスレッド ID の一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="f8483-111">Returns a list of active thread IDs.</span></span>|  
|[<span data-ttu-id="f8483-112">GetImageFromPointer メソッド</span><span class="sxs-lookup"><span data-stu-id="f8483-112">GetImageFromPointer Method</span></span>](icordebugdatatarget2-getimagefrompointer-method.md)|<span data-ttu-id="f8483-113">モジュールのアドレスから、そのモジュールのベース アドレスとサイズを返します。</span><span class="sxs-lookup"><span data-stu-id="f8483-113">Returns the module base address and size from an address in that module.</span></span>|  
|[<span data-ttu-id="f8483-114">GetImageLocation メソッド</span><span class="sxs-lookup"><span data-stu-id="f8483-114">GetImageLocation Method</span></span>](icordebugdatatarget2-getimagelocation-method.md)|<span data-ttu-id="f8483-115">モジュールのベース アドレスからモジュールのパスを返します。</span><span class="sxs-lookup"><span data-stu-id="f8483-115">Returns the path of a module from the module's base address.</span></span>|  
|[<span data-ttu-id="f8483-116">GetSymbolProviderForImage メソッド</span><span class="sxs-lookup"><span data-stu-id="f8483-116">GetSymbolProviderForImage Method</span></span>](icordebugdatatarget2-getsymbolproviderforimage-method.md)|<span data-ttu-id="f8483-117">モジュールのベース アドレスからそのモジュールのシンボル プロバイダーを返します。</span><span class="sxs-lookup"><span data-stu-id="f8483-117">Returns the symbol-provider for a module from the base address of that module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8483-118">解説</span><span class="sxs-lookup"><span data-stu-id="f8483-118">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f8483-119">このインターフェイスは .NET ネイティブでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="f8483-119">This interface is available with .NET Native only.</span></span> <span data-ttu-id="f8483-120">.NET ネイティブの外部で ICorDebug シナリオについてこのインターフェイスを実装する場合は、共通言語ランタイムはこのインターフェイスを無視します。</span><span class="sxs-lookup"><span data-stu-id="f8483-120">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8483-121">要件</span><span class="sxs-lookup"><span data-stu-id="f8483-121">Requirements</span></span>  

 <span data-ttu-id="f8483-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8483-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8483-123">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f8483-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f8483-124">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8483-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8483-125">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8483-125">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8483-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="f8483-126">See also</span></span>

- [<span data-ttu-id="f8483-127">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="f8483-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="f8483-128">デバッグ</span><span class="sxs-lookup"><span data-stu-id="f8483-128">Debugging</span></span>](index.md)
