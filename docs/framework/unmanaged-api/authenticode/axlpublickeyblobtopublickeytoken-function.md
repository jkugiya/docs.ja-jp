---
description: '詳細情報: _AxlPublicKeyBlobToPublicKeyToken 関数'
title: _AxlPublicKeyBlobToPublicKeyToken 関数
ms.date: 03/30/2017
api_name:
- _AxlPublicKeyBlobToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 2d92a746-d68c-4f53-a16e-727f071a2d80
topic_type:
- apiref
ms.openlocfilehash: df0b484bad64051eb892d4898a6c90777cc2d5cf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781936"
---
# <a name="_axlpublickeyblobtopublickeytoken-function"></a><span data-ttu-id="6b515-103">\_AxlPublicKeyBlobToPublicKeyToken 関数</span><span class="sxs-lookup"><span data-stu-id="6b515-103">\_AxlPublicKeyBlobToPublicKeyToken Function</span></span>

<span data-ttu-id="6b515-104">CSP PUBLICKEYBLOB 形式から厳密な名前の公開キー トークンを算出します。</span><span class="sxs-lookup"><span data-stu-id="6b515-104">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>

## <a name="syntax"></a><span data-ttu-id="6b515-105">構文</span><span class="sxs-lookup"><span data-stu-id="6b515-105">Syntax</span></span>

```cpp
HRESULT _AxlPublicKeyBlobToPublicKeyToken (
    [in]  PCCERT_CHAIN_CONTEXT   pCspPublicKeyBlob,
    [out] LPWSTR                 *ppwszPublicKeyToken
);
```

## <a name="parameters"></a><span data-ttu-id="6b515-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6b515-106">Parameters</span></span>

 `pCspPublicKeyBlob`\
 <span data-ttu-id="6b515-107">[in] CSP 公開キー BLOB。</span><span class="sxs-lookup"><span data-stu-id="6b515-107">[in] The CSP public key blob.</span></span>

 `ppwszPublicKeyHash`\
 <span data-ttu-id="6b515-108">[out] 16 進エンコードされた公開キー ハッシュを受け取るための WCHAR \* へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6b515-108">[out] A pointer to WCHAR \* to receive the hex-encoded public key hash.</span></span>

## <a name="return-value"></a><span data-ttu-id="6b515-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="6b515-109">Return Value</span></span>

 <span data-ttu-id="6b515-110">関数が成功した場合は `S_OK`、それ以外の場合は `S_FALSE`。</span><span class="sxs-lookup"><span data-stu-id="6b515-110">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>

## <a name="requirements"></a><span data-ttu-id="6b515-111">要件</span><span class="sxs-lookup"><span data-stu-id="6b515-111">Requirements</span></span>

<span data-ttu-id="6b515-112">**アセンブリ**: clr.dll</span><span class="sxs-lookup"><span data-stu-id="6b515-112">**Assembly**: clr.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="6b515-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="6b515-113">See also</span></span>

- [<span data-ttu-id="6b515-114">Authenticode</span><span class="sxs-lookup"><span data-stu-id="6b515-114">Authenticode</span></span>](index.md)
