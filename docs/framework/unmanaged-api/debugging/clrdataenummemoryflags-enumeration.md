---
description: '詳細情報: CLRDataEnumMemoryFlags 列挙型'
title: CLRDataEnumMemoryFlags 列挙型
ms.date: 03/30/2017
api_name:
- CLRDataEnumMemoryFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLRDataEnumMemoryFlags
helpviewer_keywords:
- CLRDataEnumMemoryFlags enumeration [.NET Framework debugging]
ms.assetid: e249f9fc-e24a-4506-903c-92781f6eab7c
topic_type:
- apiref
ms.openlocfilehash: 3522649c59177de8295416ce260c374df605efb3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662248"
---
# <a name="clrdataenummemoryflags-enumeration"></a><span data-ttu-id="ecaeb-103">CLRDataEnumMemoryFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="ecaeb-103">CLRDataEnumMemoryFlags Enumeration</span></span>

<span data-ttu-id="ecaeb-104">[ICLRDataEnumMemoryRegions:: EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md)メソッドへの呼び出しに含まれるメモリ領域を示します。</span><span class="sxs-lookup"><span data-stu-id="ecaeb-104">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecaeb-105">構文</span><span class="sxs-lookup"><span data-stu-id="ecaeb-105">Syntax</span></span>  
  
```cpp  
typedef enum CLRDataEnumMemoryFlags {  
    CLRDATA_ENUM_MEM_DEFAULT  = 0x0,  
    CLRDATA_ENUM_MEM_MINI     = CLRDATA_ENUM_MEM_DEFAULT,  
    CLRDATA_ENUM_MEM_HEAP     = 0x1  
} CLRDataEnumMemoryFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="ecaeb-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="ecaeb-106">Members</span></span>  
  
|<span data-ttu-id="ecaeb-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="ecaeb-107">Member</span></span>|<span data-ttu-id="ecaeb-108">説明</span><span class="sxs-lookup"><span data-stu-id="ecaeb-108">Description</span></span>|  
|------------|-----------------|  
|`CLRDATA_ENUM_MEM_DEFAULT`|<span data-ttu-id="ecaeb-109">ミニダンプ (スパースメモリダンプ)。</span><span class="sxs-lookup"><span data-stu-id="ecaeb-109">A minidump, that is, a sparse memory dump.</span></span>|  
|`CLRDATA_ENUM_MEM_HEAP`|<span data-ttu-id="ecaeb-110">完全なヒープダンプ。</span><span class="sxs-lookup"><span data-stu-id="ecaeb-110">A full heap dump.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ecaeb-111">要件</span><span class="sxs-lookup"><span data-stu-id="ecaeb-111">Requirements</span></span>  

 <span data-ttu-id="ecaeb-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ecaeb-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecaeb-113">**ヘッダー:** ClrData .idl, ClrData .h</span><span class="sxs-lookup"><span data-stu-id="ecaeb-113">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="ecaeb-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ecaeb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ecaeb-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecaeb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecaeb-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="ecaeb-116">See also</span></span>

- [<span data-ttu-id="ecaeb-117">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="ecaeb-117">Debugging Enumerations</span></span>](debugging-enumerations.md)
