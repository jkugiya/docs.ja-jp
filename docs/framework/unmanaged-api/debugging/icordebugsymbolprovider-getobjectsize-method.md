---
description: 詳細については、次を参照
title: ICorDebugSymbolProvider::GetObjectSize メソッド
ms.date: 03/30/2017
ms.assetid: 3c564396-ac64-4ef3-b4f6-df96f1d46fc7
ms.openlocfilehash: 72720a1af9958fd0ab91276b3967733cec77fee7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659708"
---
# <a name="icordebugsymbolprovidergetobjectsize-method"></a><span data-ttu-id="79c8a-103">ICorDebugSymbolProvider::GetObjectSize メソッド</span><span class="sxs-lookup"><span data-stu-id="79c8a-103">ICorDebugSymbolProvider::GetObjectSize Method</span></span>

<span data-ttu-id="79c8a-104">typespec シグネチャに基づいてオブジェクトのオブジェクト サイズを返します。</span><span class="sxs-lookup"><span data-stu-id="79c8a-104">Returns the object size for an object based on its typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79c8a-105">構文</span><span class="sxs-lookup"><span data-stu-id="79c8a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [out] ULONG32 *pObjectSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79c8a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="79c8a-106">Parameters</span></span>  

 `cbSignature`  
 <span data-ttu-id="79c8a-107">[in] typespec シグネチャのバイト数。</span><span class="sxs-lookup"><span data-stu-id="79c8a-107">[in] The number of bytes in the typespec signature.</span></span>  
  
 <span data-ttu-id="79c8a-108">typeSig</span><span class="sxs-lookup"><span data-stu-id="79c8a-108">typeSig</span></span>  
 <span data-ttu-id="79c8a-109">[in] typespec シグネチャ。</span><span class="sxs-lookup"><span data-stu-id="79c8a-109">[in] The typespec signature.</span></span>  
  
 `pObjectSize`  
 <span data-ttu-id="79c8a-110">[out] オブジェクトのサイズへのポインター。</span><span class="sxs-lookup"><span data-stu-id="79c8a-110">[out] A pointer to the size of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79c8a-111">解説</span><span class="sxs-lookup"><span data-stu-id="79c8a-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="79c8a-112">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="79c8a-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79c8a-113">要件</span><span class="sxs-lookup"><span data-stu-id="79c8a-113">Requirements</span></span>  

 <span data-ttu-id="79c8a-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="79c8a-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79c8a-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="79c8a-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="79c8a-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="79c8a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79c8a-117">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79c8a-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79c8a-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="79c8a-118">See also</span></span>

- [<span data-ttu-id="79c8a-119">ICorDebugSymbolProvider インターフェイス</span><span class="sxs-lookup"><span data-stu-id="79c8a-119">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="79c8a-120">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="79c8a-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
