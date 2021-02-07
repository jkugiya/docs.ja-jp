---
description: '詳細情報: IMetaDataAssemblyImport:: EnumFiles メソッド'
title: IMetaDataAssemblyImport::EnumFiles メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumFiles
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumFiles
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumFiles method [.NET Framework metadata]
- EnumFiles method [.NET Framework metadata]
ms.assetid: f0d721e2-b946-426d-8e20-9124bd04e4cb
topic_type:
- apiref
ms.openlocfilehash: 25282edd081e937e4c84334f9f004e201b9db46f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671023"
---
# <a name="imetadataassemblyimportenumfiles-method"></a><span data-ttu-id="13934-103">IMetaDataAssemblyImport::EnumFiles メソッド</span><span class="sxs-lookup"><span data-stu-id="13934-103">IMetaDataAssemblyImport::EnumFiles Method</span></span>

<span data-ttu-id="13934-104">現在のアセンブリマニフェストで参照されているファイルを列挙します。</span><span class="sxs-lookup"><span data-stu-id="13934-104">Enumerates the files referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13934-105">構文</span><span class="sxs-lookup"><span data-stu-id="13934-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumFiles (  
    [in, out] HCORENUM    *phEnum,
    [out] mdFile          rFiles[],
    [in]  ULONG           cMax,
    [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13934-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="13934-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="13934-107">[入力、出力]列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="13934-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="13934-108">このメソッドの最初の呼び出しでは、null 値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="13934-108">This must be a null value for the first call of this method.</span></span>  
  
 `rFiles`  
 <span data-ttu-id="13934-109">入出力メタデータトークンを格納するために使用される配列 `mdFile` 。</span><span class="sxs-lookup"><span data-stu-id="13934-109">[out] The array used to store the `mdFile` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="13934-110">から `mdFile` に格納できるトークンの最大数 `rFiles` 。</span><span class="sxs-lookup"><span data-stu-id="13934-110">[in] The maximum number of `mdFile` tokens that can be placed in `rFiles`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="13934-111">入出力 `mdFile` 実際に配置されたトークンの数 `rFiles` 。</span><span class="sxs-lookup"><span data-stu-id="13934-111">[out] The number of `mdFile` tokens actually placed in `rFiles`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="13934-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="13934-112">Return Value</span></span>  
  
|<span data-ttu-id="13934-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="13934-113">HRESULT</span></span>|<span data-ttu-id="13934-114">説明</span><span class="sxs-lookup"><span data-stu-id="13934-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="13934-115">`EnumFiles` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="13934-115">`EnumFiles` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="13934-116">列挙するトークンがありません。</span><span class="sxs-lookup"><span data-stu-id="13934-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="13934-117">この場合、 `pcTokens` は0に設定されます。</span><span class="sxs-lookup"><span data-stu-id="13934-117">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="13934-118">要件</span><span class="sxs-lookup"><span data-stu-id="13934-118">Requirements</span></span>  

 <span data-ttu-id="13934-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="13934-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13934-120">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="13934-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="13934-121">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="13934-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="13934-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13934-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13934-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="13934-123">See also</span></span>

- [<span data-ttu-id="13934-124">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="13934-124">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
