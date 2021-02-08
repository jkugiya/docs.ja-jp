---
description: '詳細について: ICorDebugVariableSymbol:: GetSlotIndex メソッド'
title: ICorDebugVariableSymbol::GetSlotIndex メソッド
ms.date: 03/30/2017
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
ms.openlocfilehash: 3b5cba06a5e80ffa323d2e6521e9ec4666f6f5f3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790556"
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a><span data-ttu-id="d3937-103">ICorDebugVariableSymbol::GetSlotIndex メソッド</span><span class="sxs-lookup"><span data-stu-id="d3937-103">ICorDebugVariableSymbol::GetSlotIndex Method</span></span>

<span data-ttu-id="d3937-104">ローカル変数のマネージド スロット インデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="d3937-104">Gets the managed slot index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3937-105">構文</span><span class="sxs-lookup"><span data-stu-id="d3937-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3937-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d3937-106">Parameters</span></span>  

 `pSlotIndex`  
 <span data-ttu-id="d3937-107">[out] ローカル変数のスロット インデックスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d3937-107">[out] A pointer to the local variable's slot index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d3937-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="d3937-108">Return Value</span></span>  

 <span data-ttu-id="d3937-109">正常終了した場合は、`S_OK`。</span><span class="sxs-lookup"><span data-stu-id="d3937-109">`S_OK` if successful.</span></span> <span data-ttu-id="d3937-110">変数が関数引数の場合は `E_FAIL`。</span><span class="sxs-lookup"><span data-stu-id="d3937-110">`E_FAIL` if the variable is a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3937-111">解説</span><span class="sxs-lookup"><span data-stu-id="d3937-111">Remarks</span></span>  

 <span data-ttu-id="d3937-112">ローカル変数のマネージド スロット インデックスを使用すると、変数のメタデータ情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="d3937-112">The managed slot index of a local variable can be used to retrieve the variable's metadata information</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d3937-113">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="d3937-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3937-114">要件</span><span class="sxs-lookup"><span data-stu-id="d3937-114">Requirements</span></span>  

 <span data-ttu-id="d3937-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3937-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3937-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d3937-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d3937-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d3937-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3937-118">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3937-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3937-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="d3937-119">See also</span></span>

- [<span data-ttu-id="d3937-120">ICorDebugVariableSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d3937-120">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="d3937-121">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="d3937-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
