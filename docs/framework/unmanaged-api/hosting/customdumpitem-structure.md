---
description: '詳細情報: CustomDumpItem 構造体'
title: CustomDumpItem 構造体
ms.date: 03/30/2017
api_name:
- CustomDumpItem
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CustomDumpItem
helpviewer_keywords:
- CustomDumpItem structure [.NET Framework hosting]
ms.assetid: fd9085ff-7beb-4c38-97f0-037cd8ba4f65
topic_type:
- apiref
ms.openlocfilehash: 9bd7b2bb59675bc01e24dc6e6d0ce524f3d35466
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716901"
---
# <a name="customdumpitem-structure"></a><span data-ttu-id="c4d0c-103">CustomDumpItem 構造体</span><span class="sxs-lookup"><span data-stu-id="c4d0c-103">CustomDumpItem Structure</span></span>

<span data-ttu-id="c4d0c-104">エラー報告のカスタムダンプに追加するアイテムについて説明します。</span><span class="sxs-lookup"><span data-stu-id="c4d0c-104">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4d0c-105">構文</span><span class="sxs-lookup"><span data-stu-id="c4d0c-105">Syntax</span></span>  
  
```cpp  
struct {  
    ECustomDumpItemKind itemKind;
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a><span data-ttu-id="c4d0c-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="c4d0c-106">Members</span></span>  
  
|<span data-ttu-id="c4d0c-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="c4d0c-107">Member</span></span>|<span data-ttu-id="c4d0c-108">説明</span><span class="sxs-lookup"><span data-stu-id="c4d0c-108">Description</span></span>|  
|------------|-----------------|  
|`itemKind`|<span data-ttu-id="c4d0c-109">追加する項目の種類を示す [ECustomDumpItemKind](ecustomdumpitemkind-enumeration.md) 値。</span><span class="sxs-lookup"><span data-stu-id="c4d0c-109">An [ECustomDumpItemKind](ecustomdumpitemkind-enumeration.md) value that indicates the kind of item to be added.</span></span>|  
|`pReserved`|<span data-ttu-id="c4d0c-110">現在は使用しません。</span><span class="sxs-lookup"><span data-stu-id="c4d0c-110">Not currently used.</span></span> <span data-ttu-id="c4d0c-111">共用体に追加された項目は、ポインターサイズ以下である必要があります。</span><span class="sxs-lookup"><span data-stu-id="c4d0c-111">Any items added to the union must be no larger than pointer size.</span></span> <span data-ttu-id="c4d0c-112">`struct`が必要な場合は、それを個別に割り当てて、それをポイントする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c4d0c-112">If a `struct` is required, you must allocate it separately and point to it.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4d0c-113">解説</span><span class="sxs-lookup"><span data-stu-id="c4d0c-113">Remarks</span></span>  

 <span data-ttu-id="c4d0c-114">[ICLRErrorReportingManager:: BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) は、型のパラメーターを受け取り `CustomDumpItem` ます。</span><span class="sxs-lookup"><span data-stu-id="c4d0c-114">[ICLRErrorReportingManager::BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) takes a parameter of type `CustomDumpItem`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4d0c-115">要件</span><span class="sxs-lookup"><span data-stu-id="c4d0c-115">Requirements</span></span>  

 <span data-ttu-id="c4d0c-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4d0c-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4d0c-117">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="c4d0c-117">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="c4d0c-118">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="c4d0c-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c4d0c-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4d0c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4d0c-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="c4d0c-120">See also</span></span>

- [<span data-ttu-id="c4d0c-121">ホスト構造体</span><span class="sxs-lookup"><span data-stu-id="c4d0c-121">Hosting Structures</span></span>](hosting-structures.md)
