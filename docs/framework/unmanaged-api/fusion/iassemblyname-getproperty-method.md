---
description: '詳細について: IAssemblyName:: GetProperty メソッド'
title: IAssemblyName::GetProperty メソッド
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetProperty
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetProperty
helpviewer_keywords:
- IAssemblyName::GetProperty method [.NET Framework fusion]
- GetProperty method [.NET Framework fusion]
ms.assetid: e59fda62-77d5-4e37-89cb-ce7ae4627975
topic_type:
- apiref
ms.openlocfilehash: 66528bb54e1cb4adbba8fa87088065bc40c2ee15
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760733"
---
# <a name="iassemblynamegetproperty-method"></a><span data-ttu-id="5e5dd-103">IAssemblyName::GetProperty メソッド</span><span class="sxs-lookup"><span data-stu-id="5e5dd-103">IAssemblyName::GetProperty Method</span></span>

<span data-ttu-id="5e5dd-104">指定したプロパティ識別子によって参照されるプロパティへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="5e5dd-104">Gets a pointer to the property referenced by the specified property identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e5dd-105">構文</span><span class="sxs-lookup"><span data-stu-id="5e5dd-105">Syntax</span></span>  
  
```cpp  
HRESULT GetProperty (  
    [in]      DWORD    PropertyId,  
    [out]     LPVOID   pvProperty,  
    [in, out] LPDWORD  pcbProperty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e5dd-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5e5dd-106">Parameters</span></span>  

 `PropertyId`  
 <span data-ttu-id="5e5dd-107">から要求されたプロパティの一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="5e5dd-107">[in] The unique identifier for the requested property.</span></span>  
  
 `pvProperty`  
 <span data-ttu-id="5e5dd-108">入出力返されたプロパティデータ。</span><span class="sxs-lookup"><span data-stu-id="5e5dd-108">[out] The returned property data.</span></span>  
  
 `pcbProperty`  
 <span data-ttu-id="5e5dd-109">[入力、出力]のサイズ (バイト単位) `pvProperty` 。</span><span class="sxs-lookup"><span data-stu-id="5e5dd-109">[in, out] The size, in bytes, of `pvProperty`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e5dd-110">要件</span><span class="sxs-lookup"><span data-stu-id="5e5dd-110">Requirements</span></span>  

 <span data-ttu-id="5e5dd-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5e5dd-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e5dd-112">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="5e5dd-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="5e5dd-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e5dd-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e5dd-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="5e5dd-114">See also</span></span>

- [<span data-ttu-id="5e5dd-115">IAssemblyName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5e5dd-115">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
