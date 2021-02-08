---
description: '詳細については、次の情報を参照してください: GetOffset メソッド'
title: ICorDebugInstanceFieldSymbol::GetOffset メソッド
ms.date: 03/30/2017
ms.assetid: 7e470150-2b92-4425-989c-315f48964fd2
ms.openlocfilehash: 4a877b2f78adfac5c54694ab306fd7db60f266f0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791167"
---
# <a name="icordebuginstancefieldsymbolgetoffset-method"></a><span data-ttu-id="87686-103">ICorDebugInstanceFieldSymbol::GetOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="87686-103">ICorDebugInstanceFieldSymbol::GetOffset Method</span></span>

<span data-ttu-id="87686-104">このインスタンス フィールドの親クラスにおける、このインスタンス フィールドのオフセット (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="87686-104">Gets the offset in bytes of this instance field in its parent class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87686-105">構文</span><span class="sxs-lookup"><span data-stu-id="87686-105">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
   [out] ULONG32 *pcbOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87686-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="87686-106">Parameters</span></span>  

 `pcbOffset`  
 <span data-ttu-id="87686-107">このインスタンス フィールドの親クラスにおける、このフィールドのオフセットのバイト数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="87686-107">A pointer to the number of bytes that this instance field is offset in its parent class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87686-108">解説</span><span class="sxs-lookup"><span data-stu-id="87686-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="87686-109">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="87686-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87686-110">要件</span><span class="sxs-lookup"><span data-stu-id="87686-110">Requirements</span></span>  

 <span data-ttu-id="87686-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="87686-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87686-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="87686-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="87686-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="87686-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87686-114">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87686-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87686-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="87686-115">See also</span></span>

- [<span data-ttu-id="87686-116">ICorDebugInstanceFieldSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="87686-116">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="87686-117">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="87686-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
