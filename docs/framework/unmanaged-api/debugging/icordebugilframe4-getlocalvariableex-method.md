---
description: '詳細については、次を参照してください: ICorDebugILFrame4:: Getlocal変数 Ex メソッド'
title: ICorDebugILFrame4::GetLocalVariableEx メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.GetCodeEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 0c8676f8-ca0d-4998-b64d-fefac7e38912
topic_type:
- apiref
ms.openlocfilehash: 4eb6b3abbaf05c0373a487d9bd9d575b58a9af49
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791219"
---
# <a name="icordebugilframe4getlocalvariableex-method"></a><span data-ttu-id="c5516-103">ICorDebugILFrame4::GetLocalVariableEx メソッド</span><span class="sxs-lookup"><span data-stu-id="c5516-103">ICorDebugILFrame4::GetLocalVariableEx Method</span></span>

<span data-ttu-id="c5516-104">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="c5516-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="c5516-105">この中間言語 (IL) スタック フレーム内の指定されたローカル変数の値を取得して、オプションでプロファイラー ReJIT インストルメンテーションに追加された変数にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="c5516-105">Gets the value of the specified local variable in this intermediate language (IL) stack frame, and optionally accesses a variable added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5516-106">構文</span><span class="sxs-lookup"><span data-stu-id="c5516-106">Syntax</span></span>  
  
```cpp
HRESULT GetLocalVariableEx(  
   [in] ILCodeKind flags,
   [in] DWORD dwIndex,
   [out] ICorDebugValue **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5516-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c5516-107">Parameters</span></span>  

 `flags`  
 <span data-ttu-id="c5516-108">からプロファイラー ReJIT インストルメンテーションに追加された変数がフレームに含まれるかどうかを指定する [Ilcodekind](ilcodekind-enumeration.md) 列挙体のメンバー。</span><span class="sxs-lookup"><span data-stu-id="c5516-108">[in] An [ILCodeKind](ilcodekind-enumeration.md) enumeration member that specifies whether a variable added in profiler ReJIT instrumentation is included in the frame.</span></span>  
  
 `dwIndex`  
 <span data-ttu-id="c5516-109">[in] IL スタック フレーム内のローカル変数のインデックス。</span><span class="sxs-lookup"><span data-stu-id="c5516-109">[in] The index of the local variable in the IL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="c5516-110">入出力取得された値を表す "ICorDebugValue" オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c5516-110">[out] A pointer to the address of an "ICorDebugValue" object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5516-111">解説</span><span class="sxs-lookup"><span data-stu-id="c5516-111">Remarks</span></span>  

 <span data-ttu-id="c5516-112">このメソッドは、オプションでプロファイラー ReJIT インストルメンテーションに追加された変数にアクセスする点を除いて、 [Getlocalvariable](icordebugilframe-getlocalvariable-method.md) メソッドに似ています。</span><span class="sxs-lookup"><span data-stu-id="c5516-112">This method is similar to the [GetLocalVariable](icordebugilframe-getlocalvariable-method.md) method, except that it optionally accesses a variable added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="c5516-113">値を指定してこのメソッドを呼び出す `flags` `ILCODE_ORIGINAL_IL` ことは、 [getlocalvariable](icordebugilframe-getlocalvariable-method.md)を呼び出すことと同じです。メソッドが追加のローカル変数でインストルメント化されている場合、これらの変数にはアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="c5516-113">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetLocalVariable](icordebugilframe-getlocalvariable-method.md); if the method is instrumented with additional local variables, those variables cannot be accessed.</span></span> <span data-ttu-id="c5516-114">`ILCODE_REJIT_IL` は、デバッガーがプロファイラー ReJIT インストルメンテーションに追加されたローカル変数にアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="c5516-114">`ILCODE_REJIT_IL` allows the debugger to access the local variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="c5516-115">IL がインストルメントされていない場合、メソッドは `E_INVALIDARG` を返します。</span><span class="sxs-lookup"><span data-stu-id="c5516-115">If the IL is not instrumented, the method returns `E_INVALIDARG`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5516-116">要件</span><span class="sxs-lookup"><span data-stu-id="c5516-116">Requirements</span></span>  

 <span data-ttu-id="c5516-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5516-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5516-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c5516-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c5516-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c5516-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5516-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5516-120">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5516-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="c5516-121">See also</span></span>

- [<span data-ttu-id="c5516-122">ICorDebugILFrame4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c5516-122">ICorDebugILFrame4 Interface</span></span>](icordebugilframe4-interface.md)
- [<span data-ttu-id="c5516-123">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="c5516-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="c5516-124">ReJIT: How-To ガイド</span><span class="sxs-lookup"><span data-stu-id="c5516-124">ReJIT: A How-To Guide</span></span>](/archive/blogs/davbr/rejit-a-how-to-guide)
