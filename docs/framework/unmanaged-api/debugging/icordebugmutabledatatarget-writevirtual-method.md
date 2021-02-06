---
description: '詳細について: ICorDebugMutableDataTarget:: WriteVirtual メソッド'
title: ICorDebugMutableDataTarget::WriteVirtual メソッド
ms.date: 03/30/2017
ms.assetid: 80833648-58a7-491a-8dc8-9a48e9bb3adc
ms.openlocfilehash: 3f3400456b7af51f4b24d7e14e35d641f03a8bfd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637821"
---
# <a name="icordebugmutabledatatargetwritevirtual-method"></a><span data-ttu-id="2aee1-103">ICorDebugMutableDataTarget::WriteVirtual メソッド</span><span class="sxs-lookup"><span data-stu-id="2aee1-103">ICorDebugMutableDataTarget::WriteVirtual Method</span></span>

<span data-ttu-id="2aee1-104">ターゲット プロセスのアドレス空間にメモリを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="2aee1-104">Writes memory into the target process address space.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2aee1-105">構文</span><span class="sxs-lookup"><span data-stu-id="2aee1-105">Syntax</span></span>  
  
```cpp  
HRESULT WriteVirtual(  
   [in] CORDB_ADDRESS address,  
   [in, size_is(bytesRequested)] const BYTE * pBuffer,  
   [in] ULONG32 bytesRequested);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2aee1-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2aee1-106">Parameters</span></span>  

 `address`  
 <span data-ttu-id="2aee1-107">[in] `pBuffer` の内容の書き込み先のアドレスです。</span><span class="sxs-lookup"><span data-stu-id="2aee1-107">[in] The address at which to write the contents of `pBuffer`.</span></span>  
  
 `pBuffer`  
 <span data-ttu-id="2aee1-108">[in] 書き込むバイト数が格納されているバイト配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="2aee1-108">[in] A pointer to a byte array that contains the bytes to be written.</span></span>  
  
 `address`  
 <span data-ttu-id="2aee1-109">[in] `pBuffer` のバイト数。</span><span class="sxs-lookup"><span data-stu-id="2aee1-109">[in] The number of bytes in `pBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2aee1-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="2aee1-110">Return Value</span></span>  

 <span data-ttu-id="2aee1-111">正常に完了した場合は `S_OK`、失敗した場合はその他の `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="2aee1-111">`S_OK` on success, or any other `HRESULT` on failure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2aee1-112">解説</span><span class="sxs-lookup"><span data-stu-id="2aee1-112">Remarks</span></span>  

 <span data-ttu-id="2aee1-113">バイトを書き込むことができない場合、メソッド呼び出しは失敗し、ターゲット アドレス空間のバイトは変更されません。</span><span class="sxs-lookup"><span data-stu-id="2aee1-113">If any bytes cannot be written, the method call fails without changing any bytes in the target address space.</span></span> <span data-ttu-id="2aee1-114">(それ以外の場合、ターゲットは不整合な状態になり、デバッグの信頼性がさらに低下します。)</span><span class="sxs-lookup"><span data-stu-id="2aee1-114">(Otherwise, the target would be in an inconsistent state that makes further debugging unreliable.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2aee1-115">要件</span><span class="sxs-lookup"><span data-stu-id="2aee1-115">Requirements</span></span>  

 <span data-ttu-id="2aee1-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2aee1-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2aee1-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2aee1-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2aee1-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2aee1-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2aee1-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2aee1-119">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2aee1-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="2aee1-120">See also</span></span>

- [<span data-ttu-id="2aee1-121">ICorDebugMutableDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2aee1-121">ICorDebugMutableDataTarget Interface</span></span>](icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="2aee1-122">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="2aee1-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
