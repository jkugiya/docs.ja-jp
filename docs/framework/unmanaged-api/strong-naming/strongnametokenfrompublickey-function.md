---
description: '詳細情報: StrongNameTokenFromPublicKey 関数'
title: StrongNameTokenFromPublicKey 関数
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- COM
f1_keywords:
- StrongNameTokenFromPublicKey
helpviewer_keywords:
- StrongNameTokenFromPublicKey function [.NET Framework strong naming]
ms.assetid: 997e9e57-abb2-4217-bf20-1df621a75add
topic_type:
- apiref
ms.openlocfilehash: f978c9b2727db4b293b9c92a8789fbf9ba749d41
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636282"
---
# <a name="strongnametokenfrompublickey-function"></a><span data-ttu-id="8400c-103">StrongNameTokenFromPublicKey 関数</span><span class="sxs-lookup"><span data-stu-id="8400c-103">StrongNameTokenFromPublicKey Function</span></span>

<span data-ttu-id="8400c-104">公開キーを表すトークンが取得されます。</span><span class="sxs-lookup"><span data-stu-id="8400c-104">Gets a token representing a public key.</span></span> <span data-ttu-id="8400c-105">厳密な名前トークンは、公開キーの短縮形です。</span><span class="sxs-lookup"><span data-stu-id="8400c-105">A strong name token is the shortened form of a public key.</span></span>  
  
 <span data-ttu-id="8400c-106">この関数は非推奨とされています。</span><span class="sxs-lookup"><span data-stu-id="8400c-106">This function has been deprecated.</span></span> <span data-ttu-id="8400c-107">代わりに、[ICLRStrongName::StrongNameTokenFromPublicKey](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="8400c-107">Use the [ICLRStrongName::StrongNameTokenFromPublicKey](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8400c-108">構文</span><span class="sxs-lookup"><span data-stu-id="8400c-108">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameTokenFromPublicKey (
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8400c-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8400c-109">Parameters</span></span>  

 `pbPublicKeyBlob`  
 <span data-ttu-id="8400c-110">[in] 厳密な名前のシグネチャを生成するために使用されるキーの組の公開部分を格納する [PublicKeyBlob](publickeyblob-structure.md) 型の構造体。</span><span class="sxs-lookup"><span data-stu-id="8400c-110">[in] A structure of type [PublicKeyBlob](publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="8400c-111">[in] `pbPublicKeyBlob` のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="8400c-111">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="8400c-112">[out] `pbPublicKeyBlob` に渡されたキーに対応する厳密な名前トークン。</span><span class="sxs-lookup"><span data-stu-id="8400c-112">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="8400c-113">共通言語ランタイムで、トークンが返されるメモリが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="8400c-113">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="8400c-114">呼び出し元では、[StrongNameFreeBuffer](strongnamefreebuffer-function.md) 関数を使用して、このメモリを解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8400c-114">The caller must free this memory by using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="8400c-115">[out] 返された厳密な名前トークンのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="8400c-115">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8400c-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="8400c-116">Return Value</span></span>  

 <span data-ttu-id="8400c-117">正常に完了した場合は `true`。それ以外の場合は `false`。</span><span class="sxs-lookup"><span data-stu-id="8400c-117">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8400c-118">解説</span><span class="sxs-lookup"><span data-stu-id="8400c-118">Remarks</span></span>  

 <span data-ttu-id="8400c-119">厳密な名前トークンは、キー情報をメタデータに格納する際に領域を節約するために使用される公開キーの短縮形です。</span><span class="sxs-lookup"><span data-stu-id="8400c-119">A strong name token is the shortened form of a public key used to save space when storing key information in metadata.</span></span> <span data-ttu-id="8400c-120">具体的には、厳密な名前トークンは、依存アセンブリを参照するためにアセンブリ参照で使用されます。</span><span class="sxs-lookup"><span data-stu-id="8400c-120">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
 <span data-ttu-id="8400c-121">`StrongNameTokenFromPublicKey` 関数が正常に完了しない場合、[StrongNameErrorInfo](strongnameerrorinfo-function.md) 関数を呼び出し、最後に生成されたエラーを取得します。</span><span class="sxs-lookup"><span data-stu-id="8400c-121">If the `StrongNameTokenFromPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8400c-122">必要条件</span><span class="sxs-lookup"><span data-stu-id="8400c-122">Requirements</span></span>  

 <span data-ttu-id="8400c-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8400c-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8400c-124">**ヘッダー:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="8400c-124">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="8400c-125">**ライブラリ**: mscoree.dll にリソースとして含まれます</span><span class="sxs-lookup"><span data-stu-id="8400c-125">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="8400c-126">**.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8400c-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8400c-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="8400c-127">See also</span></span>

- [<span data-ttu-id="8400c-128">StrongNameTokenFromPublicKey メソッド</span><span class="sxs-lookup"><span data-stu-id="8400c-128">StrongNameTokenFromPublicKey Method</span></span>](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="8400c-129">StrongNameGetPublicKey メソッド</span><span class="sxs-lookup"><span data-stu-id="8400c-129">StrongNameGetPublicKey Method</span></span>](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="8400c-130">PublicKeyBlob 構造体</span><span class="sxs-lookup"><span data-stu-id="8400c-130">PublicKeyBlob Structure</span></span>](publickeyblob-structure.md)
