---
description: '詳細情報: コードプロバイダー:: GetMethodParameterSymbols メソッド'
title: ICorDebugSymbolProvider::GetMethodParameterSymbols メソッド
ms.date: 03/30/2017
ms.assetid: 58b7c0b9-f6ad-4b49-b92d-0e421cfd0ec6
ms.openlocfilehash: 6ca71c7427f89cf33c5710d26b56590dbea3d2e0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659752"
---
# <a name="icordebugsymbolprovidergetmethodparametersymbols-method"></a><span data-ttu-id="cb338-103">ICorDebugSymbolProvider::GetMethodParameterSymbols メソッド</span><span class="sxs-lookup"><span data-stu-id="cb338-103">ICorDebugSymbolProvider::GetMethodParameterSymbols Method</span></span>

<span data-ttu-id="cb338-104">メソッドの指定の相対仮想アドレス (RVA: relative virtual address ) で、そのメソッドのパラメーター シンボルを取得します。</span><span class="sxs-lookup"><span data-stu-id="cb338-104">Gets a method's parameter symbols given the relative virtual address (RVA) of that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb338-105">構文</span><span class="sxs-lookup"><span data-stu-id="cb338-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodParameterSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb338-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cb338-106">Parameters</span></span>  

 `nativeRVA`  
 <span data-ttu-id="cb338-107">[in] メソッドのネイティブ相対仮想アドレス。</span><span class="sxs-lookup"><span data-stu-id="cb338-107">[in] The native relative virtual address of the method.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="cb338-108">[in] ローカル シンボルの要求数。</span><span class="sxs-lookup"><span data-stu-id="cb338-108">[in] The number of local symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="cb338-109">[out] メソッドによって取得されたシンボル数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="cb338-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="cb338-110">入出力メソッドのローカルシンボルを格納している [ICorDebugVariableSymbol](icordebugvariablesymbol-interface.md) 配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="cb338-110">[out] A pointer to an [ICorDebugVariableSymbol](icordebugvariablesymbol-interface.md) array that contains the method's local symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb338-111">解説</span><span class="sxs-lookup"><span data-stu-id="cb338-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cb338-112">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="cb338-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb338-113">要件</span><span class="sxs-lookup"><span data-stu-id="cb338-113">Requirements</span></span>  

 <span data-ttu-id="cb338-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb338-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb338-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cb338-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cb338-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb338-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb338-117">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb338-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb338-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="cb338-118">See also</span></span>

- [<span data-ttu-id="cb338-119">GetMethodLocalSymbols メソッド</span><span class="sxs-lookup"><span data-stu-id="cb338-119">GetMethodLocalSymbols Method</span></span>](icordebugsymbolprovider-getmethodlocalsymbols-method.md)
- [<span data-ttu-id="cb338-120">ICorDebugSymbolProvider インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cb338-120">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="cb338-121">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="cb338-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
