---
description: '詳細について: ICorDebugRegisterSet2:: GetRegisters メソッド'
title: ICorDebugRegisterSet2::GetRegisters メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.GetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegisters method [.NET Framework debugging]
ms.assetid: dbc498a8-ba3f-42f2-bdd9-b623c77a1019
topic_type:
- apiref
ms.openlocfilehash: 58af939b0e88185e2be23b69ca70d28e93ff873f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794779"
---
# <a name="icordebugregisterset2getregisters-method"></a><span data-ttu-id="63d93-103">ICorDebugRegisterSet2:: GetRegisters メソッド</span><span class="sxs-lookup"><span data-stu-id="63d93-103">ICorDebugRegisterSet2::GetRegisters method</span></span>

<span data-ttu-id="63d93-104">指定されたビットマスクによって指定された各レジスタの値を取得します (コードが現在実行されているプラットフォーム用)。</span><span class="sxs-lookup"><span data-stu-id="63d93-104">Gets the value of each register (for the platform on which code is currently executing) that is specified by the given bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63d93-105">構文</span><span class="sxs-lookup"><span data-stu-id="63d93-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [out, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63d93-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="63d93-106">Parameters</span></span>

 `maskCount`  
 <span data-ttu-id="63d93-107">から配列のサイズ (バイト単位) `mask` 。</span><span class="sxs-lookup"><span data-stu-id="63d93-107">[in] The size, in bytes, of the `mask` array.</span></span>  
  
 `mask`  
 <span data-ttu-id="63d93-108">からバイト配列。各ビットはレジスタに対応します。</span><span class="sxs-lookup"><span data-stu-id="63d93-108">[in] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="63d93-109">ビットが1の場合は、対応するレジスタの値が取得されます。</span><span class="sxs-lookup"><span data-stu-id="63d93-109">If the bit is 1, the corresponding register's value will be retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="63d93-110">から取得するレジスタ値の数。</span><span class="sxs-lookup"><span data-stu-id="63d93-110">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="63d93-111">入出力オブジェクトの配列 `CORDB_REGISTER` 。各オブジェクトは、レジスタの値を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="63d93-111">[out] An array of `CORDB_REGISTER` objects, each of which receives the value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63d93-112">解説</span><span class="sxs-lookup"><span data-stu-id="63d93-112">Remarks</span></span>

 <span data-ttu-id="63d93-113">メソッドは、 `GetRegisters` マスクによって指定されたレジスタから値の配列を返します。</span><span class="sxs-lookup"><span data-stu-id="63d93-113">The `GetRegisters` method returns an array of values from the registers that are specified by the mask.</span></span> <span data-ttu-id="63d93-114">配列に、マスクビットが設定されていないレジスタの値が含まれていません。</span><span class="sxs-lookup"><span data-stu-id="63d93-114">The array does not contain values of registers whose mask bit is not set.</span></span> <span data-ttu-id="63d93-115">したがって、配列のサイズは `regBuffer` マスク内の1の数と同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="63d93-115">Thus, the size of the `regBuffer` array must be equal to the number of 1's in the mask.</span></span> <span data-ttu-id="63d93-116">の値 `regCount` がマスクで示されているレジスタの数に対して小さすぎる場合、番号が大きいレジスタの値はセットから切り捨てられます。</span><span class="sxs-lookup"><span data-stu-id="63d93-116">If the value of `regCount` is too small for the number of registers indicated by the mask, the values of the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="63d93-117">`regCount`が大きすぎる場合、未使用の `regBuffer` 要素は変更されません。</span><span class="sxs-lookup"><span data-stu-id="63d93-117">If `regCount` is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="63d93-118">使用できないレジスタがマスクによって示されている場合、そのレジスタに対して不確定な値が返されます。</span><span class="sxs-lookup"><span data-stu-id="63d93-118">If an unavailable register is indicated by the mask, an indeterminate value will be returned for that register.</span></span>  
  
 <span data-ttu-id="63d93-119">メソッドは、64を超える `ICorDebugRegisterSet2::GetRegisters` レジスタを持つプラットフォームに必要です。</span><span class="sxs-lookup"><span data-stu-id="63d93-119">The `ICorDebugRegisterSet2::GetRegisters` method is necessary for platforms that have more than 64 registers.</span></span> <span data-ttu-id="63d93-120">たとえば、IA64 には128汎用レジスタと128浮動小数点レジスタがあるため、ビットマスクには64ビット以上が必要です。</span><span class="sxs-lookup"><span data-stu-id="63d93-120">For example, IA64 has 128 general purpose registers and 128 floating-point registers, so you need more than 64 bits in the bit mask.</span></span>  
  
 <span data-ttu-id="63d93-121">X86 などのプラットフォームの場合と同様に、64以上のレジスタがない場合、メソッドは単にバイト配列のバイトをに変換し、次に、 `GetRegisters` `mask` `ULONG64` マスクを取得する[](icordebugregisterset-getregisters-method.md) 、は、のようにします。 `ULONG64`</span><span class="sxs-lookup"><span data-stu-id="63d93-121">If you don't have more than 64 registers, as is the case on platforms such as x86, the `GetRegisters` method just translates the bytes in the `mask` byte array into a `ULONG64` and then calls the [ICorDebugRegisterSet::GetRegisters](icordebugregisterset-getregisters-method.md) method, which takes the `ULONG64` mask.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63d93-122">要件</span><span class="sxs-lookup"><span data-stu-id="63d93-122">Requirements</span></span>

 <span data-ttu-id="63d93-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63d93-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63d93-124">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="63d93-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="63d93-125">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="63d93-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63d93-126">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63d93-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63d93-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="63d93-127">See also</span></span>

- [<span data-ttu-id="63d93-128">ICorDebugRegisterSet2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="63d93-128">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
- [<span data-ttu-id="63d93-129">ICorDebugRegisterSet インターフェイス</span><span class="sxs-lookup"><span data-stu-id="63d93-129">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
