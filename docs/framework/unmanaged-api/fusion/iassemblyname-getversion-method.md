---
description: '詳細について: IAssemblyName:: GetVersion メソッド'
title: IAssemblyName::GetVersion メソッド
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetVersion
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetVersion
helpviewer_keywords:
- IAssemblyName::GetVersion method [.NET Framework fusion]
- GetVersion method, IAssemblyName interface [.NET Framework fusion]
ms.assetid: 42230928-2c33-41fd-9519-d96efef6c7af
topic_type:
- apiref
ms.openlocfilehash: 3339dda6a0b4f083655ece7bef86b080a8fcf5c8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760720"
---
# <a name="iassemblynamegetversion-method"></a><span data-ttu-id="23236-103">IAssemblyName::GetVersion メソッド</span><span class="sxs-lookup"><span data-stu-id="23236-103">IAssemblyName::GetVersion Method</span></span>

<span data-ttu-id="23236-104">この [IAssemblyName](iassemblyname-interface.md) オブジェクトによって参照されるアセンブリのバージョン情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="23236-104">Gets the version information for the assembly referenced by this [IAssemblyName](iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23236-105">構文</span><span class="sxs-lookup"><span data-stu-id="23236-105">Syntax</span></span>  
  
```cpp  
HRESULT GetVersion (  
    [out] LPDWORD pdwVersionHi,  
    [out] LPDWORD pdwVersionLow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="23236-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="23236-106">Parameters</span></span>  

 `pdwVersionHi`  
 <span data-ttu-id="23236-107">入出力バージョンの上位32ビット。</span><span class="sxs-lookup"><span data-stu-id="23236-107">[out] The high 32 bits of the version.</span></span>  
  
 `pdwVersionLow`  
 <span data-ttu-id="23236-108">入出力バージョンの下位32ビット。</span><span class="sxs-lookup"><span data-stu-id="23236-108">[out] The low 32 bits of the version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23236-109">要件</span><span class="sxs-lookup"><span data-stu-id="23236-109">Requirements</span></span>  

 <span data-ttu-id="23236-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="23236-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23236-111">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="23236-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="23236-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23236-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23236-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="23236-113">See also</span></span>

- [<span data-ttu-id="23236-114">IAssemblyName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23236-114">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
