---
description: '詳細については、「IXCLRDataProcess:: EndEnumModules メソッド」を参照してください。'
title: 'IXCLRDataProcess:: EndEnumModules メソッド'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EndEnumModules Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EndEnumModules Method
helpviewer.keywords:
- IXCLRDataProcess::EndEnumModules Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 454d4fa3616f9ba8312dc3d1ac02c228625aa488
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800709"
---
# <a name="ixclrdataprocessendenummodules-method"></a><span data-ttu-id="f5060-103">IXCLRDataProcess:: EndEnumModules メソッド</span><span class="sxs-lookup"><span data-stu-id="f5060-103">IXCLRDataProcess::EndEnumModules Method</span></span>

<span data-ttu-id="f5060-104">モジュールの列挙中に使用される内部反復子によって使用されるリソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="f5060-104">Releases the resources used by internal iterators used during module enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="f5060-105">構文</span><span class="sxs-lookup"><span data-stu-id="f5060-105">Syntax</span></span>

```cpp
HRESULT EndEnumModules(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="f5060-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f5060-106">Parameters</span></span>

`handle`\
<span data-ttu-id="f5060-107">入出力モジュールを列挙するハンドル。</span><span class="sxs-lookup"><span data-stu-id="f5060-107">[out] A handle for enumerating the modules.</span></span>

## <a name="remarks"></a><span data-ttu-id="f5060-108">解説</span><span class="sxs-lookup"><span data-stu-id="f5060-108">Remarks</span></span>

<span data-ttu-id="f5060-109">指定されたメソッドはインターフェイスの一部で `IXCLRDataProcess` あり、仮想メソッドテーブルの26日スロットに対応します。</span><span class="sxs-lookup"><span data-stu-id="f5060-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 26th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="f5060-110">要件</span><span class="sxs-lookup"><span data-stu-id="f5060-110">Requirements</span></span>

<span data-ttu-id="f5060-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5060-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>
<span data-ttu-id="f5060-112">**ヘッダー:** None **Library:** None **.NET Framework バージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f5060-112">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="f5060-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="f5060-113">See also</span></span>

- [<span data-ttu-id="f5060-114">デバッグ</span><span class="sxs-lookup"><span data-stu-id="f5060-114">Debugging</span></span>](index.md)
- [<span data-ttu-id="f5060-115">IXCLRDataProcess インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f5060-115">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
