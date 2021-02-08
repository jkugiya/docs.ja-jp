---
description: '詳細について: IMetaDataImport:: GetTypeRefProps メソッド'
title: IMetaDataImport::GetTypeRefProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeRefProps
helpviewer_keywords:
- IMetaDataImport::GetTypeRefProps method [.NET Framework metadata]
- GetTypeRefProps method [.NET Framework metadata]
ms.assetid: 01837955-ce1e-4068-b338-fd473bd77d1d
topic_type:
- apiref
ms.openlocfilehash: 8d4741ca2d04aaa4af48fee2cf6485de3403a525
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789126"
---
# <a name="imetadataimportgettyperefprops-method"></a><span data-ttu-id="9c4c8-103">IMetaDataImport::GetTypeRefProps メソッド</span><span class="sxs-lookup"><span data-stu-id="9c4c8-103">IMetaDataImport::GetTypeRefProps Method</span></span>

<span data-ttu-id="9c4c8-104"><xref:System.Type>指定した TypeRef トークンによって参照されるに関連付けられているメタデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="9c4c8-104">Gets the metadata associated with the <xref:System.Type> referenced by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c4c8-105">構文</span><span class="sxs-lookup"><span data-stu-id="9c4c8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeRefProps (  
   [in]  mdTypeRef   tr,  
   [out] mdToken     *ptkResolutionScope,  
   [out] LPWSTR      szName,  
   [in]  ULONG       cchName,  
   [out] ULONG       *pchName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c4c8-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9c4c8-106">Parameters</span></span>  

 `tr`  
 <span data-ttu-id="9c4c8-107">からメタデータを返す型を表す TypeRef トークン。</span><span class="sxs-lookup"><span data-stu-id="9c4c8-107">[in] The TypeRef token that represents the type to return metadata for.</span></span>  
  
 `ptkResolutionScope`  
 <span data-ttu-id="9c4c8-108">入出力参照が行われるスコープへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9c4c8-108">[out] A pointer to the scope in which the reference is made.</span></span> <span data-ttu-id="9c4c8-109">この値は、AssemblyRef または ModuleRef トークンです。</span><span class="sxs-lookup"><span data-stu-id="9c4c8-109">This value is an AssemblyRef or ModuleRef token.</span></span>  
  
 `szName`  
 <span data-ttu-id="9c4c8-110">入出力型名を格納しているバッファー。</span><span class="sxs-lookup"><span data-stu-id="9c4c8-110">[out] A buffer containing the type name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="9c4c8-111">からのワイド文字で要求されたサイズ `szName` 。</span><span class="sxs-lookup"><span data-stu-id="9c4c8-111">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="9c4c8-112">入出力のワイド文字で返されたサイズ `szName` 。</span><span class="sxs-lookup"><span data-stu-id="9c4c8-112">[out] The returned size in wide characters of `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c4c8-113">要件</span><span class="sxs-lookup"><span data-stu-id="9c4c8-113">Requirements</span></span>  

 <span data-ttu-id="9c4c8-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c4c8-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c4c8-115">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="9c4c8-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9c4c8-116">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="9c4c8-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9c4c8-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c4c8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c4c8-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="9c4c8-118">See also</span></span>

- [<span data-ttu-id="9c4c8-119">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9c4c8-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="9c4c8-120">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9c4c8-120">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
