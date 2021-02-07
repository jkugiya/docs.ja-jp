---
description: '詳細については、次のページを参照してください: いい Process:: ReadMemory メソッド'
title: ICorDebugProcess::ReadMemory メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ReadMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ReadMemory
helpviewer_keywords:
- ReadMemory method [.NET Framework debugging]
- ICorDebugProcess::ReadMemory method [.NET Framework debugging]
ms.assetid: 28e4b2f6-9589-445c-be24-24a3306795e7
topic_type:
- apiref
ms.openlocfilehash: bdf1bda9df416b6d3142e3ae09955e706f260802
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746803"
---
# <a name="icordebugprocessreadmemory-method"></a><span data-ttu-id="3349e-103">ICorDebugProcess::ReadMemory メソッド</span><span class="sxs-lookup"><span data-stu-id="3349e-103">ICorDebugProcess::ReadMemory Method</span></span>

<span data-ttu-id="3349e-104">このプロセスの指定したメモリ領域を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="3349e-104">Reads a specified area of memory for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3349e-105">構文</span><span class="sxs-lookup"><span data-stu-id="3349e-105">Syntax</span></span>  
  
```cpp  
HRESULT ReadMemory(  
    [in]  CORDB_ADDRESS address,
    [in]  DWORD size,  
    [out, size_is(size), length_is(size)] BYTE buffer[],  
    [out] SIZE_T *read);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3349e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3349e-106">Parameters</span></span>  

 `address`  
 <span data-ttu-id="3349e-107">から `CORDB_ADDRESS` 読み取るメモリのベースアドレスを指定する値。</span><span class="sxs-lookup"><span data-stu-id="3349e-107">[in] A `CORDB_ADDRESS` value that specifies the base address of the memory to be read.</span></span>  
  
 `size`  
 <span data-ttu-id="3349e-108">からメモリから読み取るバイト数。</span><span class="sxs-lookup"><span data-stu-id="3349e-108">[in] The number of bytes to be read from memory.</span></span>  
  
 `buffer`  
 <span data-ttu-id="3349e-109">入出力メモリの内容を受け取るバッファー。</span><span class="sxs-lookup"><span data-stu-id="3349e-109">[out] A buffer that receives the contents of the memory.</span></span>  
  
 `read`  
 <span data-ttu-id="3349e-110">入出力指定したバッファーに転送されたバイト数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="3349e-110">[out] A pointer to the number of bytes transferred into the specified buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3349e-111">解説</span><span class="sxs-lookup"><span data-stu-id="3349e-111">Remarks</span></span>  

 <span data-ttu-id="3349e-112">メソッドは、主に、 `ReadMemory` デバッグ対象のアンマネージ部分で使用されているメモリ領域を検査するために相互運用機能デバッグによって使用されることを意図しています。</span><span class="sxs-lookup"><span data-stu-id="3349e-112">The `ReadMemory` method is primarily intended to be used by interop debugging to inspect memory regions that are being used by the unmanaged portion of the debuggee.</span></span> <span data-ttu-id="3349e-113">このメソッドを使用して、Microsoft 中間言語 (MSIL) コードとネイティブの JIT コンパイルコードを読み取ることもできます。</span><span class="sxs-lookup"><span data-stu-id="3349e-113">This method can also be used to read Microsoft intermediate language (MSIL) code and native JIT-compiled code.</span></span>  
  
 <span data-ttu-id="3349e-114">マネージブレークポイントは、パラメーターで返されたデータから削除され `buffer` ます。</span><span class="sxs-lookup"><span data-stu-id="3349e-114">Any managed breakpoints will be removed from the data that is returned in the `buffer` parameter.</span></span> <span data-ttu-id="3349e-115">[ICorDebugProcess2:: SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md)によって設定されたネイティブブレークポイントに対して調整は行われません。</span><span class="sxs-lookup"><span data-stu-id="3349e-115">No adjustments will be made for native breakpoints set by [ICorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="3349e-116">プロセスメモリのキャッシュは実行されません。</span><span class="sxs-lookup"><span data-stu-id="3349e-116">No caching of process memory is performed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3349e-117">要件</span><span class="sxs-lookup"><span data-stu-id="3349e-117">Requirements</span></span>  

 <span data-ttu-id="3349e-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3349e-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3349e-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3349e-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3349e-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3349e-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3349e-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3349e-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
