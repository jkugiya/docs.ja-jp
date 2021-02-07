---
description: 詳細については、「ICorProfilerInfo7 インターフェイス」を参照してください。
title: ICorProfilerInfo7 インターフェイス
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
ms.openlocfilehash: 7a33472d5562ad57d38291c64f8da7021ae2fe91
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737078"
---
# <a name="icorprofilerinfo7-interface"></a><span data-ttu-id="3a017-103">ICorProfilerInfo7 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a017-103">ICorProfilerInfo7 Interface</span></span>

<span data-ttu-id="3a017-104">[.NET Framework 4.6.1 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="3a017-104">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="3a017-105">新しく定義されたメタデータをモジュールに適用し、メモリ内シンボルストリームへのアクセスを提供するメソッドを提供する [ICorProfilerInfo6](icorprofilerinfo6-interface.md) のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="3a017-105">A subclass of [ICorProfilerInfo6](icorprofilerinfo6-interface.md) that provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3a017-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="3a017-106">Methods</span></span>  
  
|<span data-ttu-id="3a017-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="3a017-107">Method</span></span>|<span data-ttu-id="3a017-108">説明</span><span class="sxs-lookup"><span data-stu-id="3a017-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3a017-109">ApplyMetaData メソッド</span><span class="sxs-lookup"><span data-stu-id="3a017-109">ApplyMetaData Method</span></span>](icorprofilerinfo7-applymetadata-method.md)|<span data-ttu-id="3a017-110">メソッドによって新たに定義されたメタデータ `IMetadataEmit::Define*` を、指定したモジュールに適用します。</span><span class="sxs-lookup"><span data-stu-id="3a017-110">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>|  
|[<span data-ttu-id="3a017-111">GetInMemorySymbolsLength メソッド</span><span class="sxs-lookup"><span data-stu-id="3a017-111">GetInMemorySymbolsLength Method</span></span>](icorprofilerinfo7-getinmemorysymbolslength-method.md)|<span data-ttu-id="3a017-112">メモリ内シンボルストリームの長さを返します。</span><span class="sxs-lookup"><span data-stu-id="3a017-112">Returns the length of an in-memory symbol stream.</span></span>|  
|[<span data-ttu-id="3a017-113">ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="3a017-113">ReadInMemorySymbols</span></span>](icorprofilerinfo7-readinmemorysymbols.md)|<span data-ttu-id="3a017-114">メモリ内シンボルストリームからバイトを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="3a017-114">Reads bytes from an in-memory symbol stream.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3a017-115">要件</span><span class="sxs-lookup"><span data-stu-id="3a017-115">Requirements</span></span>  

 <span data-ttu-id="3a017-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3a017-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a017-117">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3a017-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3a017-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a017-118">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a017-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="3a017-119">See also</span></span>

- [<span data-ttu-id="3a017-120">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a017-120">Profiling Interfaces</span></span>](profiling-interfaces.md)
