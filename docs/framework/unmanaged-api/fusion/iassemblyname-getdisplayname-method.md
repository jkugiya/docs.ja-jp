---
description: '詳細について: IAssemblyName:: GetDisplayName メソッド'
title: IAssemblyName::GetDisplayName メソッド
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetDisplayName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetDisplayName
helpviewer_keywords:
- GetDisplayName method, IAssemblyName interface [.NET Framework fusion]
- IAssemblyName::GetDisplayName method [.NET Framework fusion]
ms.assetid: 9a26547a-9a34-4284-a463-78a7d4b496cf
topic_type:
- apiref
ms.openlocfilehash: 9b52a901385fa9b3ba7cb6bcd1678d0718f8f695
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760759"
---
# <a name="iassemblynamegetdisplayname-method"></a><span data-ttu-id="6d018-103">IAssemblyName::GetDisplayName メソッド</span><span class="sxs-lookup"><span data-stu-id="6d018-103">IAssemblyName::GetDisplayName Method</span></span>

<span data-ttu-id="6d018-104">この [IAssemblyName](iassemblyname-interface.md) オブジェクトによって参照されるアセンブリの、人間が判読できる名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="6d018-104">Gets the human-readable name of the assembly referenced by this [IAssemblyName](iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d018-105">構文</span><span class="sxs-lookup"><span data-stu-id="6d018-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDisplayName (  
        [out]      LPOLESTR  szDisplayName,  
        [in, out]  LPDWORD   pccDisplayName,  
        [in]       DWORD     dwDisplayFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d018-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6d018-106">Parameters</span></span>  

 `szDisplayName`  
 <span data-ttu-id="6d018-107">入出力参照されたアセンブリの名前を格納している文字列バッファー。</span><span class="sxs-lookup"><span data-stu-id="6d018-107">[out] The string buffer that contains the name of the referenced assembly.</span></span>  
  
 `pccDisplayName`  
 <span data-ttu-id="6d018-108">[入力、出力] `szDisplayName` Null 終端文字を含むワイド文字ののサイズ。</span><span class="sxs-lookup"><span data-stu-id="6d018-108">[in, out] The size of `szDisplayName` in wide characters, including a null terminator character.</span></span>  
  
 `dwDisplayFlags`  
 <span data-ttu-id="6d018-109">からの機能に影響を与える [ASM_DISPLAY_FLAGS](asm-display-flags-enumeration.md) 値のビットごとの組み合わせ `szDisplayName` 。</span><span class="sxs-lookup"><span data-stu-id="6d018-109">[in] A bitwise combination of [ASM_DISPLAY_FLAGS](asm-display-flags-enumeration.md) values that influence the features of `szDisplayName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d018-110">要件</span><span class="sxs-lookup"><span data-stu-id="6d018-110">Requirements</span></span>  

 <span data-ttu-id="6d018-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6d018-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d018-112">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="6d018-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="6d018-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d018-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d018-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="6d018-114">See also</span></span>

- [<span data-ttu-id="6d018-115">IAssemblyName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6d018-115">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="6d018-116">fusion 列挙体</span><span class="sxs-lookup"><span data-stu-id="6d018-116">Fusion Enumerations</span></span>](fusion-enumerations.md)
