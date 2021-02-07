---
description: '詳細については、次の情報を参照してください: GetAssemblyImageBytes メソッド'
title: ICorDebugSymbolProvider::GetAssemblyImageBytes メソッド
ms.date: 03/30/2017
ms.assetid: 3db215aa-e180-4f70-8d23-6d5a0ffbc8e5
ms.openlocfilehash: 2e08b23e35913e8767135d75d28ff66efc890565
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717278"
---
# <a name="icordebugsymbolprovidergetassemblyimagebytes-method"></a><span data-ttu-id="ca0ad-103">ICorDebugSymbolProvider::GetAssemblyImageBytes メソッド</span><span class="sxs-lookup"><span data-stu-id="ca0ad-103">ICorDebugSymbolProvider::GetAssemblyImageBytes Method</span></span>

<span data-ttu-id="ca0ad-104">マージされたアセンブリ内の指定の相対仮想アドレス (RVA: relative virtual address) で、マージされたアセンブリのデータを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="ca0ad-104">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca0ad-105">構文</span><span class="sxs-lookup"><span data-stu-id="ca0ad-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyImageBytes(  
   [in] CORDB_ADDRESS rva,
   [in] ULONG32 length,
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca0ad-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ca0ad-106">Parameters</span></span>  

 `rva`  
 <span data-ttu-id="ca0ad-107">[in] マージされたアセンブリ内の相対仮想アドレス (RVA)。</span><span class="sxs-lookup"><span data-stu-id="ca0ad-107">[in] A relative virtual address (RVA) in a merged assembly.</span></span>  
  
 `length`  
 <span data-ttu-id="ca0ad-108">マージされたアセンブリから読み取るバイト数。</span><span class="sxs-lookup"><span data-stu-id="ca0ad-108">The number of bytes to read from the merged assembly.</span></span>  
  
 `ppMemoryBuffer`  
 <span data-ttu-id="ca0ad-109">マージされたアセンブリメタデータを持つメモリバッファーに関する情報を格納している、 [のオブジェクトの](icordebugmemorybuffer-interface.md) アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ca0ad-109">A pointer to the address of an [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) object that contains information about the memory buffer with merged assembly metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca0ad-110">解説</span><span class="sxs-lookup"><span data-stu-id="ca0ad-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ca0ad-111">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="ca0ad-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca0ad-112">要件</span><span class="sxs-lookup"><span data-stu-id="ca0ad-112">Requirements</span></span>  

 <span data-ttu-id="ca0ad-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ca0ad-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca0ad-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ca0ad-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ca0ad-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ca0ad-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca0ad-116">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca0ad-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca0ad-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="ca0ad-117">See also</span></span>

- [<span data-ttu-id="ca0ad-118">ICorDebugSymbolProvider インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ca0ad-118">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="ca0ad-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="ca0ad-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
