---
description: 詳細については、「Certverify認証 Odelicense 関数」を参照してください。
title: CertVerifyAuthenticodeLicense 関数
ms.date: 03/30/2017
api_name:
- CertVerifyAuthenticodeLicense
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 00118de7-33c6-41c4-8e1f-5d5e35e0da83
topic_type:
- apiref
ms.openlocfilehash: 0174223a4c1b984bf2d5d957219a85230fef8d0e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772849"
---
# <a name="certverifyauthenticodelicense-function"></a><span data-ttu-id="9769b-103">CertVerifyAuthenticodeLicense 関数</span><span class="sxs-lookup"><span data-stu-id="9769b-103">CertVerifyAuthenticodeLicense Function</span></span>

<span data-ttu-id="9769b-104">Authenticode XrML ライセンスの有効性を検証します。</span><span class="sxs-lookup"><span data-stu-id="9769b-104">Verifies the validity of an Authenticode XrML license.</span></span>

## <a name="syntax"></a><span data-ttu-id="9769b-105">構文</span><span class="sxs-lookup"><span data-stu-id="9769b-105">Syntax</span></span>

```cpp
HRESULT CertVerifyAuthenticodeLicense (
    [in]   PCRYPT_DATA_BLOB                   pLicenseBlob,
    [in]   OPTIONAL DWORD                     dwFlags,
    [out]  PAXL_AUTHENTICODE_SIGNER_INFO      pSignerInfo,
    [out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO pTimestamperInfo
);
```

## <a name="parameters"></a><span data-ttu-id="9769b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9769b-106">Parameters</span></span>

 `pLicenseBlob`\
 <span data-ttu-id="9769b-107">[in] 検証する Authenticode XrML ライセンス。</span><span class="sxs-lookup"><span data-stu-id="9769b-107">[in] The Authenticode XrML license to be verified.</span></span>

 <span data-ttu-id="9769b-108">[CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob)構造を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9769b-108">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>

 `dwFlags`\
 <span data-ttu-id="9769b-109">[in] オプション。</span><span class="sxs-lookup"><span data-stu-id="9769b-109">[in] Optional.</span></span> <span data-ttu-id="9769b-110">以下の値の組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="9769b-110">A combination of following values:</span></span>

- <span data-ttu-id="9769b-111">AXL_REVOCATION_NO_CHECK</span><span class="sxs-lookup"><span data-stu-id="9769b-111">AXL_REVOCATION_NO_CHECK</span></span>

- <span data-ttu-id="9769b-112">AXL_REVOCATION_CHECK_END_CERT_ONLY</span><span class="sxs-lookup"><span data-stu-id="9769b-112">AXL_REVOCATION_CHECK_END_CERT_ONLY</span></span>

- <span data-ttu-id="9769b-113">AXL_REVOCATION_CHECK_ENTIRE_CHAIN</span><span class="sxs-lookup"><span data-stu-id="9769b-113">AXL_REVOCATION_CHECK_ENTIRE_CHAIN</span></span>

- <span data-ttu-id="9769b-114">AXL_URL_CACHE_ONLY_RETRIEVAL</span><span class="sxs-lookup"><span data-stu-id="9769b-114">AXL_URL_CACHE_ONLY_RETRIEVAL</span></span>

- <span data-ttu-id="9769b-115">AXL_LIFETIME_SIGNING</span><span class="sxs-lookup"><span data-stu-id="9769b-115">AXL_LIFETIME_SIGNING</span></span>

- <span data-ttu-id="9769b-116">AXL_TRUST_MICROSOFT_ROOT_ONLY</span><span class="sxs-lookup"><span data-stu-id="9769b-116">AXL_TRUST_MICROSOFT_ROOT_ONLY</span></span>

 `pSignerInfo`\
 <span data-ttu-id="9769b-117">[out] 署名者の情報を受け取るため。</span><span class="sxs-lookup"><span data-stu-id="9769b-117">[out] To receive the signer's information.</span></span> <span data-ttu-id="9769b-118">ライセンスに署名がない場合、`dwError` は TRUST_E_NOSIGNATURE に設定されます。</span><span class="sxs-lookup"><span data-stu-id="9769b-118">If the license wasn't signed, `dwError` is set to TRUST_E_NOSIGNATURE.</span></span> <span data-ttu-id="9769b-119">使用後に、 [Certfree認証 Oデザイナ情報](certfreeauthenticodesignerinfo-function.md) 関数を使用してリソースを解放するのは、呼び出し元の責任です。</span><span class="sxs-lookup"><span data-stu-id="9769b-119">It is the caller's responsibility to free resources by using the [CertFreeAuthenticodeSignerInfo](certfreeauthenticodesignerinfo-function.md) function after use.</span></span>

 <span data-ttu-id="9769b-120">「 [AXL_AUTHENTICODE_SIGNER_INFO 構造](axl-authenticode-signer-info-structure.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9769b-120">See [AXL_AUTHENTICODE_SIGNER_INFO Structure](axl-authenticode-signer-info-structure.md).</span></span>

 `pTimestamperInfo`\
 <span data-ttu-id="9769b-121">[out] 可能な場合は、タイム スタンプの情報を受け取るため。</span><span class="sxs-lookup"><span data-stu-id="9769b-121">[out] To receive time stamper's information, if available.</span></span> <span data-ttu-id="9769b-122">ライセンスにタイム スタンプがない場合、`dwError` は TRUST_E_NOSIGNATURE に設定されます。</span><span class="sxs-lookup"><span data-stu-id="9769b-122">If the license was not time-stamped, `dwError` is set to TRUST_E_NOSIGNATURE.</span></span> <span data-ttu-id="9769b-123">使用後に [CertFreeAuthenticodeTimestamperInfo](certfreeauthenticodetimestamperinfo-function.md) 関数を使用してリソースを解放するのは、呼び出し元の責任です。</span><span class="sxs-lookup"><span data-stu-id="9769b-123">It is the caller's responsibility to free resources by using the [CertFreeAuthenticodeTimestamperInfo](certfreeauthenticodetimestamperinfo-function.md) function after use.</span></span>

 <span data-ttu-id="9769b-124">「 [AXL_AUTHENTICODE_TIMESTAMPER_INFO 構造](axl-authenticode-timestamper-info-structure.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9769b-124">See [AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure](axl-authenticode-timestamper-info-structure.md).</span></span>

## <a name="return-value"></a><span data-ttu-id="9769b-125">戻り値</span><span class="sxs-lookup"><span data-stu-id="9769b-125">Return Value</span></span>

 <span data-ttu-id="9769b-126">正常に終了した場合は `S_OK` を返します。</span><span class="sxs-lookup"><span data-stu-id="9769b-126">Returns `S_OK` if successful.</span></span> <span data-ttu-id="9769b-127">それ以外の場合はエラー コードを返します。</span><span class="sxs-lookup"><span data-stu-id="9769b-127">Otherwise, returns an error code.</span></span>

## <a name="requirements"></a><span data-ttu-id="9769b-128">要件</span><span class="sxs-lookup"><span data-stu-id="9769b-128">Requirements</span></span>

<span data-ttu-id="9769b-129">**アセンブリ**: clr.dll</span><span class="sxs-lookup"><span data-stu-id="9769b-129">**Assembly**: clr.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="9769b-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="9769b-130">See also</span></span>

- [<span data-ttu-id="9769b-131">Authenticode</span><span class="sxs-lookup"><span data-stu-id="9769b-131">Authenticode</span></span>](index.md)
- [<span data-ttu-id="9769b-132">GetHashFromHandle メソッド</span><span class="sxs-lookup"><span data-stu-id="9769b-132">GetHashFromHandle Method</span></span>](../hosting/iclrstrongname-gethashfromhandle-method.md)
- [<span data-ttu-id="9769b-133">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9769b-133">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
