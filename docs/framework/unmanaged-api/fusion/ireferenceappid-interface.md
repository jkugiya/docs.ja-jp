---
description: 詳細については、「IReferenceAppId インターフェイス」を参照してください。
title: IReferenceAppId インターフェイス
ms.date: 03/30/2017
api_name:
- IReferenceAppId
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IReferenceAppId
helpviewer_keywords:
- IReferenceAppId interface [.NET Framework fusion]
ms.assetid: 8eb9e565-f358-43ce-900e-a8f8a5aa6cfb
topic_type:
- apiref
ms.openlocfilehash: 66838d6ae66aa7de05d899e9fa980308718e2a38
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800072"
---
# <a name="ireferenceappid-interface"></a><span data-ttu-id="26261-103">IReferenceAppId インターフェイス</span><span class="sxs-lookup"><span data-stu-id="26261-103">IReferenceAppId Interface</span></span>

<span data-ttu-id="26261-104">現在のスコープ内のアプリケーションの一意の識別子への参照を表します。</span><span class="sxs-lookup"><span data-stu-id="26261-104">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="26261-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="26261-105">Methods</span></span>  
  
|<span data-ttu-id="26261-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="26261-106">Method</span></span>|<span data-ttu-id="26261-107">説明</span><span class="sxs-lookup"><span data-stu-id="26261-107">Description</span></span>|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|<span data-ttu-id="26261-108">このによって参照されるアプリケーションのコード識別子の文字列形式へのポインターを取得し `IReferenceAppId` ます。</span><span class="sxs-lookup"><span data-stu-id="26261-108">Gets a pointer to a string representation of the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_CodeBase`|<span data-ttu-id="26261-109">このによって参照されるアプリケーションのコード識別子を設定し `IReferenceAppId` ます。</span><span class="sxs-lookup"><span data-stu-id="26261-109">Sets the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::EnumAppPath`|<span data-ttu-id="26261-110">`IEnumReferenceIdentity`こののメンバーを表すインスタンスを格納しているインスタンスへのインターフェイスポインターを取得し `IReferenceIdentity` `IReferenceAppId` ます。</span><span class="sxs-lookup"><span data-stu-id="26261-110">Gets an interface pointer to an `IEnumReferenceIdentity` instance containing the `IReferenceIdentity` instances that represent members of this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::get_SubscriptionId`|<span data-ttu-id="26261-111">このに対するサブスクリプションのトークン識別子の文字列形式へのポインターを取得し `IReferenceAppId` ます。</span><span class="sxs-lookup"><span data-stu-id="26261-111">Gets a pointer to a string representation of the token identifier for a subscription to this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_SubscriptionId`|<span data-ttu-id="26261-112">サブスクリプションのトークン識別子を `IReferenceAppId` 指定された文字列値に設定します。</span><span class="sxs-lookup"><span data-stu-id="26261-112">Sets the token identifier for a subscription to this `IReferenceAppId` to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="26261-113">要件</span><span class="sxs-lookup"><span data-stu-id="26261-113">Requirements</span></span>  

 <span data-ttu-id="26261-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="26261-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26261-115">**ヘッダー:** 分離 .h</span><span class="sxs-lookup"><span data-stu-id="26261-115">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="26261-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26261-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26261-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="26261-117">See also</span></span>

- [<span data-ttu-id="26261-118">Fusion インターフェイス</span><span class="sxs-lookup"><span data-stu-id="26261-118">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="26261-119">IEnumReferenceIdentity インターフェイス</span><span class="sxs-lookup"><span data-stu-id="26261-119">IEnumReferenceIdentity Interface</span></span>](ienumreferenceidentity-interface.md)
- [<span data-ttu-id="26261-120">IReferenceIdentity インターフェイス</span><span class="sxs-lookup"><span data-stu-id="26261-120">IReferenceIdentity Interface</span></span>](ireferenceidentity-interface.md)
