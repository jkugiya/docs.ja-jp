---
description: '詳細について: IMetaDataConverter:: GetMetaDataFromTypeLib メソッド'
title: IMetaDataConverter::GetMetaDataFromTypeLib メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataConverter.GetMetaDataFromTypeLib
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter::GetMetaDataFromTypeLib
helpviewer_keywords:
- IMetaDataConverter::GetMetaDataFromTypeLib method [.NET Framework metadata]
- GetMetaDataFromTypeLib method [.NET Framework metadata]
ms.assetid: 97dc3a56-adfa-431f-889e-06a35ac84d51
topic_type:
- apiref
ms.openlocfilehash: d1ed5feb9f42ea0f8dc802c4dad527be5d2ed25f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789282"
---
# <a name="imetadataconvertergetmetadatafromtypelib-method"></a><span data-ttu-id="2f387-103">IMetaDataConverter::GetMetaDataFromTypeLib メソッド</span><span class="sxs-lookup"><span data-stu-id="2f387-103">IMetaDataConverter::GetMetaDataFromTypeLib Method</span></span>

<span data-ttu-id="2f387-104">指定したインスタンスによって表されるタイプライブラリのメタデータシグネチャを表す [IMetaDataImport](imetadataimport-interface.md) インスタンスへのインターフェイスポインターを取得し `ITypeLib` ます。</span><span class="sxs-lookup"><span data-stu-id="2f387-104">Gets an interface pointer to an [IMetaDataImport](imetadataimport-interface.md) instance that represents the metadata signature of the type library represented by the specified `ITypeLib` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f387-105">構文</span><span class="sxs-lookup"><span data-stu-id="2f387-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataFromTypeLib (  
    [in]  ITypeLib        *pITL,
    [out] IMetaDataImport **ppMDI  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f387-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2f387-106">Parameters</span></span>  

 `pITL`  
 <span data-ttu-id="2f387-107">から `ITypeLib` タイプライブラリを表すオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="2f387-107">[in] Pointer to an `ITypeLib` object that represents the type library.</span></span>  
  
 `ppMDI`  
 <span data-ttu-id="2f387-108">入出力メタデータシグネチャを表すインスタンスのアドレスを受け取る場所へのポインター `IMetaDataImport` 。</span><span class="sxs-lookup"><span data-stu-id="2f387-108">[out] Pointer to a location that receives the address of the `IMetaDataImport` instance that represents the metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f387-109">要件</span><span class="sxs-lookup"><span data-stu-id="2f387-109">Requirements</span></span>  

 <span data-ttu-id="2f387-110">**プラットフォーム:** 「 [システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f387-110">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f387-111">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="2f387-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2f387-112">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="2f387-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2f387-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f387-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f387-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="2f387-114">See also</span></span>

- [<span data-ttu-id="2f387-115">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2f387-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="2f387-116">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2f387-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
