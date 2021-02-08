---
description: '詳細について: ICorDebugILFrame4:: GetCodeEx メソッド'
title: ICorDebugILFrame4::GetCodeEx メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.GetLocalVariableEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: aeda0e42-29ee-4ca8-9f21-ac4641677a62
topic_type:
- apiref
ms.openlocfilehash: 1d17dfa531354b8a4b0dd3c0d3d2eb47206900cc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791232"
---
# <a name="icordebugilframe4getcodeex-method"></a><span data-ttu-id="c3020-103">ICorDebugILFrame4::GetCodeEx メソッド</span><span class="sxs-lookup"><span data-stu-id="c3020-103">ICorDebugILFrame4::GetCodeEx Method</span></span>

<span data-ttu-id="c3020-104">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="c3020-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="c3020-105">このスタック フレームが実行中のコードに対するポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="c3020-105">Gets a pointer to the code that this stack frame is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3020-106">構文</span><span class="sxs-lookup"><span data-stu-id="c3020-106">Syntax</span></span>  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,
   [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3020-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c3020-107">Parameters</span></span>  

 `flags`  
 <span data-ttu-id="c3020-108">からプロファイラーの ReJIT 要求によって定義された中間言語 (IL) がフレームに含まれるかどうかを指定する [Ilcodekind](ilcodekind-enumeration.md) 列挙体のメンバー。</span><span class="sxs-lookup"><span data-stu-id="c3020-108">[in] An [ILCodeKind](ilcodekind-enumeration.md) enumeration member that specifies whether the intermediate language (IL) defined by the profiler's ReJIT request is included in the frame.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="c3020-109">入出力このスタックフレームが実行しているコードを表す "テキストコード" オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c3020-109">[out] A pointer to the address of an "ICorDebugCode" object that represents the code that this stack frame is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3020-110">解説</span><span class="sxs-lookup"><span data-stu-id="c3020-110">Remarks</span></span>  

 <span data-ttu-id="c3020-111">このメソッドは、必要に応じて、プロファイラーの ReJIT 要求によって定義されたコードにアクセスする点を除いて、 [GetCode](icordebugframe-getcode-method.md) メソッドに似ています。</span><span class="sxs-lookup"><span data-stu-id="c3020-111">This method is similar to the [ICorDebugFrame::GetCode](icordebugframe-getcode-method.md) method, except that it optionally accesses code defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="c3020-112">の値を指定してこのメソッドを呼び出す `flags` `ILCODE_ORIGINAL_IL` ことは、 [GetCode](icordebugframe-getcode-method.md)を呼び出すことと同じです。メソッドがインストルメント化されている場合、その IL にアクセスすることはできません。</span><span class="sxs-lookup"><span data-stu-id="c3020-112">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetCode](icordebugframe-getcode-method.md); if the method is instrumented, its IL will not be accessible.</span></span> <span data-ttu-id="c3020-113">`ILCODE_REJIT_IL` を使用するとデバッガーは、プロファイラーの ReJIT 要求で定義された IL にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="c3020-113">`ILCODE_REJIT_IL` allows the debugger to access the IL defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="c3020-114">IL がインストルメント化されていない場合、 `ppCode` は **null** であり、メソッドはを返し `S_OK` ます。</span><span class="sxs-lookup"><span data-stu-id="c3020-114">If the IL is not instrumented, `ppCode` is **null**, and the method returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3020-115">要件</span><span class="sxs-lookup"><span data-stu-id="c3020-115">Requirements</span></span>  

 <span data-ttu-id="c3020-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c3020-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3020-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c3020-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c3020-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c3020-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3020-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3020-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3020-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="c3020-120">See also</span></span>

- [<span data-ttu-id="c3020-121">ICorDebugILFrame4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c3020-121">ICorDebugILFrame4 Interface</span></span>](icordebugilframe4-interface.md)
- [<span data-ttu-id="c3020-122">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="c3020-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="c3020-123">ReJIT: How-To ガイド</span><span class="sxs-lookup"><span data-stu-id="c3020-123">ReJIT: A How-To Guide</span></span>](/archive/blogs/davbr/rejit-a-how-to-guide)
