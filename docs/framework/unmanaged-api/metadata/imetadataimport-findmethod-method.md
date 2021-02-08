---
description: '詳細情報: IMetaDataImport:: FindMethod メソッド'
title: IMetaDataImport::FindMethod メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMethod
helpviewer_keywords:
- FindMethod method [.NET Framework metadata]
- IMetaDataImport::FindMethod method [.NET Framework metadata]
ms.assetid: 0f9bde1d-e306-438d-941b-d0925b322304
topic_type:
- apiref
ms.openlocfilehash: 0d2866554fcb4dcf3984310e4da24d501f1fc7b6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803556"
---
# <a name="imetadataimportfindmethod-method"></a><span data-ttu-id="8e447-103">IMetaDataImport::FindMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="8e447-103">IMetaDataImport::FindMethod Method</span></span>

<span data-ttu-id="8e447-104">指定した <xref:System.Type> と指定した名前とメタデータシグネチャを持つメソッドの MethodDef トークンへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="8e447-104">Gets a pointer to the MethodDef token for the method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e447-105">構文</span><span class="sxs-lookup"><span data-stu-id="8e447-105">Syntax</span></span>  
  
```cpp  
HRESULT FindMethod (  
   [in]  mdTypeDef          td,  
   [in]  LPCWSTR            szName,
   [in]  PCCOR_SIGNATURE    pvSigBlob,
   [in]  ULONG              cbSigBlob,
   [out] mdMethodDef        *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8e447-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8e447-106">Parameters</span></span>  

 `td`  
 <span data-ttu-id="8e447-107">から検索対象の `mdTypeDef` メンバーを囲む型 (クラスまたはインターフェイス) のトークン。</span><span class="sxs-lookup"><span data-stu-id="8e447-107">[in] The `mdTypeDef` token for the type (a class or interface) that encloses the member to search for.</span></span> <span data-ttu-id="8e447-108">この値がの場合は `mdTokenNil` 、グローバル関数の参照が行われます。</span><span class="sxs-lookup"><span data-stu-id="8e447-108">If this value is `mdTokenNil`, then the lookup is done for a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="8e447-109">から検索するメソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="8e447-109">[in] The name of the method to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="8e447-110">からメソッドのバイナリメタデータシグネチャへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8e447-110">[in] A pointer to the binary metadata signature of the method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="8e447-111">からのサイズ (バイト単位) `pvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="8e447-111">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="8e447-112">入出力一致する MethodDef トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8e447-112">[out] A pointer to the matching MethodDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8e447-113">解説</span><span class="sxs-lookup"><span data-stu-id="8e447-113">Remarks</span></span>  

 <span data-ttu-id="8e447-114">メソッドは、外側のクラスまたはインターフェイス ( `td` )、その名前 ( `szName` )、および必要に応じてシグネチャ () を使用して指定し `pvSigBlob` ます。</span><span class="sxs-lookup"><span data-stu-id="8e447-114">You specify the method using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="8e447-115">クラスまたはインターフェイスに同じ名前のメソッドが複数存在する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8e447-115">There might be multiple methods with the same name in a class or interface.</span></span> <span data-ttu-id="8e447-116">その場合は、メソッドのシグネチャを渡して、一意の一致を検索します。</span><span class="sxs-lookup"><span data-stu-id="8e447-116">In that case, pass the method's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="8e447-117">署名は特定のスコープにバインドされるため、に渡されるシグネチャは、 `FindMethod` 現在のスコープで生成される必要があります。</span><span class="sxs-lookup"><span data-stu-id="8e447-117">The signature passed to `FindMethod` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="8e447-118">署名には、外側のクラスまたは値の型を識別するトークンを埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="8e447-118">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="8e447-119">トークンは、ローカルの TypeDef テーブルのインデックスです。</span><span class="sxs-lookup"><span data-stu-id="8e447-119">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="8e447-120">現在のスコープのコンテキスト外でランタイムシグネチャを作成し、その署名を入力として使用してへの入力として使用することはできません `FindMethod` 。</span><span class="sxs-lookup"><span data-stu-id="8e447-120">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMethod`.</span></span>  
  
 <span data-ttu-id="8e447-121">`FindMethod` クラスまたはインターフェイスで直接定義されたメソッドのみを検索します。継承されたメソッドは見つかりません。</span><span class="sxs-lookup"><span data-stu-id="8e447-121">`FindMethod` finds only methods that were defined directly in the class or interface; it does not find inherited methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e447-122">要件</span><span class="sxs-lookup"><span data-stu-id="8e447-122">Requirements</span></span>  

 <span data-ttu-id="8e447-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e447-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e447-124">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="8e447-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8e447-125">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="8e447-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8e447-126">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e447-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e447-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="8e447-127">See also</span></span>

- <xref:System.Reflection.MethodInfo>
- [<span data-ttu-id="8e447-128">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8e447-128">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="8e447-129">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8e447-129">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
