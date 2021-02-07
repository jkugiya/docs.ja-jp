---
description: '詳細について: ITypeName:: GetTypeArguments メソッド'
title: ITypeName::GetTypeArguments メソッド
ms.date: 03/30/2017
api_name:
- ITypeName.GetTypeArguments
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetTypeArguments
helpviewer_keywords:
- ITypeName::GetTypeArguments method [.NET Framework hosting]
- GetTypeArguments method [.NET Framework hosting]
ms.assetid: 638d77df-ff9c-40d9-88ee-930f5f87ada1
topic_type:
- apiref
ms.openlocfilehash: b88ffcfb856905bf891ebeafa1e6dbeda2563aaf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753661"
---
# <a name="itypenamegettypearguments-method"></a><span data-ttu-id="b28ae-103">ITypeName::GetTypeArguments メソッド</span><span class="sxs-lookup"><span data-stu-id="b28ae-103">ITypeName::GetTypeArguments Method</span></span>

<span data-ttu-id="b28ae-104">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="b28ae-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b28ae-105">構文</span><span class="sxs-lookup"><span data-stu-id="b28ae-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeArguments (  
    [in] DWORD           count,  
    [out] ITypeName**    rgpArguments,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="b28ae-106">必要条件</span><span class="sxs-lookup"><span data-stu-id="b28ae-106">Requirements</span></span>  

 <span data-ttu-id="b28ae-107">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b28ae-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b28ae-108">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="b28ae-108">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b28ae-109">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="b28ae-109">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b28ae-110">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b28ae-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b28ae-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="b28ae-111">See also</span></span>

- [<span data-ttu-id="b28ae-112">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b28ae-112">Hosting Interfaces</span></span>](hosting-interfaces.md)
