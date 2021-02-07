---
description: '詳細について: IAssemblyName:: SetProperty メソッド'
title: IAssemblyName::SetProperty メソッド
ms.date: 03/30/2017
api_name:
- IAssemblyName.SetProperty
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::SetProperty
helpviewer_keywords:
- IAssemblyName::SetProperty method [.NET Framework fusion]
- SetProperty method [.NET Framework fusion]
ms.assetid: 496c3add-f60b-4073-943f-d1bcf33330cb
topic_type:
- apiref
ms.openlocfilehash: cab132c2cd8a0744a2a946a1d8b21f49012c6eac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760689"
---
# <a name="iassemblynamesetproperty-method"></a><span data-ttu-id="8c4e1-103">IAssemblyName::SetProperty メソッド</span><span class="sxs-lookup"><span data-stu-id="8c4e1-103">IAssemblyName::SetProperty Method</span></span>

<span data-ttu-id="8c4e1-104">指定したプロパティ識別子によって参照されるプロパティの値を設定します。</span><span class="sxs-lookup"><span data-stu-id="8c4e1-104">Sets the value of the property referenced by the specified property identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c4e1-105">構文</span><span class="sxs-lookup"><span data-stu-id="8c4e1-105">Syntax</span></span>  
  
```cpp  
HRESULT SetProperty (  
    [in] DWORD  PropertyId,  
    [in] LPVOID pvProperty,  
    [in] DWORD  cbProperty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c4e1-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8c4e1-106">Parameters</span></span>  

 `PropertyId`  
 <span data-ttu-id="8c4e1-107">から値が設定されるプロパティの一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="8c4e1-107">[in] The unique identifier of the property whose value will be set.</span></span>  
  
 `pvProperty`  
 <span data-ttu-id="8c4e1-108">からによって参照されるプロパティを設定する値 `PropertyId` 。</span><span class="sxs-lookup"><span data-stu-id="8c4e1-108">[in] The value to which to set the property referenced by `PropertyId`.</span></span>  
  
 `cbProperty`  
 <span data-ttu-id="8c4e1-109">からのサイズ (バイト単位) `pvProperty` 。</span><span class="sxs-lookup"><span data-stu-id="8c4e1-109">[in] The size, in bytes, of `pvProperty`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c4e1-110">要件</span><span class="sxs-lookup"><span data-stu-id="8c4e1-110">Requirements</span></span>  

 <span data-ttu-id="8c4e1-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c4e1-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c4e1-112">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="8c4e1-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="8c4e1-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c4e1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c4e1-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="8c4e1-114">See also</span></span>

- [<span data-ttu-id="8c4e1-115">IAssemblyName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8c4e1-115">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
