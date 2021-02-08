---
description: '詳細について: ICorDebugILFrame4:: EnumerateLocalVariablesEx メソッド'
title: ICorDebugILFrame4::EnumerateLocalVariablesEx メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.EnumerateLocalVariablesEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6f60aae6-70ec-4c4c-963a-138df98c4668
topic_type:
- apiref
ms.openlocfilehash: 8808b1ac337304ab37a35f7733b317dad274d48e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791245"
---
# <a name="icordebugilframe4enumeratelocalvariablesex-method"></a><span data-ttu-id="b8d44-103">ICorDebugILFrame4::EnumerateLocalVariablesEx メソッド</span><span class="sxs-lookup"><span data-stu-id="b8d44-103">ICorDebugILFrame4::EnumerateLocalVariablesEx Method</span></span>

<span data-ttu-id="b8d44-104">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="b8d44-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="b8d44-105">フレームのローカル変数の列挙子を取得し、プロファイラー ReJIT インストルメンテーションに追加される変数も含みます。</span><span class="sxs-lookup"><span data-stu-id="b8d44-105">Gets an enumerator for the local variable in the frame, and optionally includes variables added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8d44-106">構文</span><span class="sxs-lookup"><span data-stu-id="b8d44-106">Syntax</span></span>  
  
```cpp
HRESULT EnumerateLocalVariablesEx(  
   [in] ILCodeKind flags,
   [out] ICorDebugValueEnum **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8d44-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b8d44-107">Parameters</span></span>  

 `flags`  
 <span data-ttu-id="b8d44-108">からプロファイラー ReJIT インストルメンテーションに追加された変数がフレームに含まれるかどうかを指定する [Ilcodekind](ilcodekind-enumeration.md) 列挙型のメンバー。</span><span class="sxs-lookup"><span data-stu-id="b8d44-108">[in] An [ILCodeKind](ilcodekind-enumeration.md) enumeration member that specifies whether variables added in profiler ReJIT instrumentation are included in the frame.</span></span>  
  
 `ppValueEnum`  
 <span data-ttu-id="b8d44-109">入出力このフレーム内のローカル変数の列挙子である "テキスト" オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b8d44-109">[out] A pointer to the address of an "ICorDebugValueEnum" object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8d44-110">解説</span><span class="sxs-lookup"><span data-stu-id="b8d44-110">Remarks</span></span>  

 <span data-ttu-id="b8d44-111">このメソッドは、 [EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md) メソッドに似ていますが、プロファイラー rejit インストルメンテーションに追加された変数にオプションでアクセスする点が異なります。</span><span class="sxs-lookup"><span data-stu-id="b8d44-111">This method is similar to the [EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md) method, except that it optionally accesses variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="b8d44-112">をに設定すること `flags` `ILCODE_ORIGINAL_IL` は、 [EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md)を呼び出した場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="b8d44-112">Setting `flags` to `ILCODE_ORIGINAL_IL` is equivalent to calling [ICorDebugILFrame::EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md).</span></span> <span data-ttu-id="b8d44-113">`flags` を `ILCODE_REJIT_IL` に設定することにより、デバッガは プロファイラー ReJIT インストルメンテーションに追加されるローカル変数にアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="b8d44-113">Setting `flags` to `ILCODE_REJIT_IL` allows the debugger to access the local variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="b8d44-114">中間言語 (IL) がインストルメント化されていない場合は、列挙子は空になり、メソッドは `S_OK` を返します。</span><span class="sxs-lookup"><span data-stu-id="b8d44-114">If the intermediate language (IL) is not instrumented, the enumeration is empty and the method returns `S_OK`.</span></span>  
  
 <span data-ttu-id="b8d44-115">実行中のメソッドにあるすべてのローカル変数が列挙子に含まれない場合がありますが、それは一部のローカル変数が非アクティブである可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="b8d44-115">The enumerator may not include all of the local variables in the running method, since some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8d44-116">要件</span><span class="sxs-lookup"><span data-stu-id="b8d44-116">Requirements</span></span>  

 <span data-ttu-id="b8d44-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b8d44-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8d44-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b8d44-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8d44-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8d44-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8d44-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8d44-120">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8d44-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="b8d44-121">See also</span></span>

- [<span data-ttu-id="b8d44-122">ICorDebugILFrame4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b8d44-122">ICorDebugILFrame4 Interface</span></span>](icordebugilframe4-interface.md)
- [<span data-ttu-id="b8d44-123">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="b8d44-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="b8d44-124">ReJIT: How-To ガイド</span><span class="sxs-lookup"><span data-stu-id="b8d44-124">ReJIT: A How-To Guide</span></span>](/archive/blogs/davbr/rejit-a-how-to-guide)
