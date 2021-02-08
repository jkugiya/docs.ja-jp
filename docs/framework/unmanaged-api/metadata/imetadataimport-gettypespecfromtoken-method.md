---
description: '詳細については、次を参照してください: IMetaDataImport:: Gettyp Ecfromtoken メソッド'
title: IMetaDataImport::GetTypeSpecFromToken メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeSpecFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeSpecFromToken
helpviewer_keywords:
- GetTypeSpecFromToken method [.NET Framework metadata]
- IMetaDataImport::GetTypeSpecFromToken method [.NET Framework metadata]
ms.assetid: ee518bda-3296-482e-a7b7-e9d51dd1a181
topic_type:
- apiref
ms.openlocfilehash: b71f8f856da517b3e5046c20d787a555816fb728
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789113"
---
# <a name="imetadataimportgettypespecfromtoken-method"></a><span data-ttu-id="231cf-103">IMetaDataImport::GetTypeSpecFromToken メソッド</span><span class="sxs-lookup"><span data-stu-id="231cf-103">IMetaDataImport::GetTypeSpecFromToken Method</span></span>

<span data-ttu-id="231cf-104">指定したトークンが表すタイプ仕様のバイナリ メタデータ シグネチャを取得します。</span><span class="sxs-lookup"><span data-stu-id="231cf-104">Gets the binary metadata signature of the type specification represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="231cf-105">構文</span><span class="sxs-lookup"><span data-stu-id="231cf-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeSpecFromToken (
   [in]  mdTypeSpec            typespec,
   [out] PCCOR_SIGNATURE       *ppvSig,
   [out] ULONG                 *pcbSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="231cf-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="231cf-106">Parameters</span></span>  

 `typespec`  
 <span data-ttu-id="231cf-107">から要求されたメタデータ署名に関連付けられている TypeSpec トークン。</span><span class="sxs-lookup"><span data-stu-id="231cf-107">[in] The TypeSpec token associated with the requested metadata signature.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="231cf-108">入出力バイナリメタデータシグネチャへのポインター。</span><span class="sxs-lookup"><span data-stu-id="231cf-108">[out] A pointer to the binary metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="231cf-109">入出力メタデータシグネチャのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="231cf-109">[out] The size, in bytes, of the metadata signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="231cf-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="231cf-110">Return Value</span></span>  

 <span data-ttu-id="231cf-111">成功または失敗を示す HRESULT。</span><span class="sxs-lookup"><span data-stu-id="231cf-111">An HRESULT that indicates success or failure.</span></span> <span data-ttu-id="231cf-112">失敗したマクロを使用してエラーをテストできます。</span><span class="sxs-lookup"><span data-stu-id="231cf-112">Failures can be tested with the FAILED macro.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="231cf-113">要件</span><span class="sxs-lookup"><span data-stu-id="231cf-113">Requirements</span></span>  

 <span data-ttu-id="231cf-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="231cf-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="231cf-115">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="231cf-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="231cf-116">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="231cf-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="231cf-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="231cf-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="231cf-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="231cf-118">See also</span></span>

- [<span data-ttu-id="231cf-119">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="231cf-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="231cf-120">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="231cf-120">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
