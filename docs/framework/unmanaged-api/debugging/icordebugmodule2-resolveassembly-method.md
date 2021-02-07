---
description: '詳細情報: ICorDebugModule2:: ResolveAssembly メソッド'
title: ICorDebugModule2::ResolveAssembly メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.ResolveAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::ResolveAssembly
helpviewer_keywords:
- ICorDebugModule2::ResolveAssembly method [.NET Framework debugging]
- ResolveAssembly method [.NET Framework debugging]
ms.assetid: ddf9085c-7161-44bd-9609-cd2732b9009f
topic_type:
- apiref
ms.openlocfilehash: fba53b8ff76e4d3deb1876d2a20a7a2edc20bd06
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722595"
---
# <a name="icordebugmodule2resolveassembly-method"></a><span data-ttu-id="2613c-103">ICorDebugModule2::ResolveAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="2613c-103">ICorDebugModule2::ResolveAssembly Method</span></span>

<span data-ttu-id="2613c-104">指定したメタデータトークンによって参照されるアセンブリを解決します。</span><span class="sxs-lookup"><span data-stu-id="2613c-104">Resolves the assembly referenced by the specified metadata token.</span></span>

## <a name="syntax"></a><span data-ttu-id="2613c-105">構文</span><span class="sxs-lookup"><span data-stu-id="2613c-105">Syntax</span></span>

```cpp
HRESULT ResolveAssembly (
    [in]  mdToken             tkAssemblyRef,
    [out] ICorDebugAssembly   **ppAssembly
);
```

## <a name="parameters"></a><span data-ttu-id="2613c-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2613c-106">Parameters</span></span>

`tkAssemblyRef`\
<span data-ttu-id="2613c-107">から `mdToken` アセンブリを参照する値。</span><span class="sxs-lookup"><span data-stu-id="2613c-107">[in] An `mdToken` value that references the assembly.</span></span>

`ppAssembly`\
<span data-ttu-id="2613c-108">入出力アセンブリを表す、オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="2613c-108">[out] A pointer to the address of an ICorDebugAssembly object that represents the assembly.</span></span>

## <a name="remarks"></a><span data-ttu-id="2613c-109">解説</span><span class="sxs-lookup"><span data-stu-id="2613c-109">Remarks</span></span>

<span data-ttu-id="2613c-110">が呼び出されたときにアセンブリがまだ読み込まれていない場合は `ResolveAssembly` 、CORDBG_E_CANNOT_RESOLVE_ASSEMBLY の HRESULT 値が返されます。</span><span class="sxs-lookup"><span data-stu-id="2613c-110">If the assembly is not already loaded when `ResolveAssembly` is called, an HRESULT value of CORDBG_E_CANNOT_RESOLVE_ASSEMBLY is returned.</span></span>

## <a name="requirements"></a><span data-ttu-id="2613c-111">要件</span><span class="sxs-lookup"><span data-stu-id="2613c-111">Requirements</span></span>

<span data-ttu-id="2613c-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2613c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="2613c-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2613c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="2613c-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2613c-114">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="2613c-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2613c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
