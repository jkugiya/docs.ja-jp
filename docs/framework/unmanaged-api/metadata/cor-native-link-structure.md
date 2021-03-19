---
description: '詳細情報: COR_NATIVE_LINK 構造'
title: COR_NATIVE_LINK 構造体
ms.date: 03/30/2017
api_name:
- COR_NATIVE_LINK
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_NATIVE_LINK
helpviewer_keywords:
- COR_NATIVE_LINK structure [.NET Framework metadata]
ms.assetid: 6ef78d3c-1c69-4141-b687-dcb065b7a74d
topic_type:
- apiref
ms.openlocfilehash: 09c715af698a0614fd4a9a17679df6908a1497a6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678576"
---
# <a name="cor_native_link-structure"></a><span data-ttu-id="75578-103">COR_NATIVE_LINK 構造体</span><span class="sxs-lookup"><span data-stu-id="75578-103">COR_NATIVE_LINK Structure</span></span>

<span data-ttu-id="75578-104">ネイティブ コードのリンクに使用される情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="75578-104">Contains information that is used to link native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75578-105">構文</span><span class="sxs-lookup"><span data-stu-id="75578-105">Syntax</span></span>  
  
```cpp  
typedef struct
{  
    BYTE        m_linkType;  
    BYTE        m_flags;  
    mdMemberRef m_entryPoint;  
} COR_NATIVE_LINK;  
```  
  
## <a name="members"></a><span data-ttu-id="75578-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="75578-106">Members</span></span>  
  
|<span data-ttu-id="75578-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="75578-107">Member</span></span>|<span data-ttu-id="75578-108">説明</span><span class="sxs-lookup"><span data-stu-id="75578-108">Description</span></span>|  
|------------|-----------------|  
|`m_linkType`|<span data-ttu-id="75578-109">ネイティブコードでリンクされる型。</span><span class="sxs-lookup"><span data-stu-id="75578-109">The type to be linked in native code.</span></span> <span data-ttu-id="75578-110">この値は、 [CorNativeLinkType](cornativelinktype-enumeration.md) 値の1つです。</span><span class="sxs-lookup"><span data-stu-id="75578-110">This value is one of the [CorNativeLinkType](cornativelinktype-enumeration.md) values.</span></span>|  
|`m_flags`|<span data-ttu-id="75578-111">ネイティブコードをリンクするときにリンカーによって使用されるフラグ。</span><span class="sxs-lookup"><span data-stu-id="75578-111">Flags used by the linker when linking native code.</span></span> <span data-ttu-id="75578-112">この値は、 [CorNativeLinkFlags](cornativelinkflags-enumeration.md) 値の1つです。</span><span class="sxs-lookup"><span data-stu-id="75578-112">This value is one of the [CorNativeLinkFlags](cornativelinkflags-enumeration.md) values.</span></span>|  
|`m_entryPoint`|<span data-ttu-id="75578-113">エントリポイントを表す MemberRef メタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="75578-113">The MemberRef metadata token that represents the entry point.</span></span> <span data-ttu-id="75578-114">形式は `lib:entrypoint` です。</span><span class="sxs-lookup"><span data-stu-id="75578-114">The format is `lib:entrypoint`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="75578-115">要件</span><span class="sxs-lookup"><span data-stu-id="75578-115">Requirements</span></span>  

 <span data-ttu-id="75578-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="75578-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75578-117">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="75578-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="75578-118">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="75578-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="75578-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75578-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75578-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="75578-120">See also</span></span>

- [<span data-ttu-id="75578-121">メタデータ構造体</span><span class="sxs-lookup"><span data-stu-id="75578-121">Metadata Structures</span></span>](metadata-structures.md)
- [<span data-ttu-id="75578-122">CorNativeLinkType 列挙型</span><span class="sxs-lookup"><span data-stu-id="75578-122">CorNativeLinkType Enumeration</span></span>](cornativelinktype-enumeration.md)
- [<span data-ttu-id="75578-123">CorNativeLinkFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="75578-123">CorNativeLinkFlags Enumeration</span></span>](cornativelinkflags-enumeration.md)
