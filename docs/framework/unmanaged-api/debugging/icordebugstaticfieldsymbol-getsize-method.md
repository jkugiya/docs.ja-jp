---
description: '詳細については、次の情報を参照してください: GetSize メソッド'
title: ICorDebugStaticFieldSymbol::GetSize メソッド
ms.date: 03/30/2017
ms.assetid: 72389860-7e37-4656-ba46-b6aeee1860f8
ms.openlocfilehash: f6fd2fe60d7cb8a77dcff5ca259d05ae1ef195ed
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794690"
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a><span data-ttu-id="a7f6d-103">ICorDebugStaticFieldSymbol::GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="a7f6d-103">ICorDebugStaticFieldSymbol::GetSize Method</span></span>

<span data-ttu-id="a7f6d-104">静的フィールドのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="a7f6d-104">Gets the size in bytes of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7f6d-105">構文</span><span class="sxs-lookup"><span data-stu-id="a7f6d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7f6d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a7f6d-106">Parameters</span></span>  

 `pcbSize`  
 <span data-ttu-id="a7f6d-107">[out] フィールドの長さへのポインター。</span><span class="sxs-lookup"><span data-stu-id="a7f6d-107">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7f6d-108">解説</span><span class="sxs-lookup"><span data-stu-id="a7f6d-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a7f6d-109">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="a7f6d-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7f6d-110">要件</span><span class="sxs-lookup"><span data-stu-id="a7f6d-110">Requirements</span></span>  

 <span data-ttu-id="a7f6d-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a7f6d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7f6d-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a7f6d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a7f6d-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a7f6d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7f6d-114">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7f6d-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7f6d-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="a7f6d-115">See also</span></span>

- [<span data-ttu-id="a7f6d-116">ICorDebugStaticFieldSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a7f6d-116">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="a7f6d-117">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="a7f6d-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
