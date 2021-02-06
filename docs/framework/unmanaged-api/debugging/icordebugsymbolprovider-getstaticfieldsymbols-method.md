---
description: '詳細情報: コードプロバイダー:: GetStaticFieldSymbols メソッド'
title: ICorDebugSymbolProvider::GetStaticFieldSymbols メソッド
ms.date: 03/30/2017
ms.assetid: b178367f-a6e4-413c-b06f-daf3804b456b
ms.openlocfilehash: e95f77be86ef88a73ca4c833b242617a0d405e21
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659707"
---
# <a name="icordebugsymbolprovidergetstaticfieldsymbols-method"></a><span data-ttu-id="9af9a-103">ICorDebugSymbolProvider::GetStaticFieldSymbols メソッド</span><span class="sxs-lookup"><span data-stu-id="9af9a-103">ICorDebugSymbolProvider::GetStaticFieldSymbols Method</span></span>

<span data-ttu-id="9af9a-104">typespec シグネチャに対応する静的フィールド シンボルを取得します。</span><span class="sxs-lookup"><span data-stu-id="9af9a-104">Gets the static field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9af9a-105">構文</span><span class="sxs-lookup"><span data-stu-id="9af9a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugStaticFieldSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9af9a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9af9a-106">Parameters</span></span>  

 `cbSignature`  
 <span data-ttu-id="9af9a-107">[in] `typeSig` 配列のバイト数。</span><span class="sxs-lookup"><span data-stu-id="9af9a-107">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="9af9a-108">[in] `typespec` シグネチャを格納するバイト配列。</span><span class="sxs-lookup"><span data-stu-id="9af9a-108">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="9af9a-109">[in] 要求されるシンボルの数。</span><span class="sxs-lookup"><span data-stu-id="9af9a-109">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="9af9a-110">[out] メソッドによって取得されたシンボル数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="9af9a-110">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="9af9a-111">入出力要求された静的なフィールドシンボルが格納されている、表示名のある [シンボル](icordebugstaticfieldsymbol-interface.md) 配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="9af9a-111">[out] A pointer to an [ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md) array that contains the requested static field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9af9a-112">解説</span><span class="sxs-lookup"><span data-stu-id="9af9a-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9af9a-113">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="9af9a-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9af9a-114">要件</span><span class="sxs-lookup"><span data-stu-id="9af9a-114">Requirements</span></span>  

 <span data-ttu-id="9af9a-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9af9a-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9af9a-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9af9a-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9af9a-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9af9a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9af9a-118">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9af9a-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9af9a-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="9af9a-119">See also</span></span>

- [<span data-ttu-id="9af9a-120">GetInstanceFieldSymbols メソッド</span><span class="sxs-lookup"><span data-stu-id="9af9a-120">GetInstanceFieldSymbols Method</span></span>](icordebugsymbolprovider-getinstancefieldsymbols-method.md)
- [<span data-ttu-id="9af9a-121">ICorDebugSymbolProvider インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9af9a-121">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="9af9a-122">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="9af9a-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
