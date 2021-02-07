---
description: '詳細について: IMetaDataEmit2::D efineMethodSpec メソッド'
title: IMetaDataEmit2::DefineMethodSpec メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.DefineMethodSpec
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::DefineMethodSpec
helpviewer_keywords:
- DefineMethodSpec method [.NET Framework metadata]
- IMetaDataEmit2::DefineMethodSpec method [.NET Framework metadata]
ms.assetid: 3c24e552-fc69-4971-b65a-a3e4b5f7f1e8
topic_type:
- apiref
ms.openlocfilehash: 4b5283375ba194a86a83b142b3b2bdc06bfd35da
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745737"
---
# <a name="imetadataemit2definemethodspec-method"></a><span data-ttu-id="ce556-103">IMetaDataEmit2::DefineMethodSpec メソッド</span><span class="sxs-lookup"><span data-stu-id="ce556-103">IMetaDataEmit2::DefineMethodSpec Method</span></span>

<span data-ttu-id="ce556-104">メソッドのジェネリックインスタンスを作成し、その定義へのトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="ce556-104">Creates a generic instance of a method, and gets a token to the definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce556-105">構文</span><span class="sxs-lookup"><span data-stu-id="ce556-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodSpec (  
    [in]  mdToken           tkParent,
    [in]  PCCOR_SIGNATURE   pvSigBlob,
    [in]  ULONG             cbSigBlob,
    [out] mdMethodSpec      *pmi  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce556-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ce556-106">Parameters</span></span>  

 `tkParent`  
 <span data-ttu-id="ce556-107">からジェネリックインスタンスを作成するメソッドのトークン。</span><span class="sxs-lookup"><span data-stu-id="ce556-107">[in] A token for the method of which to create the generic instance.</span></span> <span data-ttu-id="ce556-108">トークンは、型または型である必要があり `mdMethodDef` `mdMemberRef` ます。</span><span class="sxs-lookup"><span data-stu-id="ce556-108">The token must be of type `mdMethodDef` or `mdMemberRef`.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="ce556-109">からメソッドのバイナリ COM + シグネチャへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ce556-109">[in] A pointer to the binary COM+ signature of the method.</span></span>  
  
 `cbSibBlob`  
 <span data-ttu-id="ce556-110">からのサイズ (バイト単位) `pvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="ce556-110">[in] The size, in bytes, of `pvSigBlob`.</span></span>  
  
 `pmi`  
 <span data-ttu-id="ce556-111">入出力メソッドのメタデータシグネチャ定義へのトークン。</span><span class="sxs-lookup"><span data-stu-id="ce556-111">[out] A token to the metadata signature definition of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce556-112">要件</span><span class="sxs-lookup"><span data-stu-id="ce556-112">Requirements</span></span>  

 <span data-ttu-id="ce556-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ce556-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce556-114">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="ce556-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ce556-115">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="ce556-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ce556-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce556-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce556-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="ce556-117">See also</span></span>

- [<span data-ttu-id="ce556-118">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ce556-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="ce556-119">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ce556-119">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
