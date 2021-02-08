---
description: '詳細については、次を参照してください: DacpMethodDescData 構造体'
title: DacpMethodDescData 構造体
ms.date: 02/01/2019
api.name:
- DacpMethodDescData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpMethodDescData Structure
helpviewer.keywords:
- DacpMethodDescData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: fe5b09874b3f8e123cb2501fcb00e3351aa44757
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801463"
---
# <a name="dacpmethoddescdata-structure"></a><span data-ttu-id="71bc7-103">DacpMethodDescData 構造体</span><span class="sxs-lookup"><span data-stu-id="71bc7-103">DacpMethodDescData Structure</span></span>

<span data-ttu-id="71bc7-104">メソッドのランタイム情報のトランスポートバッファーを定義します。</span><span class="sxs-lookup"><span data-stu-id="71bc7-104">Defines a transport buffer for a method's runtime information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="71bc7-105">構文</span><span class="sxs-lookup"><span data-stu-id="71bc7-105">Syntax</span></span>

```cpp
struct DacpMethodDescData
{
    int             bHasNativeCode;
    int             bIsDynamic;
    unsigned short  wSlotNumber;
    CLRDATA_ADDRESS NativeCodeAddr;
    CLRDATA_ADDRESS data;
    CLRDATA_ADDRESS MethodDescPtr;
    CLRDATA_ADDRESS nativeCodeInfo;
    CLRDATA_ADDRESS moduleInfo;
    mdToken         MDToken;
    CLRDATA_ADDRESS payloadGC;
    CLRDATA_ADDRESS payloadGC2;
    CLRDATA_ADDRESS managedDynamicMethodObject;
    CLRDATA_ADDRESS requestedIP;
    DacpReJitData   rejitDataCurrent;
    DacpReJitData   rejitDataRequested;
    unsigned long   cJittedRejitVersions;
};
```

## <a name="members"></a><span data-ttu-id="71bc7-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="71bc7-106">Members</span></span>

| <span data-ttu-id="71bc7-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="71bc7-107">Member</span></span>                       | <span data-ttu-id="71bc7-108">説明</span><span class="sxs-lookup"><span data-stu-id="71bc7-108">Description</span></span>                                                                                     |
| ---------------------------- | ----------------------------------------------------------------------------------------------- |
| `bHasNativeCode`             | <span data-ttu-id="71bc7-109">メソッドの特定のインスタンス化に対してランタイムにネイティブコードがあるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="71bc7-109">Indicates if the runtime has native code available for the given instantiation of the method.</span></span> |
| `bIsDynamic`                 | <span data-ttu-id="71bc7-110">軽量コード生成によってメソッドが動的に生成されるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="71bc7-110">Indicates if the method is generated dynamically through lightweight code generation.</span></span>           |
| `wSlotNumber`                | <span data-ttu-id="71bc7-111">メソッドテーブル内のメソッドのスロット番号。</span><span class="sxs-lookup"><span data-stu-id="71bc7-111">The method's slot number in the method table.</span></span>                                                   |
| `NativeCodeAddr`             | <span data-ttu-id="71bc7-112">メソッドの初期ネイティブアドレス。</span><span class="sxs-lookup"><span data-stu-id="71bc7-112">The method's initial native address.</span></span>                                                            |
| `data`                       | <span data-ttu-id="71bc7-113">ランタイムによって内部的に使用されるバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="71bc7-113">Pointer to a buffer used internally by the runtime.</span></span>                                             |
| `MethodDescPtr`              | <span data-ttu-id="71bc7-114">ランタイム内のへのポインター `MethodDesc` 。</span><span class="sxs-lookup"><span data-stu-id="71bc7-114">Pointer to the `MethodDesc` in the runtime.</span></span>                                                     |
| `nativeCodeInfo`             | <span data-ttu-id="71bc7-115">メソッドを追跡するためにランタイムによって内部的に使用されるバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="71bc7-115">Pointer to a buffer used internally by the runtime to track methods.</span></span>                            |
| `moduleInfo`                 | <span data-ttu-id="71bc7-116">モジュール情報のランタイムによって内部的に使用されるバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="71bc7-116">Pointer to a buffer used internally by the runtime for module information.</span></span>                      |
| `MDToken`                    | <span data-ttu-id="71bc7-117">指定したメソッドに関連付けられているトークン。</span><span class="sxs-lookup"><span data-stu-id="71bc7-117">Token associated with the given method.</span></span>                                                         |
| `payloadGC`                  | <span data-ttu-id="71bc7-118">ランタイムによって内部的に使用されるガベージコレクションバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="71bc7-118">Pointer to a garbage collection buffer used internally by the runtime.</span></span>                          |
| `payloadGC2`                 | <span data-ttu-id="71bc7-119">ランタイムによって内部的に使用されるガベージコレクションバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="71bc7-119">Pointer to a garbage collection buffer used internally by the runtime.</span></span>                          |
| `managedDynamicMethodObject` | <span data-ttu-id="71bc7-120">メソッドが動的である場合、ランタイムは情報追跡のためにこのバッファーを内部的に使用します。</span><span class="sxs-lookup"><span data-stu-id="71bc7-120">If the method is dynamic, the runtime uses this buffer internally for information tracking.</span></span>     |
| `requestedIP`                | <span data-ttu-id="71bc7-121">ネイティブコードアドレスが指定された場合に、要求ごとに構造体を設定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="71bc7-121">Used to populate the structure per request when given a native code address.</span></span>                    |
| `rejitDataCurrent`           | <span data-ttu-id="71bc7-122">メソッドのインストルメント化された最新バージョンに関する情報。</span><span class="sxs-lookup"><span data-stu-id="71bc7-122">Information about the latest instrumented version of the method.</span></span>                                   |
| `rejitDataRequested`         | <span data-ttu-id="71bc7-123">要求されたネイティブアドレスの rejit 情報。</span><span class="sxs-lookup"><span data-stu-id="71bc7-123">Rejit information for the requested native address.</span></span>                                             |
| `cJittedRejitVersions`       | <span data-ttu-id="71bc7-124">メソッドがインストルメンテーションによって rejitted された回数。</span><span class="sxs-lookup"><span data-stu-id="71bc7-124">Number of times the method has been rejitted through instrumentation.</span></span>                           |

## <a name="remarks"></a><span data-ttu-id="71bc7-125">解説</span><span class="sxs-lookup"><span data-stu-id="71bc7-125">Remarks</span></span>

<span data-ttu-id="71bc7-126">この構造体はランタイム内に存在し、ヘッダーまたはライブラリファイルを介して公開されることはありません。</span><span class="sxs-lookup"><span data-stu-id="71bc7-126">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="71bc7-127">これを使用するには、前に示したように構造体を定義します。</span><span class="sxs-lookup"><span data-stu-id="71bc7-127">To use it, define the structure as specified above.</span></span>

## <a name="requirements"></a><span data-ttu-id="71bc7-128">要件</span><span class="sxs-lookup"><span data-stu-id="71bc7-128">Requirements</span></span>

<span data-ttu-id="71bc7-129">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="71bc7-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="71bc7-130">**ヘッダー:** 存在</span><span class="sxs-lookup"><span data-stu-id="71bc7-130">**Header:** None</span></span>  
<span data-ttu-id="71bc7-131">**ライブラリ:** 存在</span><span class="sxs-lookup"><span data-stu-id="71bc7-131">**Library:** None</span></span>  
<span data-ttu-id="71bc7-132">**.NET Framework のバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="71bc7-132">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="71bc7-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="71bc7-133">See also</span></span>

- [<span data-ttu-id="71bc7-134">デバッグ</span><span class="sxs-lookup"><span data-stu-id="71bc7-134">Debugging</span></span>](index.md)
- [<span data-ttu-id="71bc7-135">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="71bc7-135">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="71bc7-136">共有のデータ型</span><span class="sxs-lookup"><span data-stu-id="71bc7-136">Common Data Types</span></span>](../common-data-types-unmanaged-api-reference.md)
