---
description: '詳細について: IMetaDataImport:: GetScopeProps メソッド'
title: IMetaDataImport::GetScopeProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetScopeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetScopeProps
helpviewer_keywords:
- IMetaDataImport::GetScopeProps method [.NET Framework metadata]
- GetScopeProps method [.NET Framework metadata]
ms.assetid: c8ba42d2-d9fa-43cb-bbc0-f33e1e592cb6
topic_type:
- apiref
ms.openlocfilehash: 2ed7c08cc876f467a46fe38c7c27719e5608e623
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789152"
---
# <a name="imetadataimportgetscopeprops-method"></a><span data-ttu-id="dc276-103">IMetaDataImport::GetScopeProps メソッド</span><span class="sxs-lookup"><span data-stu-id="dc276-103">IMetaDataImport::GetScopeProps Method</span></span>

<span data-ttu-id="dc276-104">現在のメタデータ スコープにあるアセンブリまたはモジュールの名前、およびオプションでバージョン ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="dc276-104">Gets the name and optionally the version identifier of the assembly or module in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc276-105">構文</span><span class="sxs-lookup"><span data-stu-id="dc276-105">Syntax</span></span>  
  
```cpp  
HRESULT GetScopeProps (  
   [out] LPWSTR           szName,  
   [in]  ULONG            cchName,  
   [out] ULONG            *pchName,  
   [out, optional] GUID   *pmvid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dc276-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="dc276-106">Parameters</span></span>  

 `szName`  
 <span data-ttu-id="dc276-107">入出力アセンブリ名またはモジュール名のバッファー。</span><span class="sxs-lookup"><span data-stu-id="dc276-107">[out] A buffer for the assembly or module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="dc276-108">からのワイド文字のサイズ `szName` 。</span><span class="sxs-lookup"><span data-stu-id="dc276-108">[in] The size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="dc276-109">入出力で返されたワイド文字の数 `szName` 。</span><span class="sxs-lookup"><span data-stu-id="dc276-109">[out] The number of wide characters returned in `szName`.</span></span>  
  
 `pmvid`  
 <span data-ttu-id="dc276-110">[out、省略可能]アセンブリまたはモジュールのバージョンを一意に識別する GUID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="dc276-110">[out, optional] A pointer to a GUID that uniquely identifies the version of the assembly or module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc276-111">解説</span><span class="sxs-lookup"><span data-stu-id="dc276-111">Remarks</span></span>  

 <span data-ttu-id="dc276-112">これらのプロパティを設定するには、 [IMetaDataEmit:: SetModuleProps](imetadataemit-setmoduleprops-method.md) メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="dc276-112">The [IMetaDataEmit::SetModuleProps](imetadataemit-setmoduleprops-method.md) method is used to set these properties.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc276-113">要件</span><span class="sxs-lookup"><span data-stu-id="dc276-113">Requirements</span></span>  

 <span data-ttu-id="dc276-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc276-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc276-115">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="dc276-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dc276-116">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="dc276-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dc276-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc276-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc276-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="dc276-118">See also</span></span>

- [<span data-ttu-id="dc276-119">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dc276-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="dc276-120">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dc276-120">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
