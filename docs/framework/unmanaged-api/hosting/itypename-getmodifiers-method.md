---
description: '詳細について: ITypeName:: GetModifiers メソッド'
title: ITypeName::GetModifiers メソッド
ms.date: 03/30/2017
api_name:
- ITypeName.GetModifiers
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetModifiers
helpviewer_keywords:
- ITypeName::GetModifiers method [.NET Framework hosting]
- GetModifiers method [.NET Framework hosting]
ms.assetid: 75508c55-3e09-4135-80da-cc811003fa82
topic_type:
- apiref
ms.openlocfilehash: 3c44d569255656f95ccceec0462d09044b46679b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753719"
---
# <a name="itypenamegetmodifiers-method"></a><span data-ttu-id="bb584-103">ITypeName::GetModifiers メソッド</span><span class="sxs-lookup"><span data-stu-id="bb584-103">ITypeName::GetModifiers Method</span></span>

<span data-ttu-id="bb584-104">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="bb584-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb584-105">構文</span><span class="sxs-lookup"><span data-stu-id="bb584-105">Syntax</span></span>  
  
```cpp  
HRESULT GetModifiers (  
    [in] DWORD           count,  
    [out] DWORD*         rgModifiers,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="bb584-106">必要条件</span><span class="sxs-lookup"><span data-stu-id="bb584-106">Requirements</span></span>  

 <span data-ttu-id="bb584-107">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bb584-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb584-108">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="bb584-108">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bb584-109">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="bb584-109">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bb584-110">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb584-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb584-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="bb584-111">See also</span></span>

- [<span data-ttu-id="bb584-112">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bb584-112">Hosting Interfaces</span></span>](hosting-interfaces.md)
