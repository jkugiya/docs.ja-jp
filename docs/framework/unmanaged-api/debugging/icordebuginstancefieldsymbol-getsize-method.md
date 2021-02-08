---
description: '詳細については、次の情報を参照してください: GetSize メソッド'
title: ICorDebugInstanceFieldSymbol::GetSize メソッド
ms.date: 03/30/2017
ms.assetid: a4af1e3b-6a9f-4855-95ba-5317565c8e2b
ms.openlocfilehash: fa143620b57ec053ab26ff79b7ea2b2f386431e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791154"
---
# <a name="icordebuginstancefieldsymbolgetsize-method"></a><span data-ttu-id="017ea-103">ICorDebugInstanceFieldSymbol::GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="017ea-103">ICorDebugInstanceFieldSymbol::GetSize Method</span></span>

<span data-ttu-id="017ea-104">インスタンス フィールドのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="017ea-104">Gets the size in bytes of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="017ea-105">構文</span><span class="sxs-lookup"><span data-stu-id="017ea-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="017ea-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="017ea-106">Parameters</span></span>  

 `pcbSize`  
 <span data-ttu-id="017ea-107">[out] フィールドの長さへのポインター。</span><span class="sxs-lookup"><span data-stu-id="017ea-107">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="017ea-108">解説</span><span class="sxs-lookup"><span data-stu-id="017ea-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="017ea-109">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="017ea-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="017ea-110">要件</span><span class="sxs-lookup"><span data-stu-id="017ea-110">Requirements</span></span>  

 <span data-ttu-id="017ea-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="017ea-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="017ea-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="017ea-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="017ea-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="017ea-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="017ea-114">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="017ea-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="017ea-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="017ea-115">See also</span></span>

- [<span data-ttu-id="017ea-116">ICorDebugInstanceFieldSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="017ea-116">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="017ea-117">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="017ea-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
