---
description: '詳細については、次の情報を参照してください: GetCodeRange メソッド'
title: ICorDebugSymbolProvider::GetCodeRange メソッド
ms.date: 03/30/2017
ms.assetid: 49a2451f-d250-4e73-aa96-9ff49d9f11c6
ms.openlocfilehash: 98b228be7483e6365815f6b783167b20fb3bcc48
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659908"
---
# <a name="icordebugsymbolprovidergetcoderange-method"></a><span data-ttu-id="a470b-103">ICorDebugSymbolProvider::GetCodeRange メソッド</span><span class="sxs-lookup"><span data-stu-id="a470b-103">ICorDebugSymbolProvider::GetCodeRange Method</span></span>

<span data-ttu-id="a470b-104">メソッド内の指定の相対仮想アドレス (RVA: relative virtual address) で、メソッド開始アドレスとサイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="a470b-104">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a470b-105">構文</span><span class="sxs-lookup"><span data-stu-id="a470b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeRange(  
   [in] ULONG32 codeRva,
   [out] ULONG32* pCodeStartAddress,
   [out] ULONG32* pCodeSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a470b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a470b-106">Parameters</span></span>  

 `codeRva`  
 <span data-ttu-id="a470b-107">[in] メソッド内の相対仮想アドレス (RVA)。</span><span class="sxs-lookup"><span data-stu-id="a470b-107">[in] The relative virtual address (RVA) in a method.</span></span>  
  
 `pCodeStartAddress`  
 <span data-ttu-id="a470b-108">[out] メソッドの開始アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="a470b-108">[out] A pointer to the starting address of the method.</span></span>  
  
 `pCodeSize`  
 <span data-ttu-id="a470b-109">メソッドのコードのサイズ (メソッドのコードのバイト数) へのポインター。</span><span class="sxs-lookup"><span data-stu-id="a470b-109">A pointer to the method code size (the number of bytes of the method's code).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a470b-110">解説</span><span class="sxs-lookup"><span data-stu-id="a470b-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a470b-111">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="a470b-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a470b-112">要件</span><span class="sxs-lookup"><span data-stu-id="a470b-112">Requirements</span></span>  

 <span data-ttu-id="a470b-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a470b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a470b-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a470b-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a470b-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a470b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a470b-116">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a470b-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a470b-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="a470b-117">See also</span></span>

- [<span data-ttu-id="a470b-118">ICorDebugSymbolProvider インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a470b-118">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="a470b-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="a470b-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
