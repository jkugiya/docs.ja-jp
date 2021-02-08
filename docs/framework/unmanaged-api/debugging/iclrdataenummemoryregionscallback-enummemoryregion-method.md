---
description: '詳細について: ICLRDataEnumMemoryRegionsCallback:: EnumMemoryRegion メソッド'
title: ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion メソッド
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegionsCallback.EnumMemoryRegion
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion
helpviewer_keywords:
- EnumMemoryRegion method [.NET Framework debugging]
- ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion method [.NET Framework debugging]
ms.assetid: 9bb93fab-57e8-4f9a-9ef3-1794504fa896
topic_type:
- apiref
ms.openlocfilehash: 733911f71898ea7019a0b8d854fb1c1bf61a2474
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801398"
---
# <a name="iclrdataenummemoryregionscallbackenummemoryregion-method"></a><span data-ttu-id="2de86-103">ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion メソッド</span><span class="sxs-lookup"><span data-stu-id="2de86-103">ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion Method</span></span>

<span data-ttu-id="2de86-104">指定されたメモリ領域を列挙しようとした結果をデバッガーに報告するために、 [ICLRDataEnumMemoryRegions:: EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="2de86-104">Called by [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2de86-105">構文</span><span class="sxs-lookup"><span data-stu-id="2de86-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemoryRegion (  
    [in] CLRDATA_ADDRESS  address,  
    [in] ULONG32          size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2de86-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2de86-106">Parameters</span></span>  

 `address`  
 <span data-ttu-id="2de86-107">から列挙されたメモリ領域の開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="2de86-107">[in] The starting address of the memory region that was to be enumerated.</span></span>  
  
 `size`  
 <span data-ttu-id="2de86-108">からメモリ領域のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="2de86-108">[in] The size, in bytes, of the memory region.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2de86-109">解説</span><span class="sxs-lookup"><span data-stu-id="2de86-109">Remarks</span></span>  

 <span data-ttu-id="2de86-110">メソッドは、 `ICLRDataEnumMemoryRegions::EnumMemoryRegions` メモリ領域を列挙するたびに、このコールバックメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2de86-110">The `ICLRDataEnumMemoryRegions::EnumMemoryRegions` method will call this callback method after each attempt to enumerate a memory region.</span></span> <span data-ttu-id="2de86-111">このメソッドがエラーを示す HRESULT を返す場合でも、列挙は続行されます。</span><span class="sxs-lookup"><span data-stu-id="2de86-111">The enumeration will continue even if this method returns an HRESULT indicating failure.</span></span>  
  
 <span data-ttu-id="2de86-112">このコールバックによって報告されたリージョンが重複しているか、重複している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2de86-112">Regions reported by this callback may be duplicates or overlapping regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2de86-113">要件</span><span class="sxs-lookup"><span data-stu-id="2de86-113">Requirements</span></span>  

 <span data-ttu-id="2de86-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2de86-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2de86-115">**ヘッダー:** ClrData .idl, ClrData .h</span><span class="sxs-lookup"><span data-stu-id="2de86-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="2de86-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2de86-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2de86-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2de86-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2de86-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="2de86-118">See also</span></span>

- [<span data-ttu-id="2de86-119">ICLRDataEnumMemoryRegionsCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2de86-119">ICLRDataEnumMemoryRegionsCallback Interface</span></span>](iclrdataenummemoryregionscallback-interface.md)
