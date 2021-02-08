---
description: '詳細について: IMetaDataImport:: GetFieldMarshal メソッド'
title: IMetaDataImport::GetFieldMarshal メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetFieldMarshal
helpviewer_keywords:
- GetFieldMarshal method [.NET Framework metadata]
- IMetaDataImport::GetFieldMarshal method [.NET Framework metadata]
ms.assetid: 4e2d88c6-8a3a-4fbe-900b-b4f4c06bf6bf
topic_type:
- apiref
ms.openlocfilehash: d6ca1f80a8b9bae4d9c02466042300bc3662f7c3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803517"
---
# <a name="imetadataimportgetfieldmarshal-method"></a><span data-ttu-id="8f869-103">IMetaDataImport::GetFieldMarshal メソッド</span><span class="sxs-lookup"><span data-stu-id="8f869-103">IMetaDataImport::GetFieldMarshal Method</span></span>

<span data-ttu-id="8f869-104">指定されたフィールドメタデータトークンによって表されるフィールドの、ネイティブなアンマネージ型へのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="8f869-104">Gets a pointer to the native, unmanaged type of the field represented by the specified field metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f869-105">構文</span><span class="sxs-lookup"><span data-stu-id="8f869-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFieldMarshal (  
   [in]  mdToken             tk,
   [out] PCCOR_SIGNATURE     *ppvNativeType,  
   [out] ULONG               *pcbNativeType
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f869-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8f869-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="8f869-107">から相互運用マーシャリング情報を取得するフィールドを表すメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="8f869-107">[in] The metadata token that represents the field to get interop marshaling information for.</span></span>  
  
 `ppvNativeType`  
 <span data-ttu-id="8f869-108">入出力フィールドのネイティブ型のメタデータシグネチャへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8f869-108">[out] A pointer to the metadata signature of the field's native type.</span></span>  
  
 `pcbNativeType`  
 <span data-ttu-id="8f869-109">入出力のサイズ (バイト単位) `ppvNativeType` 。</span><span class="sxs-lookup"><span data-stu-id="8f869-109">[out] The size in bytes of `ppvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f869-110">要件</span><span class="sxs-lookup"><span data-stu-id="8f869-110">Requirements</span></span>  

 <span data-ttu-id="8f869-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8f869-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f869-112">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="8f869-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8f869-113">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="8f869-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8f869-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f869-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f869-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="8f869-115">See also</span></span>

- [<span data-ttu-id="8f869-116">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8f869-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="8f869-117">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8f869-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
