---
description: '詳細については、次のページを参照してください: GetArgumentIndex メソッド'
title: 'いい変数 Home:: GetArgumentIndex メソッド'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetArgumentIndex
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetArgumentIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetArgumentIndex method [.NET Framework debugging]
- GetArgumentIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: e86fcc72-388d-4009-ab21-8f9c3323e9a3
topic_type:
- apiref
ms.openlocfilehash: 827ef55d3e3509cbfbfc8213ef5b53fbe2e2220e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690042"
---
# <a name="icordebugvariablehomegetargumentindex-method"></a><span data-ttu-id="215aa-103">いい変数 Home:: GetArgumentIndex メソッド</span><span class="sxs-lookup"><span data-stu-id="215aa-103">ICorDebugVariableHome::GetArgumentIndex Method</span></span>

<span data-ttu-id="215aa-104">関数の引数のインデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="215aa-104">Gets the index of a function argument.</span></span>

## <a name="syntax"></a><span data-ttu-id="215aa-105">構文</span><span class="sxs-lookup"><span data-stu-id="215aa-105">Syntax</span></span>

```cpp
HRESULT GetArgumentIndex(
    [out] ULONG32* pArgumentIndex
);
```

## <a name="parameters"></a><span data-ttu-id="215aa-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="215aa-106">Parameters</span></span>

`pArgumentIndex`\
<span data-ttu-id="215aa-107">入出力引数インデックスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="215aa-107">[out] A pointer to the argument index.</span></span>

## <a name="return-value"></a><span data-ttu-id="215aa-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="215aa-108">Return Value</span></span>

<span data-ttu-id="215aa-109">メソッドは、次の値を返します。</span><span class="sxs-lookup"><span data-stu-id="215aa-109">The method returns the following values.</span></span>

|<span data-ttu-id="215aa-110">値</span><span class="sxs-lookup"><span data-stu-id="215aa-110">Value</span></span>|<span data-ttu-id="215aa-111">説明</span><span class="sxs-lookup"><span data-stu-id="215aa-111">Description</span></span>|
|-----------|-----------------|
|`S_OK`|<span data-ttu-id="215aa-112">メソッド呼び出しによって有効な引数インデックスが返されました。</span><span class="sxs-lookup"><span data-stu-id="215aa-112">The method call returned a valid argument index.</span></span>|
|`E_FAIL`|<span data-ttu-id="215aa-113">現在の [ページ](icordebugvariablehome-interface.md) は、ローカル変数を表します。</span><span class="sxs-lookup"><span data-stu-id="215aa-113">The current [ICorDebugVariableHome](icordebugvariablehome-interface.md) instance represents a local variable.</span></span>|

## <a name="remarks"></a><span data-ttu-id="215aa-114">解説</span><span class="sxs-lookup"><span data-stu-id="215aa-114">Remarks</span></span>

<span data-ttu-id="215aa-115">引数インデックスは、この引数のメタデータを取得するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="215aa-115">The argument index can be used to retrieve metadata for this argument.</span></span>

## <a name="requirements"></a><span data-ttu-id="215aa-116">要件</span><span class="sxs-lookup"><span data-stu-id="215aa-116">Requirements</span></span>

<span data-ttu-id="215aa-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="215aa-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="215aa-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="215aa-118">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="215aa-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="215aa-119">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="215aa-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="215aa-120">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="215aa-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="215aa-121">See also</span></span>

- [<span data-ttu-id="215aa-122">ICorDebugVariableHome インターフェイス</span><span class="sxs-lookup"><span data-stu-id="215aa-122">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
