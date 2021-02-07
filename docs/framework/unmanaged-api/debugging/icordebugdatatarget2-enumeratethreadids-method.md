---
description: '詳細について: ICorDebugDataTarget2:: EnumerateThreadIDs メソッド'
title: ICorDebugDataTarget2::EnumerateThreadIDs メソッド
ms.date: 03/30/2017
ms.assetid: af02460f-2a45-496e-bc4e-a1ac4f80fe11
ms.openlocfilehash: 5bbda67e6c6de81e9de566a68f772f324d79b92f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710557"
---
# <a name="icordebugdatatarget2enumeratethreadids-method"></a><span data-ttu-id="01f2a-103">ICorDebugDataTarget2::EnumerateThreadIDs メソッド</span><span class="sxs-lookup"><span data-stu-id="01f2a-103">ICorDebugDataTarget2::EnumerateThreadIDs Method</span></span>

<span data-ttu-id="01f2a-104">アクティブなスレッド ID の一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="01f2a-104">Returns a list of active thread IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01f2a-105">構文</span><span class="sxs-lookup"><span data-stu-id="01f2a-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateThreadIDs(  
    [in] ULONG32 cThreadIds,
    [out] ULONG32 *pcThreadIds,
    [out, size_is(cThreadIds), length_is(*pcThreadIds)] ULONG32 pThreadIds[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01f2a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="01f2a-106">Parameters</span></span>  

 <span data-ttu-id="01f2a-107">cThreadIDs</span><span class="sxs-lookup"><span data-stu-id="01f2a-107">cThreadIDs</span></span>  
 <span data-ttu-id="01f2a-108">[入力] ID を返すことのできるスレッドの最大数。</span><span class="sxs-lookup"><span data-stu-id="01f2a-108">[in] The maximum number of threads whose IDs can be returned.</span></span>  
  
 <span data-ttu-id="01f2a-109">pcThreadIds</span><span class="sxs-lookup"><span data-stu-id="01f2a-109">pcThreadIds</span></span>  
 <span data-ttu-id="01f2a-110">[出力] `ULONG32` 配列に書き込まれたスレッド ID の実際の数を示す `pThreadIds` へのポインター。</span><span class="sxs-lookup"><span data-stu-id="01f2a-110">[out] A pointer to a `ULONG32` that indicates the actual number of thread IDs written to the `pThreadIds` array.</span></span>  
  
 <span data-ttu-id="01f2a-111">pThreadIDs</span><span class="sxs-lookup"><span data-stu-id="01f2a-111">pThreadIDs</span></span>  
 <span data-ttu-id="01f2a-112">スレッド識別子の配列。</span><span class="sxs-lookup"><span data-stu-id="01f2a-112">An array of thread identifiers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01f2a-113">解説</span><span class="sxs-lookup"><span data-stu-id="01f2a-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="01f2a-114">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="01f2a-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01f2a-115">要件</span><span class="sxs-lookup"><span data-stu-id="01f2a-115">Requirements</span></span>  

 <span data-ttu-id="01f2a-116">**プラットフォーム:** 「 [システム要件](../../get-started/system-requirements.md)」を参照してください。**ヘッダー:** CorDebug .idl、CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="01f2a-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="01f2a-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01f2a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01f2a-118">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01f2a-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01f2a-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="01f2a-119">See also</span></span>

- [<span data-ttu-id="01f2a-120">ICorDebugDataTarget2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="01f2a-120">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="01f2a-121">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="01f2a-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
