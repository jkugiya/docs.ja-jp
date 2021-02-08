---
description: '詳細情報: IMetaDataImport:: IsGlobal メソッド'
title: IMetaDataImport::IsGlobal メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.IsGlobal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::IsGlobal
helpviewer_keywords:
- IsGlobal method [.NET Framework metadata]
- IMetaDataImport::IsGlobal method [.NET Framework metadata]
ms.assetid: 44cf6908-f555-4ae8-b2cf-24bd974bf2fe
topic_type:
- apiref
ms.openlocfilehash: 5230b2967990e3c52b429d62dd03566c3043e45f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789074"
---
# <a name="imetadataimportisglobal-method"></a><span data-ttu-id="b24d8-103">IMetaDataImport::IsGlobal メソッド</span><span class="sxs-lookup"><span data-stu-id="b24d8-103">IMetaDataImport::IsGlobal Method</span></span>

<span data-ttu-id="b24d8-104">指定したメタデータ トークンによって表されるフィールド、メソッド、または型がグローバル スコープを保持しているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="b24d8-104">Gets a value indicating whether the field, method, or type represented by the specified metadata token has global scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b24d8-105">構文</span><span class="sxs-lookup"><span data-stu-id="b24d8-105">Syntax</span></span>  
  
```cpp  
HRESULT IsGlobal (  
   [in]  mdToken     pd,  
   [out] int         *pbGlobal  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b24d8-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b24d8-106">Parameters</span></span>  

 `pd`  
 <span data-ttu-id="b24d8-107">から型、フィールド、またはメソッドを表すメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="b24d8-107">[in] A metadata token that represents a type, field, or method.</span></span>  
  
 `pbGlobal`  
 <span data-ttu-id="b24d8-108">[out] 1: オブジェクトにグローバルスコープがある場合は、それ以外の場合は 0 (ゼロ)。</span><span class="sxs-lookup"><span data-stu-id="b24d8-108">[out] 1 if the object has global scope; otherwise, 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b24d8-109">要件</span><span class="sxs-lookup"><span data-stu-id="b24d8-109">Requirements</span></span>  

 <span data-ttu-id="b24d8-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b24d8-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b24d8-111">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="b24d8-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b24d8-112">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="b24d8-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b24d8-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b24d8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b24d8-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="b24d8-114">See also</span></span>

- [<span data-ttu-id="b24d8-115">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b24d8-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="b24d8-116">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b24d8-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
