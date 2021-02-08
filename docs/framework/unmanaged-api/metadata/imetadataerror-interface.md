---
description: 詳細については、「IMetaDataError インターフェイス」を参照してください。
title: IMetaDataError インターフェイス
ms.date: 03/30/2017
api_name:
- IMetaDataError
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataError
helpviewer_keywords:
- IMetaDataError interface [.NET Framework metadata]
ms.assetid: 0020b62c-ea88-40c7-a9ee-16b064f81624
topic_type:
- apiref
ms.openlocfilehash: f32c8abc3cccce770b86ce47016d9b7e18acad23
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771692"
---
# <a name="imetadataerror-interface"></a><span data-ttu-id="2351c-103">IMetaDataError インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2351c-103">IMetaDataError Interface</span></span>

<span data-ttu-id="2351c-104">メタデータのマージ中にエラーを報告するためのコールバックメカニズムを提供します。</span><span class="sxs-lookup"><span data-stu-id="2351c-104">Provides a callback mechanism for reporting errors during the metadata merge.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2351c-105">インターフェイスは、 `IMetaDataError` クライアントによって実装される必要があります。</span><span class="sxs-lookup"><span data-stu-id="2351c-105">The `IMetaDataError` interface must be implemented by the client.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2351c-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="2351c-106">Methods</span></span>  
  
|<span data-ttu-id="2351c-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="2351c-107">Method</span></span>|<span data-ttu-id="2351c-108">説明</span><span class="sxs-lookup"><span data-stu-id="2351c-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2351c-109">OnError メソッド</span><span class="sxs-lookup"><span data-stu-id="2351c-109">OnError Method</span></span>](imetadataerror-onerror-method.md)|<span data-ttu-id="2351c-110">メタデータのマージ中に発生したエラーの通知を提供します。</span><span class="sxs-lookup"><span data-stu-id="2351c-110">Provides notification of errors that occur during the metadata merge.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2351c-111">要件</span><span class="sxs-lookup"><span data-stu-id="2351c-111">Requirements</span></span>  

 <span data-ttu-id="2351c-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2351c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2351c-113">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="2351c-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2351c-114">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="2351c-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2351c-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2351c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2351c-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="2351c-116">See also</span></span>

- [<span data-ttu-id="2351c-117">メタデータ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2351c-117">Metadata Interfaces</span></span>](metadata-interfaces.md)
