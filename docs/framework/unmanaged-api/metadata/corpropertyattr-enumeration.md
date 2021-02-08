---
description: 詳細については、「CorPropertyAttr 列挙型」を参照してください。
title: CorPropertyAttr 列挙型
ms.date: 03/30/2017
api_name:
- CorPropertyAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPropertyAttr
helpviewer_keywords:
- CorPropertyAttr enumeration [.NET Framework metadata]
ms.assetid: 58ac8202-854d-4efd-acfb-d2da8b446e12
topic_type:
- apiref
ms.openlocfilehash: 1f3e2fccb11a067c6c46350a2c36d47007875755
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784237"
---
# <a name="corpropertyattr-enumeration"></a><span data-ttu-id="b19fa-103">CorPropertyAttr 列挙型</span><span class="sxs-lookup"><span data-stu-id="b19fa-103">CorPropertyAttr Enumeration</span></span>

<span data-ttu-id="b19fa-104">プロパティのメタデータを記述する値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="b19fa-104">Contains values that describe the metadata of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b19fa-105">構文</span><span class="sxs-lookup"><span data-stu-id="b19fa-105">Syntax</span></span>  
  
```cpp  
typedef enum CorPropertyAttr {  
  
    prSpecialName           =   0x0200,
    prReservedMask          =   0xf400,  
    prRTSpecialName         =   0x0400,  
    prHasDefault            =   0x1000,  
    prUnused                =   0xe9ff  
  
} CorPropertyAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="b19fa-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="b19fa-106">Members</span></span>  
  
|<span data-ttu-id="b19fa-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="b19fa-107">Member</span></span>|<span data-ttu-id="b19fa-108">説明</span><span class="sxs-lookup"><span data-stu-id="b19fa-108">Description</span></span>|  
|------------|-----------------|  
|`prSpecialName`|<span data-ttu-id="b19fa-109">プロパティが特別であり、その名前がどのように説明するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b19fa-109">Specifies that the property is special, and that its name describes how.</span></span>|  
|`prReservedMask`|<span data-ttu-id="b19fa-110">共通言語ランタイムによる内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="b19fa-110">Reserved for internal use by the common language runtime.</span></span>|  
|`prRTSpecialName`|<span data-ttu-id="b19fa-111">共通言語ランタイムメタデータの内部 Api がプロパティ名のエンコーディングを確認する必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="b19fa-111">Specifies that the common language runtime metadata internal APIs should check the encoding of the property name.</span></span>|  
|`prHasDefault`|<span data-ttu-id="b19fa-112">プロパティが既定値を持つことを指定します。</span><span class="sxs-lookup"><span data-stu-id="b19fa-112">Specifies that the property has a default value.</span></span>|  
|`prUnused`|<span data-ttu-id="b19fa-113">未使用。</span><span class="sxs-lookup"><span data-stu-id="b19fa-113">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b19fa-114">要件</span><span class="sxs-lookup"><span data-stu-id="b19fa-114">Requirements</span></span>  

 <span data-ttu-id="b19fa-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b19fa-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b19fa-116">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="b19fa-116">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="b19fa-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b19fa-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b19fa-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="b19fa-118">See also</span></span>

- [<span data-ttu-id="b19fa-119">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="b19fa-119">Metadata Enumerations</span></span>](metadata-enumerations.md)
