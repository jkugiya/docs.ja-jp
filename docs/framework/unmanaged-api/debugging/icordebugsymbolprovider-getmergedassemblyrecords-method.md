---
description: '詳細については、次の情報を参照してください: GetMergedAssemblyRecords メソッド'
title: ICorDebugSymbolProvider::GetMergedAssemblyRecords メソッド
ms.date: 03/30/2017
ms.assetid: cc4c510d-550d-4941-af34-81987caf3425
ms.openlocfilehash: f12bb3a49d7b49f9f8916c9d04417340502d44ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659882"
---
# <a name="icordebugsymbolprovidergetmergedassemblyrecords-method"></a><span data-ttu-id="b4372-103">ICorDebugSymbolProvider::GetMergedAssemblyRecords メソッド</span><span class="sxs-lookup"><span data-stu-id="b4372-103">ICorDebugSymbolProvider::GetMergedAssemblyRecords Method</span></span>

<span data-ttu-id="b4372-104">すべてのマージされたアセンブリのシンボル レコードを取得します。</span><span class="sxs-lookup"><span data-stu-id="b4372-104">Gets the symbol records for all the merged assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4372-105">構文</span><span class="sxs-lookup"><span data-stu-id="b4372-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMergedAssemblyRecords(  
   [in] ULONG32 cRequestedRecords,  
   [out] ULONG32 *pcFetchedRecords,  
   [out, size_is(cRequestedRecords), length_is(*pcFetchedRecords)] ICorDebugMergedAssemblyRecord *pRecords[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4372-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b4372-106">Parameters</span></span>  

 `cRequestedRecords`  
 <span data-ttu-id="b4372-107">[in] 要求されるシンボル レコードの数。</span><span class="sxs-lookup"><span data-stu-id="b4372-107">[in] The number of symbol records requested.</span></span>  
  
 `pcFetchedRecords`  
 <span data-ttu-id="b4372-108">[out] メソッドによって取得されたシンボル レコード数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="b4372-108">[out] A pointer to the number of symbol records retrieved by the method.</span></span>  
  
 `pRecords`  
 <span data-ttu-id="b4372-109">[ICorDebugMergedAssemblyRecord](icordebugmergedassemblyrecord-interface.md)オブジェクトの配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="b4372-109">A pointer to an array of [ICorDebugMergedAssemblyRecord](icordebugmergedassemblyrecord-interface.md) objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4372-110">解説</span><span class="sxs-lookup"><span data-stu-id="b4372-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b4372-111">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="b4372-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4372-112">要件</span><span class="sxs-lookup"><span data-stu-id="b4372-112">Requirements</span></span>  

 <span data-ttu-id="b4372-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b4372-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4372-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b4372-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b4372-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4372-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4372-116">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4372-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4372-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="b4372-117">See also</span></span>

- [<span data-ttu-id="b4372-118">ICorDebugSymbolProvider インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b4372-118">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="b4372-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="b4372-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
