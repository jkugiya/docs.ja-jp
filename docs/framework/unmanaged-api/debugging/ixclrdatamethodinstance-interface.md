---
description: 詳細については、「IXCLRDataMethodInstance インターフェイス」を参照してください。
title: IXCLRDataMethodInstance インターフェイス
ms.date: 02/01/2019
api.name:
- IXCLRDataMethodInstance Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodInstance Interface
helpviewer.keywords:
- IXCLRDataMethodInstance Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 4e9ad57988420ff14b297c693c31c0dc5b3b181c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800787"
---
# <a name="ixclrdatamethodinstance-interface"></a><span data-ttu-id="addd0-103">IXCLRDataMethodInstance インターフェイス</span><span class="sxs-lookup"><span data-stu-id="addd0-103">IXCLRDataMethodInstance Interface</span></span>

<span data-ttu-id="addd0-104">メソッドインスタンスに関する情報を照会するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="addd0-104">Provides methods for querying information about a method instance.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="addd0-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="addd0-105">Methods</span></span>

| <span data-ttu-id="addd0-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="addd0-106">Method</span></span>                                                                                                                  | <span data-ttu-id="addd0-107">説明</span><span class="sxs-lookup"><span data-stu-id="addd0-107">Description</span></span>                                 |
| ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------- |
| [<span data-ttu-id="addd0-108">GetILAddressMap</span><span class="sxs-lookup"><span data-stu-id="addd0-108">GetILAddressMap</span></span>](ixclrdatamethodinstance-getiladdressmap-method.md) | <span data-ttu-id="addd0-109">マッピング情報をアドレス付けする IL を取得します。</span><span class="sxs-lookup"><span data-stu-id="addd0-109">Gets the IL to address mapping information.</span></span> |
| [<span data-ttu-id="addd0-110">GetRepresentativeEntryAddress</span><span class="sxs-lookup"><span data-stu-id="addd0-110">GetRepresentativeEntryAddress</span></span>](ixclrdatamethodinstance-getrepresentativeentryaddress-method.md) | <span data-ttu-id="addd0-111">メソッドに対して使用可能なすべてのエントリポイントのネイティブコンパイルを行うための最も代表的なエントリポイントアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="addd0-111">Gets the most representative entry point address for the native compilation of all the possible entry points for a method.</span></span> |

## <a name="remarks"></a><span data-ttu-id="addd0-112">解説</span><span class="sxs-lookup"><span data-stu-id="addd0-112">Remarks</span></span>

<span data-ttu-id="addd0-113">このインターフェイスはランタイム内に存在し、ヘッダーまたはライブラリファイルを介して公開されることはありません。</span><span class="sxs-lookup"><span data-stu-id="addd0-113">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="addd0-114">ただし、これは、 `IUnknown` `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` 通常の com 機構を通じて取得できる GUID を使用してから派生する com インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="addd0-114">However, it's a COM interface that derives from `IUnknown` with GUID `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="addd0-115">要件</span><span class="sxs-lookup"><span data-stu-id="addd0-115">Requirements</span></span>

<span data-ttu-id="addd0-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="addd0-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="addd0-117">**ヘッダー:** 存在</span><span class="sxs-lookup"><span data-stu-id="addd0-117">**Header:** None</span></span>  
<span data-ttu-id="addd0-118">**ライブラリ:** 存在</span><span class="sxs-lookup"><span data-stu-id="addd0-118">**Library:** None</span></span>  
<span data-ttu-id="addd0-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="addd0-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="addd0-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="addd0-120">See also</span></span>

- [<span data-ttu-id="addd0-121">デバッグ</span><span class="sxs-lookup"><span data-stu-id="addd0-121">Debugging</span></span>](index.md)
- [<span data-ttu-id="addd0-122">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="addd0-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
