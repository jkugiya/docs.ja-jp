---
description: 詳細については、「ICorProfilerInfo8 インターフェイス」を参照してください。
title: ICorProfilerInfo8 インターフェイス
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 4538c9d314283c67ab0bfe6af3f3768062cffda4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646544"
---
# <a name="icorprofilerinfo8-interface"></a><span data-ttu-id="9096c-103">ICorProfilerInfo8 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9096c-103">ICorProfilerInfo8 Interface</span></span>

<span data-ttu-id="9096c-104">動的メソッドに関する情報を照会するメソッドを提供する [ICorProfilerInfo7](icorprofilerinfo7-interface.md) のサブクラス。</span><span class="sxs-lookup"><span data-stu-id="9096c-104">A subclass of [ICorProfilerInfo7](icorprofilerinfo7-interface.md) that provides methods to query information about dynamic methods.</span></span>

## <a name="methods"></a><span data-ttu-id="9096c-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="9096c-105">Methods</span></span>  

| <span data-ttu-id="9096c-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="9096c-106">Method</span></span>|<span data-ttu-id="9096c-107">説明</span><span class="sxs-lookup"><span data-stu-id="9096c-107">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="9096c-108">IsFunctionDynamic メソッド</span><span class="sxs-lookup"><span data-stu-id="9096c-108">IsFunctionDynamic Method</span></span>](icorprofilerinfo8-isfunctiondynamic-method.md)| <span data-ttu-id="9096c-109">関数にメタデータが関連付けられていないかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="9096c-109">Determines if a function does not have associated metadata.</span></span>|
|[<span data-ttu-id="9096c-110">GetFunctionFromIP3 メソッド</span><span class="sxs-lookup"><span data-stu-id="9096c-110">GetFunctionFromIP3 Method</span></span>](icorprofilerinfo8-getfunctionfromip3-method.md)| <span data-ttu-id="9096c-111">マネージコード命令ポインターを FunctionID にマップします。</span><span class="sxs-lookup"><span data-stu-id="9096c-111">Maps a managed code instruction pointer to a FunctionID.</span></span> <span data-ttu-id="9096c-112">このメソッドは、動的メソッドと非動的メソッドの両方に対して機能します。</span><span class="sxs-lookup"><span data-stu-id="9096c-112">This method works for both dynamic and non-dynamic methods.</span></span> |
|[<span data-ttu-id="9096c-113">GetDynamicFunctionInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="9096c-113">GetDynamicFunctionInfo Method</span></span>](icorprofilerinfo8-getdynamicfunctioninfo-method.md)| <span data-ttu-id="9096c-114">動的メソッドに関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="9096c-114">Retrieves information about dynamic methods.</span></span> |

## <a name="requirements"></a><span data-ttu-id="9096c-115">要件</span><span class="sxs-lookup"><span data-stu-id="9096c-115">Requirements</span></span>  

<span data-ttu-id="9096c-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9096c-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="9096c-117">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9096c-117">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="9096c-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9096c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="9096c-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="9096c-119">See also</span></span>

- [<span data-ttu-id="9096c-120">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="9096c-120">Profiling Interfaces</span></span>](profiling-interfaces.md)
