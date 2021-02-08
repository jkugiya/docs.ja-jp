---
description: 詳細については、「CorLocalRefPreservation 列挙型」を参照してください。
title: CorLocalRefPreservation 列挙型
ms.date: 03/30/2017
api_name:
- CorLocalRefPreservation
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorLocalRefPreservation
helpviewer_keywords:
- CorLocalRefPreservation enumeration [.NET Framework metadata]
ms.assetid: 44757163-1228-4213-a4c4-d4de503cc75d
topic_type:
- apiref
ms.openlocfilehash: afcdf6ce22c5f786e8f728cc1e45ad3ca44e7ef5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784419"
---
# <a name="corlocalrefpreservation-enumeration"></a><span data-ttu-id="a0d3f-103">CorLocalRefPreservation 列挙型</span><span class="sxs-lookup"><span data-stu-id="a0d3f-103">CorLocalRefPreservation Enumeration</span></span>

<span data-ttu-id="a0d3f-104">ローカル参照の処理のためのフラグ値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="a0d3f-104">Contains flag values for the treatment of local references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0d3f-105">構文</span><span class="sxs-lookup"><span data-stu-id="a0d3f-105">Syntax</span></span>  
  
```cpp  
typedef enum CorLocalRefPreservation  
{  
    MDPreserveLocalRefsNone     =   0x00000000,  
    MDPreserveLocalTypeRef      =   0x00000001,  
    MDPreserveLocalMemberRef    =   0x00000002  
} CorLocalRefPreservation;  
```  
  
## <a name="members"></a><span data-ttu-id="a0d3f-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="a0d3f-106">Members</span></span>  
  
|<span data-ttu-id="a0d3f-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="a0d3f-107">Member</span></span>|<span data-ttu-id="a0d3f-108">説明</span><span class="sxs-lookup"><span data-stu-id="a0d3f-108">Description</span></span>|  
|------------|-----------------|  
|`MDPreserveLocalRefsNone`|<span data-ttu-id="a0d3f-109">ローカル参照を保持しません。</span><span class="sxs-lookup"><span data-stu-id="a0d3f-109">Preserve no local references.</span></span>|  
|`MDPreserveLocalTypeRef`|<span data-ttu-id="a0d3f-110">ローカル型参照を保持します。</span><span class="sxs-lookup"><span data-stu-id="a0d3f-110">Preserve local type references.</span></span>|  
|`MDPreserveLocalMemberRef`|<span data-ttu-id="a0d3f-111">ローカルメンバー参照を保持します。</span><span class="sxs-lookup"><span data-stu-id="a0d3f-111">Preserve local member references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a0d3f-112">要件</span><span class="sxs-lookup"><span data-stu-id="a0d3f-112">Requirements</span></span>  

 <span data-ttu-id="a0d3f-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a0d3f-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0d3f-114">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="a0d3f-114">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="a0d3f-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0d3f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0d3f-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="a0d3f-116">See also</span></span>

- [<span data-ttu-id="a0d3f-117">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="a0d3f-117">Metadata Enumerations</span></span>](metadata-enumerations.md)
