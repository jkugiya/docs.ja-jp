---
description: '詳細について: IMetaDataImport:: IsValidToken メソッド'
title: IMetaDataImport::IsValidToken メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.IsValidToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::IsValidToken
helpviewer_keywords:
- IMetaDataImport::IsValidToken method [.NET Framework metadata]
- IsValidToken method [.NET Framework metadata]
ms.assetid: aeb0fc63-9eff-4384-9284-cb9900572d74
topic_type:
- apiref
ms.openlocfilehash: 68589496213c93f81cfbd0992f9b210e03d6f178
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789061"
---
# <a name="imetadataimportisvalidtoken-method"></a><span data-ttu-id="7f9c6-103">IMetaDataImport::IsValidToken メソッド</span><span class="sxs-lookup"><span data-stu-id="7f9c6-103">IMetaDataImport::IsValidToken Method</span></span>

<span data-ttu-id="7f9c6-104">指定したトークンが、コード オブジェクトへの有効な参照を保持しているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="7f9c6-104">Gets a value indicating whether the specified token holds a valid reference to a code object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f9c6-105">構文</span><span class="sxs-lookup"><span data-stu-id="7f9c6-105">Syntax</span></span>  
  
```cpp  
BOOL IsValidToken (  
   [in] mdToken     tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f9c6-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7f9c6-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="7f9c6-107">から参照の有効性を確認するトークン。</span><span class="sxs-lookup"><span data-stu-id="7f9c6-107">[in] The token to check the reference validity for.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7f9c6-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="7f9c6-108">Return Value</span></span>  

 <span data-ttu-id="7f9c6-109">`true``tk`が現在のスコープ内の有効なメタデータトークンである場合は。</span><span class="sxs-lookup"><span data-stu-id="7f9c6-109">`true` if `tk` is a valid metadata token within the current scope.</span></span> <span data-ttu-id="7f9c6-110">それ以外の場合は `false`。</span><span class="sxs-lookup"><span data-stu-id="7f9c6-110">Otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f9c6-111">要件</span><span class="sxs-lookup"><span data-stu-id="7f9c6-111">Requirements</span></span>  

 <span data-ttu-id="7f9c6-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7f9c6-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f9c6-113">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="7f9c6-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7f9c6-114">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="7f9c6-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7f9c6-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f9c6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f9c6-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="7f9c6-116">See also</span></span>

- [<span data-ttu-id="7f9c6-117">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7f9c6-117">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="7f9c6-118">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7f9c6-118">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
