---
description: '詳細については、次のページを参照してください:: テキストの表示方法'
title: ICorDebugILFrame::GetIP メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::GetIP method [.NET Framework debugging]
ms.assetid: 18217ba1-1776-4297-a3b9-f77e64b0fead
topic_type:
- apiref
ms.openlocfilehash: f3977d4fbe57b24e7b98b7a597b0db7ad171eb1c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691875"
---
# <a name="icordebugilframegetip-method"></a><span data-ttu-id="fe06a-103">ICorDebugILFrame::GetIP メソッド</span><span class="sxs-lookup"><span data-stu-id="fe06a-103">ICorDebugILFrame::GetIP Method</span></span>

<span data-ttu-id="fe06a-104">命令ポインターの値と、命令ポインターの値が取得された方法を示すビットごとの組み合わせ値を取得します。</span><span class="sxs-lookup"><span data-stu-id="fe06a-104">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe06a-105">構文</span><span class="sxs-lookup"><span data-stu-id="fe06a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe06a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fe06a-106">Parameters</span></span>  

 `pnOffset`  
 <span data-ttu-id="fe06a-107">入出力命令ポインターの値。</span><span class="sxs-lookup"><span data-stu-id="fe06a-107">[out] The value of the instruction pointer.</span></span>  
  
 `pMappingResult`  
 <span data-ttu-id="fe06a-108">入出力命令ポインターの値の取得方法を示す CorDebugMappingResult 列挙値のビットごとの組み合わせへのポインター。</span><span class="sxs-lookup"><span data-stu-id="fe06a-108">[out] A pointer to a bitwise combination of the CorDebugMappingResult enumeration values that describe how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe06a-109">解説</span><span class="sxs-lookup"><span data-stu-id="fe06a-109">Remarks</span></span>  

 <span data-ttu-id="fe06a-110">命令ポインターの値は、関数の MSIL (Microsoft 中間言語) コードへのスタックフレームのオフセットです。</span><span class="sxs-lookup"><span data-stu-id="fe06a-110">The value of the instruction pointer is the stack frame's offset into the function's Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="fe06a-111">スタックフレームがアクティブな場合、このアドレスは次に実行する命令になります。</span><span class="sxs-lookup"><span data-stu-id="fe06a-111">If the stack frame is active, this address is the next instruction to execute.</span></span> <span data-ttu-id="fe06a-112">スタックフレームがアクティブでない場合、このアドレスはスタックフレームが再アクティブ化されたときに次に実行される命令になります。</span><span class="sxs-lookup"><span data-stu-id="fe06a-112">If the stack frame is not active, this address is the next instruction to execute when the stack frame is reactivated.</span></span>  
  
 <span data-ttu-id="fe06a-113">このフレームが just-in-time (JIT) でコンパイルされたフレームである場合、命令ポインターの値は、実際のネイティブ命令ポインターから逆方向にマッピングすることによって決定されます。したがって、値は概数にすぎない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fe06a-113">If this frame is a just-in-time (JIT) compiled frame, the value of the instruction pointer will be determined by mapping backwards from the actual native instruction pointer, so the value may be only approximate.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe06a-114">要件</span><span class="sxs-lookup"><span data-stu-id="fe06a-114">Requirements</span></span>  

 <span data-ttu-id="fe06a-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fe06a-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe06a-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fe06a-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fe06a-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fe06a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe06a-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe06a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
