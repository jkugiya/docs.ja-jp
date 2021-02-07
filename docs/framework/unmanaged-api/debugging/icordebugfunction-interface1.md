---
description: '詳細については、次を参照してください: の関数インターフェイス'
title: ICorDebugFunction インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction
helpviewer_keywords:
- ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: 783faea9-8083-41c1-b04a-51a81ac4c8f3
topic_type:
- apiref
ms.openlocfilehash: 835625341889e89e15ceb66ca71531cf7b8311c4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692382"
---
# <a name="icordebugfunction-interface"></a><span data-ttu-id="8ac64-103">ICorDebugFunction インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8ac64-103">ICorDebugFunction Interface</span></span>

<span data-ttu-id="8ac64-104">マネージド関数またはマネージド メソッドを表します。</span><span class="sxs-lookup"><span data-stu-id="8ac64-104">Represents a managed function or method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8ac64-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="8ac64-105">Methods</span></span>  
  
|<span data-ttu-id="8ac64-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="8ac64-106">Method</span></span>|<span data-ttu-id="8ac64-107">説明</span><span class="sxs-lookup"><span data-stu-id="8ac64-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8ac64-108">CreateBreakpoint メソッド</span><span class="sxs-lookup"><span data-stu-id="8ac64-108">CreateBreakpoint Method</span></span>](icordebugfunction-createbreakpoint-method.md)|<span data-ttu-id="8ac64-109">この関数の先頭にブレークポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="8ac64-109">Creates a breakpoint at the beginning of this function.</span></span>|  
|[<span data-ttu-id="8ac64-110">GetClass メソッド</span><span class="sxs-lookup"><span data-stu-id="8ac64-110">GetClass Method</span></span>](icordebugfunction-getclass-method.md)|<span data-ttu-id="8ac64-111">この関数がメンバーとなっているクラスを表す、のオブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="8ac64-111">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>|  
|[<span data-ttu-id="8ac64-112">GetCurrentVersionNumber メソッド</span><span class="sxs-lookup"><span data-stu-id="8ac64-112">GetCurrentVersionNumber Method</span></span>](icordebugfunction-getcurrentversionnumber-method.md)|<span data-ttu-id="8ac64-113">この関数に対して行われた最新の編集のバージョン番号を取得します。</span><span class="sxs-lookup"><span data-stu-id="8ac64-113">Gets the version number of the latest edit made to this function.</span></span>|  
|[<span data-ttu-id="8ac64-114">GetILCode メソッド</span><span class="sxs-lookup"><span data-stu-id="8ac64-114">GetILCode Method</span></span>](icordebugfunction-getilcode-method.md)|<span data-ttu-id="8ac64-115">この関数の MSIL (Microsoft 中間言語) コードを取得します。</span><span class="sxs-lookup"><span data-stu-id="8ac64-115">Gets the Microsoft intermediate language (MSIL) code for this function.</span></span>|  
|[<span data-ttu-id="8ac64-116">GetLocalVarSigToken メソッド</span><span class="sxs-lookup"><span data-stu-id="8ac64-116">GetLocalVarSigToken Method</span></span>](icordebugfunction-getlocalvarsigtoken-method.md)|<span data-ttu-id="8ac64-117">このインスタンスによって表される関数のローカル変数シグネチャのメタデータトークンを取得し `ICorDebugFunction` ます。</span><span class="sxs-lookup"><span data-stu-id="8ac64-117">Gets the metadata token for the local variable signature of the function that is represented by this `ICorDebugFunction` instance.</span></span>|  
|[<span data-ttu-id="8ac64-118">GetModule メソッド</span><span class="sxs-lookup"><span data-stu-id="8ac64-118">GetModule Method</span></span>](icordebugfunction-getmodule-method.md)|<span data-ttu-id="8ac64-119">この関数が定義されているモジュールを取得します。</span><span class="sxs-lookup"><span data-stu-id="8ac64-119">Gets the module in which this function is defined.</span></span>|  
|[<span data-ttu-id="8ac64-120">GetNativeCode メソッド</span><span class="sxs-lookup"><span data-stu-id="8ac64-120">GetNativeCode Method</span></span>](icordebugfunction-getnativecode-method.md)|<span data-ttu-id="8ac64-121">この関数のネイティブコードを取得します。</span><span class="sxs-lookup"><span data-stu-id="8ac64-121">Gets the native code for this function.</span></span>|  
|[<span data-ttu-id="8ac64-122">GetToken メソッド</span><span class="sxs-lookup"><span data-stu-id="8ac64-122">GetToken Method</span></span>](icordebugfunction-gettoken-method.md)|<span data-ttu-id="8ac64-123">この関数のメタデータトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="8ac64-123">Gets the metadata token for this function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ac64-124">解説</span><span class="sxs-lookup"><span data-stu-id="8ac64-124">Remarks</span></span>  

 <span data-ttu-id="8ac64-125">インターフェイスは、 `ICorDebugFunction` ジェネリック型パラメーターを持つ関数を表していません。</span><span class="sxs-lookup"><span data-stu-id="8ac64-125">The `ICorDebugFunction` interface does not represent a function with generic type parameters.</span></span> <span data-ttu-id="8ac64-126">たとえば、インスタンスはを `ICorDebugFunction` 表しますが、では `Func<T>` ありません `Func<string>` 。</span><span class="sxs-lookup"><span data-stu-id="8ac64-126">For example, an `ICorDebugFunction` instance would represent `Func<T>` but not `Func<string>`.</span></span> <span data-ttu-id="8ac64-127">[ICorDebugILFrame2:: EnumerateTypeParameters](icordebugilframe2-enumeratetypeparameters-method.md)を呼び出して、ジェネリック型パラメーターを取得します。</span><span class="sxs-lookup"><span data-stu-id="8ac64-127">Call [ICorDebugILFrame2::EnumerateTypeParameters](icordebugilframe2-enumeratetypeparameters-method.md) to get the generic type parameters.</span></span>  
  
 <span data-ttu-id="8ac64-128">メソッドのメタデータトークン、 `mdMethodDef` 、およびメソッドのオブジェクト間のリレーションシップ `ICorDebugFunction` は、関数でエディットコンティニュが許可されているかどうかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="8ac64-128">The relationship between a method's metadata token, `mdMethodDef`, and a method's `ICorDebugFunction` object is dependent upon whether Edit and Continue is allowed on the function:</span></span>  
  
- <span data-ttu-id="8ac64-129">関数でエディットコンティニュを使用できない場合は、オブジェクトとトークンの間に一対一のリレーションシップが存在し `ICorDebugFunction` `mdMethodDef` ます。</span><span class="sxs-lookup"><span data-stu-id="8ac64-129">If Edit and Continue is not allowed on the function, a one-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="8ac64-130">つまり、関数は、1つの `ICorDebugFunction` オブジェクトと1つのトークンを持ち `mdMethodDef` ます。</span><span class="sxs-lookup"><span data-stu-id="8ac64-130">That is, the function has one `ICorDebugFunction` object and one `mdMethodDef` token.</span></span>  
  
- <span data-ttu-id="8ac64-131">関数でエディットコンティニュが許可されている場合は、オブジェクトとトークンの間に多対一のリレーションシップが存在し `ICorDebugFunction` `mdMethodDef` ます。</span><span class="sxs-lookup"><span data-stu-id="8ac64-131">If Edit and Continue is allowed on the function, a many-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="8ac64-132">つまり、関数は、 `ICorDebugFunction` 関数の各バージョンに1つずつ、1つのトークンのみを含むのインスタンスを多数持つことができ `mdMethodDef` ます。</span><span class="sxs-lookup"><span data-stu-id="8ac64-132">That is, the function may have many instances of `ICorDebugFunction`, one for each version of the function, but only one `mdMethodDef` token.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8ac64-133">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="8ac64-133">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ac64-134">要件</span><span class="sxs-lookup"><span data-stu-id="8ac64-134">Requirements</span></span>  

 <span data-ttu-id="8ac64-135">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ac64-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ac64-136">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8ac64-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8ac64-137">**ライブラリ:**  CorGuids .lib</span><span class="sxs-lookup"><span data-stu-id="8ac64-137">**Library:**  CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ac64-138">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ac64-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ac64-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="8ac64-139">See also</span></span>

- [<span data-ttu-id="8ac64-140">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="8ac64-140">Debugging Interfaces</span></span>](debugging-interfaces.md)
