---
description: '詳細について: ICorDebugThread4:: GetBlockingObjects メソッド'
title: ICorDebugThread4::GetBlockingObjects メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.GetBlockingObjects Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::GetBlockingObjects
helpviewer_keywords:
- GetBlockingObjects method [.NET Framework debugging]
- ICorDebugThread4::GetBlockingObjects method [.NET Framework debugging]
ms.assetid: a7e6c54e-7be9-4e52-bbb4-95f52458e8e4
topic_type:
- apiref
ms.openlocfilehash: 6a60ebe6f5f6dac93dcb11dad7658aba9c934329
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800956"
---
# <a name="icordebugthread4getblockingobjects-method"></a><span data-ttu-id="29a03-103">ICorDebugThread4::GetBlockingObjects メソッド</span><span class="sxs-lookup"><span data-stu-id="29a03-103">ICorDebugThread4::GetBlockingObjects Method</span></span>

<span data-ttu-id="29a03-104">スレッドブロック情報を提供する [CorDebugBlockingObject](cordebugblockingobject-structure.md) 構造体の順序付けられた列挙体を提供します。</span><span class="sxs-lookup"><span data-stu-id="29a03-104">Provides an ordered enumeration of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29a03-105">構文</span><span class="sxs-lookup"><span data-stu-id="29a03-105">Syntax</span></span>  
  
```cpp  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
```  
  
## <a name="parameters"></a><span data-ttu-id="29a03-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="29a03-106">Parameters</span></span>  

 `ppBlockingObjectEnum`  
 <span data-ttu-id="29a03-107">入出力 [CorDebugBlockingObject](cordebugblockingobject-structure.md) 構造体の順序付けられた列挙体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="29a03-107">[out] A pointer to an ordered enumeration of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29a03-108">解説</span><span class="sxs-lookup"><span data-stu-id="29a03-108">Remarks</span></span>  

 <span data-ttu-id="29a03-109">返された列挙体の最初の要素は、スレッドをブロックしている最初の構造体に対応します。</span><span class="sxs-lookup"><span data-stu-id="29a03-109">The first element in the returned enumeration corresponds to the first structure that is blocking the thread.</span></span> <span data-ttu-id="29a03-110">2番目の要素は、非同期プロシージャ呼び出し (APC) の実行中に検出されるブロッキング項目に対応します。</span><span class="sxs-lookup"><span data-stu-id="29a03-110">The second element corresponds to a blocking item that is encountered while running an asynchronous procedure call (APC) when blocked on the first, and so on.</span></span>  
  
 <span data-ttu-id="29a03-111">列挙は、現在の同期済みの状態の間のみ有効です。</span><span class="sxs-lookup"><span data-stu-id="29a03-111">The enumeration is valid only for the duration of the current synchronized state.</span></span>  
  
 <span data-ttu-id="29a03-112">このメソッドは、デバッグ対象が synchronized 状態のときに呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="29a03-112">This method must be called while the debuggee is in a synchronized state.</span></span>  
  
 <span data-ttu-id="29a03-113">`ppBlockingObjectEnum`が有効なポインターでない場合、結果は未定義になります。</span><span class="sxs-lookup"><span data-stu-id="29a03-113">If `ppBlockingObjectEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="29a03-114">スレッドがブロックされていて、エラーを特定できない場合、メソッドは失敗を示す HRESULT を返します。それ以外の場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="29a03-114">If a thread is blocked and the error cannot be determined, the method returns an HRESULT that indicates failure; otherwise, it returns S_OK.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29a03-115">要件</span><span class="sxs-lookup"><span data-stu-id="29a03-115">Requirements</span></span>  

 <span data-ttu-id="29a03-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="29a03-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29a03-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="29a03-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="29a03-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29a03-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29a03-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29a03-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29a03-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="29a03-120">See also</span></span>

- [<span data-ttu-id="29a03-121">ICorDebugThread4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="29a03-121">ICorDebugThread4 Interface</span></span>](icordebugthread4-interface.md)
- [<span data-ttu-id="29a03-122">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="29a03-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="29a03-123">デバッグ</span><span class="sxs-lookup"><span data-stu-id="29a03-123">Debugging</span></span>](index.md)
