---
description: '詳細については、次の情報を参照してください: GetAssemblyImageMetadata メソッド'
title: ICorDebugSymbolProvider::GetAssemblyImageMetadata メソッド
ms.date: 03/30/2017
ms.assetid: c3c9de67-b865-4ecf-b887-1f1d0719a0c0
ms.openlocfilehash: 4abe5cc2b2a31f89e6ca4f8fc643f26eac276515
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717187"
---
# <a name="icordebugsymbolprovidergetassemblyimagemetadata-method"></a><span data-ttu-id="add75-103">ICorDebugSymbolProvider::GetAssemblyImageMetadata メソッド</span><span class="sxs-lookup"><span data-stu-id="add75-103">ICorDebugSymbolProvider::GetAssemblyImageMetadata Method</span></span>

<span data-ttu-id="add75-104">マージされたアセンブリのメタデータを返します。</span><span class="sxs-lookup"><span data-stu-id="add75-104">Returns the metadata from a merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="add75-105">構文</span><span class="sxs-lookup"><span data-stu-id="add75-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyImageMetadata(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="add75-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="add75-106">Parameters</span></span>  

 `ppMemoryBuffer`  
 <span data-ttu-id="add75-107">入出力マージされたアセンブリのメタデータのサイズとアドレスに関する情報を格納して [いる、のオブジェクトの](icordebugmemorybuffer-interface.md) アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="add75-107">[out] A pointer to the address of an [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) object that contains information about the size and address of the merged assembly's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="add75-108">解説</span><span class="sxs-lookup"><span data-stu-id="add75-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="add75-109">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="add75-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="add75-110">要件</span><span class="sxs-lookup"><span data-stu-id="add75-110">Requirements</span></span>  

 <span data-ttu-id="add75-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="add75-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="add75-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="add75-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="add75-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="add75-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="add75-114">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="add75-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="add75-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="add75-115">See also</span></span>

- [<span data-ttu-id="add75-116">ICorDebugSymbolProvider インターフェイス</span><span class="sxs-lookup"><span data-stu-id="add75-116">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="add75-117">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="add75-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
