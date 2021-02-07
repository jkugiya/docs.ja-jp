---
description: '詳細情報: _AxlRSAKeyValueToPublicKeyToken 関数'
title: _AxlRSAKeyValueToPublicKeyToken 関数
ms.date: 03/30/2017
api_name:
- _AxlRSAKeyValueToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: d60f19fe-7bec-47ba-b60e-ba9ce66abf8c
topic_type:
- apiref
ms.openlocfilehash: 01fc4cdc1d9985375748307ca2d7fff97191c908
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747271"
---
# <a name="_axlrsakeyvaluetopublickeytoken-function"></a><span data-ttu-id="d4604-103">\_AxlRSAKeyValueToPublicKeyToken 関数</span><span class="sxs-lookup"><span data-stu-id="d4604-103">\_AxlRSAKeyValueToPublicKeyToken function</span></span>

<span data-ttu-id="d4604-104">Modulus および Exponent を、厳密な名前の公開キー トークンに変換します。</span><span class="sxs-lookup"><span data-stu-id="d4604-104">Converts a Modulus and Exponent to a strong name public key token.</span></span>

## <a name="syntax"></a><span data-ttu-id="d4604-105">構文</span><span class="sxs-lookup"><span data-stu-id="d4604-105">Syntax</span></span>

```cpp
HRESULT _AxlRSAKeyValueToPublicKeyToken (
    [in]  PCRYPT_DATA_BLOB pModulusBlob,
    [in]  PCRYPT_DATA_BLOB pExponentBlob,
    [out] LPWSTR           *ppwszPublicKeyToken
);
```

## <a name="parameters"></a><span data-ttu-id="d4604-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d4604-106">Parameters</span></span>

 `pModulusBlob`\
 <span data-ttu-id="d4604-107">からBase64 でエンコードされた剰余 blob ( \<Modulus> 要素から)。</span><span class="sxs-lookup"><span data-stu-id="d4604-107">[in] The base64-encoded Modulus blob (from the \<Modulus> element).</span></span>  <span data-ttu-id="d4604-108">[CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob)構造を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4604-108">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>

 `pExponentBlob`\
 <span data-ttu-id="d4604-109">からBase64 でエンコードされた指数 (要素からの \<Exponent> ) blob。</span><span class="sxs-lookup"><span data-stu-id="d4604-109">[in] The base64-encoded Exponent blob (from the \<Exponent> element).</span></span> <span data-ttu-id="d4604-110">[CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob)構造を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4604-110">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>

 `ppwszPublicKeyToken`\
 <span data-ttu-id="d4604-111">[out] 16 進エンコードされた公開キー トークンを受け取るための WCHAR \* へのポインター。</span><span class="sxs-lookup"><span data-stu-id="d4604-111">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>

## <a name="return-value"></a><span data-ttu-id="d4604-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="d4604-112">Return Value</span></span>

 <span data-ttu-id="d4604-113">関数が成功した場合は `S_OK`。</span><span class="sxs-lookup"><span data-stu-id="d4604-113">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="d4604-114">それ以外の場合はエラー コードを返します。</span><span class="sxs-lookup"><span data-stu-id="d4604-114">Otherwise, returns an error code.</span></span>

## <a name="requirements"></a><span data-ttu-id="d4604-115">要件</span><span class="sxs-lookup"><span data-stu-id="d4604-115">Requirements</span></span>

<span data-ttu-id="d4604-116">**アセンブリ**: clr.dll</span><span class="sxs-lookup"><span data-stu-id="d4604-116">**Assembly**: clr.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="d4604-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="d4604-117">See also</span></span>

- [<span data-ttu-id="d4604-118">Authenticode</span><span class="sxs-lookup"><span data-stu-id="d4604-118">Authenticode</span></span>](index.md)
