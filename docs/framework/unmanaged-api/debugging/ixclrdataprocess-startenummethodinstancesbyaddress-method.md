---
description: '詳細については、「IXCLRDataProcess:: StartEnumMethodInstancesByAddress メソッド」を参照してください。'
title: 'IXCLRDataProcess:: StartEnumMethodInstancesByAddress メソッド'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 155d09192b60b8671435abb439f07dfbb290bc87
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800591"
---
# <a name="ixclrdataprocessstartenummethodinstancesbyaddress-method"></a><span data-ttu-id="81a05-103">IXCLRDataProcess:: StartEnumMethodInstancesByAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="81a05-103">IXCLRDataProcess::StartEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="81a05-104">指定されたアドレスから開始するのメソッドインスタンスを列挙するハンドルを提供し `AppDomain` ます。</span><span class="sxs-lookup"><span data-stu-id="81a05-104">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="81a05-105">構文</span><span class="sxs-lookup"><span data-stu-id="81a05-105">Syntax</span></span>

```cpp
HRESULT StartEnumMethodInstancesByAddress(
    [in] CLRDATA_ADDRESS     address,
    [in] IXCLRDataAppDomain *appDomain,
    [out] CLRDATA_ENUM      *handle
);
```

## <a name="parameters"></a><span data-ttu-id="81a05-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="81a05-106">Parameters</span></span>

`address`\
<span data-ttu-id="81a05-107">から最初のメソッドインスタンスのアドレス。</span><span class="sxs-lookup"><span data-stu-id="81a05-107">[in] The address of the first method instance.</span></span>

`appDomain`\
<span data-ttu-id="81a05-108">からメソッドインスタンスの AppDomain。</span><span class="sxs-lookup"><span data-stu-id="81a05-108">[in] The AppDomain of the method instances.</span></span>

`handle`\
<span data-ttu-id="81a05-109">入出力メソッドインスタンスを列挙するハンドル。</span><span class="sxs-lookup"><span data-stu-id="81a05-109">[out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="81a05-110">解説</span><span class="sxs-lookup"><span data-stu-id="81a05-110">Remarks</span></span>

<span data-ttu-id="81a05-111">指定されたメソッドはインターフェイスの一部で `IXCLRDataProcess` あり、仮想メソッドテーブルの28番目のスロットに対応します。</span><span class="sxs-lookup"><span data-stu-id="81a05-111">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 28th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="81a05-112">要件</span><span class="sxs-lookup"><span data-stu-id="81a05-112">Requirements</span></span>

<span data-ttu-id="81a05-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="81a05-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="81a05-114">**ヘッダー:** 存在</span><span class="sxs-lookup"><span data-stu-id="81a05-114">**Header:** None</span></span>  
<span data-ttu-id="81a05-115">**ライブラリ:** 存在</span><span class="sxs-lookup"><span data-stu-id="81a05-115">**Library:** None</span></span>  
<span data-ttu-id="81a05-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="81a05-116">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="81a05-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="81a05-117">See also</span></span>

- [<span data-ttu-id="81a05-118">CLRDataSourceType 列挙型</span><span class="sxs-lookup"><span data-stu-id="81a05-118">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="81a05-119">デバッグ</span><span class="sxs-lookup"><span data-stu-id="81a05-119">Debugging</span></span>](index.md)
- [<span data-ttu-id="81a05-120">IXCLRDataProcess インターフェイス</span><span class="sxs-lookup"><span data-stu-id="81a05-120">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
