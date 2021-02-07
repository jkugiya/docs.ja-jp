---
description: '詳細について: ITypeNameFactory::P arseTypeName メソッド'
title: ITypeNameFactory::ParseTypeName メソッド
ms.date: 03/30/2017
api_name:
- ITypeNameFactory.ParseTypeName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ParseTypeName
helpviewer_keywords:
- ITypeNameFactory::ParseTypeName method [.NET Framework hosting]
- ParseTypeName method [.NET Framework hosting]
ms.assetid: 13c9f063-371c-4911-a5e7-e1e0b88ae382
topic_type:
- apiref
ms.openlocfilehash: e0ff068dd0d095c3eed1c7a697d0c72919306996
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99680201"
---
# <a name="itypenamefactoryparsetypename-method"></a><span data-ttu-id="4dfd1-103">ITypeNameFactory::ParseTypeName メソッド</span><span class="sxs-lookup"><span data-stu-id="4dfd1-103">ITypeNameFactory::ParseTypeName Method</span></span>

<span data-ttu-id="4dfd1-104">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="4dfd1-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4dfd1-105">構文</span><span class="sxs-lookup"><span data-stu-id="4dfd1-105">Syntax</span></span>  
  
```cpp  
HRESULT ParseTypeName (  
    [in]  LPCWSTR             szName,  
    [out] DWORD*              pError,  
    [out, retval] ITypeName** ppTypeName  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="4dfd1-106">必要条件</span><span class="sxs-lookup"><span data-stu-id="4dfd1-106">Requirements</span></span>  

 <span data-ttu-id="4dfd1-107">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4dfd1-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4dfd1-108">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="4dfd1-108">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4dfd1-109">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="4dfd1-109">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4dfd1-110">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4dfd1-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dfd1-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="4dfd1-111">See also</span></span>

- [<span data-ttu-id="4dfd1-112">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4dfd1-112">Hosting Interfaces</span></span>](hosting-interfaces.md)
