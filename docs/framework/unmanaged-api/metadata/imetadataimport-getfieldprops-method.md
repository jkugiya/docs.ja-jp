---
description: '詳細について: IMetaDataImport:: GetFieldProps メソッド'
title: IMetaDataImport::GetFieldProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetFieldProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetFieldProps
helpviewer_keywords:
- IMetaDataImport::GetFieldProps method [.NET Framework metadata]
- GetFieldProps method [.NET Framework metadata]
ms.assetid: 7b0e9b10-8cef-4ba6-8432-40bf63e65ab1
topic_type:
- apiref
ms.openlocfilehash: 76735f837ff53b46b35cdf8c39990ed8689cc69c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789204"
---
# <a name="imetadataimportgetfieldprops-method"></a><span data-ttu-id="5287f-103">IMetaDataImport::GetFieldProps メソッド</span><span class="sxs-lookup"><span data-stu-id="5287f-103">IMetaDataImport::GetFieldProps Method</span></span>

<span data-ttu-id="5287f-104">指定した FieldDef トークンによって参照されるフィールドに関連付けられているメタデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="5287f-104">Gets metadata associated with the field referenced by the specified FieldDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5287f-105">構文</span><span class="sxs-lookup"><span data-stu-id="5287f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFieldProps (  
   [in]  mdFieldDef        mb,
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szField,  
   [in]  ULONG             cchField,
   [out] ULONG             *pchField,  
   [out] DWORD             *pdwAttr,  
   [in]  PCCOR_SIGNATURE   *ppvSigBlob,
   [out] ULONG             *pcbSigBlob,
   [out] DWORD             *pdwCPlusTypeFlag,
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5287f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5287f-106">Parameters</span></span>  

 `mb`  
 <span data-ttu-id="5287f-107">から関連付けられたメタデータを取得する対象のフィールドを表す FieldDef トークン。</span><span class="sxs-lookup"><span data-stu-id="5287f-107">[in] A FieldDef token that represents the field to get associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="5287f-108">入出力フィールドが属するクラスの型を表す TypeDef トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5287f-108">[out] A pointer to a TypeDef token that represents the type of the class that the field belongs to.</span></span>  
  
 `szField`  
 <span data-ttu-id="5287f-109">入出力フィールドの名前。</span><span class="sxs-lookup"><span data-stu-id="5287f-109">[out] The name of the field.</span></span>  
  
 `cchField`  
 <span data-ttu-id="5287f-110">から *Szfield* のバッファーのサイズ (ワイド文字単位)。</span><span class="sxs-lookup"><span data-stu-id="5287f-110">[in] The size in wide characters of the buffer for *szField*.</span></span>  
  
 `pchField`  
 <span data-ttu-id="5287f-111">入出力返されたバッファーの実際のサイズ。</span><span class="sxs-lookup"><span data-stu-id="5287f-111">[out] The actual size of the returned buffer.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="5287f-112">入出力フィールドのメタデータに関連付けられているフラグ。</span><span class="sxs-lookup"><span data-stu-id="5287f-112">[out] Flags associated with the field's metadata.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="5287f-113">からフィールドを説明するバイナリメタデータ値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5287f-113">[in] A pointer to the binary metadata value that describes the field.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="5287f-114">入出力のサイズ (バイト単位) `ppvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="5287f-114">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="5287f-115">入出力フィールドの値の型を指定するフラグ。</span><span class="sxs-lookup"><span data-stu-id="5287f-115">[out] A flag that specifies the value type of the field.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="5287f-116">入出力フィールドの定数値。</span><span class="sxs-lookup"><span data-stu-id="5287f-116">[out] A constant value for the field.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="5287f-117">入出力の文字数のサイズ `ppValue` 。文字列が存在しない場合は0。</span><span class="sxs-lookup"><span data-stu-id="5287f-117">[out] The size in chars of `ppValue`, or zero if no string exists.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5287f-118">要件</span><span class="sxs-lookup"><span data-stu-id="5287f-118">Requirements</span></span>  

 <span data-ttu-id="5287f-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5287f-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5287f-120">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="5287f-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5287f-121">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="5287f-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5287f-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5287f-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5287f-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="5287f-123">See also</span></span>

- [<span data-ttu-id="5287f-124">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5287f-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="5287f-125">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5287f-125">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
