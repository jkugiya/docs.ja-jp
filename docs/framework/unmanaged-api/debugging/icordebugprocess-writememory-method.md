---
description: '詳細については、次を参照してください: WriteMemory Method:: メソッド'
title: ICorDebugProcess::WriteMemory メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.WriteMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::WriteMemory
helpviewer_keywords:
- ICorDebugProcess::WriteMemory method [.NET Framework debugging]
- WriteMemory method [.NET Framework debugging]
ms.assetid: d5c07d86-045d-4391-893b-0bcd2959f90e
topic_type:
- apiref
ms.openlocfilehash: 6ea48aff2e1ea812d851a228976b458f58a60e14
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746624"
---
# <a name="icordebugprocesswritememory-method"></a><span data-ttu-id="9f811-103">ICorDebugProcess::WriteMemory メソッド</span><span class="sxs-lookup"><span data-stu-id="9f811-103">ICorDebugProcess::WriteMemory Method</span></span>

<span data-ttu-id="9f811-104">このプロセスのメモリ領域にデータを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="9f811-104">Writes data to an area of memory in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f811-105">構文</span><span class="sxs-lookup"><span data-stu-id="9f811-105">Syntax</span></span>  
  
```cpp  
HRESULT WriteMemory(  
    [in]  CORDB_ADDRESS address,  
    [in]  DWORD size,  
    [in, size_is(size)] BYTE buffer[],  
    [out] SIZE_T *written);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f811-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9f811-106">Parameters</span></span>  

 `address`  
 <span data-ttu-id="9f811-107">から `CORDB_ADDRESS` データが書き込まれるメモリ領域のベースアドレスを表す値。</span><span class="sxs-lookup"><span data-stu-id="9f811-107">[in] A `CORDB_ADDRESS` value that is the base address of the memory area to which data is written.</span></span> <span data-ttu-id="9f811-108">データ転送が行われる前に、システムは、ベースアドレスを開始位置として、指定したサイズのメモリ領域が書き込み可能であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9f811-108">Before data transfer occurs, the system verifies that the memory area of the specified size, beginning at the base address, is accessible for writing.</span></span> <span data-ttu-id="9f811-109">アクセスできない場合、メソッドは失敗します。</span><span class="sxs-lookup"><span data-stu-id="9f811-109">If it is not accessible, the method fails.</span></span>  
  
 `size`  
 <span data-ttu-id="9f811-110">からメモリ領域に書き込まれるバイト数。</span><span class="sxs-lookup"><span data-stu-id="9f811-110">[in] The number of bytes to be written to the memory area.</span></span>  
  
 `buffer`  
 <span data-ttu-id="9f811-111">から書き込むデータを格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="9f811-111">[in] A buffer that contains data to be written.</span></span>  
  
 `written`  
 <span data-ttu-id="9f811-112">入出力このプロセスのメモリ領域に書き込まれたバイト数を受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="9f811-112">[out] A pointer to a variable that receives the number of bytes written to the memory area in this process.</span></span> <span data-ttu-id="9f811-113">`written`が NULL の場合、このパラメーターは無視されます。</span><span class="sxs-lookup"><span data-stu-id="9f811-113">If `written` is NULL, this parameter is ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f811-114">解説</span><span class="sxs-lookup"><span data-stu-id="9f811-114">Remarks</span></span>  

 <span data-ttu-id="9f811-115">データは、ブレークポイントの背後に自動的に書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="9f811-115">Data is automatically written behind any breakpoints.</span></span> <span data-ttu-id="9f811-116">.NET Framework バージョン2.0 では、ネイティブデバッガーは、このメソッドを使用して命令ストリームにブレークポイントを挿入することはできません。</span><span class="sxs-lookup"><span data-stu-id="9f811-116">In the .NET Framework version 2.0, native debuggers should not use this method to inject breakpoints into the instruction stream.</span></span> <span data-ttu-id="9f811-117">代わりに [ICorDebugProcess2:: SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md) を使用してください。</span><span class="sxs-lookup"><span data-stu-id="9f811-117">Use [ICorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md) instead.</span></span>  
  
 <span data-ttu-id="9f811-118">メソッドは、 `WriteMemory` マネージコードの外部でのみ使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9f811-118">The `WriteMemory` method should be used only outside of managed code.</span></span> <span data-ttu-id="9f811-119">不適切に使用された場合、このメソッドはランタイムを破損する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9f811-119">This method can corrupt the runtime if used improperly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f811-120">要件</span><span class="sxs-lookup"><span data-stu-id="9f811-120">Requirements</span></span>  

 <span data-ttu-id="9f811-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9f811-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f811-122">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9f811-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9f811-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9f811-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9f811-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f811-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
