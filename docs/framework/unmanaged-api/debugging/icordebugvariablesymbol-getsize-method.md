---
description: '詳細について: ICorDebugVariableSymbol:: GetSize メソッド'
title: ICorDebugVariableSymbol::GetSize メソッド
ms.date: 03/30/2017
ms.assetid: add0cd9d-9a29-49b1-ae07-d9d3786b4ccd
ms.openlocfilehash: f4098bf5e053ab66dd7966d4b665cfad4dee01d5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790582"
---
# <a name="icordebugvariablesymbolgetsize-method"></a><span data-ttu-id="315e2-103">ICorDebugVariableSymbol::GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="315e2-103">ICorDebugVariableSymbol::GetSize Method</span></span>

<span data-ttu-id="315e2-104">変数のサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="315e2-104">Gets the size of a variable in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="315e2-105">構文</span><span class="sxs-lookup"><span data-stu-id="315e2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="315e2-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="315e2-106">Parameters</span></span>  

 `pcbValue`  
 <span data-ttu-id="315e2-107">変数のサイズが格納されている 32 ビットの符号なし整数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="315e2-107">A pointer to a 32-bit unsigned integer containing the size of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="315e2-108">解説</span><span class="sxs-lookup"><span data-stu-id="315e2-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="315e2-109">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="315e2-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="315e2-110">要件</span><span class="sxs-lookup"><span data-stu-id="315e2-110">Requirements</span></span>  

 <span data-ttu-id="315e2-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="315e2-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="315e2-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="315e2-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="315e2-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="315e2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="315e2-114">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="315e2-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="315e2-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="315e2-115">See also</span></span>

- [<span data-ttu-id="315e2-116">ICorDebugVariableSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="315e2-116">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="315e2-117">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="315e2-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
