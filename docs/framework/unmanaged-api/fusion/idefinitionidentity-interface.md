---
description: 詳細については、「IDefinitionIdentity インターフェイス」を参照してください。
title: IDefinitionIdentity インターフェイス
ms.date: 03/30/2017
api_name:
- IDefinitionIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDefinitionIdentity
helpviewer_keywords:
- IDefinitionIdentity interface [.NET Framework fusion]
ms.assetid: ce5ba888-5fbe-4efd-91cf-f0ff94d8428b
topic_type:
- apiref
ms.openlocfilehash: 3471879cc822b655b786dd9d8234950cb4b99c1d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760655"
---
# <a name="idefinitionidentity-interface"></a><span data-ttu-id="01eb2-103">IDefinitionIdentity インターフェイス</span><span class="sxs-lookup"><span data-stu-id="01eb2-103">IDefinitionIdentity Interface</span></span>

<span data-ttu-id="01eb2-104">現在のスコープ内のアプリケーションを定義するコードの一意の署名を表します。</span><span class="sxs-lookup"><span data-stu-id="01eb2-104">Represents the unique signature of the code that defines the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="01eb2-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="01eb2-105">Methods</span></span>  
  
|<span data-ttu-id="01eb2-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="01eb2-106">Method</span></span>|<span data-ttu-id="01eb2-107">説明</span><span class="sxs-lookup"><span data-stu-id="01eb2-107">Description</span></span>|  
|------------|-----------------|  
|`IDefinitionIdentity::Clone`|<span data-ttu-id="01eb2-108">`IDefinitionIdentity` `IDefinitionIdentity` 指定した属性の変更を除き、このと同一の新しいオブジェクトへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="01eb2-108">Gets an interface pointer to a new `IDefinitionIdentity` object that is identical to this `IDefinitionIdentity`, except for the specified attribute changes.</span></span>|  
|`IDefinitionIdentity::EnumAttributes`|<span data-ttu-id="01eb2-109">このに関連付けられている属性を格納している [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md) オブジェクトへのインターフェイスポインターを取得し `IDefinitionIdentity` ます。</span><span class="sxs-lookup"><span data-stu-id="01eb2-109">Gets an interface pointer to an [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md) object that contains the attributes associated with this `IDefinitionIdentity`.</span></span>|  
|`IDefinitionIdentity::GetAttribute`|<span data-ttu-id="01eb2-110">指定した名前空間内の指定した名前の属性の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="01eb2-110">Gets the value of the attribute with the specified name in the specified namespace.</span></span>|  
|`IDefinitionIdentity::SetAttribute`|<span data-ttu-id="01eb2-111">指定した名前空間の指定した名前を持つ属性を、指定した値に設定します。</span><span class="sxs-lookup"><span data-stu-id="01eb2-111">Sets the attribute that has the specified name in the specified namespace to the specified value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="01eb2-112">要件</span><span class="sxs-lookup"><span data-stu-id="01eb2-112">Requirements</span></span>  

 <span data-ttu-id="01eb2-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="01eb2-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01eb2-114">**ヘッダー:** 分離 .h</span><span class="sxs-lookup"><span data-stu-id="01eb2-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="01eb2-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01eb2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01eb2-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="01eb2-116">See also</span></span>

- [<span data-ttu-id="01eb2-117">Fusion インターフェイス</span><span class="sxs-lookup"><span data-stu-id="01eb2-117">Fusion Interfaces</span></span>](fusion-interfaces.md)
