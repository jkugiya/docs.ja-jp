---
description: 詳細については、「Certfree認証 Oデザイナ情報関数」を参照してください。
title: CertFreeAuthenticodeSignerInfo 関数
ms.date: 03/30/2017
api_name:
- CertFreeAuthenticodeSignerInfo
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 8029633c-b6e4-4665-a7c2-89607c3247ef
topic_type:
- apiref
ms.openlocfilehash: 6e8a97e8fee37d885c7d32102ed8cc7654992223
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772979"
---
# <a name="certfreeauthenticodesignerinfo-function"></a><span data-ttu-id="836b7-103">CertFreeAuthenticodeSignerInfo 関数</span><span class="sxs-lookup"><span data-stu-id="836b7-103">CertFreeAuthenticodeSignerInfo Function</span></span>

<span data-ttu-id="836b7-104">[AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md)構造に割り当てられたリソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="836b7-104">Frees resources allocated for the [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) structure.</span></span>

## <a name="syntax"></a><span data-ttu-id="836b7-105">構文</span><span class="sxs-lookup"><span data-stu-id="836b7-105">Syntax</span></span>

```cpp
HRESULT CertFreeAuthenticodeSignerInfo (
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);
```

## <a name="parameters"></a><span data-ttu-id="836b7-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="836b7-106">Parameters</span></span>

 `pSignerInfo`\
 <span data-ttu-id="836b7-107">[in, out] リリースされる署名者情報。</span><span class="sxs-lookup"><span data-stu-id="836b7-107">[in, out] Signer information to be released.</span></span> <span data-ttu-id="836b7-108">[AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md)構造を参照してください。</span><span class="sxs-lookup"><span data-stu-id="836b7-108">See the [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) structure.</span></span>

## <a name="return-value"></a><span data-ttu-id="836b7-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="836b7-109">Return Value</span></span>

 <span data-ttu-id="836b7-110">関数が成功した場合は `S_OK`。</span><span class="sxs-lookup"><span data-stu-id="836b7-110">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="836b7-111">それ以外の場合はエラー コードを返します。</span><span class="sxs-lookup"><span data-stu-id="836b7-111">Otherwise, returns an error code.</span></span>

## <a name="requirements"></a><span data-ttu-id="836b7-112">要件</span><span class="sxs-lookup"><span data-stu-id="836b7-112">Requirements</span></span>

<span data-ttu-id="836b7-113">**アセンブリ**: clr.dll</span><span class="sxs-lookup"><span data-stu-id="836b7-113">**Assembly**: clr.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="836b7-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="836b7-114">See also</span></span>

- [<span data-ttu-id="836b7-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="836b7-115">Authenticode</span></span>](index.md)
