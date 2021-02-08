---
description: '詳細情報: StrongNameSignatureGenerationEx 関数'
title: StrongNameSignatureGenerationEx 関数
ms.date: 03/30/2017
api_name:
- StrongNameSignatureGenerationEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureGenerationEx
helpviewer_keywords:
- StrongNameSignatureGenerationEx function [.NET Framework strong naming]
ms.assetid: 9a75469e-aa49-4e32-ad48-3bafd5202f09
topic_type:
- apiref
ms.openlocfilehash: e4d35cf51df6047d3a89d4146ceb8bf62e3f1b8b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798876"
---
# <a name="strongnamesignaturegenerationex-function"></a><span data-ttu-id="1e108-103">StrongNameSignatureGenerationEx 関数</span><span class="sxs-lookup"><span data-stu-id="1e108-103">StrongNameSignatureGenerationEx Function</span></span>

<span data-ttu-id="1e108-104">指定したフラグに従って、指定したアセンブリの厳密な名前の署名を生成します。</span><span class="sxs-lookup"><span data-stu-id="1e108-104">Generates a strong name signature for the specified assembly, according to the specified flags.</span></span>  
  
 <span data-ttu-id="1e108-105">この関数は非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="1e108-105">This function has been deprecated.</span></span> <span data-ttu-id="1e108-106">代わりに [ICLRStrongName:: StrongNameSignatureGenerationEx](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="1e108-106">Use the [ICLRStrongName::StrongNameSignatureGenerationEx](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e108-107">構文</span><span class="sxs-lookup"><span data-stu-id="1e108-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureGenerationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob,  
    [in]  DWORD     dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e108-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e108-108">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="1e108-109">から厳密な名前の署名が生成されるアセンブリのマニフェストを含むファイルへのパス。</span><span class="sxs-lookup"><span data-stu-id="1e108-109">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="1e108-110">から公開キーと秘密キーのペアを格納するキーコンテナーの名前。</span><span class="sxs-lookup"><span data-stu-id="1e108-110">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="1e108-111">`pbKeyBlob`が null の場合、では、 `wszKeyContainer` 暗号化サービスプロバイダー (CSP) 内の有効なコンテナーを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e108-111">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="1e108-112">この場合、コンテナーに格納されているキーペアがファイルの署名に使用されます。</span><span class="sxs-lookup"><span data-stu-id="1e108-112">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="1e108-113">`pbKeyBlob`が null でない場合、キーペアは、バイナリラージオブジェクト (BLOB) に格納されていると見なされます。</span><span class="sxs-lookup"><span data-stu-id="1e108-113">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="1e108-114">から公開/秘密キーのペアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e108-114">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="1e108-115">このペアは、Win32 関数によって作成される形式です `CryptExportKey` 。</span><span class="sxs-lookup"><span data-stu-id="1e108-115">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="1e108-116">`pbKeyBlob`が null の場合、によって指定されたキーコンテナーには、キーのペアが含まれていると `wszKeyContainer` 見なされます。</span><span class="sxs-lookup"><span data-stu-id="1e108-116">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="1e108-117">からのサイズ (バイト単位) `pbKeyBlob` 。</span><span class="sxs-lookup"><span data-stu-id="1e108-117">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="1e108-118">入出力共通言語ランタイムが署名を返す場所へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e108-118">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="1e108-119">`ppbSignatureBlob`が null の場合、ランタイムはによって指定されたファイルに署名を格納し `wszFilePath` ます。</span><span class="sxs-lookup"><span data-stu-id="1e108-119">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="1e108-120">`ppbSignatureBlob`が null でない場合は、共通言語ランタイムによって、署名を返す領域が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="1e108-120">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="1e108-121">呼び出し元は、 [StrongNameFreeBuffer](strongnamefreebuffer-function.md) 関数を使用してこの領域を解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e108-121">The caller must free this space using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="1e108-122">入出力返されたシグネチャのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="1e108-122">[out] The size, in bytes, of the returned signature.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="1e108-123">から次の値の1つまたは複数です。</span><span class="sxs-lookup"><span data-stu-id="1e108-123">[in] One or more of the following values:</span></span>  
  
- <span data-ttu-id="1e108-124">`SN_SIGN_ALL_FILES` (0x00000001)-リンクされたモジュールのすべてのハッシュを再計算します。</span><span class="sxs-lookup"><span data-stu-id="1e108-124">`SN_SIGN_ALL_FILES` (0x00000001) - Recompute all hashes for linked modules.</span></span>  
  
- <span data-ttu-id="1e108-125">`SN_TEST_SIGN` (0x00000002)-アセンブリに対してテストを行います。</span><span class="sxs-lookup"><span data-stu-id="1e108-125">`SN_TEST_SIGN` (0x00000002) - Test-sign the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1e108-126">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e108-126">Return Value</span></span>  

 <span data-ttu-id="1e108-127">`true` 正常に完了した場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="1e108-127">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e108-128">解説</span><span class="sxs-lookup"><span data-stu-id="1e108-128">Remarks</span></span>  

 <span data-ttu-id="1e108-129">`wszFilePath`署名を作成せずに署名のサイズを計算するには、に null を指定します。</span><span class="sxs-lookup"><span data-stu-id="1e108-129">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="1e108-130">署名は、ファイルに直接格納するか、呼び出し元に返すことができます。</span><span class="sxs-lookup"><span data-stu-id="1e108-130">The signature can be either stored directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="1e108-131">が指定されていて `SN_SIGN_ALL_FILES` も、公開キーが含まれていない場合 ( `pbKeyBlob` との両方が null の場合 `wszFilePath` )、リンクされたモジュールのハッシュは再計算されますが、アセンブリは再署名されません。</span><span class="sxs-lookup"><span data-stu-id="1e108-131">If `SN_SIGN_ALL_FILES` is specified but a public key is not included (both `pbKeyBlob` and `wszFilePath` are null), hashes for linked modules are recomputed, but the assembly is not re-signed.</span></span>  
  
 <span data-ttu-id="1e108-132">が指定されている場合 `SN_TEST_SIGN` 、共通言語ランタイムヘッダーは、アセンブリが厳密な名前で署名されていることを示すために変更されません。</span><span class="sxs-lookup"><span data-stu-id="1e108-132">If `SN_TEST_SIGN` is specified, the common language runtime header is not modified to indicate that the assembly is signed with a strong name.</span></span>  
  
 <span data-ttu-id="1e108-133">関数が `StrongNameSignatureGenerationEx` 正常に完了しない場合は、 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 関数を呼び出して、最後に生成されたエラーを取得します。</span><span class="sxs-lookup"><span data-stu-id="1e108-133">If the `StrongNameSignatureGenerationEx` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e108-134">要件</span><span class="sxs-lookup"><span data-stu-id="1e108-134">Requirements</span></span>  

 <span data-ttu-id="1e108-135">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1e108-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e108-136">**ヘッダー:** StrongName</span><span class="sxs-lookup"><span data-stu-id="1e108-136">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="1e108-137">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="1e108-137">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1e108-138">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e108-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e108-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="1e108-139">See also</span></span>

- [<span data-ttu-id="1e108-140">StrongNameSignatureGenerationEx メソッド</span><span class="sxs-lookup"><span data-stu-id="1e108-140">StrongNameSignatureGenerationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="1e108-141">StrongNameSignatureGeneration メソッド</span><span class="sxs-lookup"><span data-stu-id="1e108-141">StrongNameSignatureGeneration Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="1e108-142">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1e108-142">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
