---
description: 詳細については、「IDefinitionAppId インターフェイス」を参照してください。
title: IDefinitionAppId インターフェイス
ms.date: 03/30/2017
api_name:
- IDefinitionAppId
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDefinitionAppId
helpviewer_keywords:
- IDefinitionAppId interface [.NET Framework fusion]
ms.assetid: e72f2550-bdec-4a20-a2f4-2e14847266c1
topic_type:
- apiref
ms.openlocfilehash: 3c68044e7e747521e190fad404e89d6d0a994611
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760668"
---
# <a name="idefinitionappid-interface"></a><span data-ttu-id="c8fe1-103">IDefinitionAppId インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c8fe1-103">IDefinitionAppId Interface</span></span>

<span data-ttu-id="c8fe1-104">現在のスコープ内のアプリケーションを定義するコードの一意の識別子を表します。</span><span class="sxs-lookup"><span data-stu-id="c8fe1-104">Represents a unique identifier for the code that defines the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c8fe1-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="c8fe1-105">Methods</span></span>  
  
|<span data-ttu-id="c8fe1-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="c8fe1-106">Method</span></span>|<span data-ttu-id="c8fe1-107">説明</span><span class="sxs-lookup"><span data-stu-id="c8fe1-107">Description</span></span>|  
|------------|-----------------|  
|`IDefinitionAppId::get_Codebase`|<span data-ttu-id="c8fe1-108">このオブジェクトのコードを表す書式設定された文字列を取得し `IDefinitionAppId` ます。</span><span class="sxs-lookup"><span data-stu-id="c8fe1-108">Gets a formatted string that represents the code in this `IDefinitionAppId` object.</span></span>|  
|`IDefinitionAppId::put_Codebase`|<span data-ttu-id="c8fe1-109">このオブジェクトのコード `IDefinitionAppId` を、指定した書式設定された文字列値に設定します。</span><span class="sxs-lookup"><span data-stu-id="c8fe1-109">Sets the code of this `IDefinitionAppId` object to the specified formatted string value.</span></span>|  
|`IDefinitionAppId::EnumAppPath`|<span data-ttu-id="c8fe1-110">現在のアプリケーションパス内のアセンブリを格納する [IEnumDefinitionIdentity](ienumdefinitionidentity-interface.md) オブジェクトへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="c8fe1-110">Gets an interface pointer to an [IEnumDefinitionIdentity](ienumdefinitionidentity-interface.md) object that contains the assemblies in the current application path.</span></span>|  
|`IDefinitionAppId::SetAppPath`|<span data-ttu-id="c8fe1-111">現在のスコープ内のアセンブリのアプリケーションパスを、指定した [IDefinitionIdentity](idefinitionidentity-interface.md) オブジェクトによって参照される値に設定します。</span><span class="sxs-lookup"><span data-stu-id="c8fe1-111">Sets the application path for the assembly in the current scope to the value referenced by the specified [IDefinitionIdentity](idefinitionidentity-interface.md) object.</span></span>|  
|`IDefinitionAppId::get_SubscriptionId`|<span data-ttu-id="c8fe1-112">このオブジェクトに対するサブスクリプションのトークン識別子の文字列形式へのポインターを取得し `IDefinitionAppId` ます。</span><span class="sxs-lookup"><span data-stu-id="c8fe1-112">Gets a pointer to a string representation of the token identifier for a subscription to this `IDefinitionAppId` object.</span></span>|  
|`IDefinitionAppId::put_SubscriptionId`|<span data-ttu-id="c8fe1-113">このオブジェクトに対するサブスクリプションのトークン識別子 `IDefinitionAppId` を、指定された文字列値に設定します。</span><span class="sxs-lookup"><span data-stu-id="c8fe1-113">Sets the token identifier for a subscription to this `IDefinitionAppId` object to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c8fe1-114">要件</span><span class="sxs-lookup"><span data-stu-id="c8fe1-114">Requirements</span></span>  

 <span data-ttu-id="c8fe1-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8fe1-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8fe1-116">**ヘッダー:** 分離 .h</span><span class="sxs-lookup"><span data-stu-id="c8fe1-116">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="c8fe1-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8fe1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8fe1-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="c8fe1-118">See also</span></span>

- [<span data-ttu-id="c8fe1-119">Fusion インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c8fe1-119">Fusion Interfaces</span></span>](fusion-interfaces.md)
