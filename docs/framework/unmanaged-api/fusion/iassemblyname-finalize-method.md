---
description: '詳細について: IAssemblyName:: Finalize メソッド'
title: IAssemblyName::Finalize メソッド
ms.date: 03/30/2017
api_name:
- IAssemblyName.Finalize
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::Finalize
helpviewer_keywords:
- Finalize method [.NET Framework fusion]
- IAssemblyName::Finalize method [.NET Framework fusion]
ms.assetid: 610e792d-98ef-411f-90b0-5b9a3813f547
topic_type:
- apiref
ms.openlocfilehash: d6277fdbc15f6f907d5e758dac4a3670570d585d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760772"
---
# <a name="iassemblynamefinalize-method"></a><span data-ttu-id="64e58-103">IAssemblyName::Finalize メソッド</span><span class="sxs-lookup"><span data-stu-id="64e58-103">IAssemblyName::Finalize Method</span></span>

<span data-ttu-id="64e58-104">この [IAssemblyName](iassemblyname-interface.md) オブジェクトが、デストラクターが呼び出される前にリソースを解放し、その他のクリーンアップ操作を実行できるようにします。</span><span class="sxs-lookup"><span data-stu-id="64e58-104">Allows this [IAssemblyName](iassemblyname-interface.md) object to release resources and perform other cleanup operations before its destructor is called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64e58-105">構文</span><span class="sxs-lookup"><span data-stu-id="64e58-105">Syntax</span></span>  
  
```cpp  
HRESULT Finalize ();  
```  
  
## <a name="requirements"></a><span data-ttu-id="64e58-106">必要条件</span><span class="sxs-lookup"><span data-stu-id="64e58-106">Requirements</span></span>  

 <span data-ttu-id="64e58-107">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="64e58-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64e58-108">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="64e58-108">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="64e58-109">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64e58-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64e58-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="64e58-110">See also</span></span>

- [<span data-ttu-id="64e58-111">IAssemblyName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="64e58-111">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
