---
description: '詳細について: IMetaDataConverter:: GetMetaDataFromTypeInfo メソッド'
title: IMetaDataConverter::GetMetaDataFromTypeInfo メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataConverter.GetMetaDataFromTypeInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter::GetMetaDataFromTypeInfo
helpviewer_keywords:
- GetMetaDataFromTypeInfo method [.NET Framework metadata]
- IMetaDataConverter::GetMetaDataFromTypeInfo method [.NET Framework metadata]
ms.assetid: d44484bb-23a3-49c3-9e46-69d0d9ab4f0f
topic_type:
- apiref
ms.openlocfilehash: 224be07463b19ed9e22bef1a9d454d91a8086304
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753628"
---
# <a name="imetadataconvertergetmetadatafromtypeinfo-method"></a><span data-ttu-id="166af-103">IMetaDataConverter::GetMetaDataFromTypeInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="166af-103">IMetaDataConverter::GetMetaDataFromTypeInfo Method</span></span>

<span data-ttu-id="166af-104">指定したインスタンスによって参照されるタイプライブラリのメタデータシグネチャを表す [IMetaDataImport](imetadataimport-interface.md) インスタンスへのポインターを取得し `ITypeInfo` ます。</span><span class="sxs-lookup"><span data-stu-id="166af-104">Gets a pointer to an [IMetaDataImport](imetadataimport-interface.md) instance that represents the metadata signature of the type library referenced by the specified `ITypeInfo` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="166af-105">構文</span><span class="sxs-lookup"><span data-stu-id="166af-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataFromTypeInfo (  
    [in]  ITypeInfo         *pITI,  
    [out] IMetaDataImport   **ppMDI  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="166af-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="166af-106">Parameters</span></span>  

 `pITI`  
 <span data-ttu-id="166af-107">から `ITypeInfo` タイプライブラリを参照するオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="166af-107">[in] A pointer to an `ITypeInfo` object that refers to the type library.</span></span>  
  
 `ppMDI`  
 <span data-ttu-id="166af-108">入出力メタデータシグネチャを表すインスタンスのアドレスを受け取る場所へのポインター `IMetaDataImport` 。</span><span class="sxs-lookup"><span data-stu-id="166af-108">[out] A pointer to a location that receives the address of the `IMetaDataImport` instance that represents the metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="166af-109">要件</span><span class="sxs-lookup"><span data-stu-id="166af-109">Requirements</span></span>  

 <span data-ttu-id="166af-110">**プラットフォーム:** 「 [システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="166af-110">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="166af-111">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="166af-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="166af-112">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="166af-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="166af-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="166af-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="166af-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="166af-114">See also</span></span>

- [<span data-ttu-id="166af-115">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="166af-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="166af-116">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="166af-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
