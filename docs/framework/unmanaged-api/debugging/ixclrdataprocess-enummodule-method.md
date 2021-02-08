---
description: '詳細については、「IXCLRDataProcess:: EnumModule メソッド」を参照してください。'
title: 'IXCLRDataProcess:: EnumModule メソッド'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EnumModule Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EnumModule Method
helpviewer.keywords:
- IXCLRDataProcess::EnumModule Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 33b15da6939a0fb78a4eeafcf75e1a2b2f0d0ab1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800683"
---
# <a name="ixclrdataprocessenummodule-method"></a><span data-ttu-id="e8cfa-103">IXCLRDataProcess:: EnumModule メソッド</span><span class="sxs-lookup"><span data-stu-id="e8cfa-103">IXCLRDataProcess::EnumModule Method</span></span>

<span data-ttu-id="e8cfa-104">このプロセスのモジュールを列挙します。</span><span class="sxs-lookup"><span data-stu-id="e8cfa-104">Enumerates the modules of this process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="e8cfa-105">構文</span><span class="sxs-lookup"><span data-stu-id="e8cfa-105">Syntax</span></span>

```cpp
HRESULT EnumModule(
    [in, out] CLRDATA_ENUM  *handle,
    [out] IXCLRDataModule  **mod
);
```

## <a name="parameters"></a><span data-ttu-id="e8cfa-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e8cfa-106">Parameters</span></span>

`handle`\
<span data-ttu-id="e8cfa-107">[入力、出力]モジュールを列挙するハンドル。</span><span class="sxs-lookup"><span data-stu-id="e8cfa-107">[in, out] A handle for enumerating the modules.</span></span>

`mod`\
<span data-ttu-id="e8cfa-108">入出力列挙されたモジュール。</span><span class="sxs-lookup"><span data-stu-id="e8cfa-108">[out] The enumerated module.</span></span>

## <a name="remarks"></a><span data-ttu-id="e8cfa-109">解説</span><span class="sxs-lookup"><span data-stu-id="e8cfa-109">Remarks</span></span>

<span data-ttu-id="e8cfa-110">指定されたメソッドはインターフェイスの一部で `IXCLRDataProcess` あり、仮想メソッドテーブルの25スロットに対応します。</span><span class="sxs-lookup"><span data-stu-id="e8cfa-110">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 25th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="e8cfa-111">要件</span><span class="sxs-lookup"><span data-stu-id="e8cfa-111">Requirements</span></span>

<span data-ttu-id="e8cfa-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8cfa-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="e8cfa-113">**ヘッダー:** 存在</span><span class="sxs-lookup"><span data-stu-id="e8cfa-113">**Header:** None</span></span>  
<span data-ttu-id="e8cfa-114">**ライブラリ:** 存在</span><span class="sxs-lookup"><span data-stu-id="e8cfa-114">**Library:** None</span></span>  
<span data-ttu-id="e8cfa-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e8cfa-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="e8cfa-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="e8cfa-116">See also</span></span>

- [<span data-ttu-id="e8cfa-117">CLRDataSourceType 列挙型</span><span class="sxs-lookup"><span data-stu-id="e8cfa-117">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="e8cfa-118">デバッグ</span><span class="sxs-lookup"><span data-stu-id="e8cfa-118">Debugging</span></span>](index.md)
- [<span data-ttu-id="e8cfa-119">IXCLRDataModule インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e8cfa-119">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
- [<span data-ttu-id="e8cfa-120">IXCLRDataProcess インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e8cfa-120">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
