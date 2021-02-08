---
description: 詳細については、「CorRefToDefCheck 列挙型」を参照してください。
title: CorRefToDefCheck 列挙型
ms.date: 03/30/2017
api_name:
- CorRefToDefCheck
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRefToDefCheck
helpviewer_keywords:
- CorRefToDefCheck enumeration [.NET Framework metadata]
ms.assetid: f9a80f1a-55af-4459-b095-8441aae16119
topic_type:
- apiref
ms.openlocfilehash: ca9d1c7ceb3d9f82ef8d5f1f54d869db64053e69
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784250"
---
# <a name="correftodefcheck-enumeration"></a><span data-ttu-id="eed5e-103">CorRefToDefCheck 列挙型</span><span class="sxs-lookup"><span data-stu-id="eed5e-103">CorRefToDefCheck Enumeration</span></span>

<span data-ttu-id="eed5e-104">コードを最適化するために定義に変換される、参照先アイテムを制御するフラグを指定します。</span><span class="sxs-lookup"><span data-stu-id="eed5e-104">Specifies flags to control which referenced items are converted to their definitions in order to optimize the code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eed5e-105">構文</span><span class="sxs-lookup"><span data-stu-id="eed5e-105">Syntax</span></span>  
  
```cpp  
typedef enum CorRefToDefCheck {  
    MDRefToDefDefault           = 0x00000003,  
    MDRefToDefAll               = 0xffffffff,  
    MDRefToDefNone              = 0x00000000,  
    MDTypeRefToDef              = 0x00000001,  
    MDMemberRefToDef            = 0x00000002  
} CorRefToDefCheck;  
```  
  
## <a name="members"></a><span data-ttu-id="eed5e-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="eed5e-106">Members</span></span>  
  
|<span data-ttu-id="eed5e-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="eed5e-107">Member</span></span>|<span data-ttu-id="eed5e-108">説明</span><span class="sxs-lookup"><span data-stu-id="eed5e-108">Description</span></span>|  
|------------|-----------------|  
|`MDRefToDefDefault`|<span data-ttu-id="eed5e-109">型参照とメンバー参照を定義に変換する必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="eed5e-109">Specifies that type references and member references should be converted to definitions.</span></span> <span data-ttu-id="eed5e-110">これは既定値 ( `MDTypeRefToDef` &#124; `MDMemberRefToDef` ) です。</span><span class="sxs-lookup"><span data-stu-id="eed5e-110">This is the default value (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).</span></span>|  
|`MDRefToDefAll`|<span data-ttu-id="eed5e-111">参照されるすべての項目を定義に変換することを指定します。</span><span class="sxs-lookup"><span data-stu-id="eed5e-111">Specifies that all referenced items should be converted to definitions.</span></span>|  
|`MDRefToDefNone`|<span data-ttu-id="eed5e-112">参照される項目を定義に変換しないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="eed5e-112">Specifies that no referenced items should be converted to definitions.</span></span>|  
|`MDTypeRefToDef`|<span data-ttu-id="eed5e-113">型の参照のみを型定義に変換することを指定します。</span><span class="sxs-lookup"><span data-stu-id="eed5e-113">Specifies that only type references should be converted to type definitions.</span></span>|  
|`MDMemberRefToDef`|<span data-ttu-id="eed5e-114">メンバー参照のみを定義に変換することを指定します。</span><span class="sxs-lookup"><span data-stu-id="eed5e-114">Specifies that only member references should be converted to definitions.</span></span> <span data-ttu-id="eed5e-115">つまり、メンバー参照は、メソッド定義またはフィールド定義に変換される必要があります。</span><span class="sxs-lookup"><span data-stu-id="eed5e-115">That is, member references should be converted to either method definitions or field definitions.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="eed5e-116">要件</span><span class="sxs-lookup"><span data-stu-id="eed5e-116">Requirements</span></span>  

 <span data-ttu-id="eed5e-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eed5e-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eed5e-118">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="eed5e-118">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="eed5e-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eed5e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eed5e-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="eed5e-120">See also</span></span>

- [<span data-ttu-id="eed5e-121">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="eed5e-121">Metadata Enumerations</span></span>](metadata-enumerations.md)
