---
description: '詳細情報: StrongNameGetPublicKeyEx メソッド'
title: StrongNameGetPublicKeyEx メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName2.StrongNameGetPublicKeyEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StrongNameGetPublicKeyEx
helpviewer_keywords:
- StrongNameGetPublicKeyEx method, ICLRStrongName2 interface [.NET Framework hosting]
- ICLRStrongName2::StrongNameGetPublicKeyEx method [.NET Framework hosting]
ms.assetid: 63d8260c-fb32-4f8f-a357-768afd570f68
topic_type:
- apiref
ms.openlocfilehash: bc9d40afc34509f852a0961823e264255125fa16
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679304"
---
# <a name="strongnamegetpublickeyex-method"></a><span data-ttu-id="f306f-103">StrongNameGetPublicKeyEx メソッド</span><span class="sxs-lookup"><span data-stu-id="f306f-103">StrongNameGetPublicKeyEx Method</span></span>

<span data-ttu-id="f306f-104">公開キーと秘密キーのペアから公開キーを取得し、ハッシュアルゴリズムと署名アルゴリズムを指定します。</span><span class="sxs-lookup"><span data-stu-id="f306f-104">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f306f-105">構文</span><span class="sxs-lookup"><span data-stu-id="f306f-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetPublicKey (
    [in]  LPCWSTR   pwzKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
    [in]  ULONG     uHashAlgId,  
    [in]  ULONG     uReserved,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f306f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f306f-106">Parameters</span></span>  

 `pwzKeyContainer`  
 <span data-ttu-id="f306f-107">から公開キーと秘密キーのペアを格納するキーコンテナーの名前。</span><span class="sxs-lookup"><span data-stu-id="f306f-107">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="f306f-108">`pbKeyBlob`が null の場合、では、 `szKeyContainer` 暗号化サービスプロバイダー (CSP) 内の有効なコンテナーを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f306f-108">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="f306f-109">この場合、メソッドは、 `StrongNameGetPublicKeyEx` コンテナーに格納されているキーペアから公開キーを抽出します。</span><span class="sxs-lookup"><span data-stu-id="f306f-109">In this case, the `StrongNameGetPublicKeyEx` method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="f306f-110">`pbKeyBlob`が null でない場合、キーペアは、バイナリラージオブジェクト (BLOB) に格納されていると見なされます。</span><span class="sxs-lookup"><span data-stu-id="f306f-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="f306f-111">キーは 1024-Rivest-shamir-adleman-Rivest-shamir-adleman (RSA) 署名キーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="f306f-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="f306f-112">この時点では、他の種類のキーはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="f306f-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="f306f-113">から公開/秘密キーのペアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f306f-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="f306f-114">このペアは、Win32 関数によって作成される形式です `CryptExportKey` 。</span><span class="sxs-lookup"><span data-stu-id="f306f-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="f306f-115">`pbKeyBlob`が null の場合、によって指定されたキーコンテナーには、キーのペアが含まれていると `szKeyContainer` 見なされます。</span><span class="sxs-lookup"><span data-stu-id="f306f-115">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="f306f-116">からのサイズ (バイト単位) `pbKeyBlob` 。</span><span class="sxs-lookup"><span data-stu-id="f306f-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="f306f-117">入出力返された公開キー BLOB。</span><span class="sxs-lookup"><span data-stu-id="f306f-117">[out] The returned public key BLOB.</span></span> <span data-ttu-id="f306f-118">パラメーターは、 `ppbPublicKeyBlob` 共通言語ランタイムによって割り当てられ、呼び出し元に返されます。</span><span class="sxs-lookup"><span data-stu-id="f306f-118">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="f306f-119">呼び出し元は、 [ICLRStrongName:: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) メソッドを使用して、メモリを解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f306f-119">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="f306f-120">入出力返される公開キー BLOB のサイズ。</span><span class="sxs-lookup"><span data-stu-id="f306f-120">[out] The size of the returned public key BLOB.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="f306f-121">からアセンブリハッシュアルゴリズム。</span><span class="sxs-lookup"><span data-stu-id="f306f-121">[in] The assembly hash algorithm.</span></span> <span data-ttu-id="f306f-122">許容される値の一覧については、「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f306f-122">See the Remarks section for a list of accepted values.</span></span>  
  
 `uReserved`  
 <span data-ttu-id="f306f-123">から将来使用するために予約されています。既定値は null です。</span><span class="sxs-lookup"><span data-stu-id="f306f-123">[in] Reserved for future use; defaults to null.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f306f-124">戻り値</span><span class="sxs-lookup"><span data-stu-id="f306f-124">Return Value</span></span>  

 <span data-ttu-id="f306f-125">`S_OK` メソッドが正常に完了した場合は。それ以外の場合は、失敗を示す HRESULT 値 (「リストの [一般的な Hresult 値](/windows/win32/seccrypto/common-hresult-values) 」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="f306f-125">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f306f-126">解説</span><span class="sxs-lookup"><span data-stu-id="f306f-126">Remarks</span></span>  

 <span data-ttu-id="f306f-127">公開キーは [Publickeyblob](../strong-naming/publickeyblob-structure.md) 構造に含まれています。</span><span class="sxs-lookup"><span data-stu-id="f306f-127">The public key is contained in a [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f306f-128">解説</span><span class="sxs-lookup"><span data-stu-id="f306f-128">Remarks</span></span>  

 <span data-ttu-id="f306f-129">次の表は、パラメーターで許容される値のセットを示して `uHashAlgId` います。</span><span class="sxs-lookup"><span data-stu-id="f306f-129">The following table shows the set of accepted values for the `uHashAlgId` parameter.</span></span>  
  
|<span data-ttu-id="f306f-130">名前</span><span class="sxs-lookup"><span data-stu-id="f306f-130">Name</span></span>|<span data-ttu-id="f306f-131">値</span><span class="sxs-lookup"><span data-stu-id="f306f-131">Value</span></span>|  
|----------|-----------|  
|<span data-ttu-id="f306f-132">なし</span><span class="sxs-lookup"><span data-stu-id="f306f-132">None</span></span>|<span data-ttu-id="f306f-133">0</span><span class="sxs-lookup"><span data-stu-id="f306f-133">0</span></span>|  
|<span data-ttu-id="f306f-134">SHA-1</span><span class="sxs-lookup"><span data-stu-id="f306f-134">SHA-1</span></span>|<span data-ttu-id="f306f-135">0x8004</span><span class="sxs-lookup"><span data-stu-id="f306f-135">0x8004</span></span>|  
|<span data-ttu-id="f306f-136">SHA-256</span><span class="sxs-lookup"><span data-stu-id="f306f-136">SHA-256</span></span>|<span data-ttu-id="f306f-137">0x800c</span><span class="sxs-lookup"><span data-stu-id="f306f-137">0x800c</span></span>|  
|<span data-ttu-id="f306f-138">SHA-384</span><span class="sxs-lookup"><span data-stu-id="f306f-138">SHA-384</span></span>|<span data-ttu-id="f306f-139">0x800d</span><span class="sxs-lookup"><span data-stu-id="f306f-139">0x800d</span></span>|  
|<span data-ttu-id="f306f-140">SHA-512</span><span class="sxs-lookup"><span data-stu-id="f306f-140">SHA-512</span></span>|<span data-ttu-id="f306f-141">0x800e</span><span class="sxs-lookup"><span data-stu-id="f306f-141">0x800e</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f306f-142">要件</span><span class="sxs-lookup"><span data-stu-id="f306f-142">Requirements</span></span>  

 <span data-ttu-id="f306f-143">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f306f-143">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f306f-144">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="f306f-144">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f306f-145">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="f306f-145">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f306f-146">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f306f-146">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f306f-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="f306f-147">See also</span></span>

- [<span data-ttu-id="f306f-148">StrongNameTokenFromPublicKey メソッド</span><span class="sxs-lookup"><span data-stu-id="f306f-148">StrongNameTokenFromPublicKey Method</span></span>](iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="f306f-149">PublicKeyBlob 構造体</span><span class="sxs-lookup"><span data-stu-id="f306f-149">PublicKeyBlob Structure</span></span>](../strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="f306f-150">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f306f-150">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
- [<span data-ttu-id="f306f-151">StrongNameGetPublicKey メソッド</span><span class="sxs-lookup"><span data-stu-id="f306f-151">StrongNameGetPublicKey Method</span></span>](iclrstrongname-strongnamegetpublickey-method.md)
