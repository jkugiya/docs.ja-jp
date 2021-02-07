---
description: '詳細情報: IAssemblyName:: GetName メソッド'
title: IAssemblyName::GetName メソッド
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetName
helpviewer_keywords:
- GetName method, IAssemblyName interface [.NET Framework debugging]
- IAssemblyName::GetName method [.NET Framework fusion]
ms.assetid: 1dee9781-1cf3-48a9-a376-d18ea1f73280
topic_type:
- apiref
ms.openlocfilehash: 04cd6258c2fc60c9fc40e1e4b731e5c04a8d3112
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760746"
---
# <a name="iassemblynamegetname-method"></a><span data-ttu-id="b6b5d-103">IAssemblyName::GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="b6b5d-103">IAssemblyName::GetName Method</span></span>

<span data-ttu-id="b6b5d-104">この [IAssemblyName](iassemblyname-interface.md) オブジェクトによって参照されるアセンブリの単純な、暗号化されていない名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="b6b5d-104">Gets the simple, unencrypted name of the assembly referenced by this [IAssemblyName](iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6b5d-105">構文</span><span class="sxs-lookup"><span data-stu-id="b6b5d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in, out] LPDWORD lpcwBuffer,  
    [out]     WCHAR *pwzName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6b5d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b6b5d-106">Parameters</span></span>  

 `lpcwBuffer`  
 <span data-ttu-id="b6b5d-107">[入力、出力] `pwzName` Null 終端文字を含むワイド文字ののサイズ。</span><span class="sxs-lookup"><span data-stu-id="b6b5d-107">[in, out] The size of `pwzName` in wide characters, including the null terminator character.</span></span>  
  
 `pwzName`  
 <span data-ttu-id="b6b5d-108">入出力参照されたアセンブリの名前を保持するバッファー。</span><span class="sxs-lookup"><span data-stu-id="b6b5d-108">[out] A buffer to hold the name of the referenced assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6b5d-109">要件</span><span class="sxs-lookup"><span data-stu-id="b6b5d-109">Requirements</span></span>  

 <span data-ttu-id="b6b5d-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6b5d-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6b5d-111">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="b6b5d-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="b6b5d-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6b5d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6b5d-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="b6b5d-113">See also</span></span>

- [<span data-ttu-id="b6b5d-114">IAssemblyName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b6b5d-114">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
