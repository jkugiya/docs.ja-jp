---
description: ': ISOSDacInterface:: GetMethodDescPtrFromIP メソッドの詳細について説明します。'
title: 'ISOSDacInterface:: GetMethodDescPtrFromIP メソッド'
ms.date: 02/01/2019
api.name:
- ISOSDacInterface::GetMethodDescPtrFromIP Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetMethodDescPtrFromIP Method
helpviewer.keywords:
- ISOSDacInterface::GetMethodDescPtrFromIP Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 8d7c7071b7b3fc520faea71c8d7792317745cfde
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790413"
---
# <a name="isosdacinterfacegetmethoddescptrfromip-method"></a><span data-ttu-id="2a261-103">ISOSDacInterface:: GetMethodDescPtrFromIP メソッド</span><span class="sxs-lookup"><span data-stu-id="2a261-103">ISOSDacInterface::GetMethodDescPtrFromIP Method</span></span>

<span data-ttu-id="2a261-104">指定されたネイティブ命令アドレスを格納しているメソッドに対応する MethodDesc のポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="2a261-104">Retrieves the pointer of the MethodDesc corresponding the method containing the given native instruction address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="2a261-105">構文</span><span class="sxs-lookup"><span data-stu-id="2a261-105">Syntax</span></span>

```cpp
HRESULT GetMethodDescPtrFromIP(
    CLRDATA_ADDRESS ip,
    CLRDATA_ADDRESS * ppMD
);
```

## <a name="parameters"></a><span data-ttu-id="2a261-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2a261-106">Parameters</span></span>

`ip`\
<span data-ttu-id="2a261-107">から実行時のメソッド内のアドレス。</span><span class="sxs-lookup"><span data-stu-id="2a261-107">[in] An address within the method at runtime.</span></span>

`ppMD`\
<span data-ttu-id="2a261-108">入出力 `MethodDesc` 特定のメソッドののアドレス。</span><span class="sxs-lookup"><span data-stu-id="2a261-108">[out] The address of the `MethodDesc` for the particular method.</span></span>

## <a name="remarks"></a><span data-ttu-id="2a261-109">解説</span><span class="sxs-lookup"><span data-stu-id="2a261-109">Remarks</span></span>

<span data-ttu-id="2a261-110">指定されたメソッドは[ `ISOSDacInterface` インターフェイス](isosdacinterface-interface.md)の一部であり、仮想メソッドテーブルの22スロットに対応します。</span><span class="sxs-lookup"><span data-stu-id="2a261-110">The provided method is part of the [`ISOSDacInterface` interface](isosdacinterface-interface.md) and corresponds to the 22nd slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="2a261-111">要件</span><span class="sxs-lookup"><span data-stu-id="2a261-111">Requirements</span></span>

<span data-ttu-id="2a261-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2a261-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="2a261-113">**ヘッダー:** 存在</span><span class="sxs-lookup"><span data-stu-id="2a261-113">**Header:** None</span></span>  
<span data-ttu-id="2a261-114">**ライブラリ:** 存在</span><span class="sxs-lookup"><span data-stu-id="2a261-114">**Library:** None</span></span>  
<span data-ttu-id="2a261-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2a261-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="2a261-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="2a261-116">See also</span></span>

- [<span data-ttu-id="2a261-117">デバッグ</span><span class="sxs-lookup"><span data-stu-id="2a261-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="2a261-118">ISOSDacInterface インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2a261-118">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)
