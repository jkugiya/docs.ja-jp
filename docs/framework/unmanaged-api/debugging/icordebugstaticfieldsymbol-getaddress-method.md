---
description: 詳細については、次の説明
title: ICorDebugStaticFieldSymbol::GetAddress メソッド
ms.date: 03/30/2017
ms.assetid: 5a6c9a5a-ec72-4c40-a9c3-cee7baa63687
ms.openlocfilehash: 1944839ff6afc31dc3667111397cbb088b95b412
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801008"
---
# <a name="icordebugstaticfieldsymbolgetaddress-method"></a><span data-ttu-id="c49d7-103">ICorDebugStaticFieldSymbol::GetAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="c49d7-103">ICorDebugStaticFieldSymbol::GetAddress Method</span></span>

<span data-ttu-id="c49d7-104">静的フィールドのアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="c49d7-104">Gets the address of a static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c49d7-105">構文</span><span class="sxs-lookup"><span data-stu-id="c49d7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAddress(  
   [out] CORDB_ADDRESS *pRVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c49d7-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c49d7-106">Parameters</span></span>  

 <span data-ttu-id="c49d7-107">pRVA</span><span class="sxs-lookup"><span data-stu-id="c49d7-107">pRVA</span></span>  
 <span data-ttu-id="c49d7-108">[out] 静的フィールドの相対仮想アドレス (RVA) へのポインター。</span><span class="sxs-lookup"><span data-stu-id="c49d7-108">[out] A pointer to the relative virtual address (RVA) of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c49d7-109">解説</span><span class="sxs-lookup"><span data-stu-id="c49d7-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c49d7-110">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="c49d7-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c49d7-111">要件</span><span class="sxs-lookup"><span data-stu-id="c49d7-111">Requirements</span></span>  

 <span data-ttu-id="c49d7-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c49d7-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c49d7-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c49d7-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c49d7-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c49d7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c49d7-115">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c49d7-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c49d7-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="c49d7-116">See also</span></span>

- [<span data-ttu-id="c49d7-117">ICorDebugStaticFieldSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c49d7-117">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="c49d7-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="c49d7-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
