---
description: '詳細については、次を参照してください: いいね。'
title: ICorDebugGuidToTypeEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugGuidToTypeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGuidToTypeEnum
helpviewer_keywords:
- ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: aa32b12b-05fc-4ea8-a904-adae25034269
topic_type:
- apiref
ms.openlocfilehash: abcdc9537f6f6ff2e0ac9b2be86734efbf303493
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660987"
---
# <a name="icordebugguidtotypeenum-interface"></a><span data-ttu-id="7acc2-103">ICorDebugGuidToTypeEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7acc2-103">ICorDebugGuidToTypeEnum Interface</span></span>

<span data-ttu-id="7acc2-104">整数のセットとそれに対応する型の間のマッピングを定義する列挙子を提供します。これは、テキストインスタンスによって表されます。</span><span class="sxs-lookup"><span data-stu-id="7acc2-104">Provides an enumerator that defines the mapping between a set of GUIDs and their corresponding types, which are represented by ICorDebugType instances.</span></span> <span data-ttu-id="7acc2-105">このインターフェイスは、ICorDebugEnum インターフェイスからメソッドを継承します。</span><span class="sxs-lookup"><span data-stu-id="7acc2-105">This interface inherits the methods from the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7acc2-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="7acc2-106">Methods</span></span>  
  
|<span data-ttu-id="7acc2-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="7acc2-107">Method</span></span>|<span data-ttu-id="7acc2-108">説明</span><span class="sxs-lookup"><span data-stu-id="7acc2-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7acc2-109">いいね Totypeenum:: Next</span><span class="sxs-lookup"><span data-stu-id="7acc2-109">ICorDebugGuidToTypeEnum::Next</span></span>](icordebugguidtotypeenum-next-method.md)|<span data-ttu-id="7acc2-110">Guid を型情報にマップする、指定された数の [Cordebugguidtotypemapping](cordebugguidtotypemapping-structure.md) インスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="7acc2-110">Gets the specified number of [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7acc2-111">解説</span><span class="sxs-lookup"><span data-stu-id="7acc2-111">Remarks</span></span>  

 <span data-ttu-id="7acc2-112">`ICorDebugGuidToTypeEnum`インターフェイスオブジェクトは、 [ICorDebugAppDomain3:: GetCachedWinRTTypes](icordebugappdomain3-getcachedwinrttypes-method.md)メソッドを呼び出すことによって取得できます。</span><span class="sxs-lookup"><span data-stu-id="7acc2-112">An `ICorDebugGuidToTypeEnum` interface object can be retrieved by calling the [ICorDebugAppDomain3::GetCachedWinRTTypes](icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span> <span data-ttu-id="7acc2-113">デバッガーは、このインターフェイスの[Next](icordebugguidtotypeenum-next-method.md)メソッドを呼び出して、 [ICorDebugAppDomain3:: GetCachedWinRTTypes](icordebugappdomain3-getcachedwinrttypes-method.md)メソッドの呼び出しに使用されるアプリケーションドメインに読み込まれた Windows ランタイム型のマネージ表現のマッピングを表す[cordebugguidtotypemapping](cordebugguidtotypemapping-structure.md)オブジェクトを取得できます。</span><span class="sxs-lookup"><span data-stu-id="7acc2-113">A debugger can call this interface's [Next](icordebugguidtotypeenum-next-method.md) method to retrieve [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) objects that represent mappings of managed representations of Windows Runtime types loaded in the application domain used for the call to the [ICorDebugAppDomain3::GetCachedWinRTTypes](icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7acc2-114">要件</span><span class="sxs-lookup"><span data-stu-id="7acc2-114">Requirements</span></span>  

 <span data-ttu-id="7acc2-115">**プラットフォーム:** Windows ランタイム</span><span class="sxs-lookup"><span data-stu-id="7acc2-115">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="7acc2-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7acc2-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7acc2-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7acc2-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7acc2-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7acc2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7acc2-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="7acc2-119">See also</span></span>

- [<span data-ttu-id="7acc2-120">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="7acc2-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
