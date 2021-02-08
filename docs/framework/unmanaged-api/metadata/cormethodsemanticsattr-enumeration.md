---
description: '詳細については、次を参照してください: CorMethodSemanticsAttr 列挙型'
title: CorMethodSemanticsAttr 列挙型
ms.date: 03/30/2017
api_name:
- CorMethodSemanticsAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodSemanticsAttr
helpviewer_keywords:
- CorMethodSemanticsAttr enumeration [.NET Framework metadata]
ms.assetid: ca2af325-eb9d-4a91-90e4-267e45b98611
topic_type:
- apiref
ms.openlocfilehash: 4079e81ae2389ff0684fd11d0751b191a7289932
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784367"
---
# <a name="cormethodsemanticsattr-enumeration"></a><span data-ttu-id="64610-103">CorMethodSemanticsAttr 列挙型</span><span class="sxs-lookup"><span data-stu-id="64610-103">CorMethodSemanticsAttr Enumeration</span></span>

<span data-ttu-id="64610-104">メソッドとそれに関連付けられているプロパティまたはイベントとの関係を記述する値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="64610-104">Contains values that describe the relationship between a method and an associated property or event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64610-105">構文</span><span class="sxs-lookup"><span data-stu-id="64610-105">Syntax</span></span>  
  
```cpp  
typedef enum CorMethodSemanticsAttr {  
  
    msSetter    =   0x0001,  
    msGetter    =   0x0002,  
    msOther     =   0x0004,  
    msAddOn     =   0x0008,  
    msRemoveOn  =   0x0010,  
    msFire      =   0x0020,  
  
} CorMethodSemanticsAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="64610-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="64610-106">Members</span></span>  
  
|<span data-ttu-id="64610-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="64610-107">Member</span></span>|<span data-ttu-id="64610-108">説明</span><span class="sxs-lookup"><span data-stu-id="64610-108">Description</span></span>|  
|------------|-----------------|  
|`msSetter`|<span data-ttu-id="64610-109">メソッドがプロパティのアクセサーであることを指定し `set` ます。</span><span class="sxs-lookup"><span data-stu-id="64610-109">Specifies that the method is a `set` accessor for a property.</span></span>|  
|`msGetter`|<span data-ttu-id="64610-110">メソッドがプロパティのアクセサーであることを指定し `get` ます。</span><span class="sxs-lookup"><span data-stu-id="64610-110">Specifies that the method is a `get` accessor for a property.</span></span>|  
|`msOther`|<span data-ttu-id="64610-111">メソッドが、ここで定義されたプロパティ以外のプロパティまたはイベントへのリレーションシップを持つことを指定します。</span><span class="sxs-lookup"><span data-stu-id="64610-111">Specifies that the method has a relationship to a property or an event other than those defined here.</span></span>|  
|`msAddOn`|<span data-ttu-id="64610-112">メソッドがイベントのハンドラーメソッドを追加することを指定します。</span><span class="sxs-lookup"><span data-stu-id="64610-112">Specifies that the method adds handler methods for an event.</span></span>|  
|`msRemoveOn`|<span data-ttu-id="64610-113">メソッドがイベントのハンドラーメソッドを削除することを指定します。</span><span class="sxs-lookup"><span data-stu-id="64610-113">Specifies that the method removes handler methods for an event.</span></span>|  
|`msFire`|<span data-ttu-id="64610-114">メソッドがイベントを発生させることを指定します。</span><span class="sxs-lookup"><span data-stu-id="64610-114">Specifies that the method raises an event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="64610-115">要件</span><span class="sxs-lookup"><span data-stu-id="64610-115">Requirements</span></span>  

 <span data-ttu-id="64610-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="64610-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64610-117">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="64610-117">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="64610-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64610-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64610-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="64610-119">See also</span></span>

- [<span data-ttu-id="64610-120">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="64610-120">Metadata Enumerations</span></span>](metadata-enumerations.md)
