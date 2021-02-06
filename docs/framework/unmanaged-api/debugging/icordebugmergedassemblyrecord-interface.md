---
description: 詳細については、「ICorDebugMergedAssemblyRecord インターフェイス」を参照してください。
title: ICorDebugMergedAssemblyRecord インターフェイス
ms.date: 03/30/2017
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
ms.openlocfilehash: e64c0ee30a8e8956dd336a30e6c81962c75f04e9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650288"
---
# <a name="icordebugmergedassemblyrecord-interface"></a><span data-ttu-id="2535e-103">ICorDebugMergedAssemblyRecord インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2535e-103">ICorDebugMergedAssemblyRecord Interface</span></span>

<span data-ttu-id="2535e-104">マージされたアセンブリに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="2535e-104">Provides information about a merged assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2535e-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="2535e-105">Methods</span></span>  
  
|<span data-ttu-id="2535e-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="2535e-106">Method</span></span>|<span data-ttu-id="2535e-107">説明</span><span class="sxs-lookup"><span data-stu-id="2535e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2535e-108">GetCulture メソッド</span><span class="sxs-lookup"><span data-stu-id="2535e-108">GetCulture Method</span></span>](icordebugmergedassemblyrecord-getculture-method.md)|<span data-ttu-id="2535e-109">アセンブリのカルチャ名文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="2535e-109">Gets the culture name string of the assembly.</span></span>|  
|[<span data-ttu-id="2535e-110">GetIndex メソッド</span><span class="sxs-lookup"><span data-stu-id="2535e-110">GetIndex Method</span></span>](icordebugmergedassemblyrecord-getindex-method.md)|<span data-ttu-id="2535e-111">アセンブリのプレフィックス インデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="2535e-111">Gets the assembly's prefix index.</span></span>|  
|[<span data-ttu-id="2535e-112">GetPublicKey メソッド</span><span class="sxs-lookup"><span data-stu-id="2535e-112">GetPublicKey Method</span></span>](icordebugmergedassemblyrecord-getpublickey-method.md)|<span data-ttu-id="2535e-113">アセンブリの公開キーを取得します。</span><span class="sxs-lookup"><span data-stu-id="2535e-113">Gets the assembly's public key.</span></span>|  
|[<span data-ttu-id="2535e-114">GetPublicKeyToken メソッド</span><span class="sxs-lookup"><span data-stu-id="2535e-114">GetPublicKeyToken Method</span></span>](icordebugmergedassemblyrecord-getpublickeytoken-method.md)|<span data-ttu-id="2535e-115">アセンブリの公開キー トークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="2535e-115">Gets the assembly's public key token.</span></span>|  
|[<span data-ttu-id="2535e-116">GetSimpleName メソッド</span><span class="sxs-lookup"><span data-stu-id="2535e-116">GetSimpleName Method</span></span>](icordebugmergedassemblyrecord-getsimplename-method.md)|<span data-ttu-id="2535e-117">アセンブリの簡易名を取得します。</span><span class="sxs-lookup"><span data-stu-id="2535e-117">Gets the simple name of the assembly.</span></span>|  
|[<span data-ttu-id="2535e-118">GetVersion メソッド</span><span class="sxs-lookup"><span data-stu-id="2535e-118">GetVersion Method</span></span>](icordebugmergedassemblyrecord-getversion-method.md)|<span data-ttu-id="2535e-119">アセンブリのバージョン情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="2535e-119">Gets the assembly's version information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2535e-120">解説</span><span class="sxs-lookup"><span data-stu-id="2535e-120">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2535e-121">このインターフェイスは .NET ネイティブでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="2535e-121">This interface is available with .NET Native only.</span></span> <span data-ttu-id="2535e-122">.NET ネイティブの外部で ICorDebug シナリオについてこのインターフェイスを実装する場合は、共通言語ランタイムはこのインターフェイスを無視します。</span><span class="sxs-lookup"><span data-stu-id="2535e-122">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2535e-123">要件</span><span class="sxs-lookup"><span data-stu-id="2535e-123">Requirements</span></span>  

 <span data-ttu-id="2535e-124">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2535e-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2535e-125">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2535e-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2535e-126">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2535e-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2535e-127">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2535e-127">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2535e-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="2535e-128">See also</span></span>

- [<span data-ttu-id="2535e-129">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="2535e-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="2535e-130">デバッグ</span><span class="sxs-lookup"><span data-stu-id="2535e-130">Debugging</span></span>](index.md)
