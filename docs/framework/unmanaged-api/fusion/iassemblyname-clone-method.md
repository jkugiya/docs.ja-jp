---
description: '詳細情報: IAssemblyName:: Clone メソッド'
title: IAssemblyName::Clone メソッド
ms.date: 03/30/2017
api_name:
- IAssemblyName.Clone
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::Clone
helpviewer_keywords:
- Clone method, IAssemblyName interface [.NET Framework fusion]
- IAssemblyName::Clone method [.NET Framework fusion]
ms.assetid: 7b345e08-5e16-4e3d-a044-4e19d0892943
topic_type:
- apiref
ms.openlocfilehash: b1d8ba2aec73565e9f6acaa44a5ef3731baa3af9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760785"
---
# <a name="iassemblynameclone-method"></a><span data-ttu-id="ec503-103">IAssemblyName::Clone メソッド</span><span class="sxs-lookup"><span data-stu-id="ec503-103">IAssemblyName::Clone Method</span></span>

<span data-ttu-id="ec503-104">この [IAssemblyName](iassemblyname-interface.md) オブジェクトの簡易コピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="ec503-104">Creates a shallow copy of this [IAssemblyName](iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec503-105">構文</span><span class="sxs-lookup"><span data-stu-id="ec503-105">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] IAssemblyName **pName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec503-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ec503-106">Parameters</span></span>  

 `pName`  
 <span data-ttu-id="ec503-107">入出力このオブジェクトの返されたコピー `IAssemblyName` 。</span><span class="sxs-lookup"><span data-stu-id="ec503-107">[out] The returned copy of this `IAssemblyName` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec503-108">要件</span><span class="sxs-lookup"><span data-stu-id="ec503-108">Requirements</span></span>  

 <span data-ttu-id="ec503-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec503-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec503-110">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="ec503-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="ec503-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec503-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec503-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="ec503-112">See also</span></span>

- [<span data-ttu-id="ec503-113">IAssemblyName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ec503-113">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
