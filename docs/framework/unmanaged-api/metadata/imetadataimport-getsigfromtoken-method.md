---
description: '詳細について: IMetaDataImport:: GetSigFromToken メソッド'
title: IMetaDataImport::GetSigFromToken メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetSigFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetSigFromToken
helpviewer_keywords:
- IMetaDataImport::GetSigFromToken method [.NET Framework metadata]
- GetSigFromToken method [.NET Framework metadata]
ms.assetid: ab894dc4-f7b6-4afc-bfcb-582a4b7e53a2
topic_type:
- apiref
ms.openlocfilehash: 16b77fe5866319e24b33ec4ce9d2d56797f04514
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789139"
---
# <a name="imetadataimportgetsigfromtoken-method"></a><span data-ttu-id="fd129-103">IMetaDataImport::GetSigFromToken メソッド</span><span class="sxs-lookup"><span data-stu-id="fd129-103">IMetaDataImport::GetSigFromToken Method</span></span>

<span data-ttu-id="fd129-104">指定したトークンに関連付けられているバイナリ メタデータ シグネチャを取得します。</span><span class="sxs-lookup"><span data-stu-id="fd129-104">Gets the binary metadata signature associated with the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd129-105">構文</span><span class="sxs-lookup"><span data-stu-id="fd129-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSigFromToken (
   [in]   mdSignature        mdSig,
   [out]  PCCOR_SIGNATURE    *ppvSig,
   [out]  ULONG              *pcbSig
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd129-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fd129-106">Parameters</span></span>  

 `mdSig`  
 <span data-ttu-id="fd129-107">からバイナリメタデータシグネチャを返すトークン。</span><span class="sxs-lookup"><span data-stu-id="fd129-107">[in] The token to return the binary metadata signature for.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="fd129-108">入出力返されたメタデータシグネチャへのポインター。</span><span class="sxs-lookup"><span data-stu-id="fd129-108">[out] A pointer to the returned metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="fd129-109">入出力バイナリメタデータシグネチャのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="fd129-109">[out] The size in bytes of the binary metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd129-110">要件</span><span class="sxs-lookup"><span data-stu-id="fd129-110">Requirements</span></span>  

 <span data-ttu-id="fd129-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd129-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd129-112">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="fd129-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fd129-113">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="fd129-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fd129-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd129-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd129-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="fd129-115">See also</span></span>

- [<span data-ttu-id="fd129-116">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fd129-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="fd129-117">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fd129-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
