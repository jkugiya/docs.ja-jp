---
description: '詳細について: ITypeName:: GetAssemblyName メソッド'
title: ITypeName::GetAssemblyName メソッド
ms.date: 03/30/2017
api_name:
- ITypeName.GetAssemblyName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetAssemblyName
helpviewer_keywords:
- ITypeName::GetAssemblyName method [.NET Framework hosting]
- GetAssemblyName method [.NET Framework hosting]
ms.assetid: 97801d99-f5f1-4a30-882f-959827093fac
topic_type:
- apiref
ms.openlocfilehash: c2e84ec2fc7c6a300611643783d61b46c14997ce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789347"
---
# <a name="itypenamegetassemblyname-method"></a><span data-ttu-id="b6ffb-103">ITypeName::GetAssemblyName メソッド</span><span class="sxs-lookup"><span data-stu-id="b6ffb-103">ITypeName::GetAssemblyName Method</span></span>

<span data-ttu-id="b6ffb-104">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="b6ffb-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6ffb-105">構文</span><span class="sxs-lookup"><span data-stu-id="b6ffb-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyName (  
    [out, retval] BSTR* rgbszAssemblyNames  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="b6ffb-106">必要条件</span><span class="sxs-lookup"><span data-stu-id="b6ffb-106">Requirements</span></span>  

 <span data-ttu-id="b6ffb-107">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6ffb-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6ffb-108">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="b6ffb-108">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b6ffb-109">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="b6ffb-109">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b6ffb-110">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6ffb-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6ffb-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="b6ffb-111">See also</span></span>

- [<span data-ttu-id="b6ffb-112">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b6ffb-112">Hosting Interfaces</span></span>](hosting-interfaces.md)
