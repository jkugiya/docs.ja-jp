---
description: '詳細情報: IXCLRDataModule:: Request メソッド'
title: 'IXCLRDataModule:: Request メソッド'
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::Request Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::Request Method
helpviewer.keywords:
- IXCLRDataModule::Request Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 96f4153c58a228cfb22a5cd25a53b6e60fc4dfd1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800735"
---
# <a name="ixclrdatamodulerequest-method"></a><span data-ttu-id="78ff5-103">IXCLRDataModule:: Request メソッド</span><span class="sxs-lookup"><span data-stu-id="78ff5-103">IXCLRDataModule::Request Method</span></span>

<span data-ttu-id="78ff5-104">モジュールのデータで指定されたバッファーへの読み込みを要求します。</span><span class="sxs-lookup"><span data-stu-id="78ff5-104">Requests to populate the buffer given with the module's data.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="78ff5-105">構文</span><span class="sxs-lookup"><span data-stu-id="78ff5-105">Syntax</span></span>

```cpp
HRESULT Request([in] ULONG32 reqCode,
    [in] ULONG32 inBufferSize,
    [in, size_is(inBufferSize)] BYTE* inBuffer,
    [in] ULONG32 outBufferSize,
    [out, size_is(outBufferSize)] BYTE* outBuffer);
```

## <a name="parameters"></a><span data-ttu-id="78ff5-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="78ff5-106">Parameters</span></span>

`reqCode`\
<span data-ttu-id="78ff5-107">から送信される要求の種類。</span><span class="sxs-lookup"><span data-stu-id="78ff5-107">[in] Request type to be sent.</span></span>

`inBufferSize`\
<span data-ttu-id="78ff5-108">[in] 渡される入力バッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="78ff5-108">[in] size of the input buffer to be passed in.</span></span>

`inBuffer`\
<span data-ttu-id="78ff5-109">[in、size_is (inBufferSize)]要求で送信される生データのバッファーポインター。</span><span class="sxs-lookup"><span data-stu-id="78ff5-109">[in, size_is(inBufferSize)] Buffer pointer for the raw data to be sent in the request.</span></span>

`outBufferSize`\
<span data-ttu-id="78ff5-110">から出力バッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="78ff5-110">[in] Size of the output buffer.</span></span>

`outBuffer`\
<span data-ttu-id="78ff5-111">[out、size_is (outBufferSize)]要求応答を格納するために使用するバッファーポインター。</span><span class="sxs-lookup"><span data-stu-id="78ff5-111">[out, size_is(outBufferSize)] Buffer pointer to used to store the request response.</span></span>

## <a name="remarks"></a><span data-ttu-id="78ff5-112">解説</span><span class="sxs-lookup"><span data-stu-id="78ff5-112">Remarks</span></span>

<span data-ttu-id="78ff5-113">指定されたメソッドはインターフェイスの一部で `IXCLRDataModule` あり、仮想メソッドテーブルの37th スロットに対応します。</span><span class="sxs-lookup"><span data-stu-id="78ff5-113">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 37th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="78ff5-114">要件</span><span class="sxs-lookup"><span data-stu-id="78ff5-114">Requirements</span></span>

<span data-ttu-id="78ff5-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78ff5-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>
<span data-ttu-id="78ff5-116">**ヘッダー:** None **Library:** None **.NET Framework バージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="78ff5-116">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="78ff5-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="78ff5-117">See also</span></span>

- [<span data-ttu-id="78ff5-118">デバッグ</span><span class="sxs-lookup"><span data-stu-id="78ff5-118">Debugging</span></span>](index.md)
- [<span data-ttu-id="78ff5-119">IXCLRDataModule インターフェイス</span><span class="sxs-lookup"><span data-stu-id="78ff5-119">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
