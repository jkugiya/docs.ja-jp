---
description: 詳細については、「ICorProfilerInfo6 インターフェイス」を参照してください。
title: ICorProfilerInfo6 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo6
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 6f2bb148-1e2b-4e45-a5a5-0ceddc40064b
ms.openlocfilehash: c093930b102ca99a8524e6d5d6129690f80a5353
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737156"
---
# <a name="icorprofilerinfo6-interface"></a><span data-ttu-id="95841-103">ICorProfilerInfo6 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="95841-103">ICorProfilerInfo6 Interface</span></span>

<span data-ttu-id="95841-104">[.NET Framework 4.6 以降のバージョンでサポートされています]</span><span class="sxs-lookup"><span data-stu-id="95841-104">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="95841-105">特定の NGen モジュールで定義され、特定のメソッドにインラインで定義されているすべてのメソッドの列挙子を提供する [ICorProfilerInfo5](icorprofilerinfo5-interface.md) のサブクラス。</span><span class="sxs-lookup"><span data-stu-id="95841-105">A subclass of [ICorProfilerInfo5](icorprofilerinfo5-interface.md) that provides an enumerator for all methods that are defined in a given NGen module and inline a given method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="95841-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="95841-106">Methods</span></span>  
  
|<span data-ttu-id="95841-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="95841-107">Method</span></span>|<span data-ttu-id="95841-108">説明</span><span class="sxs-lookup"><span data-stu-id="95841-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="95841-109">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="95841-109">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>](icorprofilerinfo6-enumngenmodulemethodsinliningthismethod-method.md)|<span data-ttu-id="95841-110">特定の NGen モジュールに属し、特定のメソッドの本体にインライン化されているすべてのメソッドの列挙子を返します。</span><span class="sxs-lookup"><span data-stu-id="95841-110">Returns an enumerator for all methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="95841-111">要件</span><span class="sxs-lookup"><span data-stu-id="95841-111">Requirements</span></span>  

 <span data-ttu-id="95841-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="95841-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95841-113">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="95841-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="95841-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95841-114">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95841-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="95841-115">See also</span></span>

- [<span data-ttu-id="95841-116">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="95841-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
