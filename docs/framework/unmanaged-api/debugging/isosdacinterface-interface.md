---
description: 'の詳細情報: ISOSDacInterface インターフェイス'
title: ISOSDacInterface インターフェイス
ms.date: 02/01/2019
api.name:
- ISOSDacInterface Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface Interface
helpviewer.keywords:
- ISOSDacInterface Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: ddb99b7c6fca6870024f04933861d01e4b31ea9e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790400"
---
# <a name="isosdacinterface-interface"></a><span data-ttu-id="1d22e-103">ISOSDacInterface インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1d22e-103">ISOSDacInterface Interface</span></span>

<span data-ttu-id="1d22e-104">からデータにアクセスするためのヘルパーメソッドを提供 `SOS` します。</span><span class="sxs-lookup"><span data-stu-id="1d22e-104">Provides helper methods to access data from `SOS`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="1d22e-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="1d22e-105">Methods</span></span>

| <span data-ttu-id="1d22e-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="1d22e-106">Method</span></span>                                                                                                               | <span data-ttu-id="1d22e-107">説明</span><span class="sxs-lookup"><span data-stu-id="1d22e-107">Description</span></span>                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="1d22e-108">GetMethodDescData</span><span class="sxs-lookup"><span data-stu-id="1d22e-108">GetMethodDescData</span></span>](isosdacinterface-getmethoddescdata-method.md) | <span data-ttu-id="1d22e-109">指定された MethodDesc ポインターのデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="1d22e-109">Gets the data for the given MethodDesc pointer.</span></span> |
| [<span data-ttu-id="1d22e-110">GetMethodDescPtrFromIP</span><span class="sxs-lookup"><span data-stu-id="1d22e-110">GetMethodDescPtrFromIP</span></span>](isosdacinterface-getmethoddescptrfromip-method.md) | <span data-ttu-id="1d22e-111">指定されたネイティブ命令アドレスを格納しているメソッドに対応する MethodDesc のポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="1d22e-111">Retrieves the pointer of the MethodDesc corresponding the method containing the given native instruction address.</span></span> |
| [<span data-ttu-id="1d22e-112">GetModuleData</span><span class="sxs-lookup"><span data-stu-id="1d22e-112">GetModuleData</span></span>](isosdacinterface-getmoduledata-method.md)| <span data-ttu-id="1d22e-113">指定したアドレスに読み込まれたモジュールに対応するデータをフェッチします。</span><span class="sxs-lookup"><span data-stu-id="1d22e-113">Fetches the data corresponding to the module loaded at a given address.</span></span> |

## <a name="remarks"></a><span data-ttu-id="1d22e-114">解説</span><span class="sxs-lookup"><span data-stu-id="1d22e-114">Remarks</span></span>

<span data-ttu-id="1d22e-115">このインターフェイスはランタイム内に存在し、ヘッダーまたはライブラリファイルを介して公開されることはありません。</span><span class="sxs-lookup"><span data-stu-id="1d22e-115">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="1d22e-116">ただし、これは、 `IUnknown` `436f00f2-b42a-4b9f-870c-e73db66ae930` 通常の com 機構を通じて取得できる GUID を使用してから派生する com インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="1d22e-116">However, it's a COM interface that derives from `IUnknown` with GUID `436f00f2-b42a-4b9f-870c-e73db66ae930` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="1d22e-117">要件</span><span class="sxs-lookup"><span data-stu-id="1d22e-117">Requirements</span></span>

<span data-ttu-id="1d22e-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1d22e-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="1d22e-119">**ヘッダー:** 存在</span><span class="sxs-lookup"><span data-stu-id="1d22e-119">**Header:** None</span></span>  
<span data-ttu-id="1d22e-120">**ライブラリ:** 存在</span><span class="sxs-lookup"><span data-stu-id="1d22e-120">**Library:** None</span></span>  
<span data-ttu-id="1d22e-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1d22e-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="1d22e-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="1d22e-122">See also</span></span>

- [<span data-ttu-id="1d22e-123">デバッグ</span><span class="sxs-lookup"><span data-stu-id="1d22e-123">Debugging</span></span>](index.md)
- [<span data-ttu-id="1d22e-124">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="1d22e-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
