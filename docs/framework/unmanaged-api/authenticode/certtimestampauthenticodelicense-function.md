---
description: '詳細については、次を参照してください: Certタイムの認証 Odelicense 関数'
title: CertTimestampAuthenticodeLicense 関数
ms.date: 03/30/2017
api_name:
- CertTimestampAuthenticodeLicense
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: d468325a-21c5-43ce-8567-84e342b22308
topic_type:
- apiref
ms.openlocfilehash: 79b1a924a99a76c18e6434abfed0a90da71eb6f9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772920"
---
# <a name="certtimestampauthenticodelicense-function"></a><span data-ttu-id="51b38-103">CertTimestampAuthenticodeLicense 関数</span><span class="sxs-lookup"><span data-stu-id="51b38-103">CertTimestampAuthenticodeLicense Function</span></span>

<span data-ttu-id="51b38-104">Authenticode XrML ライセンスにタイム スタンプを付けます。</span><span class="sxs-lookup"><span data-stu-id="51b38-104">Time-stamps an Authenticode XrML license.</span></span>

## <a name="syntax"></a><span data-ttu-id="51b38-105">構文</span><span class="sxs-lookup"><span data-stu-id="51b38-105">Syntax</span></span>

```cpp
HRESULT CertTimestampAuthenticodeLicense (
    [in]  PCRYPT_DATA_BLOB   pSignedLicenseBlob,
    [in]  LPCWSTR            pwszTimestampURI,
    [out] PCRYPT_DATA_BLOB   pTimestampSignatureBlob
);
```

## <a name="parameters"></a><span data-ttu-id="51b38-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="51b38-106">Parameters</span></span>

 `pSignedLicenseBlob`\
 <span data-ttu-id="51b38-107">[in] タイム スタンプが付けられる、署名付きの Authenticode XrML ライセンス。</span><span class="sxs-lookup"><span data-stu-id="51b38-107">[in] The signed Authenticode XrML license to be time-stamped.</span></span> <span data-ttu-id="51b38-108">[CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob)構造を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51b38-108">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>

 `pwszTimestampURI`\
 <span data-ttu-id="51b38-109">[in] タイム スタンプ サーバーの URI。</span><span class="sxs-lookup"><span data-stu-id="51b38-109">[in] The time-stamp server's URI.</span></span>

 `pTimestampSignatureBlob`\
 <span data-ttu-id="51b38-110">[out] base64 でエンコードされたタイム スタンプの署名を取得するための、CRYPT_DATA_BLOB へのポインター。</span><span class="sxs-lookup"><span data-stu-id="51b38-110">[out] A pointer to CRYPT_DATA_BLOB to receive the base64-encoded time-stamp signature.</span></span> <span data-ttu-id="51b38-111">呼び出し元は、 `pTimestampSignatureBlob` -> `pbData` 使用後にを解放する必要が `HepFree()` あります。</span><span class="sxs-lookup"><span data-stu-id="51b38-111">It is the caller's responsibility to free `pTimestampSignatureBlob`->`pbData` with `HepFree()` after use.</span></span> <span data-ttu-id="51b38-112">[CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob)構造を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51b38-112">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>

## <a name="remarks"></a><span data-ttu-id="51b38-113">解説</span><span class="sxs-lookup"><span data-stu-id="51b38-113">Remarks</span></span>

 <span data-ttu-id="51b38-114">タイム スタンプの署名は、実際は PKCS #7 SignedData メッセージで、この内容は、ライセンスの署名の SignatureValue のバイナリ形式です。</span><span class="sxs-lookup"><span data-stu-id="51b38-114">The time-stamp signature is actually a PKCS #7 SignedData message whose content is the binary form of the SignatureValue from the license's signature.</span></span> <span data-ttu-id="51b38-115">これは基本的に、ライセンスの副署名として機能します。</span><span class="sxs-lookup"><span data-stu-id="51b38-115">Basically, this acts as a counter-signature of the license.</span></span>

## <a name="return-value"></a><span data-ttu-id="51b38-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="51b38-116">Return Value</span></span>

 <span data-ttu-id="51b38-117">関数が成功した場合は `S_OK`。</span><span class="sxs-lookup"><span data-stu-id="51b38-117">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="51b38-118">それ以外の場合はエラー コードを返します。</span><span class="sxs-lookup"><span data-stu-id="51b38-118">Otherwise, returns an error code.</span></span>

## <a name="requirements"></a><span data-ttu-id="51b38-119">要件</span><span class="sxs-lookup"><span data-stu-id="51b38-119">Requirements</span></span>

<span data-ttu-id="51b38-120">**アセンブリ**: clr.dll</span><span class="sxs-lookup"><span data-stu-id="51b38-120">**Assembly**: clr.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="51b38-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="51b38-121">See also</span></span>

- [<span data-ttu-id="51b38-122">Authenticode</span><span class="sxs-lookup"><span data-stu-id="51b38-122">Authenticode</span></span>](index.md)
