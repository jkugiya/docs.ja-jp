---
description: '詳細情報: StrongNameGetPublicKey 関数'
title: StrongNameGetPublicKey 関数
ms.date: 03/30/2017
api_name:
- StrongNameGetPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey function [.NET Framework strong naming]
ms.assetid: 5b58c87f-3f72-40df-9b9a-291076931cc3
topic_type:
- apiref
ms.openlocfilehash: c94ffdd20e83b03da27b2f44ebbc279cfd8b8afc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99670569"
---
# <a name="strongnamegetpublickey-function"></a><span data-ttu-id="d09ce-103">StrongNameGetPublicKey 関数</span><span class="sxs-lookup"><span data-stu-id="d09ce-103">StrongNameGetPublicKey Function</span></span>

<span data-ttu-id="d09ce-104">秘密/公開キーの組から公開キーが取得されます。</span><span class="sxs-lookup"><span data-stu-id="d09ce-104">Gets the public key from a private/public key pair.</span></span> <span data-ttu-id="d09ce-105">キーペアは、暗号化サービスプロバイダー (CSP) 内のキーコンテナー名として、またはバイトの未加工コレクションとして指定できます。</span><span class="sxs-lookup"><span data-stu-id="d09ce-105">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
 <span data-ttu-id="d09ce-106">この関数は非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="d09ce-106">This function has been deprecated.</span></span> <span data-ttu-id="d09ce-107">代わりに [ICLRStrongName:: StrongNameGetPublicKey](../hosting/iclrstrongname-strongnamegetpublickey-method.md) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="d09ce-107">Use the [ICLRStrongName::StrongNameGetPublicKey](../hosting/iclrstrongname-strongnamegetpublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d09ce-108">構文</span><span class="sxs-lookup"><span data-stu-id="d09ce-108">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetPublicKey (
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d09ce-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d09ce-109">Parameters</span></span>  

 `szKeyContainer`  
 <span data-ttu-id="d09ce-110">から公開キーと秘密キーのペアを格納するキーコンテナーの名前。</span><span class="sxs-lookup"><span data-stu-id="d09ce-110">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="d09ce-111">`pbKeyBlob`が null の場合、は `szKeyContainer` CSP 内の有効なコンテナーを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d09ce-111">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="d09ce-112">この場合、は、 `StrongNameGetPublicKey` コンテナーに格納されているキーペアから公開キーを抽出します。</span><span class="sxs-lookup"><span data-stu-id="d09ce-112">In this case, `StrongNameGetPublicKey` extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="d09ce-113">`pbKeyBlob`が null でない場合、キーペアは、バイナリラージオブジェクト (BLOB) に格納されていると見なされます。</span><span class="sxs-lookup"><span data-stu-id="d09ce-113">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="d09ce-114">キーは 1024-Rivest-shamir-adleman-Rivest-shamir-adleman (RSA) 署名キーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="d09ce-114">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="d09ce-115">この時点では、他の種類のキーはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d09ce-115">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="d09ce-116">から公開/秘密キーのペアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d09ce-116">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="d09ce-117">このペアは、Win32 関数によって作成される形式です `CryptExportKey` 。</span><span class="sxs-lookup"><span data-stu-id="d09ce-117">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="d09ce-118">`pbKeyBlob`が null の場合、によって指定されたキーコンテナーには、キーのペアが含まれていると `szKeyContainer` 見なされます。</span><span class="sxs-lookup"><span data-stu-id="d09ce-118">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="d09ce-119">からのサイズ (バイト単位) `pbKeyBlob` 。</span><span class="sxs-lookup"><span data-stu-id="d09ce-119">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="d09ce-120">入出力返された公開キー BLOB。</span><span class="sxs-lookup"><span data-stu-id="d09ce-120">[out] The returned public key BLOB.</span></span> <span data-ttu-id="d09ce-121">パラメーターは、 `ppbPublicKeyBlob` 共通言語ランタイムによって割り当てられ、呼び出し元に返されます。</span><span class="sxs-lookup"><span data-stu-id="d09ce-121">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="d09ce-122">呼び出し元は、 [StrongNameFreeBuffer](strongnamefreebuffer-function.md) 関数を使用してメモリを解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d09ce-122">The caller must free the memory by using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="d09ce-123">入出力返される公開キー BLOB のサイズ。</span><span class="sxs-lookup"><span data-stu-id="d09ce-123">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d09ce-124">戻り値</span><span class="sxs-lookup"><span data-stu-id="d09ce-124">Return Value</span></span>  

 <span data-ttu-id="d09ce-125">`true` 正常に完了した場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="d09ce-125">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d09ce-126">解説</span><span class="sxs-lookup"><span data-stu-id="d09ce-126">Remarks</span></span>  

 <span data-ttu-id="d09ce-127">公開キーは [Publickeyblob](publickeyblob-structure.md) 構造に含まれています。</span><span class="sxs-lookup"><span data-stu-id="d09ce-127">The public key is contained in a [PublicKeyBlob](publickeyblob-structure.md) structure.</span></span>  
  
 <span data-ttu-id="d09ce-128">関数が `StrongNameGetPublicKey` 正常に完了しない場合は、 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 関数を呼び出して、最後に生成されたエラーを取得します。</span><span class="sxs-lookup"><span data-stu-id="d09ce-128">If the `StrongNameGetPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d09ce-129">要件</span><span class="sxs-lookup"><span data-stu-id="d09ce-129">Requirements</span></span>  

 <span data-ttu-id="d09ce-130">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d09ce-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d09ce-131">**ヘッダー:** StrongName</span><span class="sxs-lookup"><span data-stu-id="d09ce-131">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="d09ce-132">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="d09ce-132">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d09ce-133">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d09ce-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d09ce-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="d09ce-134">See also</span></span>

- [<span data-ttu-id="d09ce-135">StrongNameGetPublicKey メソッド</span><span class="sxs-lookup"><span data-stu-id="d09ce-135">StrongNameGetPublicKey Method</span></span>](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="d09ce-136">StrongNameTokenFromPublicKey メソッド</span><span class="sxs-lookup"><span data-stu-id="d09ce-136">StrongNameTokenFromPublicKey Method</span></span>](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="d09ce-137">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d09ce-137">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="d09ce-138">PublicKeyBlob 構造体</span><span class="sxs-lookup"><span data-stu-id="d09ce-138">PublicKeyBlob Structure</span></span>](publickeyblob-structure.md)
