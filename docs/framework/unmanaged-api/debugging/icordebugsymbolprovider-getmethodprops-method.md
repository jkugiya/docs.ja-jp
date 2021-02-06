---
description: 詳細については、次の説明
title: ICorDebugSymbolProvider::GetMethodProps メソッド
ms.date: 03/30/2017
ms.assetid: 8f836b80-b7a5-460b-bf76-5f0e45652aea
ms.openlocfilehash: 53a329426ecadfe5559c0e6a08ffbd250163e177
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659726"
---
# <a name="icordebugsymbolprovidergetmethodprops-method"></a><span data-ttu-id="1e63d-103">ICorDebugSymbolProvider::GetMethodProps メソッド</span><span class="sxs-lookup"><span data-stu-id="1e63d-103">ICorDebugSymbolProvider::GetMethodProps Method</span></span>

<span data-ttu-id="1e63d-104">メソッドの指定の相対仮想アドレス (RVA) で、そのメソッドのプロパティに関する情報 (メソッドのメタデータ トークンなど) と、そのジェネリック パラメーターに関する情報を返します。</span><span class="sxs-lookup"><span data-stu-id="1e63d-104">Returns information about method properties, such as the method's metadata token and information about its generic parameters, given a relative virtual address (RVA) in that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e63d-105">構文</span><span class="sxs-lookup"><span data-stu-id="1e63d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodProps(  
   [in]  ULONG32 codeRva,  
   [out] mdToken *pMethodToken,  
   [out] ULONG32 *pcGenericParams,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e63d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e63d-106">Parameters</span></span>  

 `codeRVA`  
 <span data-ttu-id="1e63d-107">[in]情報を取得するメソッドでの相対仮想アドレス。</span><span class="sxs-lookup"><span data-stu-id="1e63d-107">[in] A relative virtual address in the method about which information is to be retrieved.</span></span>  
  
 `pMethodToken`  
 <span data-ttu-id="1e63d-108">[out] メソッドのメタデータ トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e63d-108">[out] A pointer to the method's metadata token.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="1e63d-109">[out] このメソッドに関連付けられているジェネリック パラメーターの数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e63d-109">[out] A pointer to the number of generic parameters associated with this method.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="1e63d-110">[in] `signature` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="1e63d-110">[in] The size of the `signature` array.</span></span> <span data-ttu-id="1e63d-111">「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1e63d-111">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="1e63d-112">[out] 返される `signature` 配列のサイズへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e63d-112">[out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="1e63d-113">[out] すべてのジェネリック パラメーターの typespec シグネチャを保持するバッファー。</span><span class="sxs-lookup"><span data-stu-id="1e63d-113">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e63d-114">解説</span><span class="sxs-lookup"><span data-stu-id="1e63d-114">Remarks</span></span>  

 <span data-ttu-id="1e63d-115">メソッドの配列の必要なサイズを取得するには `signature` 、 `cbSignature` 引数を0に設定し、 `signature` を **null** に設定します。</span><span class="sxs-lookup"><span data-stu-id="1e63d-115">To get the required size of the method's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="1e63d-116">このメソッドから制御が戻ると、`pcbSignature` には `signature` 配列の必要なバイト数が格納されます。</span><span class="sxs-lookup"><span data-stu-id="1e63d-116">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1e63d-117">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="1e63d-117">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e63d-118">要件</span><span class="sxs-lookup"><span data-stu-id="1e63d-118">Requirements</span></span>  

 <span data-ttu-id="1e63d-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1e63d-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e63d-120">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1e63d-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1e63d-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1e63d-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1e63d-122">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e63d-122">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e63d-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="1e63d-123">See also</span></span>

- [<span data-ttu-id="1e63d-124">GetTypeProps メソッド</span><span class="sxs-lookup"><span data-stu-id="1e63d-124">GetTypeProps Method</span></span>](icordebugsymbolprovider-gettypeprops-method.md)
- [<span data-ttu-id="1e63d-125">ICorDebugSymbolProvider インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1e63d-125">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="1e63d-126">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="1e63d-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
