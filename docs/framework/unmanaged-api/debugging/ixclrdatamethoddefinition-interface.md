---
description: 詳細については、「IXCLRDataMethodDefinition インターフェイス」を参照してください。
title: IXCLRDataMethodDefinition インターフェイス
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition Interface
helpviewer.keywords:
- IXCLRDataMethodDefinition Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: d73246b42a0bfb982c87b04d5490e945f7caa745
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790348"
---
# <a name="ixclrdatamethoddefinition-interface"></a><span data-ttu-id="466ce-103">IXCLRDataMethodDefinition インターフェイス</span><span class="sxs-lookup"><span data-stu-id="466ce-103">IXCLRDataMethodDefinition Interface</span></span>

<span data-ttu-id="466ce-104">メソッド定義に関する情報を照会するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="466ce-104">Provides methods for querying information about a method definition.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="466ce-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="466ce-105">Methods</span></span>

<span data-ttu-id="466ce-106">次のメソッドは、インターフェイスで使用できるメソッドの一部です。</span><span class="sxs-lookup"><span data-stu-id="466ce-106">The following methods are some of the methods available in the interface.</span></span>

| <span data-ttu-id="466ce-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="466ce-107">Method</span></span>                                                                                                                          | <span data-ttu-id="466ce-108">説明</span><span class="sxs-lookup"><span data-stu-id="466ce-108">Description</span></span>                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="466ce-109">StartEnumInstances</span><span class="sxs-lookup"><span data-stu-id="466ce-109">StartEnumInstances</span></span>](ixclrdatamethoddefinition-startenuminstances-method.md) | <span data-ttu-id="466ce-110">指定されたのメソッドインスタンスの列挙体のハンドルを提供 `IXCLRDataAppDomain` します。</span><span class="sxs-lookup"><span data-stu-id="466ce-110">Provides a handle for the enumeration of method instances for a given `IXCLRDataAppDomain`.</span></span> |
| [<span data-ttu-id="466ce-111">EnumInstance</span><span class="sxs-lookup"><span data-stu-id="466ce-111">EnumInstance</span></span>](ixclrdatamethoddefinition-enuminstance-method.md)             | <span data-ttu-id="466ce-112">このメソッド定義のインスタンスを列挙します。</span><span class="sxs-lookup"><span data-stu-id="466ce-112">Enumerates the instances of this method definition.</span></span>                                         |
| [<span data-ttu-id="466ce-113">EndEnumInstances</span><span class="sxs-lookup"><span data-stu-id="466ce-113">EndEnumInstances</span></span>](ixclrdatamethoddefinition-endenuminstances-method.md)     | <span data-ttu-id="466ce-114">インスタンスの列挙中に使用される内部反復子によって使用されるリソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="466ce-114">Releases the resources used by internal iterators used during instance enumeration.</span></span>         |

## <a name="remarks"></a><span data-ttu-id="466ce-115">解説</span><span class="sxs-lookup"><span data-stu-id="466ce-115">Remarks</span></span>

<span data-ttu-id="466ce-116">このインターフェイスはランタイム内に存在し、ヘッダーまたはライブラリファイルを介して公開されることはありません。</span><span class="sxs-lookup"><span data-stu-id="466ce-116">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="466ce-117">ただし、これは、 `IUnknown` `AAF60008-FB2C-420b-8FB1-42D244A54A97` 通常の com 機構を通じて取得できる GUID を使用してから派生する com インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="466ce-117">However, it's a COM interface that derives from `IUnknown` with GUID `AAF60008-FB2C-420b-8FB1-42D244A54A97` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="466ce-118">要件</span><span class="sxs-lookup"><span data-stu-id="466ce-118">Requirements</span></span>

<span data-ttu-id="466ce-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="466ce-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="466ce-120">**ヘッダー:** 存在</span><span class="sxs-lookup"><span data-stu-id="466ce-120">**Header:** None</span></span>  
<span data-ttu-id="466ce-121">**ライブラリ:** 存在</span><span class="sxs-lookup"><span data-stu-id="466ce-121">**Library:** None</span></span>  
<span data-ttu-id="466ce-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="466ce-122">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="466ce-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="466ce-123">See also</span></span>

- [<span data-ttu-id="466ce-124">デバッグ</span><span class="sxs-lookup"><span data-stu-id="466ce-124">Debugging</span></span>](index.md)
- [<span data-ttu-id="466ce-125">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="466ce-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
