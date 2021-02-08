---
description: '詳細については、次を参照してください: CorNativeLinkType 列挙型'
title: CorNativeLinkType 列挙型
ms.date: 03/30/2017
api_name:
- CorNativeLinkType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeLinkType
helpviewer_keywords:
- CorNativeLinkType enumeration [.NET Framework metadata]
ms.assetid: 4f86ff37-2dab-4e64-819a-76b3bfe828ff
topic_type:
- apiref
ms.openlocfilehash: 40efc75a793da8b024eff3d7c2c620123eca08b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784341"
---
# <a name="cornativelinktype-enumeration"></a><span data-ttu-id="c5283-103">CorNativeLinkType 列挙型</span><span class="sxs-lookup"><span data-stu-id="c5283-103">CorNativeLinkType Enumeration</span></span>

<span data-ttu-id="c5283-104">ネイティブ コード内のリンクの種類を示す値を提供します。</span><span class="sxs-lookup"><span data-stu-id="c5283-104">Provides values that indicate the type linked in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5283-105">構文</span><span class="sxs-lookup"><span data-stu-id="c5283-105">Syntax</span></span>  
  
```cpp  
typedef enum
{  
    nltNone       = 1,  
    nltAnsi       = 2,  
    nltUnicode    = 3,  
    nltAuto       = 4,  
    nltOle        = 5,  
    nltMaxValue   = 7  
} CorNativeLinkType;  
```  
  
## <a name="members"></a><span data-ttu-id="c5283-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="c5283-106">Members</span></span>  
  
|<span data-ttu-id="c5283-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="c5283-107">Member</span></span>|<span data-ttu-id="c5283-108">説明</span><span class="sxs-lookup"><span data-stu-id="c5283-108">Description</span></span>|  
|------------|-----------------|  
|`nltNone`|<span data-ttu-id="c5283-109">キーワードが指定されていないことを示します。</span><span class="sxs-lookup"><span data-stu-id="c5283-109">Indicates that none of the keywords are specified.</span></span>|  
|`nltAnsi`|<span data-ttu-id="c5283-110">ANSI キーワードが指定されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="c5283-110">Indicates that an ANSI keyword is specified.</span></span>|  
|`nltUnicode`|<span data-ttu-id="c5283-111">Unicode キーワードが指定されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="c5283-111">Indicates that a Unicode keyword is specified</span></span>|  
|`nltAuto`|<span data-ttu-id="c5283-112">Auto キーワードが指定されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="c5283-112">Indicates that an auto keyword is specified.</span></span>|  
|`nltOle`|<span data-ttu-id="c5283-113">OLE キーワードが指定されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="c5283-113">Indicates that an OLE keyword is specified.</span></span>|  
|`nltMaxValue`|<span data-ttu-id="c5283-114">使用されていません。</span><span class="sxs-lookup"><span data-stu-id="c5283-114">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c5283-115">要件</span><span class="sxs-lookup"><span data-stu-id="c5283-115">Requirements</span></span>  

 <span data-ttu-id="c5283-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5283-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5283-117">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="c5283-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c5283-118">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="c5283-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c5283-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5283-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5283-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="c5283-120">See also</span></span>

- [<span data-ttu-id="c5283-121">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="c5283-121">Metadata Enumerations</span></span>](metadata-enumerations.md)
