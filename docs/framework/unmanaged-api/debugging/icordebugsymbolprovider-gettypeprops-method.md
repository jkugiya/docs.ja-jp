---
description: 詳細については、次の説明
title: ICorDebugSymbolProvider::GetTypeProps メソッド
ms.date: 03/30/2017
ms.assetid: 35ac4140-91ea-4c77-b1c4-1daf41986ca5
ms.openlocfilehash: b6a4a5a68e1e377fa839940832dfc49574009641
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659661"
---
# <a name="icordebugsymbolprovidergettypeprops-method"></a><span data-ttu-id="41d22-103">ICorDebugSymbolProvider::GetTypeProps メソッド</span><span class="sxs-lookup"><span data-stu-id="41d22-103">ICorDebugSymbolProvider::GetTypeProps Method</span></span>

<span data-ttu-id="41d22-104">Vtable の指定の相対仮想アドレス (RVA) における、ジェネリック パラメーターのシグネチャの数などの型のプロパティに関する情報を返します。</span><span class="sxs-lookup"><span data-stu-id="41d22-104">Returns information about a type's properties, such as the number of signature of its generic parameters, given a relative virtual address (RVA) in a vtable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41d22-105">構文</span><span class="sxs-lookup"><span data-stu-id="41d22-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeProps(  
   [in]  ULONG32 vtableRva,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41d22-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="41d22-106">Parameters</span></span>  

 `tableRva`  
 <span data-ttu-id="41d22-107">[in] vtable の相対仮想アドレス (RVA)。</span><span class="sxs-lookup"><span data-stu-id="41d22-107">[in] A relative virtual address (RVA) in a vtable.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="41d22-108">[in] `signature` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="41d22-108">[in] The size of the `signature` array.</span></span> <span data-ttu-id="41d22-109">「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="41d22-109">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="41d22-110">[out] [out] 返される `signature` 配列のサイズへのポインター。</span><span class="sxs-lookup"><span data-stu-id="41d22-110">[out] [out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="41d22-111">[out] すべてのジェネリック パラメーターの typespec シグネチャを保持するバッファー。</span><span class="sxs-lookup"><span data-stu-id="41d22-111">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41d22-112">解説</span><span class="sxs-lookup"><span data-stu-id="41d22-112">Remarks</span></span>  

 <span data-ttu-id="41d22-113">型の配列の必要なサイズを取得するには `signature` 、 `cbSignature` 引数を0に設定し、 `signature` を **null** に設定します。</span><span class="sxs-lookup"><span data-stu-id="41d22-113">To get the required size of the type's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="41d22-114">このメソッドから制御が戻ると、`pcbSignature` には `signature` 配列の必要なバイト数が格納されます。</span><span class="sxs-lookup"><span data-stu-id="41d22-114">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="41d22-115">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="41d22-115">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41d22-116">要件</span><span class="sxs-lookup"><span data-stu-id="41d22-116">Requirements</span></span>  

 <span data-ttu-id="41d22-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="41d22-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41d22-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="41d22-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="41d22-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="41d22-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41d22-120">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41d22-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41d22-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="41d22-121">See also</span></span>

- [<span data-ttu-id="41d22-122">GetMethodProps メソッド</span><span class="sxs-lookup"><span data-stu-id="41d22-122">GetMethodProps Method</span></span>](icordebugsymbolprovider-getmethodprops-method.md)
- [<span data-ttu-id="41d22-123">ICorDebugSymbolProvider インターフェイス</span><span class="sxs-lookup"><span data-stu-id="41d22-123">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="41d22-124">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="41d22-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
