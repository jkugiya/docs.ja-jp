---
description: '詳細について: IMetaDataImport2:: GetMethodSpecProps メソッド'
title: IMetaDataImport2::GetMethodSpecProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetMethodSpecProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetMethodSpecProps
helpviewer_keywords:
- GetMethodSpecProps method [.NET Framework metadata]
- IMetaDataImport2::GetMethodSpecProps method [.NET Framework metadata]
ms.assetid: 9544b711-e669-4eaf-8630-ee862e5e4489
topic_type:
- apiref
ms.openlocfilehash: 77f3f78905d1f7f44af0e9c7a75746b4e5b6e684
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688651"
---
# <a name="imetadataimport2getmethodspecprops-method"></a><span data-ttu-id="15c2d-103">IMetaDataImport2::GetMethodSpecProps メソッド</span><span class="sxs-lookup"><span data-stu-id="15c2d-103">IMetaDataImport2::GetMethodSpecProps Method</span></span>

<span data-ttu-id="15c2d-104">指定した MethodSpec トークンによって参照されるメソッドのメタデータシグネチャを取得します。</span><span class="sxs-lookup"><span data-stu-id="15c2d-104">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15c2d-105">構文</span><span class="sxs-lookup"><span data-stu-id="15c2d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodSpecProps (  
   [in]  mdMethodSpec     mi,  
   [out] mdToken          *tkParent,  
   [out] PCCOR_SIGNATURE  *ppvSigBlob,
   [out] ULONG            *pcbSigBlob  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="15c2d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="15c2d-106">Parameters</span></span>  

 `mi`  
 <span data-ttu-id="15c2d-107">からメソッドのインスタンス化を表す MethodSpec トークン。</span><span class="sxs-lookup"><span data-stu-id="15c2d-107">[in] A MethodSpec token that represents the instantiation of the method.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="15c2d-108">入出力メソッド定義を表す MethodDef または MethodRef トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="15c2d-108">[out] A pointer to the MethodDef or MethodRef token that represents the method definition.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="15c2d-109">入出力メソッドのバイナリメタデータシグネチャへのポインター。</span><span class="sxs-lookup"><span data-stu-id="15c2d-109">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="15c2d-110">入出力のサイズ (バイト単位) `ppvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="15c2d-110">[out] The size, in bytes, of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15c2d-111">要件</span><span class="sxs-lookup"><span data-stu-id="15c2d-111">Requirements</span></span>  

 <span data-ttu-id="15c2d-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="15c2d-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15c2d-113">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="15c2d-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="15c2d-114">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="15c2d-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="15c2d-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15c2d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15c2d-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="15c2d-116">See also</span></span>

- [<span data-ttu-id="15c2d-117">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="15c2d-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="15c2d-118">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="15c2d-118">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
