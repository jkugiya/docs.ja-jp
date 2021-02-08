---
description: 詳細については、「ICLRDataEnumMemoryRegionsCallback インターフェイス」を参照してください。
title: ICLRDataEnumMemoryRegionsCallback インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegionsCallback
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegionsCallback
helpviewer_keywords:
- ICLRDataEnumMemoryRegionsCallback interface [.NET Framework debugging]
ms.assetid: 3f1af8b0-8478-48e0-a7ec-3e90e0b97649
topic_type:
- apiref
ms.openlocfilehash: 863192844c4d4d8a35d1e73d38adea3a513bc944
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801372"
---
# <a name="iclrdataenummemoryregionscallback-interface"></a><span data-ttu-id="ab87f-103">ICLRDataEnumMemoryRegionsCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ab87f-103">ICLRDataEnumMemoryRegionsCallback Interface</span></span>

<span data-ttu-id="ab87f-104">[ICLRDataEnumMemoryRegions:: EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md)のコールバックメソッドを提供し、指定されたメモリ領域を列挙しようとした結果をデバッガーに報告します。</span><span class="sxs-lookup"><span data-stu-id="ab87f-104">Provides a callback method for [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ab87f-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="ab87f-105">Methods</span></span>  
  
|<span data-ttu-id="ab87f-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="ab87f-106">Method</span></span>|<span data-ttu-id="ab87f-107">説明</span><span class="sxs-lookup"><span data-stu-id="ab87f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ab87f-108">EnumMemoryRegion メソッド</span><span class="sxs-lookup"><span data-stu-id="ab87f-108">EnumMemoryRegion Method</span></span>](iclrdataenummemoryregionscallback-enummemoryregion-method.md)|<span data-ttu-id="ab87f-109">`ICLRDataEnumMemoryRegions::EnumMemoryRegions`指定されたメモリ領域を列挙しようとした結果をデバッガーに報告するために、によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="ab87f-109">Called by `ICLRDataEnumMemoryRegions::EnumMemoryRegions` to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ab87f-110">要件</span><span class="sxs-lookup"><span data-stu-id="ab87f-110">Requirements</span></span>  

 <span data-ttu-id="ab87f-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab87f-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab87f-112">**ヘッダー:** ClrData .idl, ClrData .h</span><span class="sxs-lookup"><span data-stu-id="ab87f-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="ab87f-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab87f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab87f-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab87f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab87f-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="ab87f-115">See also</span></span>

- [<span data-ttu-id="ab87f-116">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="ab87f-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
