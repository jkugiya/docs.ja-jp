---
description: 詳細については、「ICorDebugDataTarget3 インターフェイス」を参照してください。
title: ICorDebugDataTarget3 インターフェイス
ms.date: 03/30/2017
ms.assetid: f477af85-994f-4df0-ae78-404ed252bf49
ms.openlocfilehash: fa786b920d1a2e72dc2a7918e0514773862a0e85
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710440"
---
# <a name="icordebugdatatarget3-interface"></a><span data-ttu-id="59cde-103">ICorDebugDataTarget3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="59cde-103">ICorDebugDataTarget3 Interface</span></span>

<span data-ttu-id="59cde-104">提供され [たモジュール](icordebugdatatarget-interface.md) に関する情報を提供するために、によって、参照インターフェイスを論理的に拡張します。</span><span class="sxs-lookup"><span data-stu-id="59cde-104">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span>  
  
## <a name="method"></a><span data-ttu-id="59cde-105">Method</span><span class="sxs-lookup"><span data-stu-id="59cde-105">Method</span></span>  
  
|<span data-ttu-id="59cde-106">Method</span><span class="sxs-lookup"><span data-stu-id="59cde-106">Method</span></span>|<span data-ttu-id="59cde-107">説明</span><span class="sxs-lookup"><span data-stu-id="59cde-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="59cde-108">GetLoadedModules メソッド</span><span class="sxs-lookup"><span data-stu-id="59cde-108">GetLoadedModules Method</span></span>](icordebugdatatarget3-getloadedmodules-method.md)|<span data-ttu-id="59cde-109">これまでに読み込まれたモジュールの一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="59cde-109">Gets a list of the modules that have been loaded so far.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59cde-110">解説</span><span class="sxs-lookup"><span data-stu-id="59cde-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="59cde-111">このインターフェイスは .NET ネイティブでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="59cde-111">This interface is available with .NET Native only.</span></span> <span data-ttu-id="59cde-112">.NET ネイティブの外部で ICorDebug シナリオについてこのインターフェイスを実装する場合は、共通言語ランタイムはこのインターフェイスを無視します。</span><span class="sxs-lookup"><span data-stu-id="59cde-112">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59cde-113">要件</span><span class="sxs-lookup"><span data-stu-id="59cde-113">Requirements</span></span>  

 <span data-ttu-id="59cde-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="59cde-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59cde-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="59cde-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="59cde-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="59cde-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59cde-117">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59cde-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59cde-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="59cde-118">See also</span></span>

- [<span data-ttu-id="59cde-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="59cde-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="59cde-120">デバッグ</span><span class="sxs-lookup"><span data-stu-id="59cde-120">Debugging</span></span>](index.md)
