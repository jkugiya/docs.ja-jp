---
description: '詳細については、「IXCLRDataProcess:: EnumMethodInstanceByAddress メソッド」を参照してください。'
title: 'IXCLRDataProcess:: EnumMethodInstanceByAddress メソッド'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: a0d59956288e39be188628d10c63a52d09d17638
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800696"
---
# <a name="ixclrdataprocessenummethodinstancebyaddress-method"></a><span data-ttu-id="05736-103">IXCLRDataProcess:: EnumMethodInstanceByAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="05736-103">IXCLRDataProcess::EnumMethodInstanceByAddress Method</span></span>

<span data-ttu-id="05736-104">このプロセスのメソッドインスタンスを、アドレスオフセットを開始位置として列挙します。</span><span class="sxs-lookup"><span data-stu-id="05736-104">Enumerates the method instances of this process starting at an address offset.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="05736-105">構文</span><span class="sxs-lookup"><span data-stu-id="05736-105">Syntax</span></span>

```cpp
HRESULT EnumMethodInstanceByAddress(
    [in] CLRDATA_ENUM              *handle,
    [out] IXCLRDataMethodInstance **method
);
```

## <a name="parameters"></a><span data-ttu-id="05736-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="05736-106">Parameters</span></span>

`handle`\
<span data-ttu-id="05736-107">からメソッドインスタンスを列挙するハンドル。</span><span class="sxs-lookup"><span data-stu-id="05736-107">[in] A handle for enumerating the method instances.</span></span>

`mod`\
<span data-ttu-id="05736-108">入出力列挙されたメソッドインスタンス。</span><span class="sxs-lookup"><span data-stu-id="05736-108">[out] The enumerated method instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="05736-109">解説</span><span class="sxs-lookup"><span data-stu-id="05736-109">Remarks</span></span>

<span data-ttu-id="05736-110">指定されたメソッドはインターフェイスの一部で `IXCLRDataProcess` あり、仮想メソッドテーブルの29スロットに対応します。</span><span class="sxs-lookup"><span data-stu-id="05736-110">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 29th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="05736-111">要件</span><span class="sxs-lookup"><span data-stu-id="05736-111">Requirements</span></span>

<span data-ttu-id="05736-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="05736-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>
<span data-ttu-id="05736-113">**ヘッダー:** None **Library:** None **.NET Framework バージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="05736-113">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="05736-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="05736-114">See also</span></span>

- [<span data-ttu-id="05736-115">CLRDataSourceType 列挙型</span><span class="sxs-lookup"><span data-stu-id="05736-115">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="05736-116">デバッグ</span><span class="sxs-lookup"><span data-stu-id="05736-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="05736-117">IXCLRDataProcess インターフェイス</span><span class="sxs-lookup"><span data-stu-id="05736-117">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
