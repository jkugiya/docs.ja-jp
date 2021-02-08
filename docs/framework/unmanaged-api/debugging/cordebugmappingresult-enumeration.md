---
description: 詳細については、「CorDebugMappingResult 列挙型」を参照してください。
title: CorDebugMappingResult 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugMappingResult
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugMappingResult
helpviewer_keywords:
- CorDebugMappingResult enumeration [.NET Framework debugging]
ms.assetid: 701281dd-2936-45c8-a1f0-3bf7332b093b
topic_type:
- apiref
ms.openlocfilehash: 03454e2fbfa8fabca89805ea51a6cfba27aa792f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801593"
---
# <a name="cordebugmappingresult-enumeration"></a><span data-ttu-id="78cd9-103">CorDebugMappingResult 列挙型</span><span class="sxs-lookup"><span data-stu-id="78cd9-103">CorDebugMappingResult Enumeration</span></span>

<span data-ttu-id="78cd9-104">命令ポインター (IP) の値が得られた方法の詳細を提供します。</span><span class="sxs-lookup"><span data-stu-id="78cd9-104">Provides the details of how the value of the instruction pointer (IP) was obtained.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78cd9-105">構文</span><span class="sxs-lookup"><span data-stu-id="78cd9-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugMappingResult {  
    MAPPING_PROLOG              = 0x1,  
    MAPPING_EPILOG              = 0x2,  
    MAPPING_NO_INFO             = 0x4,  
    MAPPING_UNMAPPED_ADDRESS    = 0x8,  
    MAPPING_EXACT               = 0x10,  
    MAPPING_APPROXIMATE         = 0x20,  
} CorDebugMappingResult;  
```  
  
## <a name="members"></a><span data-ttu-id="78cd9-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="78cd9-106">Members</span></span>  
  
|<span data-ttu-id="78cd9-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="78cd9-107">Member</span></span>|<span data-ttu-id="78cd9-108">説明</span><span class="sxs-lookup"><span data-stu-id="78cd9-108">Description</span></span>|  
|------------|-----------------|  
|`MAPPING_PROLOG`|<span data-ttu-id="78cd9-109">ネイティブコードはプロローグ内にあるため、IP の値は0です。</span><span class="sxs-lookup"><span data-stu-id="78cd9-109">The native code is in the prolog, so the value of the IP is 0.</span></span>|  
|`MAPPING_EPILOG`|<span data-ttu-id="78cd9-110">ネイティブコードはエピローグ内にあるため、IP の値はメソッドの最後の命令のアドレスになります。</span><span class="sxs-lookup"><span data-stu-id="78cd9-110">The native code is in an epilog, so the value of the IP is the address of the last instruction of the method.</span></span>|  
|`MAPPING_NO_INFO`|<span data-ttu-id="78cd9-111">メソッドに使用できるマッピング情報がないため、IP の値は0になります。</span><span class="sxs-lookup"><span data-stu-id="78cd9-111">No mapping information is available for the method, so the value of the IP is 0.</span></span>|  
|`MAPPING_UNMAPPED_ADDRESS`|<span data-ttu-id="78cd9-112">メソッドのマッピング情報は存在しますが、現在のアドレスを MSIL (Microsoft 中間言語) コードにマップすることはできません。</span><span class="sxs-lookup"><span data-stu-id="78cd9-112">Although there is mapping information for the method, the current address cannot be mapped to Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="78cd9-113">IP の値は0です。</span><span class="sxs-lookup"><span data-stu-id="78cd9-113">The value of the IP is 0.</span></span>|  
|`MAPPING_EXACT`|<span data-ttu-id="78cd9-114">メソッドが MSIL コードに厳密にマップされているか、フレームが解釈されているため、IP の値は正確です。</span><span class="sxs-lookup"><span data-stu-id="78cd9-114">Either the method maps exactly to MSIL code or the frame has been interpreted, so the value of the IP is accurate.</span></span>|  
|`MAPPING_APPROXIMATE`|<span data-ttu-id="78cd9-115">メソッドは正常にマップされましたが、IP の値は概数である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="78cd9-115">The method was successfully mapped, but the value of the IP may be approximate.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78cd9-116">解説</span><span class="sxs-lookup"><span data-stu-id="78cd9-116">Remarks</span></span>  

 <span data-ttu-id="78cd9-117">指示ポインターの値を取得するには、「ツール」を [使用します](icordebugilframe-getip-method.md) 。</span><span class="sxs-lookup"><span data-stu-id="78cd9-117">You can use the [ICorDebugILFrame::GetIP](icordebugilframe-getip-method.md) method to obtain the value of the instruction pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78cd9-118">要件</span><span class="sxs-lookup"><span data-stu-id="78cd9-118">Requirements</span></span>  

 <span data-ttu-id="78cd9-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78cd9-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78cd9-120">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="78cd9-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="78cd9-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="78cd9-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78cd9-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78cd9-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78cd9-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="78cd9-123">See also</span></span>

- [<span data-ttu-id="78cd9-124">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="78cd9-124">Debugging Enumerations</span></span>](debugging-enumerations.md)
