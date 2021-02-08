---
description: '詳細について: ICorDebugAppDomain3:: GetCachedWinRTTypes メソッド'
title: ICorDebugAppDomain3::GetCachedWinRTTypes メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain3.GetCachedWinRTTypes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypes
helpviewer_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypes method [.NET Framework debugging]
- GetCachedWinRTTypes method, ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 9afd0e04-a403-41e2-9528-a6dcbcdcbd4d
topic_type:
- apiref
ms.openlocfilehash: 813fb6c05d5e1e5f119424c6e983b86b3ff5889d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772238"
---
# <a name="icordebugappdomain3getcachedwinrttypes-method"></a><span data-ttu-id="38354-103">ICorDebugAppDomain3::GetCachedWinRTTypes メソッド</span><span class="sxs-lookup"><span data-stu-id="38354-103">ICorDebugAppDomain3::GetCachedWinRTTypes Method</span></span>

<span data-ttu-id="38354-104">キャッシュされているすべての Windows ランタイム型の列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="38354-104">Gets an enumerator for all cached Windows Runtime types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38354-105">構文</span><span class="sxs-lookup"><span data-stu-id="38354-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedWinRTTypes (
    [out] ICorDebugGuidToTypeEnum **ppGuidToTypeEnum)  
;  
```  
  
## <a name="parameters"></a><span data-ttu-id="38354-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="38354-106">Parameters</span></span>  

 `ppGuidToTypeEnum`  
 <span data-ttu-id="38354-107">入出力アプリケーションドメインに現在読み込まれている Windows ランタイム型のマネージ表現を列挙できる、コードの種類が表示され [たインターフェイスオブジェクト](icordebugguidtotypeenum-interface.md) へのポインター。</span><span class="sxs-lookup"><span data-stu-id="38354-107">[out] A pointer to an [ICorDebugGuidToTypeEnum](icordebugguidtotypeenum-interface.md) interface object that can enumerate the managed representations of Windows Runtime types currently loaded in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38354-108">要件</span><span class="sxs-lookup"><span data-stu-id="38354-108">Requirements</span></span>  

 <span data-ttu-id="38354-109">**プラットフォーム:** Windows ランタイム</span><span class="sxs-lookup"><span data-stu-id="38354-109">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="38354-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="38354-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="38354-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38354-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38354-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38354-112">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38354-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="38354-113">See also</span></span>

- [<span data-ttu-id="38354-114">ICorDebugAppDomain3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="38354-114">ICorDebugAppDomain3 Interface</span></span>](icordebugappdomain3-interface.md)
