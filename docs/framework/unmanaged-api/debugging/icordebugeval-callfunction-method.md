---
description: '詳細については、次を参照してください: いいね:: CallFunction メソッド'
title: ICorDebugEval::CallFunction メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval.CallFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::CallFunction
helpviewer_keywords:
- ICorDebugEval::CallFunction method [.NET Framework debugging]
- CallFunction method [.NET Framework debugging]
ms.assetid: 7f470c5c-e1c0-4d8d-aad8-830f113ae751
topic_type:
- apiref
ms.openlocfilehash: c0978ab3bdffc83e3eb5e3a6553e7f374ab6d5da
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694189"
---
# <a name="icordebugevalcallfunction-method"></a><span data-ttu-id="39c01-103">ICorDebugEval::CallFunction メソッド</span><span class="sxs-lookup"><span data-stu-id="39c01-103">ICorDebugEval::CallFunction Method</span></span>

<span data-ttu-id="39c01-104">指定された関数の呼び出しを設定します。</span><span class="sxs-lookup"><span data-stu-id="39c01-104">Sets up a call to the specified function.</span></span>

<span data-ttu-id="39c01-105">このメソッドは .NET Framework バージョン2.0 では廃止されています。</span><span class="sxs-lookup"><span data-stu-id="39c01-105">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="39c01-106">代わりに [ICorDebugEval2:: CallParameterizedFunction](icordebugeval2-callparameterizedfunction-method.md) を使用してください。</span><span class="sxs-lookup"><span data-stu-id="39c01-106">Use [ICorDebugEval2::CallParameterizedFunction](icordebugeval2-callparameterizedfunction-method.md) instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="39c01-107">構文</span><span class="sxs-lookup"><span data-stu-id="39c01-107">Syntax</span></span>

```cpp
HRESULT CallFunction (
    [in] ICorDebugFunction  *pFunction,
    [in] ULONG32            nArgs,
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]
);
```

## <a name="parameters"></a><span data-ttu-id="39c01-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="39c01-108">Parameters</span></span>

`pFunction`\
<span data-ttu-id="39c01-109">から呼び出される関数を指定する、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="39c01-109">[in] Pointer to an ICorDebugFunction object that specifies the function to be called.</span></span>

`nArgs`\
<span data-ttu-id="39c01-110">から関数の引数の数。</span><span class="sxs-lookup"><span data-stu-id="39c01-110">[in] The number of arguments for the function.</span></span>

`ppArgs`\
<span data-ttu-id="39c01-111">からポインターの配列。各ポインターは、関数に渡される引数を指定する ICorDebugValue オブジェクトを指します。</span><span class="sxs-lookup"><span data-stu-id="39c01-111">[in] An array of pointers, each of which points to an ICorDebugValue object that specifies an argument to be passed to the function.</span></span>

## <a name="remarks"></a><span data-ttu-id="39c01-112">解説</span><span class="sxs-lookup"><span data-stu-id="39c01-112">Remarks</span></span>

<span data-ttu-id="39c01-113">関数が virtual の場合、 `CallFunction` は仮想ディスパッチを実行します。</span><span class="sxs-lookup"><span data-stu-id="39c01-113">If the function is virtual, `CallFunction` will perform virtual dispatch.</span></span> <span data-ttu-id="39c01-114">関数が別のアプリケーションドメインにある場合は、すべての引数がそのアプリケーションドメインにも存在する限り、遷移が発生します。</span><span class="sxs-lookup"><span data-stu-id="39c01-114">If the function is in a different application domain, a transition will occur as long as all arguments are also in that application domain.</span></span>

## <a name="requirements"></a><span data-ttu-id="39c01-115">要件</span><span class="sxs-lookup"><span data-stu-id="39c01-115">Requirements</span></span>

<span data-ttu-id="39c01-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39c01-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="39c01-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="39c01-117">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="39c01-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="39c01-118">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="39c01-119">**.NET Framework のバージョン:** 1.1、1.0</span><span class="sxs-lookup"><span data-stu-id="39c01-119">**.NET Framework Versions:** 1.1, 1.0</span></span>

## <a name="see-also"></a><span data-ttu-id="39c01-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="39c01-120">See also</span></span>

- [<span data-ttu-id="39c01-121">CallParameterizedFunction メソッド</span><span class="sxs-lookup"><span data-stu-id="39c01-121">CallParameterizedFunction Method</span></span>](icordebugeval2-callparameterizedfunction-method.md)
