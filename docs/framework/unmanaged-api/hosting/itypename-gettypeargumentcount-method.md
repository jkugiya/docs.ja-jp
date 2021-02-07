---
description: '詳細について: ITypeName:: GetTypeArgumentCount メソッド'
title: ITypeName::GetTypeArgumentCount メソッド
ms.date: 03/30/2017
api_name:
- ITypeName.GetTypeArgumentCount
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetTypeArgumentCount
helpviewer_keywords:
- GetTypeArgumentCount method [.NET Framework hosting]
- ITypeName::GetTypeArgumentCount method [.NET Framework hosting]
ms.assetid: ecb5480c-761a-4b02-83e0-b79abc67fd08
topic_type:
- apiref
ms.openlocfilehash: dc628194a949c46711193df78f1a384a9a1098bb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753680"
---
# <a name="itypenamegettypeargumentcount-method"></a><span data-ttu-id="bc116-103">ITypeName::GetTypeArgumentCount メソッド</span><span class="sxs-lookup"><span data-stu-id="bc116-103">ITypeName::GetTypeArgumentCount Method</span></span>

<span data-ttu-id="bc116-104">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="bc116-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc116-105">構文</span><span class="sxs-lookup"><span data-stu-id="bc116-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeArgumentCount (  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="bc116-106">必要条件</span><span class="sxs-lookup"><span data-stu-id="bc116-106">Requirements</span></span>  

 <span data-ttu-id="bc116-107">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc116-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc116-108">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="bc116-108">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bc116-109">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="bc116-109">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bc116-110">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc116-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc116-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="bc116-111">See also</span></span>

- [<span data-ttu-id="bc116-112">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bc116-112">Hosting Interfaces</span></span>](hosting-interfaces.md)
