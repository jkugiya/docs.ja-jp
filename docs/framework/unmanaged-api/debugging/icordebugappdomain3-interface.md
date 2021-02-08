---
description: 詳細については、「ICorDebugAppDomain3 インターフェイス」を参照してください。
title: ICorDebugAppDomain3 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3
helpviewer_keywords:
- ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 875ef5be-c1e7-4d95-97e9-d3a667aeaba0
topic_type:
- apiref
ms.openlocfilehash: 6575aa685759102443babeaf82774e6221b80693
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772212"
---
# <a name="icordebugappdomain3-interface"></a><span data-ttu-id="48d46-103">ICorDebugAppDomain3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="48d46-103">ICorDebugAppDomain3 Interface</span></span>

<span data-ttu-id="48d46-104">アプリケーションドメインに現在読み込まれている Windows ランタイム型のマネージ表現に関する情報を取得するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="48d46-104">Provides methods to retrieve information about the managed representations of Windows Runtime types currently loaded in an application domain.</span></span> <span data-ttu-id="48d46-105">このインターフェイスは、"ICorDebugAppDomain2" というインターフェイスを拡張したものです。</span><span class="sxs-lookup"><span data-stu-id="48d46-105">This interface is an extension of the ICorDebugAppDomain and ICorDebugAppDomain2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="48d46-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="48d46-106">Methods</span></span>  
  
|<span data-ttu-id="48d46-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="48d46-107">Method</span></span>|<span data-ttu-id="48d46-108">説明</span><span class="sxs-lookup"><span data-stu-id="48d46-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="48d46-109">ICorDebugAppDomain3:: GetCachedWinRTTypes</span><span class="sxs-lookup"><span data-stu-id="48d46-109">ICorDebugAppDomain3::GetCachedWinRTTypes</span></span>](icordebugappdomain3-getcachedwinrttypes-method.md)|<span data-ttu-id="48d46-110">キャッシュされているすべての Windows ランタイム型の列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="48d46-110">Gets an enumerator for all cached Windows Runtime types.</span></span>|  
|[<span data-ttu-id="48d46-111">ICorDebugAppDomain3:: GetCachedWinRTTypesForIIDs</span><span class="sxs-lookup"><span data-stu-id="48d46-111">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span></span>](icordebugappdomain3-getcachedwinrttypesforiids-method.md)|<span data-ttu-id="48d46-112">インターフェイス識別子に基づいて、アプリケーションドメイン内のキャッシュされた Windows ランタイム型の列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="48d46-112">Gets an enumerator for cached Windows Runtime types in an application domain based on their interface identifiers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48d46-113">解説</span><span class="sxs-lookup"><span data-stu-id="48d46-113">Remarks</span></span>  

 <span data-ttu-id="48d46-114">このインターフェイスは、デバッガーがの関数評価呼び出しと共に使用することを意図 `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)` しています。</span><span class="sxs-lookup"><span data-stu-id="48d46-114">This interface is meant to be used by a debugger in conjunction with a function evaluation call to `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`.</span></span> <span data-ttu-id="48d46-115">メソッドが Windows ランタイムサーバーオブジェクトでサポートされているインターフェイス識別子を取得すると、デバッガーはこのインターフェイスで定義されているメソッドを使用して、これらのインターフェイスに対応するマネージ型にマップすることができます。</span><span class="sxs-lookup"><span data-stu-id="48d46-115">When the method retrieves the interface identifiers supported by a Windows Runtime server object, the debugger may use the methods defined in this interface to map them to managed types that correspond to those interfaces.</span></span>  
  
 <span data-ttu-id="48d46-116">このインターフェイスのインスタンスを取得するには、の `QueryInterface` インスタンス上でを実行します。または、ICorDebugAppDomain2 インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="48d46-116">To retrieve an instance of this interface, run `QueryInterface` on an instance of the ICorDebugAppDomain or ICorDebugAppDomain2 interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="48d46-117">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="48d46-117">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48d46-118">要件</span><span class="sxs-lookup"><span data-stu-id="48d46-118">Requirements</span></span>  

 <span data-ttu-id="48d46-119">**プラットフォーム:** Windows ランタイム</span><span class="sxs-lookup"><span data-stu-id="48d46-119">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="48d46-120">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="48d46-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="48d46-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48d46-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48d46-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48d46-122">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48d46-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="48d46-123">See also</span></span>

- [<span data-ttu-id="48d46-124">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="48d46-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
