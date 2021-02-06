---
description: '詳細情報: コードプロバイダー:: GetMethodLocalSymbols メソッド'
title: ICorDebugSymbolProvider::GetMethodLocalSymbols メソッド
ms.date: 03/30/2017
ms.assetid: 8b989e38-e779-49d1-9e90-f1f920484b08
ms.openlocfilehash: f4eaac208d98b25ae4a53acfd977d354c6f6ac1b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659817"
---
# <a name="icordebugsymbolprovidergetmethodlocalsymbols-method"></a><span data-ttu-id="62ade-103">ICorDebugSymbolProvider::GetMethodLocalSymbols メソッド</span><span class="sxs-lookup"><span data-stu-id="62ade-103">ICorDebugSymbolProvider::GetMethodLocalSymbols Method</span></span>

<span data-ttu-id="62ade-104">メソッドの指定の相対仮想アドレス (RVA) で、そのメソッドのローカル シンボルを取得します。</span><span class="sxs-lookup"><span data-stu-id="62ade-104">Gets a method's local symbols given the relative virtual address (RVA) of that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62ade-105">構文</span><span class="sxs-lookup"><span data-stu-id="62ade-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodLocalSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62ade-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="62ade-106">Parameters</span></span>  

 `nativeRVA`  
 <span data-ttu-id="62ade-107">[in] メソッドのネイティブ相対仮想アドレス。</span><span class="sxs-lookup"><span data-stu-id="62ade-107">[in] The native relative virtual address of the method.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="62ade-108">[in] ローカル シンボルの要求数。</span><span class="sxs-lookup"><span data-stu-id="62ade-108">[in] The number of local symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="62ade-109">[out] メソッドによって取得されたシンボル数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="62ade-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="62ade-110">入出力メソッドのローカルシンボルを格納している [ICorDebugVariableSymbol](icordebugvariablesymbol-interface.md) 配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="62ade-110">[out] A pointer to an [ICorDebugVariableSymbol](icordebugvariablesymbol-interface.md) array that contains the method's local symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62ade-111">解説</span><span class="sxs-lookup"><span data-stu-id="62ade-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="62ade-112">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="62ade-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62ade-113">要件</span><span class="sxs-lookup"><span data-stu-id="62ade-113">Requirements</span></span>  

 <span data-ttu-id="62ade-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="62ade-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62ade-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="62ade-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="62ade-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="62ade-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62ade-117">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62ade-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62ade-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="62ade-118">See also</span></span>

- [<span data-ttu-id="62ade-119">GetMethodParameterSymbols メソッド</span><span class="sxs-lookup"><span data-stu-id="62ade-119">GetMethodParameterSymbols Method</span></span>](icordebugsymbolprovider-getmethodparametersymbols-method.md)
- [<span data-ttu-id="62ade-120">ICorDebugSymbolProvider インターフェイス</span><span class="sxs-lookup"><span data-stu-id="62ade-120">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="62ade-121">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="62ade-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
