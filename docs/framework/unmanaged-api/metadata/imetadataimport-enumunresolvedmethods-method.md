---
description: '詳細について: IMetaDataImport:: EnumUnresolvedMethods メソッド'
title: IMetaDataImport::EnumUnresolvedMethods メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumUnresolvedMethods
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumUnresolvedMethods
helpviewer_keywords:
- EnumUnresolvedMethods method [.NET Framework metadata]
- IMetaDataImport::EnumUnresolvedMethods method [.NET Framework metadata]
ms.assetid: eb3187d7-74cf-44b1-aeeb-7a8d2b60e3b7
topic_type:
- apiref
ms.openlocfilehash: e894ecdde91a2263783234d73fa50d890a13e413
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799331"
---
# <a name="imetadataimportenumunresolvedmethods-method"></a><span data-ttu-id="d032b-103">IMetaDataImport::EnumUnresolvedMethods メソッド</span><span class="sxs-lookup"><span data-stu-id="d032b-103">IMetaDataImport::EnumUnresolvedMethods Method</span></span>

<span data-ttu-id="d032b-104">現在のメタデータ スコープ内の未解決のメソッドを表す MemberDef トークンを列挙します。</span><span class="sxs-lookup"><span data-stu-id="d032b-104">Enumerates MemberDef tokens representing the unresolved methods in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d032b-105">構文</span><span class="sxs-lookup"><span data-stu-id="d032b-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumUnresolvedMethods (  
   [in, out] HCORENUM    *phEnum,  
   [out]     mdToken     rMethods[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d032b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d032b-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="d032b-107">[入力、出力]列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="d032b-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="d032b-108">このメソッドの最初の呼び出しでは、この値は NULL である必要があります。</span><span class="sxs-lookup"><span data-stu-id="d032b-108">This must be NULL for the first call of this method.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="d032b-109">入出力MemberDef トークンを格納するために使用される配列。</span><span class="sxs-lookup"><span data-stu-id="d032b-109">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="d032b-110">[in] `rMethods` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="d032b-110">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="d032b-111">入出力で返された MemberDef トークンの数 `rMethods` 。</span><span class="sxs-lookup"><span data-stu-id="d032b-111">[out] The number of MemberDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d032b-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="d032b-112">Return Value</span></span>  
  
|<span data-ttu-id="d032b-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d032b-113">HRESULT</span></span>|<span data-ttu-id="d032b-114">説明</span><span class="sxs-lookup"><span data-stu-id="d032b-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="d032b-115">`EnumUnresolvedMethods` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="d032b-115">`EnumUnresolvedMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="d032b-116">列挙するトークンがありません。</span><span class="sxs-lookup"><span data-stu-id="d032b-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="d032b-117">この場合、 `pcTokens` は0になります。</span><span class="sxs-lookup"><span data-stu-id="d032b-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d032b-118">解説</span><span class="sxs-lookup"><span data-stu-id="d032b-118">Remarks</span></span>  

 <span data-ttu-id="d032b-119">未解決のメソッドとは、宣言されていても実装されていないメソッドです。</span><span class="sxs-lookup"><span data-stu-id="d032b-119">An unresolved method is one that has been declared but not implemented.</span></span> <span data-ttu-id="d032b-120">メソッドがマークされ、 `miForwardRef` `mdPinvokeImpl` またはが0に設定されている場合、メソッドは列挙体に含まれ `miRuntime` ます。</span><span class="sxs-lookup"><span data-stu-id="d032b-120">A method is included in the enumeration if the method is marked `miForwardRef` and either `mdPinvokeImpl` or `miRuntime` is set to zero.</span></span> <span data-ttu-id="d032b-121">つまり、未解決のメソッドは、とマークされているものの、 `miForwardRef` アンマネージコードでは実装されていない (PInvoke 経由で)、またはランタイム自体によって内部的に実装されていないクラスメソッドです。</span><span class="sxs-lookup"><span data-stu-id="d032b-121">In other words, an unresolved method is a class method that is marked `miForwardRef` but which is not implemented in unmanaged code (reached via PInvoke) nor implemented internally by the runtime itself</span></span>  
  
 <span data-ttu-id="d032b-122">列挙体には、モジュールスコープ (globals) またはインターフェイスまたは抽象クラスで定義されているすべてのメソッドが除外されます。</span><span class="sxs-lookup"><span data-stu-id="d032b-122">The enumeration excludes all methods that are defined either at module scope (globals) or in interfaces or abstract classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d032b-123">要件</span><span class="sxs-lookup"><span data-stu-id="d032b-123">Requirements</span></span>  

 <span data-ttu-id="d032b-124">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d032b-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d032b-125">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="d032b-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d032b-126">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="d032b-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d032b-127">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d032b-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d032b-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="d032b-128">See also</span></span>

- [<span data-ttu-id="d032b-129">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d032b-129">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="d032b-130">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d032b-130">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
