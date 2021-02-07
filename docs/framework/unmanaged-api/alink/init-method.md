---
description: '詳細情報: Init メソッド'
title: Init メソッド
ms.date: 03/30/2017
api_name:
- IALink.Init
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- Init
helpviewer_keywords:
- Init method
ms.assetid: e48b5c64-049f-4f93-ad87-d07ae9cd5845
topic_type:
- apiref
ms.openlocfilehash: 531e05a09cbecbfb67c8c004d1e4ba1deb7e59a0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662560"
---
# <a name="init-method"></a><span data-ttu-id="ffecc-103">Init メソッド</span><span class="sxs-lookup"><span data-stu-id="ffecc-103">Init Method</span></span>

<span data-ttu-id="ffecc-104">使用する [Ialink インターフェイス](ialink-interface.md) を実装するオブジェクトを準備します。</span><span class="sxs-lookup"><span data-stu-id="ffecc-104">Prepares objects implementing the [IALink Interface](ialink-interface.md) for use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffecc-105">構文</span><span class="sxs-lookup"><span data-stu-id="ffecc-105">Syntax</span></span>  
  
```cpp  
HRESULT Init(  
    IMetaDataDispenserEx* pDispenser,  
    IMetaDataError* pErrorHandler  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="ffecc-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ffecc-106">Parameters</span></span>  

 `pDispenser`  
 <span data-ttu-id="ffecc-107">[IMetaDataDispenserEx インターフェイス](../metadata/imetadatadispenserex-interface.md) のメタデータディスペンサーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ffecc-107">[IMetaDataDispenserEx Interface](../metadata/imetadatadispenserex-interface.md) pointer to the metadata dispenser.</span></span>  
  
 `pErrorHandler`  
 <span data-ttu-id="ffecc-108">[IMetaDataError インターフェイス](../metadata/imetadataerror-interface.md) は、省略可能なエラー処理インターフェイスへのポインターです。</span><span class="sxs-lookup"><span data-stu-id="ffecc-108">[IMetaDataError Interface](../metadata/imetadataerror-interface.md) pointer to an optional error handling interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ffecc-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="ffecc-109">Return Value</span></span>  

 <span data-ttu-id="ffecc-110">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="ffecc-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffecc-111">要件</span><span class="sxs-lookup"><span data-stu-id="ffecc-111">Requirements</span></span>  

 <span data-ttu-id="ffecc-112">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="ffecc-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffecc-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="ffecc-113">See also</span></span>

- [<span data-ttu-id="ffecc-114">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ffecc-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="ffecc-115">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ffecc-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="ffecc-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="ffecc-116">ALink API</span></span>](index.md)
