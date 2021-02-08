---
description: '詳細については、「IXCLRDataProcess:: StartEnumModules メソッド」を参照してください。'
title: 'IXCLRDataProcess:: StartEnumModules メソッド'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::StartEnumModules Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::StartEnumModules Method
helpviewer.keywords:
- IXCLRDataProcess::StartEnumModules Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 2e90c646ee8815ec10ce0bbd7538f13d7b5dcf8a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800581"
---
# <a name="ixclrdataprocessstartenummodules-method"></a><span data-ttu-id="0e9f7-103">IXCLRDataProcess:: StartEnumModules メソッド</span><span class="sxs-lookup"><span data-stu-id="0e9f7-103">IXCLRDataProcess::StartEnumModules Method</span></span>

<span data-ttu-id="0e9f7-104">プロセスのモジュールを列挙するハンドルを提供します。</span><span class="sxs-lookup"><span data-stu-id="0e9f7-104">Provides a handle to enumerate the modules of a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="0e9f7-105">構文</span><span class="sxs-lookup"><span data-stu-id="0e9f7-105">Syntax</span></span>

```cpp
HRESULT StartEnumModules(
    [out] CLRDATA_ENUM *handle
);
```

## <a name="parameters"></a><span data-ttu-id="0e9f7-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0e9f7-106">Parameters</span></span>

`handle`\
<span data-ttu-id="0e9f7-107">入出力モジュールを列挙するハンドル。</span><span class="sxs-lookup"><span data-stu-id="0e9f7-107">[out] A handle for enumerating the modules.</span></span>

## <a name="remarks"></a><span data-ttu-id="0e9f7-108">解説</span><span class="sxs-lookup"><span data-stu-id="0e9f7-108">Remarks</span></span>

<span data-ttu-id="0e9f7-109">指定されたメソッドはインターフェイスの一部で `IXCLRDataProcess` あり、仮想メソッドテーブルの24番のスロットに対応します。</span><span class="sxs-lookup"><span data-stu-id="0e9f7-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 24th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="0e9f7-110">要件</span><span class="sxs-lookup"><span data-stu-id="0e9f7-110">Requirements</span></span>

<span data-ttu-id="0e9f7-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0e9f7-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="0e9f7-112">**ヘッダー:** 存在</span><span class="sxs-lookup"><span data-stu-id="0e9f7-112">**Header:** None</span></span>  
<span data-ttu-id="0e9f7-113">**ライブラリ:** 存在</span><span class="sxs-lookup"><span data-stu-id="0e9f7-113">**Library:** None</span></span>  
<span data-ttu-id="0e9f7-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0e9f7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="0e9f7-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="0e9f7-115">See also</span></span>

- [<span data-ttu-id="0e9f7-116">CLRDataSourceType 列挙型</span><span class="sxs-lookup"><span data-stu-id="0e9f7-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="0e9f7-117">デバッグ</span><span class="sxs-lookup"><span data-stu-id="0e9f7-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="0e9f7-118">IXCLRDataProcess インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0e9f7-118">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
