---
description: '詳細情報: _AxlGetIssuerPublicKeyHash 関数'
title: _AxlGetIssuerPublicKeyHash 関数
ms.date: 03/30/2017
api_name:
- _AxlGetIssuerPublicKeyHash
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: fb626b41-b888-4625-84c3-2c02b5e3866f
topic_type:
- apiref
ms.openlocfilehash: 586a072b33376a2fdade119fe3db0f48addfa3f5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747362"
---
# <a name="_axlgetissuerpublickeyhash-function"></a><span data-ttu-id="6c356-103">\_AxlGetIssuerPublicKeyHash 関数</span><span class="sxs-lookup"><span data-stu-id="6c356-103">\_AxlGetIssuerPublicKeyHash Function</span></span>

<span data-ttu-id="6c356-104">指定された証明書の署名に使用する秘密キーに関連付けられている公開キーの SHA-1 ハッシュを取得します。</span><span class="sxs-lookup"><span data-stu-id="6c356-104">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>

## <a name="syntax"></a><span data-ttu-id="6c356-105">構文</span><span class="sxs-lookup"><span data-stu-id="6c356-105">Syntax</span></span>

```cpp
HRESULT _AxlGetIssuerPublicKeyHash (
    [in]  IN PCRYPT_DATA_BLOB   pChainContext,
    [out] LPWSTR                *ppwszPublicKeyHash
);
```

## <a name="parameters"></a><span data-ttu-id="6c356-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6c356-106">Parameters</span></span>

 `pChainContext`\
 <span data-ttu-id="6c356-107">[in] CSP 公開キー BLOB。</span><span class="sxs-lookup"><span data-stu-id="6c356-107">[in] The CSP public key blob.</span></span> <span data-ttu-id="6c356-108">[CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob)構造を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c356-108">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>

 `ppwszPublicKeyHash`\
 <span data-ttu-id="6c356-109">[out] 16 進エンコードされた公開キー トークンを受け取るための WCHAR \* へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c356-109">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>

## <a name="return-value"></a><span data-ttu-id="6c356-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="6c356-110">Return Value</span></span>

 <span data-ttu-id="6c356-111">関数が成功した場合は `S_OK`、それ以外の場合は `S_FALSE`。</span><span class="sxs-lookup"><span data-stu-id="6c356-111">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>

## <a name="requirements"></a><span data-ttu-id="6c356-112">要件</span><span class="sxs-lookup"><span data-stu-id="6c356-112">Requirements</span></span>

<span data-ttu-id="6c356-113">**アセンブリ**: clr.dll</span><span class="sxs-lookup"><span data-stu-id="6c356-113">**Assembly**: clr.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="6c356-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="6c356-114">See also</span></span>

- [<span data-ttu-id="6c356-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="6c356-115">Authenticode</span></span>](index.md)
