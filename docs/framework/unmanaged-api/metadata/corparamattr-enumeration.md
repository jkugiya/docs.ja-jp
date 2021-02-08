---
description: 詳細については、「CorParamAttr 列挙型」を参照してください。
title: CorParamAttr 列挙型
ms.date: 03/30/2017
api_name:
- CorParamAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorParamAttr
helpviewer_keywords:
- CorParamAttr enumeration [.NET Framework metadata]
ms.assetid: a7ff90ad-dad8-48e8-917d-4aa9a118cbc8
topic_type:
- apiref
ms.openlocfilehash: c07569d3fb92b20a7985dbfeb2205af727866051
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784289"
---
# <a name="corparamattr-enumeration"></a><span data-ttu-id="59918-103">CorParamAttr 列挙型</span><span class="sxs-lookup"><span data-stu-id="59918-103">CorParamAttr Enumeration</span></span>

<span data-ttu-id="59918-104">メソッド パラメーターのメタデータを記述する値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="59918-104">Contains values that describe the metadata of a method parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59918-105">構文</span><span class="sxs-lookup"><span data-stu-id="59918-105">Syntax</span></span>  
  
```cpp  
typedef enum CorParamAttr {  
  
    pdIn                        =   0x0001,  
    pdOut                       =   0x0002,  
    pdOptional                  =   0x0010,  
  
    pdReservedMask              =   0xf000,  
    pdHasDefault                =   0x1000,  
    pdHasFieldMarshal           =   0x2000,  
  
    pdUnused                    =   0xcfe0  
  
} CorParamAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="59918-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="59918-106">Members</span></span>  
  
|<span data-ttu-id="59918-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="59918-107">Member</span></span>|<span data-ttu-id="59918-108">説明</span><span class="sxs-lookup"><span data-stu-id="59918-108">Description</span></span>|  
|------------|-----------------|  
|`pdIn`|<span data-ttu-id="59918-109">パラメーターがメソッドの呼び出しに渡されることを指定します。</span><span class="sxs-lookup"><span data-stu-id="59918-109">Specifies that the parameter is passed into the method call.</span></span>|  
|`pdOut`|<span data-ttu-id="59918-110">パラメーターがメソッドの戻り値から渡されることを指定します。</span><span class="sxs-lookup"><span data-stu-id="59918-110">Specifies that the parameter is passed from the method return.</span></span>|  
|`pdOptional`|<span data-ttu-id="59918-111">パラメーターが省略可能であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="59918-111">Specifies that the parameter is optional.</span></span>|  
|`pdReservedMask`|<span data-ttu-id="59918-112">共通言語ランタイムによる内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="59918-112">Reserved for internal use by the common language runtime.</span></span>|  
|`pdHasDefault`|<span data-ttu-id="59918-113">パラメーターが既定の値を使用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="59918-113">Specifies that the parameter has a default value.</span></span>|  
|`pdHasFieldMarshal`|<span data-ttu-id="59918-114">パラメーターにマーシャリング情報があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="59918-114">Specifies that the parameter has marshaling information.</span></span>|  
|`pdUnused`|<span data-ttu-id="59918-115">未使用。</span><span class="sxs-lookup"><span data-stu-id="59918-115">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="59918-116">要件</span><span class="sxs-lookup"><span data-stu-id="59918-116">Requirements</span></span>  

 <span data-ttu-id="59918-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="59918-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59918-118">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="59918-118">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="59918-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59918-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59918-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="59918-120">See also</span></span>

- [<span data-ttu-id="59918-121">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="59918-121">Metadata Enumerations</span></span>](metadata-enumerations.md)
