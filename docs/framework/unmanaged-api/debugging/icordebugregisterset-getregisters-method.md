---
description: '詳細については、次のページを参照してください: いいね!:: GetRegisters メソッド'
title: ICorDebugRegisterSet::GetRegisters メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetRegisters method [.NET Framework debugging]
ms.assetid: fdf91864-48ea-4aa6-b70c-361b7a3184c7
topic_type:
- apiref
ms.openlocfilehash: efb0f19fe9eb823912203b82267803739fc3e2cd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690848"
---
# <a name="icordebugregistersetgetregisters-method"></a><span data-ttu-id="d5b57-103">ICorDebugRegisterSet::GetRegisters メソッド</span><span class="sxs-lookup"><span data-stu-id="d5b57-103">ICorDebugRegisterSet::GetRegisters Method</span></span>

<span data-ttu-id="d5b57-104">ビットマスクによって指定された、(現在コードを実行しているコンピューター上の) 各レジスタの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="d5b57-104">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5b57-105">構文</span><span class="sxs-lookup"><span data-stu-id="d5b57-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG64       mask,
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5b57-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d5b57-106">Parameters</span></span>  

 `mask`  
 <span data-ttu-id="d5b57-107">から取得するレジスタ値を指定するビットマスク。</span><span class="sxs-lookup"><span data-stu-id="d5b57-107">[in] A bit mask that specifies which register values are to be retrieved.</span></span> <span data-ttu-id="d5b57-108">各ビットは、レジスタに対応します。</span><span class="sxs-lookup"><span data-stu-id="d5b57-108">Each bit corresponds to a register.</span></span> <span data-ttu-id="d5b57-109">ビットが1に設定されている場合は、レジスタの値が取得されます。それ以外の場合は、レジスタの値は取得されません。</span><span class="sxs-lookup"><span data-stu-id="d5b57-109">If a bit is set to one, the register's value is retrieved; otherwise, the register's value is not retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="d5b57-110">から取得するレジスタ値の数。</span><span class="sxs-lookup"><span data-stu-id="d5b57-110">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="d5b57-111">入出力オブジェクトの配列 `CORDB_REGISTER` 。各オブジェクトは、レジスタの値を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="d5b57-111">[out] An array of `CORDB_REGISTER` objects, each of which receives a value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5b57-112">解説</span><span class="sxs-lookup"><span data-stu-id="d5b57-112">Remarks</span></span>  

 <span data-ttu-id="d5b57-113">配列のサイズは、ビットマスクで1に設定されているビット数と同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5b57-113">The size of the array should be equal to the number of bits set to one in the bit mask.</span></span> <span data-ttu-id="d5b57-114">パラメーターは、 `regCount` レジスタ値を受け取るバッファー内の要素の数を指定します。</span><span class="sxs-lookup"><span data-stu-id="d5b57-114">The `regCount` parameter specifies the number of elements in the buffer that will receive the register values.</span></span> <span data-ttu-id="d5b57-115">`regCount`マスクによって示されるレジスタの数に対して値が小さすぎる場合は、番号が大きいレジスタがセットから切り捨てられます。</span><span class="sxs-lookup"><span data-stu-id="d5b57-115">If the `regCount` value is too small for the number of registers indicated by the mask, the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="d5b57-116">`regCount`値が大きすぎる場合、未使用の `regBuffer` 要素は変更されません。</span><span class="sxs-lookup"><span data-stu-id="d5b57-116">If the `regCount` value is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="d5b57-117">使用できないレジスタがビットマスクによって指定されている場合、は `GetRegisters` そのレジスタの不定値を返します。</span><span class="sxs-lookup"><span data-stu-id="d5b57-117">If the bit mask specifies a register that is unavailable, `GetRegisters` returns an indeterminate value for that register.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5b57-118">要件</span><span class="sxs-lookup"><span data-stu-id="d5b57-118">Requirements</span></span>  

 <span data-ttu-id="d5b57-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d5b57-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5b57-120">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d5b57-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d5b57-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d5b57-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5b57-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5b57-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5b57-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="d5b57-123">See also</span></span>

- [<span data-ttu-id="d5b57-124">ICorDebugRegisterSet インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d5b57-124">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="d5b57-125">ICorDebugRegisterSet2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d5b57-125">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
