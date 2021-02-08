---
description: 詳細については、「IXCLRDataProcess インターフェイス」を参照してください。
title: IXCLRDataProcess インターフェイス
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess Interface
helpviewer.keywords:
- IXCLRDataProcess Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: b611491e5c9a5957c07a305a3f395b67ad208649
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800644"
---
# <a name="ixclrdataprocess-interface"></a><span data-ttu-id="b66c6-103">IXCLRDataProcess インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b66c6-103">IXCLRDataProcess Interface</span></span>

<span data-ttu-id="b66c6-104">プロセスに関する情報を照会するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="b66c6-104">Provides methods for querying information about a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="b66c6-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="b66c6-105">Methods</span></span>

| <span data-ttu-id="b66c6-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="b66c6-106">Method</span></span>                                                                                                                                               | <span data-ttu-id="b66c6-107">説明</span><span class="sxs-lookup"><span data-stu-id="b66c6-107">Description</span></span>                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="b66c6-108">GetRuntimeNameByAddress</span><span class="sxs-lookup"><span data-stu-id="b66c6-108">GetRuntimeNameByAddress</span></span>](ixclrdataprocess-getruntimenamebyaddress-method.md)                     | <span data-ttu-id="b66c6-109">指定されたアドレスの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="b66c6-109">Gets a name for the given address.</span></span>                                                               |
| [<span data-ttu-id="b66c6-110">GetAppDomainByUniqueId</span><span class="sxs-lookup"><span data-stu-id="b66c6-110">GetAppDomainByUniqueId</span></span>](ixclrdataprocess-getappdomainbyuniqueid-method.md)                       | <span data-ttu-id="b66c6-111">`AppDomain`プロセス内のを一意の id で取得します。</span><span class="sxs-lookup"><span data-stu-id="b66c6-111">Gets an `AppDomain` in a process by its unique id.</span></span>                                              |
| [<span data-ttu-id="b66c6-112">StartEnumModules</span><span class="sxs-lookup"><span data-stu-id="b66c6-112">StartEnumModules</span></span>](ixclrdataprocess-startenummodules-method.md)                                   | <span data-ttu-id="b66c6-113">プロセスのモジュールを列挙するハンドルを提供します。</span><span class="sxs-lookup"><span data-stu-id="b66c6-113">Provides a handle to enumerate the modules of a process.</span></span>                                        |
| [<span data-ttu-id="b66c6-114">EnumModule</span><span class="sxs-lookup"><span data-stu-id="b66c6-114">EnumModule</span></span>](ixclrdataprocess-enummodule-method.md)                                               | <span data-ttu-id="b66c6-115">このプロセスのモジュールを列挙します。</span><span class="sxs-lookup"><span data-stu-id="b66c6-115">Enumerates the modules of this process.</span></span>                                                         |
| [<span data-ttu-id="b66c6-116">EndEnumModules</span><span class="sxs-lookup"><span data-stu-id="b66c6-116">EndEnumModules</span></span>](ixclrdataprocess-endenummodules-method.md)                                       | <span data-ttu-id="b66c6-117">モジュールの列挙中に使用される内部反復子によって使用されるリソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="b66c6-117">Releases the resources used by internal iterators used during module enumeration.</span></span>               |
| [<span data-ttu-id="b66c6-118">StartEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="b66c6-118">StartEnumMethodInstancesByAddress</span></span>](ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | <span data-ttu-id="b66c6-119">指定されたアドレスから開始するのメソッドインスタンスを列挙するハンドルを提供し `AppDomain` ます。</span><span class="sxs-lookup"><span data-stu-id="b66c6-119">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span> |
| [<span data-ttu-id="b66c6-120">EnumMethodInstanceByAddress</span><span class="sxs-lookup"><span data-stu-id="b66c6-120">EnumMethodInstanceByAddress</span></span>](ixclrdataprocess-enummethodinstancebyaddress-method.md)             | <span data-ttu-id="b66c6-121">このプロセスのメソッドインスタンスを、アドレスオフセットを開始位置として列挙します。</span><span class="sxs-lookup"><span data-stu-id="b66c6-121">Enumerates the method instances of this process starting at an address offset.</span></span>                  |
| [<span data-ttu-id="b66c6-122">EndEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="b66c6-122">EndEnumMethodInstancesByAddress</span></span>](ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | <span data-ttu-id="b66c6-123">インスタンスの列挙中に使用される内部反復子によって使用されるリソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="b66c6-123">Releases the resources used by internal iterators used during instance enumeration.</span></span>             |

## <a name="remarks"></a><span data-ttu-id="b66c6-124">解説</span><span class="sxs-lookup"><span data-stu-id="b66c6-124">Remarks</span></span>

<span data-ttu-id="b66c6-125">このインターフェイスはランタイム内に存在し、ヘッダーまたはライブラリファイルを介して公開されることはありません。</span><span class="sxs-lookup"><span data-stu-id="b66c6-125">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="b66c6-126">ただし、これは、 `IUnknown` `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` 通常の com 機構を通じて取得できる GUID を使用してから派生する com インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="b66c6-126">However, it's a COM interface that derives from `IUnknown` with GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="b66c6-127">要件</span><span class="sxs-lookup"><span data-stu-id="b66c6-127">Requirements</span></span>

<span data-ttu-id="b66c6-128">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b66c6-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>
<span data-ttu-id="b66c6-129">**ヘッダー:** 存在</span><span class="sxs-lookup"><span data-stu-id="b66c6-129">**Header:** None</span></span>  
<span data-ttu-id="b66c6-130">**ライブラリ:** 存在</span><span class="sxs-lookup"><span data-stu-id="b66c6-130">**Library:** None</span></span>  
<span data-ttu-id="b66c6-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b66c6-131">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="b66c6-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="b66c6-132">See also</span></span>

- [<span data-ttu-id="b66c6-133">デバッグ</span><span class="sxs-lookup"><span data-stu-id="b66c6-133">Debugging</span></span>](index.md)
- [<span data-ttu-id="b66c6-134">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="b66c6-134">Debugging Interfaces</span></span>](debugging-interfaces.md)
