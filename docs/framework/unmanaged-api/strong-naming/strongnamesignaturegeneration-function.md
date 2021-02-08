---
description: '詳細情報: StrongNameSignatureGeneration 関数'
title: StrongNameSignatureGeneration 関数
ms.date: 03/30/2017
api_name:
- StrongNameSignatureGeneration
api_location:
- mscoree.dll
- mscorsn.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureGeneration
helpviewer_keywords:
- StrongNameSignatureGeneration function [.NET Framework strong naming]
ms.assetid: 839b765c-3e41-44ce-bf1b-dc10453db18e
ms.openlocfilehash: 6f5a164e73af743cdd13390c60d00d553e5e0312
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798902"
---
# <a name="strongnamesignaturegeneration-function"></a><span data-ttu-id="915f5-103">StrongNameSignatureGeneration 関数</span><span class="sxs-lookup"><span data-stu-id="915f5-103">StrongNameSignatureGeneration Function</span></span>

<span data-ttu-id="915f5-104">指定したアセンブリに対して厳密な名前の署名が生成されます。</span><span class="sxs-lookup"><span data-stu-id="915f5-104">Generates a strong name signature for the specified assembly.</span></span>  
  
 <span data-ttu-id="915f5-105">この関数は非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="915f5-105">This function has been deprecated.</span></span> <span data-ttu-id="915f5-106">代わりに [ICLRStrongName:: StrongNameSignatureGeneration](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="915f5-106">Use the [ICLRStrongName::StrongNameSignatureGeneration](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="915f5-107">構文</span><span class="sxs-lookup"><span data-stu-id="915f5-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureGeneration (
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="915f5-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="915f5-108">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="915f5-109">から厳密な名前の署名が生成されるアセンブリのマニフェストを含むファイルへのパス。</span><span class="sxs-lookup"><span data-stu-id="915f5-109">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="915f5-110">から公開キーと秘密キーのペアを格納するキーコンテナーの名前。</span><span class="sxs-lookup"><span data-stu-id="915f5-110">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="915f5-111">`pbKeyBlob`が null の場合、では、 `wszKeyContainer` 暗号化サービスプロバイダー (CSP) 内の有効なコンテナーを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="915f5-111">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="915f5-112">この場合、コンテナーに格納されているキーペアがファイルの署名に使用されます。</span><span class="sxs-lookup"><span data-stu-id="915f5-112">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="915f5-113">`pbKeyBlob`が null でない場合、キーペアは、バイナリラージオブジェクト (BLOB) に格納されていると見なされます。</span><span class="sxs-lookup"><span data-stu-id="915f5-113">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="915f5-114">キーは 1024-Rivest-shamir-adleman-Rivest-shamir-adleman (RSA) 署名キーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="915f5-114">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="915f5-115">この時点では、他の種類のキーはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="915f5-115">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="915f5-116">から公開/秘密キーのペアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="915f5-116">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="915f5-117">このペアは、Win32 関数によって作成される形式です `CryptExportKey` 。</span><span class="sxs-lookup"><span data-stu-id="915f5-117">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="915f5-118">`pbKeyBlob`が null の場合、によって指定されたキーコンテナーには、キーのペアが含まれていると `wszKeyContainer` 見なされます。</span><span class="sxs-lookup"><span data-stu-id="915f5-118">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="915f5-119">からのサイズ (バイト単位) `pbKeyBlob` 。</span><span class="sxs-lookup"><span data-stu-id="915f5-119">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="915f5-120">入出力共通言語ランタイムが署名を返す場所へのポインター。</span><span class="sxs-lookup"><span data-stu-id="915f5-120">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="915f5-121">`ppbSignatureBlob`が null の場合、ランタイムはによって指定されたファイルに署名を格納し `wszFilePath` ます。</span><span class="sxs-lookup"><span data-stu-id="915f5-121">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="915f5-122">`ppbSignatureBlob`が null でない場合は、共通言語ランタイムによって、署名を返す領域が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="915f5-122">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="915f5-123">呼び出し元は、 [StrongNameFreeBuffer](strongnamefreebuffer-function.md) 関数を使用してこの領域を解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="915f5-123">The caller must free this space using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="915f5-124">入出力返されたシグネチャのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="915f5-124">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="915f5-125">戻り値</span><span class="sxs-lookup"><span data-stu-id="915f5-125">Return Value</span></span>  

 <span data-ttu-id="915f5-126">`true` 正常に完了した場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="915f5-126">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="915f5-127">解説</span><span class="sxs-lookup"><span data-stu-id="915f5-127">Remarks</span></span>  

 <span data-ttu-id="915f5-128">`wszFilePath`署名を作成せずに署名のサイズを計算するには、に null を指定します。</span><span class="sxs-lookup"><span data-stu-id="915f5-128">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="915f5-129">署名は、ファイルに直接格納するか、呼び出し元に返すことができます。</span><span class="sxs-lookup"><span data-stu-id="915f5-129">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="915f5-130">関数が `StrongNameSignatureGeneration` 正常に完了しない場合は、 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 関数を呼び出して、最後に生成されたエラーを取得します。</span><span class="sxs-lookup"><span data-stu-id="915f5-130">If the `StrongNameSignatureGeneration` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="915f5-131">要件</span><span class="sxs-lookup"><span data-stu-id="915f5-131">Requirements</span></span>  

 <span data-ttu-id="915f5-132">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="915f5-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="915f5-133">**ヘッダー:** StrongName</span><span class="sxs-lookup"><span data-stu-id="915f5-133">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="915f5-134">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="915f5-134">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="915f5-135">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="915f5-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="915f5-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="915f5-136">See also</span></span>

- [<span data-ttu-id="915f5-137">StrongNameSignatureGeneration メソッド</span><span class="sxs-lookup"><span data-stu-id="915f5-137">StrongNameSignatureGeneration Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="915f5-138">StrongNameSignatureGenerationEx メソッド</span><span class="sxs-lookup"><span data-stu-id="915f5-138">StrongNameSignatureGenerationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="915f5-139">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="915f5-139">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
