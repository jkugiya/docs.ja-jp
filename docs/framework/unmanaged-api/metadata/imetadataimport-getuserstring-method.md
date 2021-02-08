---
description: '詳細情報: IMetaDataImport:: GetUserString メソッド'
title: IMetaDataImport::GetUserString メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetUserString
helpviewer_keywords:
- IMetaDataImport::GetUserString method [.NET Framework metadata]
- GetUserString method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 0fd3bb47-58b5-4083-b241-b9719df7a285
topic_type:
- apiref
ms.openlocfilehash: 074d196c74be30f5879410ad44b9bb5c096eb153
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789100"
---
# <a name="imetadataimportgetuserstring-method"></a><span data-ttu-id="3e46e-103">IMetaDataImport::GetUserString メソッド</span><span class="sxs-lookup"><span data-stu-id="3e46e-103">IMetaDataImport::GetUserString Method</span></span>

<span data-ttu-id="3e46e-104">指定したメタデータ トークンで表されるリテラル文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="3e46e-104">Gets the literal string represented by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e46e-105">構文</span><span class="sxs-lookup"><span data-stu-id="3e46e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetUserString (  
   [in]   mdString    stk,  
   [out]  LPWSTR      szString,  
   [in]   ULONG       cchString,  
   [out]  ULONG       *pchString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e46e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3e46e-106">Parameters</span></span>  

 `stk`  
 <span data-ttu-id="3e46e-107">から関連付けられている文字列を返す文字列トークン。</span><span class="sxs-lookup"><span data-stu-id="3e46e-107">[in] The String token to return the associated string for.</span></span>  
  
 `szString`  
 <span data-ttu-id="3e46e-108">入出力要求された文字列のコピー。</span><span class="sxs-lookup"><span data-stu-id="3e46e-108">[out] A copy of the requested string.</span></span>  
  
 `cchString`  
 <span data-ttu-id="3e46e-109">から要求されたのワイド文字単位の最大サイズ `szString` 。</span><span class="sxs-lookup"><span data-stu-id="3e46e-109">[in] The maximum size in wide characters of the requested `szString`.</span></span>  
  
 `pchString`  
 <span data-ttu-id="3e46e-110">入出力返されたのワイド文字のサイズ `szString` 。</span><span class="sxs-lookup"><span data-stu-id="3e46e-110">[out] The size in wide characters of the returned `szString`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e46e-111">要件</span><span class="sxs-lookup"><span data-stu-id="3e46e-111">Requirements</span></span>  

 <span data-ttu-id="3e46e-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3e46e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e46e-113">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="3e46e-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3e46e-114">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="3e46e-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3e46e-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e46e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e46e-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="3e46e-116">See also</span></span>

- [<span data-ttu-id="3e46e-117">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3e46e-117">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="3e46e-118">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3e46e-118">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
