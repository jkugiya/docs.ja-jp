---
description: '詳細については、「IXCLRDataProcess:: GetAppDomainByUniqueId メソッド」を参照してください。'
title: 'IXCLRDataProcess:: GetAppDomainByUniqueId メソッド'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::GetAppDomainByUniqueId Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::GetAppDomainByUniqueId Method
helpviewer.keywords:
- IXCLRDataProcess::GetAppDomainByUniqueId Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 7087362efbb810fcb6e1b6f7eb9f23c54c38fade
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800670"
---
# <a name="ixclrdataprocessgetappdomainbyuniqueid-method"></a><span data-ttu-id="898ee-103">IXCLRDataProcess:: GetAppDomainByUniqueId メソッド</span><span class="sxs-lookup"><span data-stu-id="898ee-103">IXCLRDataProcess::GetAppDomainByUniqueId Method</span></span>

<span data-ttu-id="898ee-104">一意の `AppDomain` 識別子に基づいて、プロセス内のを取得します。</span><span class="sxs-lookup"><span data-stu-id="898ee-104">Gets an `AppDomain` in a process based on its unique identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="898ee-105">構文</span><span class="sxs-lookup"><span data-stu-id="898ee-105">Syntax</span></span>

```cpp
HRESULT GetAppDomainByUniqueID(
    [in] ULONG64               id,
    [out] IXCLRDataAppDomain **appDomain
);
```

## <a name="parameters"></a><span data-ttu-id="898ee-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="898ee-106">Parameters</span></span>

`id`\
<span data-ttu-id="898ee-107">からAppDomain の一意識別子</span><span class="sxs-lookup"><span data-stu-id="898ee-107">[in] The unique identifier of the AppDomain</span></span>

`appDomain`\
<span data-ttu-id="898ee-108">入出力AppDomain</span><span class="sxs-lookup"><span data-stu-id="898ee-108">[out] The AppDomain</span></span>

## <a name="remarks"></a><span data-ttu-id="898ee-109">解説</span><span class="sxs-lookup"><span data-stu-id="898ee-109">Remarks</span></span>

<span data-ttu-id="898ee-110">指定されたメソッドはインターフェイスの一部で `IXCLRDataProcess` あり、仮想メソッドテーブルの20番目のスロットに対応します。</span><span class="sxs-lookup"><span data-stu-id="898ee-110">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 20th slot of the virtual method table.</span></span> <span data-ttu-id="898ee-111">返されるは、 `IXCLRDataAppDomain*` 他の api との対話に使用されます。</span><span class="sxs-lookup"><span data-stu-id="898ee-111">The `IXCLRDataAppDomain*` returned is used for interaction with other APIs.</span></span>

## <a name="requirements"></a><span data-ttu-id="898ee-112">要件</span><span class="sxs-lookup"><span data-stu-id="898ee-112">Requirements</span></span>

<span data-ttu-id="898ee-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="898ee-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>
<span data-ttu-id="898ee-114">**ヘッダー:** None **Library:** None **.NET Framework バージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="898ee-114">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="898ee-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="898ee-115">See also</span></span>

- [<span data-ttu-id="898ee-116">デバッグ</span><span class="sxs-lookup"><span data-stu-id="898ee-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="898ee-117">IXCLRDataProcess インターフェイス</span><span class="sxs-lookup"><span data-stu-id="898ee-117">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
