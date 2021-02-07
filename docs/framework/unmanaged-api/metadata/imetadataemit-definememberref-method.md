---
description: '詳細について: IMetaDataEmit::D efineMemberRef メソッド'
title: IMetaDataEmit::DefineMemberRef メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMemberRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMemberRef
helpviewer_keywords:
- DefineMemberRef method [.NET Framework metadata]
- IMetaDataEmit::DefineMemberRef method [.NET Framework metadata]
ms.assetid: 21b5bcb8-ea75-4962-8acc-ad17584061e5
topic_type:
- apiref
ms.openlocfilehash: 1d88294cea14369c8a8f16b6048f96472fbb9502
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753420"
---
# <a name="imetadataemitdefinememberref-method"></a><span data-ttu-id="65139-103">IMetaDataEmit::DefineMemberRef メソッド</span><span class="sxs-lookup"><span data-stu-id="65139-103">IMetaDataEmit::DefineMemberRef Method</span></span>

<span data-ttu-id="65139-104">現在のスコープ外のモジュールのメンバーへの参照を定義し、その参照定義へのトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="65139-104">Defines a reference to a member of a module outside the current scope, and gets a token to that reference definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65139-105">構文</span><span class="sxs-lookup"><span data-stu-id="65139-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineMemberRef (
    [in]  mdToken           tkImport,
    [in]  LPCWSTR           szName,
    [in]  PCCOR_SIGNATURE   pvSigBlob,
    [in]  ULONG             cbSigBlob,
    [out] mdMemberRef       *pmr
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65139-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="65139-106">Parameters</span></span>  

 `tkImport`  
 <span data-ttu-id="65139-107">からメンバーがグローバルでない場合は、ターゲットメンバーのクラスまたはインターフェイスのトークン。メンバーがグローバルの場合は、 `mdModuleRef` その他のファイルのトークン。</span><span class="sxs-lookup"><span data-stu-id="65139-107">[in] Token for the target member's class or interface, if the member is not global; if the member is global, the `mdModuleRef` token for that other file.</span></span>  
  
 `szName`  
 <span data-ttu-id="65139-108">からターゲットメンバーの名前。</span><span class="sxs-lookup"><span data-stu-id="65139-108">[in] The name of the target member.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="65139-109">からターゲットメンバーのシグネチャ。</span><span class="sxs-lookup"><span data-stu-id="65139-109">[in] The signature of the target member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="65139-110">からのバイト数 `pvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="65139-110">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="65139-111">入出力 `mdMemberRef` 割り当てられたトークン。</span><span class="sxs-lookup"><span data-stu-id="65139-111">[out] The `mdMemberRef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65139-112">要件</span><span class="sxs-lookup"><span data-stu-id="65139-112">Requirements</span></span>  

 <span data-ttu-id="65139-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="65139-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65139-114">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="65139-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="65139-115">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="65139-115">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="65139-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65139-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65139-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="65139-117">See also</span></span>

- [<span data-ttu-id="65139-118">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="65139-118">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="65139-119">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="65139-119">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
