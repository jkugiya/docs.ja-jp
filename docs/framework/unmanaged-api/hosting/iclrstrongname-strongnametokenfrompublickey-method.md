---
description: '詳細について: ICLRStrongName:: StrongNameTokenFromPublicKey メソッド'
title: ICLRStrongName::StrongNameTokenFromPublicKey メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameTokenFromPublicKey
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromPublicKey
helpviewer_keywords:
- ICLRStrongName::StrongNameTokenFromPublicKey method [.NET Framework hosting]
- StrongNameTokenFromPublicKey method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 7962ce88-7e86-4a6f-8298-621b01ffc3c2
topic_type:
- apiref
ms.openlocfilehash: de245b151e5ca016a00793a8901c0fd990a3f804
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789745"
---
# <a name="iclrstrongnamestrongnametokenfrompublickey-method"></a><span data-ttu-id="ad81f-103">ICLRStrongName::StrongNameTokenFromPublicKey メソッド</span><span class="sxs-lookup"><span data-stu-id="ad81f-103">ICLRStrongName::StrongNameTokenFromPublicKey Method</span></span>

<span data-ttu-id="ad81f-104">公開キーを表すトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="ad81f-104">Gets a token that represents a public key.</span></span> <span data-ttu-id="ad81f-105">厳密な名前トークンは、公開キーの短縮形です。</span><span class="sxs-lookup"><span data-stu-id="ad81f-105">A strong name token is the shortened form of a public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad81f-106">構文</span><span class="sxs-lookup"><span data-stu-id="ad81f-106">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameTokenFromPublicKey (
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad81f-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ad81f-107">Parameters</span></span>  

 `pbPublicKeyBlob`  
 <span data-ttu-id="ad81f-108">から厳密な名前の署名を生成するために使用されるキーペアの公開部分を格納する [Publickeyblob](../strong-naming/publickeyblob-structure.md) 型の構造体。</span><span class="sxs-lookup"><span data-stu-id="ad81f-108">[in] A structure of type [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="ad81f-109">からのサイズ (バイト単位) `pbPublicKeyBlob` 。</span><span class="sxs-lookup"><span data-stu-id="ad81f-109">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="ad81f-110">入出力渡されたキーに対応する厳密な名前トークン `pbPublicKeyBlob` 。</span><span class="sxs-lookup"><span data-stu-id="ad81f-110">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="ad81f-111">共通言語ランタイムは、トークンを返すメモリを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="ad81f-111">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="ad81f-112">呼び出し元は、 [ICLRStrongName:: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) メソッドを使用して、このメモリを解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ad81f-112">The caller must free this memory by using the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="ad81f-113">入出力返された厳密な名前トークンのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="ad81f-113">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ad81f-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="ad81f-114">Return Value</span></span>  

 <span data-ttu-id="ad81f-115">`S_OK` メソッドが正常に完了した場合は。それ以外の場合は、失敗を示す HRESULT 値 (「リストの [一般的な Hresult 値](/windows/win32/seccrypto/common-hresult-values) 」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="ad81f-115">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad81f-116">解説</span><span class="sxs-lookup"><span data-stu-id="ad81f-116">Remarks</span></span>  

 <span data-ttu-id="ad81f-117">厳密な名前トークンは、キー情報をメタデータに格納するときに領域を節約するために使用される公開キーの短縮形です。</span><span class="sxs-lookup"><span data-stu-id="ad81f-117">A strong name token is the shortened form of a public key that is used to save space when storing key information in metadata.</span></span> <span data-ttu-id="ad81f-118">具体的には、アセンブリ参照では、依存アセンブリを参照するために厳密な名前トークンが使用されます。</span><span class="sxs-lookup"><span data-stu-id="ad81f-118">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad81f-119">要件</span><span class="sxs-lookup"><span data-stu-id="ad81f-119">Requirements</span></span>  

 <span data-ttu-id="ad81f-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad81f-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad81f-121">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="ad81f-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ad81f-122">**ライブラリ:** mscoree.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="ad81f-122">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="ad81f-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad81f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad81f-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="ad81f-124">See also</span></span>

- [<span data-ttu-id="ad81f-125">StrongNameGetPublicKey メソッド</span><span class="sxs-lookup"><span data-stu-id="ad81f-125">StrongNameGetPublicKey Method</span></span>](iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="ad81f-126">PublicKeyBlob 構造体</span><span class="sxs-lookup"><span data-stu-id="ad81f-126">PublicKeyBlob Structure</span></span>](../strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="ad81f-127">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ad81f-127">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
