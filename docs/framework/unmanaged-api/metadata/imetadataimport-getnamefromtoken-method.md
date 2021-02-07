---
description: '詳細について: IMetaDataImport:: GetNameFromToken メソッド'
title: IMetaDataImport::GetNameFromToken メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetNameFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNameFromToken
helpviewer_keywords:
- GetNameFromToken method [.NET Framework metadata]
- IMetaDataImport::GetNameFromToken method [.NET Framework metadata]
ms.assetid: 32114ecf-8916-4ab2-a201-179c017344f1
topic_type:
- apiref
ms.openlocfilehash: 6195020a2b291a47e908b257896bdba64b0a40d9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99720853"
---
# <a name="imetadataimportgetnamefromtoken-method"></a><span data-ttu-id="37b6d-103">IMetaDataImport::GetNameFromToken メソッド</span><span class="sxs-lookup"><span data-stu-id="37b6d-103">IMetaDataImport::GetNameFromToken Method</span></span>

<span data-ttu-id="37b6d-104">指定したメタデータ トークンによって参照されるオブジェクトの UTF-8 名を取得します。</span><span class="sxs-lookup"><span data-stu-id="37b6d-104">Gets the UTF-8 name of the object referenced by the specified metadata token.</span></span> <span data-ttu-id="37b6d-105">このメソッドは、互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="37b6d-105">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37b6d-106">構文</span><span class="sxs-lookup"><span data-stu-id="37b6d-106">Syntax</span></span>  
  
```cpp  
HRESULT GetNameFromToken (  
   [in] mdToken      tk,  
   [out] MDUTF8CSTR  *pszUtf8NamePtr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37b6d-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="37b6d-107">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="37b6d-108">から名前を返すオブジェクトを表すトークン。</span><span class="sxs-lookup"><span data-stu-id="37b6d-108">[in] The token representing the object to return the name for.</span></span>  
  
 `pszUtf8NamePtr`  
 <span data-ttu-id="37b6d-109">入出力ヒープ内の UTF-8 オブジェクト名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="37b6d-109">[out] A pointer to the UTF-8 object name in the heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37b6d-110">解説</span><span class="sxs-lookup"><span data-stu-id="37b6d-110">Remarks</span></span>  

 <span data-ttu-id="37b6d-111">`GetNameFromToken` は互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="37b6d-111">`GetNameFromToken` is obsolete.</span></span> <span data-ttu-id="37b6d-112">別の方法として、フィールドやメソッドなど、必要な特定の種類のトークンのプロパティを取得するには、メソッドを呼び出し `GetFieldProps` `GetMethodProps` ます。</span><span class="sxs-lookup"><span data-stu-id="37b6d-112">As an alternative, call a method to get the properties of the particular type of token required, such as `GetFieldProps` for a field or `GetMethodProps` for a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37b6d-113">要件</span><span class="sxs-lookup"><span data-stu-id="37b6d-113">Requirements</span></span>  

 <span data-ttu-id="37b6d-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="37b6d-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37b6d-115">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="37b6d-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="37b6d-116">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="37b6d-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="37b6d-117">**.NET Framework のバージョン:** 1.0</span><span class="sxs-lookup"><span data-stu-id="37b6d-117">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37b6d-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="37b6d-118">See also</span></span>

- [<span data-ttu-id="37b6d-119">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="37b6d-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="37b6d-120">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="37b6d-120">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
