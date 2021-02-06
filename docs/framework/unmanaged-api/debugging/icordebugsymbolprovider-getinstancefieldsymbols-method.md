---
description: '詳細情報: コードプロバイダー:: GetInstanceFieldSymbols メソッド'
title: ICorDebugSymbolProvider::GetInstanceFieldSymbols メソッド
ms.date: 03/30/2017
ms.assetid: a29b9233-ee67-4b53-b8bc-c00b281e7edb
ms.openlocfilehash: 379d943743bb1fe21edbcca2265b4d8613d4f4b8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659895"
---
# <a name="icordebugsymbolprovidergetinstancefieldsymbols-method"></a><span data-ttu-id="aa2d2-103">ICorDebugSymbolProvider::GetInstanceFieldSymbols メソッド</span><span class="sxs-lookup"><span data-stu-id="aa2d2-103">ICorDebugSymbolProvider::GetInstanceFieldSymbols Method</span></span>

<span data-ttu-id="aa2d2-104">typespec シグネチャに対応するインスタンス フィールド シンボルを取得します。</span><span class="sxs-lookup"><span data-stu-id="aa2d2-104">Gets the instance field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa2d2-105">構文</span><span class="sxs-lookup"><span data-stu-id="aa2d2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInstanceFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugInstanceFieldSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa2d2-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa2d2-106">Parameters</span></span>  

 `cbSignature`  
 <span data-ttu-id="aa2d2-107">[in] `typeSig` 配列のバイト数。</span><span class="sxs-lookup"><span data-stu-id="aa2d2-107">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="aa2d2-108">[in] `typespec` シグネチャを格納するバイト配列。</span><span class="sxs-lookup"><span data-stu-id="aa2d2-108">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="aa2d2-109">[in] 要求されるシンボルの数。</span><span class="sxs-lookup"><span data-stu-id="aa2d2-109">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="aa2d2-110">[out] メソッドによって取得されたシンボル数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa2d2-110">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="aa2d2-111">入出力要求されたインスタンスフィールドシンボルが格納されている、コード例の [シンボル](icordebugstaticfieldsymbol-interface.md) 配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa2d2-111">[out] A pointer to an [ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md) array that contains the requested instance field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aa2d2-112">解説</span><span class="sxs-lookup"><span data-stu-id="aa2d2-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aa2d2-113">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="aa2d2-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa2d2-114">要件</span><span class="sxs-lookup"><span data-stu-id="aa2d2-114">Requirements</span></span>  

 <span data-ttu-id="aa2d2-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aa2d2-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa2d2-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aa2d2-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aa2d2-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aa2d2-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aa2d2-118">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa2d2-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa2d2-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="aa2d2-119">See also</span></span>

- [<span data-ttu-id="aa2d2-120">GetStaticFieldSymbols メソッド</span><span class="sxs-lookup"><span data-stu-id="aa2d2-120">GetStaticFieldSymbols Method</span></span>](icordebugsymbolprovider-getstaticfieldsymbols-method.md)
- [<span data-ttu-id="aa2d2-121">ICorDebugSymbolProvider インターフェイス</span><span class="sxs-lookup"><span data-stu-id="aa2d2-121">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="aa2d2-122">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="aa2d2-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
