---
description: '詳細については、次を参照してください: ICorDebugRegisterSet2:: GetRegistersAvailable メソッド'
title: ICorDebugRegisterSet2::GetRegistersAvailable メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.GetRegistersAvailable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::GetRegistersAvailable
helpviewer_keywords:
- GetRegistersAvailable method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegistersAvailable method [.NET Framework debugging]
ms.assetid: f3ed344b-0d3a-44e8-8000-2a97e0805a2c
topic_type:
- apiref
ms.openlocfilehash: 3839647e69efd63aefd1aa154c457f292e684336
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790725"
---
# <a name="icordebugregisterset2getregistersavailable-method"></a><span data-ttu-id="73586-103">ICorDebugRegisterSet2::GetRegistersAvailable メソッド</span><span class="sxs-lookup"><span data-stu-id="73586-103">ICorDebugRegisterSet2::GetRegistersAvailable Method</span></span>

<span data-ttu-id="73586-104">使用できるレジスタのビットマップを提供するバイト配列を取得します。</span><span class="sxs-lookup"><span data-stu-id="73586-104">Gets an array of bytes that provides a bitmap of the available registers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73586-105">構文</span><span class="sxs-lookup"><span data-stu-id="73586-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRegistersAvailable (  
    [in] ULONG32 numChunks,  
    [out, size_is(numChunks)] BYTE availableRegChunks[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73586-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="73586-106">Parameters</span></span>  

 `numChunks`  
 <span data-ttu-id="73586-107">[in] `availableRegChunks` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="73586-107">[in] The size of the `availableRegChunks` array.</span></span>  
  
 `availableRegChunks`  
 <span data-ttu-id="73586-108">入出力バイト配列。各ビットはレジスタに対応します。</span><span class="sxs-lookup"><span data-stu-id="73586-108">[out] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="73586-109">レジスタが使用可能な場合は、レジスタの対応するビットが設定されます。</span><span class="sxs-lookup"><span data-stu-id="73586-109">If a register is available, the register's corresponding bit is set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73586-110">解説</span><span class="sxs-lookup"><span data-stu-id="73586-110">Remarks</span></span>  

 <span data-ttu-id="73586-111">CorDebugRegister 列挙子の値は、異なるマイクロプロセッサのレジスタを指定します。</span><span class="sxs-lookup"><span data-stu-id="73586-111">The values of the CorDebugRegister enumeration specify the registers of different microprocessors.</span></span> <span data-ttu-id="73586-112">各値の上位5ビットは、バイト配列へのインデックスです `availableRegChunks` 。</span><span class="sxs-lookup"><span data-stu-id="73586-112">The upper five bits of each value are the index into the `availableRegChunks` array of bytes.</span></span> <span data-ttu-id="73586-113">各値の下位3ビットは、インデックス付きバイト内のビット位置を識別します。</span><span class="sxs-lookup"><span data-stu-id="73586-113">The lower three bits of each value identify the bit position within the indexed byte.</span></span> <span data-ttu-id="73586-114">特定の `CorDebugRegister` レジスタを指定する値を指定すると、マスク内のレジスタの位置は次のように決定されます。</span><span class="sxs-lookup"><span data-stu-id="73586-114">Given a `CorDebugRegister` value that specifies a particular register, the register's position in the mask is determined as follows:</span></span>  
  
1. <span data-ttu-id="73586-115">配列内の正しいバイトにアクセスするために必要なインデックスを抽出し `availableRegChunks` ます。</span><span class="sxs-lookup"><span data-stu-id="73586-115">Extract the index needed to access the correct byte in the `availableRegChunks` array:</span></span>  
  
     <span data-ttu-id="73586-116">`CorDebugRegister` 値 >> 3</span><span class="sxs-lookup"><span data-stu-id="73586-116">`CorDebugRegister` value >> 3</span></span>  
  
2. <span data-ttu-id="73586-117">インデックス付きバイト内のビット位置を抽出します。ビットゼロは最下位ビットです。</span><span class="sxs-lookup"><span data-stu-id="73586-117">Extract the bit position within the indexed byte, where bit zero is the least significant bit:</span></span>  
  
     <span data-ttu-id="73586-118">`CorDebugRegister` 値 & 7</span><span class="sxs-lookup"><span data-stu-id="73586-118">`CorDebugRegister` value & 7</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73586-119">要件</span><span class="sxs-lookup"><span data-stu-id="73586-119">Requirements</span></span>  

 <span data-ttu-id="73586-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="73586-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73586-121">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="73586-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73586-122">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73586-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73586-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73586-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73586-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="73586-124">See also</span></span>

- [<span data-ttu-id="73586-125">ICorDebugRegisterSet2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="73586-125">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
- [<span data-ttu-id="73586-126">ICorDebugRegisterSet インターフェイス</span><span class="sxs-lookup"><span data-stu-id="73586-126">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
