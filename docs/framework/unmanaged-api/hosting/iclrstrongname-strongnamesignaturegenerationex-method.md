---
description: '詳細について: ICLRStrongName:: StrongNameSignatureGenerationEx メソッド'
title: ICLRStrongName::StrongNameSignatureGenerationEx メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureGenerationEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureGenerationEx
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureGenerationEx method [.NET Framework hosting]
- StrongNameSignatureGenerationEx method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: c3f34584-c6e2-41fd-bb44-e44da8546309
topic_type:
- apiref
ms.openlocfilehash: 911f55aa509c25eb0d95d6d2a31c9f715af2080d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781871"
---
# <a name="iclrstrongnamestrongnamesignaturegenerationex-method"></a><span data-ttu-id="b1354-103">ICLRStrongName::StrongNameSignatureGenerationEx メソッド</span><span class="sxs-lookup"><span data-stu-id="b1354-103">ICLRStrongName::StrongNameSignatureGenerationEx Method</span></span>

<span data-ttu-id="b1354-104">指定したフラグに従って、指定したアセンブリの厳密な名前の署名を生成します。</span><span class="sxs-lookup"><span data-stu-id="b1354-104">Generates a strong name signature for the specified assembly, according to the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1354-105">構文</span><span class="sxs-lookup"><span data-stu-id="b1354-105">Syntax</span></span>  
  
```cpp
HRESULT StrongNameSignatureGenerationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob,  
    [in]  DWORD     dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1354-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b1354-106">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="b1354-107">から厳密な名前の署名が生成されるアセンブリのマニフェストを含むファイルへのパス。</span><span class="sxs-lookup"><span data-stu-id="b1354-107">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="b1354-108">から公開キーと秘密キーのペアを格納するキーコンテナーの名前。</span><span class="sxs-lookup"><span data-stu-id="b1354-108">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="b1354-109">`pbKeyBlob`が null の場合、では、 `wszKeyContainer` 暗号化サービスプロバイダー (CSP) 内の有効なコンテナーを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b1354-109">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="b1354-110">この場合、コンテナーに格納されているキーペアがファイルの署名に使用されます。</span><span class="sxs-lookup"><span data-stu-id="b1354-110">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="b1354-111">`pbKeyBlob`が null でない場合、キーペアは、バイナリラージオブジェクト (BLOB) に格納されていると見なされます。</span><span class="sxs-lookup"><span data-stu-id="b1354-111">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="b1354-112">から公開/秘密キーのペアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b1354-112">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="b1354-113">このペアは、Win32 関数によって作成される形式です `CryptExportKey` 。</span><span class="sxs-lookup"><span data-stu-id="b1354-113">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="b1354-114">`pbKeyBlob`が null の場合、によって指定されたキーコンテナーには、キーのペアが含まれていると `wszKeyContainer` 見なされます。</span><span class="sxs-lookup"><span data-stu-id="b1354-114">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="b1354-115">からのサイズ (バイト単位) `pbKeyBlob` 。</span><span class="sxs-lookup"><span data-stu-id="b1354-115">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="b1354-116">入出力共通言語ランタイムが署名を返す場所へのポインター。</span><span class="sxs-lookup"><span data-stu-id="b1354-116">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="b1354-117">`ppbSignatureBlob`が null の場合、ランタイムはによって指定されたファイルに署名を格納し `wszFilePath` ます。</span><span class="sxs-lookup"><span data-stu-id="b1354-117">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="b1354-118">`ppbSignatureBlob`が null でない場合は、共通言語ランタイムによって、署名を返す領域が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="b1354-118">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="b1354-119">呼び出し元は、 [ICLRStrongName:: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) メソッドを使用してこの領域を解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b1354-119">The caller must free this space using the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="b1354-120">入出力返されたシグネチャのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="b1354-120">[out] The size, in bytes, of the returned signature.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="b1354-121">から次の値の1つまたは複数です。</span><span class="sxs-lookup"><span data-stu-id="b1354-121">[in] One or more of the following values:</span></span>  
  
- <span data-ttu-id="b1354-122">`SN_SIGN_ALL_FILES` (0x00000001)-リンクされたモジュールのすべてのハッシュを再計算します。</span><span class="sxs-lookup"><span data-stu-id="b1354-122">`SN_SIGN_ALL_FILES` (0x00000001) - Recompute all hashes for linked modules.</span></span>  
  
- <span data-ttu-id="b1354-123">`SN_TEST_SIGN` (0x00000002)-アセンブリに対してテストを行います。</span><span class="sxs-lookup"><span data-stu-id="b1354-123">`SN_TEST_SIGN` (0x00000002) - Test-sign the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b1354-124">戻り値</span><span class="sxs-lookup"><span data-stu-id="b1354-124">Return Value</span></span>  

 <span data-ttu-id="b1354-125">`S_OK` メソッドが正常に完了した場合は。それ以外の場合は、失敗を示す HRESULT 値 (「リストの [一般的な Hresult 値](/windows/win32/seccrypto/common-hresult-values) 」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="b1354-125">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1354-126">解説</span><span class="sxs-lookup"><span data-stu-id="b1354-126">Remarks</span></span>  

 <span data-ttu-id="b1354-127">`wszFilePath`署名を作成せずに署名のサイズを計算するには、に null を指定します。</span><span class="sxs-lookup"><span data-stu-id="b1354-127">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="b1354-128">署名は、ファイルに直接格納するか、呼び出し元に返すことができます。</span><span class="sxs-lookup"><span data-stu-id="b1354-128">The signature can be either stored directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="b1354-129">が指定されていて `SN_SIGN_ALL_FILES` も、公開キーが含まれていない場合 ( `pbKeyBlob` との両方が null の場合 `wszFilePath` )、リンクされたモジュールのハッシュは再計算されますが、アセンブリは再署名されません。</span><span class="sxs-lookup"><span data-stu-id="b1354-129">If `SN_SIGN_ALL_FILES` is specified but a public key is not included (both `pbKeyBlob` and `wszFilePath` are null), hashes for linked modules are recomputed, but the assembly is not re-signed.</span></span>  
  
 <span data-ttu-id="b1354-130">が指定されている場合 `SN_TEST_SIGN` 、共通言語ランタイムヘッダーは、アセンブリが厳密な名前で署名されていることを示すために変更されません。</span><span class="sxs-lookup"><span data-stu-id="b1354-130">If `SN_TEST_SIGN` is specified, the common language runtime header is not modified to indicate that the assembly is signed with a strong name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1354-131">要件</span><span class="sxs-lookup"><span data-stu-id="b1354-131">Requirements</span></span>  

 <span data-ttu-id="b1354-132">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b1354-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1354-133">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="b1354-133">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="b1354-134">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="b1354-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b1354-135">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1354-135">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1354-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="b1354-136">See also</span></span>

- [<span data-ttu-id="b1354-137">StrongNameSignatureGeneration メソッド</span><span class="sxs-lookup"><span data-stu-id="b1354-137">StrongNameSignatureGeneration Method</span></span>](iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="b1354-138">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b1354-138">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
