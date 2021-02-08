---
description: 詳細については、「ICorDebugILFrame4 インターフェイス」を参照してください。
title: ICorDebugILFrame4 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame4
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1e739183-3e05-49e5-846f-4075256e41de
topic_type:
- apiref
ms.openlocfilehash: f2d29229f039509ed7799399f0d4d701e8cafba7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791206"
---
# <a name="icordebugilframe4-interface"></a><span data-ttu-id="9573e-103">ICorDebugILFrame4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9573e-103">ICorDebugILFrame4 Interface</span></span>

<span data-ttu-id="9573e-104">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="9573e-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="9573e-105">ローカル変数にアクセスできるようにするメソッドおよび中間言語 (IL) コードのスタック フレームのコードを提供します。</span><span class="sxs-lookup"><span data-stu-id="9573e-105">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="9573e-106">パラメーターは、プロファイラーの ReJIT インストルメンテーションに追加される変数およびコードへデバッガーがアクセスできるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="9573e-106">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9573e-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="9573e-107">Methods</span></span>  
  
|<span data-ttu-id="9573e-108">メソッド</span><span class="sxs-lookup"><span data-stu-id="9573e-108">Method</span></span>|<span data-ttu-id="9573e-109">説明</span><span class="sxs-lookup"><span data-stu-id="9573e-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9573e-110">EnumerateLocalVariablesEx メソッド</span><span class="sxs-lookup"><span data-stu-id="9573e-110">EnumerateLocalVariablesEx Method</span></span>](icordebugilframe4-enumeratelocalvariablesex-method.md)|<span data-ttu-id="9573e-111">現在のフレームで使用可能なローカル変数の一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="9573e-111">Returns a list of the local variables available in the current frame.</span></span>|  
|[<span data-ttu-id="9573e-112">GetCodeEx メソッド</span><span class="sxs-lookup"><span data-stu-id="9573e-112">GetCodeEx Method</span></span>](icordebugilframe4-getcodeex-method.md)|<span data-ttu-id="9573e-113">このスタック フレームが実行するコードを返します。</span><span class="sxs-lookup"><span data-stu-id="9573e-113">Returns the code that this stack frame is running.</span></span>|  
|[<span data-ttu-id="9573e-114">GetLocalVariableEx メソッド</span><span class="sxs-lookup"><span data-stu-id="9573e-114">GetLocalVariableEx Method</span></span>](icordebugilframe4-getlocalvariableex-method.md)|<span data-ttu-id="9573e-115">IL フレーム内のローカル変数の値を返します。</span><span class="sxs-lookup"><span data-stu-id="9573e-115">Returns the value of a local variable in the IL frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9573e-116">解説</span><span class="sxs-lookup"><span data-stu-id="9573e-116">Remarks</span></span>  

 <span data-ttu-id="9573e-117">これらのメソッドは、 [EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md)、 [GetCode](icordebugframe-getcode-method.md)、および [getlocalvariable](icordebugilframe-getlocalvariable-method.md) の各メソッドによって提供される機能に加えて機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="9573e-117">These methods offer functionality in addition to that provided by the [EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md), [GetCode](icordebugframe-getcode-method.md), and [GetLocalVariable](icordebugilframe-getlocalvariable-method.md) methods.</span></span> <span data-ttu-id="9573e-118">各メソッドには、追加のローカル変数またはプロファイラーの ReJIT 要求によって定義されているコードが参照可能かどうかを指定する `flags` パラメーターが含まれます。</span><span class="sxs-lookup"><span data-stu-id="9573e-118">Each method includes a `flags` parameter that specifies whether additional local variables or code defined by a profiler's ReJIT request are visible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9573e-119">要件</span><span class="sxs-lookup"><span data-stu-id="9573e-119">Requirements</span></span>  

 <span data-ttu-id="9573e-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9573e-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9573e-121">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9573e-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9573e-122">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9573e-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9573e-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9573e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9573e-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="9573e-124">See also</span></span>

- [<span data-ttu-id="9573e-125">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="9573e-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="9573e-126">デバッグ</span><span class="sxs-lookup"><span data-stu-id="9573e-126">Debugging</span></span>](index.md)
