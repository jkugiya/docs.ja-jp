---
description: '詳細について: IMetaDataImport:: GetCustomAttributeProps メソッド'
title: IMetaDataImport::GetCustomAttributeProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetCustomAttributeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetCustomAttributeProps
helpviewer_keywords:
- GetCustomAttributeProps method [.NET Framework metadata]
- IMetaDataImport::GetCustomAttributeProps method [.NET Framework metadata]
ms.assetid: 6eefb243-a281-41c1-bcdc-7e17513bc446
topic_type:
- apiref
ms.openlocfilehash: 9bd8e83301252d7ead225146e562d3a58feb244a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745383"
---
# <a name="imetadataimportgetcustomattributeprops-method"></a><span data-ttu-id="77152-103">IMetaDataImport::GetCustomAttributeProps メソッド</span><span class="sxs-lookup"><span data-stu-id="77152-103">IMetaDataImport::GetCustomAttributeProps Method</span></span>

<span data-ttu-id="77152-104">指定したメタデータ トークンのカスタム属性の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="77152-104">Gets the value of the custom attribute, given its metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77152-105">構文</span><span class="sxs-lookup"><span data-stu-id="77152-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCustomAttributeProps (  
   [in]            mdCustomAttribute   cv,  
   [out, optional] mdToken             *ptkObj,  
   [out, optional] mdToken             *ptkType,  
   [out, optional] void const          **ppBlob,  
   [out, optional] ULONG               *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77152-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="77152-106">Parameters</span></span>  

 `cv`  
 <span data-ttu-id="77152-107">[in] 取得するカスタム属性を表すメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="77152-107">[in] A metadata token that represents the custom attribute to be retrieved.</span></span>  
  
 `ptkObj`  
 <span data-ttu-id="77152-108">[out](省略可能) カスタム属性が変更されるオブジェクトを表すメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="77152-108">[out, optional] A metadata token representing the object that the custom attribute modifies.</span></span> <span data-ttu-id="77152-109">この値には、`mdCustomAttribute` を除く任意の種類のトークンを指定できます。</span><span class="sxs-lookup"><span data-stu-id="77152-109">This value can be any type of metadata token except `mdCustomAttribute`.</span></span>  
  
 `ptkType`  
 <span data-ttu-id="77152-110">[out](省略可能) 返されるカスタム属性の <xref:System.Type> を表す `mdMethodDef` または `mdMemberRef` メタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="77152-110">[out, optional] An `mdMethodDef` or `mdMemberRef` metadata token representing the <xref:System.Type> of the returned custom attribute.</span></span>  
  
 `ppBlob`  
 <span data-ttu-id="77152-111">[out](省略可能) カスタム属性の値であるデータの配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="77152-111">[out, optional] A pointer to an array of data that is the value of the custom attribute.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="77152-112">[out](省略可能) \*`ppBlob` に返されたデータのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="77152-112">[out, optional] The size in bytes of the data returned in \*`ppBlob`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77152-113">解説</span><span class="sxs-lookup"><span data-stu-id="77152-113">Remarks</span></span>  

 <span data-ttu-id="77152-114">カスタム属性はデータの配列として格納され、その形式はメタデータ エンジンによって解釈されます。</span><span class="sxs-lookup"><span data-stu-id="77152-114">A custom attribute is stored as an array of data, the format which is understood by the metadata engine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77152-115">要件</span><span class="sxs-lookup"><span data-stu-id="77152-115">Requirements</span></span>  

 <span data-ttu-id="77152-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="77152-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77152-117">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="77152-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="77152-118">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="77152-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="77152-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77152-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77152-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="77152-120">See also</span></span>

- [<span data-ttu-id="77152-121">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="77152-121">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="77152-122">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="77152-122">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
