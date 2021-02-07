---
description: '詳細情報: CeeSectionRelocExtra Union'
title: CeeSectionRelocExtra 共用体
ms.date: 03/30/2017
api_name:
- CeeSectionRelocExtra Union
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CeeSectionRelocExtra
helpviewer_keywords:
- CeeSectionRelocExtra union [.NET Framework metadata]
ms.assetid: d9568cf6-7f98-4cd6-ab36-0a2bd509afcc
topic_type:
- apiref
ms.openlocfilehash: 40001c1a0772e24633f4232da8e7817f3747f8ea
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678849"
---
# <a name="ceesectionrelocextra-union"></a><span data-ttu-id="681a3-103">CeeSectionRelocExtra 共用体</span><span class="sxs-lookup"><span data-stu-id="681a3-103">CeeSectionRelocExtra Union</span></span>

<span data-ttu-id="681a3-104">セクションを再配置するために [ICeeGen](iceegen-interface.md) インターフェイスによって使用されるアドレスオフセットを表します。</span><span class="sxs-lookup"><span data-stu-id="681a3-104">Represents an address offset that is used by the [ICeeGen](iceegen-interface.md) interface to relocate a section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="681a3-105">構文</span><span class="sxs-lookup"><span data-stu-id="681a3-105">Syntax</span></span>  
  
```cpp  
typedef union  {  
    USHORT highAdj;  
} CeeSectionRelocExtra;  
```  
  
## <a name="members"></a><span data-ttu-id="681a3-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="681a3-106">Members</span></span>  
  
|<span data-ttu-id="681a3-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="681a3-107">Member</span></span>|<span data-ttu-id="681a3-108">説明</span><span class="sxs-lookup"><span data-stu-id="681a3-108">Description</span></span>|  
|------------|-----------------|  
|`highAdj`|<span data-ttu-id="681a3-109">セクションの上限アドレスの調整。</span><span class="sxs-lookup"><span data-stu-id="681a3-109">The upper address adjustment for the section.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="681a3-110">要件</span><span class="sxs-lookup"><span data-stu-id="681a3-110">Requirements</span></span>  

 <span data-ttu-id="681a3-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="681a3-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="681a3-112">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="681a3-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="681a3-113">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="681a3-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="681a3-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="681a3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="681a3-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="681a3-115">See also</span></span>

- [<span data-ttu-id="681a3-116">メタデータ共用体</span><span class="sxs-lookup"><span data-stu-id="681a3-116">Metadata Unions</span></span>](metadata-unions.md)
