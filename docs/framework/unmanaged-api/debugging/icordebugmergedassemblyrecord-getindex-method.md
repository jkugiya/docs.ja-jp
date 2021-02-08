---
description: '詳細について: ICorDebugMergedAssemblyRecord:: GetIndex メソッド'
title: ICorDebugMergedAssemblyRecord::GetCulture メソッド
ms.date: 03/30/2017
ms.assetid: 98701444-b9bc-4978-9548-89ac3394147d
ms.openlocfilehash: f3a51c5ed5edacc9678c965ac385d0969e2ee8a7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801112"
---
# <a name="icordebugmergedassemblyrecordgetindex-method"></a><span data-ttu-id="4993d-103">ICorDebugMergedAssemblyRecord::GetCulture メソッド</span><span class="sxs-lookup"><span data-stu-id="4993d-103">ICorDebugMergedAssemblyRecord::GetIndex Method</span></span>

<span data-ttu-id="4993d-104">アセンブリのプレフィックス インデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="4993d-104">Gets the assembly's prefix index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4993d-105">構文</span><span class="sxs-lookup"><span data-stu-id="4993d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetIndex(  
   [out] ULONG32 *pIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4993d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4993d-106">Parameters</span></span>  

 `pIndex`  
 <span data-ttu-id="4993d-107">[out] プレフィックス インデックスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="4993d-107">[out] A pointer to the prefix index.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4993d-108">解説</span><span class="sxs-lookup"><span data-stu-id="4993d-108">Remarks</span></span>  

 <span data-ttu-id="4993d-109">プレフィックス インデックスは、マージされたメタデータの型名での名前の競合を回避する目的で使用されます。</span><span class="sxs-lookup"><span data-stu-id="4993d-109">The prefix index is used to prevent name collisions in the merged metadata type names.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4993d-110">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="4993d-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4993d-111">要件</span><span class="sxs-lookup"><span data-stu-id="4993d-111">Requirements</span></span>  

 <span data-ttu-id="4993d-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4993d-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4993d-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4993d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4993d-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4993d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4993d-115">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4993d-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4993d-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="4993d-116">See also</span></span>

- [<span data-ttu-id="4993d-117">ICorDebugMergedAssemblyRecord インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4993d-117">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="4993d-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="4993d-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
