---
description: '詳細について: IMetaDataImport:: GetTypeDefProps メソッド'
title: IMetaDataImport::GetTypeDefProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeDefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeDefProps
helpviewer_keywords:
- GetTypeDefProps method [.NET Framework metadata]
- IMetaDataImport::GetTypeDefProps method [.NET Framework metadata]
ms.assetid: 00061a25-ba05-47a7-b984-fd916b06b149
topic_type:
- apiref
ms.openlocfilehash: da5c6117f636098ed0cfeddc541979d235729d63
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799277"
---
# <a name="imetadataimportgettypedefprops-method"></a><span data-ttu-id="450ca-103">IMetaDataImport::GetTypeDefProps メソッド</span><span class="sxs-lookup"><span data-stu-id="450ca-103">IMetaDataImport::GetTypeDefProps Method</span></span>

<span data-ttu-id="450ca-104"><xref:System.Type>指定した TypeDef トークンによって表されるのメタデータ情報を返します。</span><span class="sxs-lookup"><span data-stu-id="450ca-104">Returns metadata information for the <xref:System.Type> represented by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="450ca-105">構文</span><span class="sxs-lookup"><span data-stu-id="450ca-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeDefProps (  
   [in]  mdTypeDef   td,  
   [out] LPWSTR      szTypeDef,  
   [in]  ULONG       cchTypeDef,  
   [out] ULONG       *pchTypeDef,  
   [out] DWORD       *pdwTypeDefFlags,  
   [out] mdToken     *ptkExtends  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="450ca-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="450ca-106">Parameters</span></span>  

 `td`  
 <span data-ttu-id="450ca-107">からメタデータを返す型を表す TypeDef トークン。</span><span class="sxs-lookup"><span data-stu-id="450ca-107">[in] The TypeDef token that represents the type to return metadata for.</span></span>  
  
 `szTypeDef`  
 <span data-ttu-id="450ca-108">入出力型名を格納しているバッファー。</span><span class="sxs-lookup"><span data-stu-id="450ca-108">[out] A buffer containing the type name.</span></span>  
  
 `cchTypeDef`  
 <span data-ttu-id="450ca-109">からのワイド文字のサイズ `szTypeDef` 。</span><span class="sxs-lookup"><span data-stu-id="450ca-109">[in] The size in wide characters of `szTypeDef`.</span></span>  
  
 `pchTypeDef`  
 <span data-ttu-id="450ca-110">入出力で返されたワイド文字の数 `szTypeDef` 。</span><span class="sxs-lookup"><span data-stu-id="450ca-110">[out] The number of wide characters returned in `szTypeDef`.</span></span>  
  
 `pdwTypeDefFlags`  
 <span data-ttu-id="450ca-111">入出力型定義を変更するすべてのフラグへのポインター。</span><span class="sxs-lookup"><span data-stu-id="450ca-111">[out] A pointer to any flags that modify the type definition.</span></span> <span data-ttu-id="450ca-112">この値は、 [Cortypeattr](cortypeattr-enumeration.md) 列挙子のビットマスクです。</span><span class="sxs-lookup"><span data-stu-id="450ca-112">This value is a bitmask from the [CorTypeAttr](cortypeattr-enumeration.md) enumeration.</span></span>  
  
 `ptkExtends`  
 <span data-ttu-id="450ca-113">入出力要求された型の基本型を表す TypeDef または TypeRef メタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="450ca-113">[out] A TypeDef or TypeRef metadata token that represents the base type of the requested type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="450ca-114">要件</span><span class="sxs-lookup"><span data-stu-id="450ca-114">Requirements</span></span>  

 <span data-ttu-id="450ca-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="450ca-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="450ca-116">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="450ca-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="450ca-117">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="450ca-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="450ca-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="450ca-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="450ca-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="450ca-119">See also</span></span>

- [<span data-ttu-id="450ca-120">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="450ca-120">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="450ca-121">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="450ca-121">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
