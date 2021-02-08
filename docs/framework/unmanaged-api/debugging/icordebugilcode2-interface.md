---
description: 詳細については、「ICorDebugILCode2 インターフェイス」を参照してください。
title: ICorDebugILCode2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugILCode2
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: f9dc2afd-df8a-464d-bdbf-5af0a1d4bf85
topic_type:
- apiref
ms.openlocfilehash: 52e47b8cbf8f9926797e193944fd7e97b2e4dbcd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791414"
---
# <a name="icordebugilcode2-interface"></a><span data-ttu-id="c174d-103">ICorDebugILCode2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c174d-103">ICorDebugILCode2 Interface</span></span>

<span data-ttu-id="c174d-104">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="c174d-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="c174d-105">では、この [コード](icordebugilcode-interface.md) インターフェイスを論理的に拡張して、関数のローカル変数シグネチャのトークンを返すメソッドを提供し、プロファイラーのインストルメント化された中間言語 (il) オフセットを元のメソッドの il オフセットにマップします。</span><span class="sxs-lookup"><span data-stu-id="c174d-105">Logically extends the [ICorDebugILCode](icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c174d-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="c174d-106">Methods</span></span>  
  
|<span data-ttu-id="c174d-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="c174d-107">Method</span></span>|<span data-ttu-id="c174d-108">説明</span><span class="sxs-lookup"><span data-stu-id="c174d-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c174d-109">GetInstrumentedILMap メソッド</span><span class="sxs-lookup"><span data-stu-id="c174d-109">GetInstrumentedILMap Method</span></span>](icordebugilcode2-getinstrumentedilmap-method.md)|<span data-ttu-id="c174d-110">プロファイラーのインストルメント化された IL オフセットから、このインスタンスに対する元のメソッドの IL オフセットへのマップを返します。</span><span class="sxs-lookup"><span data-stu-id="c174d-110">Returns a map from profiler instrumented IL offsets to original method IL offsets for this instance.</span></span>|  
|[<span data-ttu-id="c174d-111">GetLocalVarSigToken メソッド</span><span class="sxs-lookup"><span data-stu-id="c174d-111">GetLocalVarSigToken Method</span></span>](icordebugilcode2-getlocalvarsigtoken-method.md)|<span data-ttu-id="c174d-112">このインスタンスで示される関数について、ローカル変数のシグネチャのメタデータ トークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="c174d-112">Gets the metadata token for the local variable signature for the function that is represented by this instance.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c174d-113">要件</span><span class="sxs-lookup"><span data-stu-id="c174d-113">Requirements</span></span>  

 <span data-ttu-id="c174d-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c174d-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c174d-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c174d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c174d-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c174d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c174d-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c174d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c174d-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="c174d-118">See also</span></span>

- [<span data-ttu-id="c174d-119">ICorDebugILCode インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c174d-119">ICorDebugILCode Interface</span></span>](icordebugilcode-interface.md)
- [<span data-ttu-id="c174d-120">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="c174d-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="c174d-121">デバッグ</span><span class="sxs-lookup"><span data-stu-id="c174d-121">Debugging</span></span>](index.md)
