---
description: '詳細について: ITypeName:: GetNames メソッド'
title: ITypeName::GetNames メソッド
ms.date: 03/30/2017
api_name:
- ITypeName.GetNames
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetNames
helpviewer_keywords:
- ITypeName::GetNames method [.NET Framework hosting]
- GetNames method [.NET Framework hosting]
ms.assetid: e2a3637b-d1e9-4d93-9e9b-0555fbff793d
topic_type:
- apiref
ms.openlocfilehash: 958e24947adc02713d48f16b916c3ed669080b8e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753693"
---
# <a name="itypenamegetnames-method"></a><span data-ttu-id="130a0-103">ITypeName::GetNames メソッド</span><span class="sxs-lookup"><span data-stu-id="130a0-103">ITypeName::GetNames Method</span></span>

<span data-ttu-id="130a0-104">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="130a0-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="130a0-105">構文</span><span class="sxs-lookup"><span data-stu-id="130a0-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNames (  
    [in] DWORD           count,  
    [out] BSTR*          rgbszNames,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="130a0-106">必要条件</span><span class="sxs-lookup"><span data-stu-id="130a0-106">Requirements</span></span>  

 <span data-ttu-id="130a0-107">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="130a0-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="130a0-108">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="130a0-108">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="130a0-109">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="130a0-109">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="130a0-110">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="130a0-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="130a0-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="130a0-111">See also</span></span>

- [<span data-ttu-id="130a0-112">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="130a0-112">Hosting Interfaces</span></span>](hosting-interfaces.md)
