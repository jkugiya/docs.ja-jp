---
description: '詳細については、次のページを参照してください: \n Datatの説明:: ReadVirtual メソッド'
title: ICorDebugDataTarget::ReadVirtual メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.ReadVirtual Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::ReadVirtual
helpviewer_keywords:
- ICorDebugDataTarget::ReadVirtual method [.NET Framework debugging]
- ReadVirtual method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: 55e57640-b3d2-413d-b4f4-fbc27fb8e37c
topic_type:
- apiref
ms.openlocfilehash: 4525ba1e5dc685813d963dab96879b886987f38f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710609"
---
# <a name="icordebugdatatargetreadvirtual-method"></a><span data-ttu-id="4f7de-103">ICorDebugDataTarget::ReadVirtual メソッド</span><span class="sxs-lookup"><span data-stu-id="4f7de-103">ICorDebugDataTarget::ReadVirtual Method</span></span>

<span data-ttu-id="4f7de-104">指定したアドレスを開始位置として連続したメモリのブロックを取得し、指定したバッファー内でそれを返します。</span><span class="sxs-lookup"><span data-stu-id="4f7de-104">Gets a block of contiguous memory starting at the specified address, and returns it in the supplied buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f7de-105">構文</span><span class="sxs-lookup"><span data-stu-id="4f7de-105">Syntax</span></span>  
  
```cpp  
HRESULT ReadVirtual(  
    [in] CORDB_ADDRESS   address,  
    [out, size_is(bytesRequested), length_is(*pBytesRead)]  
          BYTE *     pBuffer,  
    [in]  ULONG32    bytesRequested,  
    [out] ULONG32 *  pBytesRead);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f7de-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4f7de-106">Parameters</span></span>  

 `address`  
 <span data-ttu-id="4f7de-107">から要求されたメモリの開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="4f7de-107">[in] The start address of requested memory.</span></span>  
  
 `pbuffer`  
 <span data-ttu-id="4f7de-108">入出力メモリが格納されるバッファー。</span><span class="sxs-lookup"><span data-stu-id="4f7de-108">[out] The buffer where the memory will be stored.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="4f7de-109">からターゲットアドレスから取得するバイト数。</span><span class="sxs-lookup"><span data-stu-id="4f7de-109">[in] The number of bytes to get from the target address.</span></span>  
  
 `pBytesRead`  
 <span data-ttu-id="4f7de-110">入出力ターゲットアドレスから実際に読み取られたバイト数。</span><span class="sxs-lookup"><span data-stu-id="4f7de-110">[out] The number of bytes actually read from the target address.</span></span> <span data-ttu-id="4f7de-111">これはよりも小さくなる可能性があり `bytesRequested` ます。</span><span class="sxs-lookup"><span data-stu-id="4f7de-111">This can be fewer than `bytesRequested`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f7de-112">解説</span><span class="sxs-lookup"><span data-stu-id="4f7de-112">Remarks</span></span>  

 <span data-ttu-id="4f7de-113">最初のバイト (指定した開始アドレス) を読み取ることができる場合、呼び出しは成功を返します (null で終わる文字列など、自己記述型の長さを持つデータ構造の効率的な読み取りをサポートするため)。</span><span class="sxs-lookup"><span data-stu-id="4f7de-113">If the first byte (at the specified start address) can be read, the call should return success (to support efficient reading of data structures with self-describing length, like null-terminated strings).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f7de-114">要件</span><span class="sxs-lookup"><span data-stu-id="4f7de-114">Requirements</span></span>  

 <span data-ttu-id="4f7de-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4f7de-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f7de-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4f7de-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4f7de-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4f7de-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f7de-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f7de-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f7de-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="4f7de-119">See also</span></span>

- [<span data-ttu-id="4f7de-120">ICorDebugDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4f7de-120">ICorDebugDataTarget Interface</span></span>](icordebugdatatarget-interface.md)
- [<span data-ttu-id="4f7de-121">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="4f7de-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="4f7de-122">デバッグ</span><span class="sxs-lookup"><span data-stu-id="4f7de-122">Debugging</span></span>](index.md)
