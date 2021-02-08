---
description: '詳細情報: CertFreeAuthenticodeTimestamperInfo 関数'
title: CertFreeAuthenticodeTimestamperInfo 関数
ms.date: 03/30/2017
api_name:
- CertFreeAuthenticodeTimestamperInfo
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 3eb14c49-68c2-4516-ac89-e5bd7473831c
topic_type:
- apiref
ms.openlocfilehash: 5234a90ea1d0272a7409b1b0b4def2160b77a513
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772940"
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a><span data-ttu-id="e76b8-103">CertFreeAuthenticodeTimestamperInfo 関数</span><span class="sxs-lookup"><span data-stu-id="e76b8-103">CertFreeAuthenticodeTimestamperInfo Function</span></span>

<span data-ttu-id="e76b8-104">[AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md)構造に割り当てられたリソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="e76b8-104">Frees resources allocated for the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) structure.</span></span>

## <a name="syntax"></a><span data-ttu-id="e76b8-105">構文</span><span class="sxs-lookup"><span data-stu-id="e76b8-105">Syntax</span></span>

```cpp
HRESULT CertFreeAuthenticodeTimestamperInfo (
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo
);
```

## <a name="parameters"></a><span data-ttu-id="e76b8-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e76b8-106">Parameters</span></span>

 `pTimestamperInfo`\
 <span data-ttu-id="e76b8-107">[入力、出力] 解放されるタイム スタンパー情報。</span><span class="sxs-lookup"><span data-stu-id="e76b8-107">[in, out] The time stamper information to be released.</span></span> <span data-ttu-id="e76b8-108">[AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md)構造を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e76b8-108">See the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) structure.</span></span>

## <a name="return-value"></a><span data-ttu-id="e76b8-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="e76b8-109">Return Value</span></span>

 <span data-ttu-id="e76b8-110">関数が成功した場合は `S_OK`。</span><span class="sxs-lookup"><span data-stu-id="e76b8-110">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="e76b8-111">それ以外の場合はエラー コードを返します。</span><span class="sxs-lookup"><span data-stu-id="e76b8-111">Otherwise, returns an error code.</span></span>

## <a name="requirements"></a><span data-ttu-id="e76b8-112">要件</span><span class="sxs-lookup"><span data-stu-id="e76b8-112">Requirements</span></span>

<span data-ttu-id="e76b8-113">**アセンブリ**: clr.dll</span><span class="sxs-lookup"><span data-stu-id="e76b8-113">**Assembly**: clr.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="e76b8-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="e76b8-114">See also</span></span>

- [<span data-ttu-id="e76b8-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="e76b8-115">Authenticode</span></span>](index.md)
