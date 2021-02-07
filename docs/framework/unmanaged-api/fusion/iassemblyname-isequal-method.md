---
description: '詳細について: IAssemblyName:: IsEqual メソッド'
title: IAssemblyName::IsEqual メソッド
ms.date: 03/30/2017
api_name:
- IAssemblyName.IsEqual
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::IsEqual
helpviewer_keywords:
- IsEqual method [.NET Framework fusion]
- IAssemblyName::IsEqual method [.NET Framework fusion]
ms.assetid: 6dfc220f-d0d4-45b3-bfce-5829f817766f
topic_type:
- apiref
ms.openlocfilehash: f1bb0e26a217354e904ff79b397771d727a7a661
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760688"
---
# <a name="iassemblynameisequal-method"></a><span data-ttu-id="bc1f7-103">IAssemblyName::IsEqual メソッド</span><span class="sxs-lookup"><span data-stu-id="bc1f7-103">IAssemblyName::IsEqual Method</span></span>

<span data-ttu-id="bc1f7-104">指定した[](iassemblyname-interface.md) `IAssemblyName` 比較フラグに基づいて、指定した IAssemblyName オブジェクトがこのと等しいかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="bc1f7-104">Determines whether a specified [IAssemblyName](iassemblyname-interface.md) object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc1f7-105">構文</span><span class="sxs-lookup"><span data-stu-id="bc1f7-105">Syntax</span></span>  
  
```cpp  
HRESULT IsEqual (  
    [in] IAssemblyName  *pName,  
    [in] DWORD          dwCmpFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc1f7-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bc1f7-106">Parameters</span></span>  

 `pName`  
 <span data-ttu-id="bc1f7-107">から `IAssemblyName` このと比較するオブジェクト `IAssemblyName` 。</span><span class="sxs-lookup"><span data-stu-id="bc1f7-107">[in] The `IAssemblyName` object to which to compare this `IAssemblyName`.</span></span>  
  
 `dwCmpFlags`  
 <span data-ttu-id="bc1f7-108">から比較に影響を与える [ASM_CMP_FLAGS](asm-cmp-flags-enumeration.md) 値のビットごとの組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="bc1f7-108">[in] A bitwise combination of [ASM_CMP_FLAGS](asm-cmp-flags-enumeration.md) values that influence the comparison.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc1f7-109">要件</span><span class="sxs-lookup"><span data-stu-id="bc1f7-109">Requirements</span></span>  

 <span data-ttu-id="bc1f7-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc1f7-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc1f7-111">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="bc1f7-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="bc1f7-112">**.Net Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc1f7-112">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc1f7-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="bc1f7-113">See also</span></span>

- [<span data-ttu-id="bc1f7-114">IAssemblyName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bc1f7-114">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="bc1f7-115">fusion 列挙体</span><span class="sxs-lookup"><span data-stu-id="bc1f7-115">Fusion Enumerations</span></span>](fusion-enumerations.md)
