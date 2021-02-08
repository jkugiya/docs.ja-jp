---
description: '詳細について: ICorDebugThread4:: HadUnhandledException メソッド'
title: ICorDebugThread4::HadUnhandledException メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.HadUnhandledException Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::HadUnhandledException
helpviewer_keywords:
- ICorDebugThread4::HadUnhandledException method [.NET Framework debugging]
- HadUnhandledException method [.NET Framework debugging]
ms.assetid: 05558daa-39e2-4c38-aeaf-e2aec4a09468
topic_type:
- apiref
ms.openlocfilehash: cd0ccdbdd68c37b5fbdbd705da7136e5d36baa60
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800930"
---
# <a name="icordebugthread4hadunhandledexception-method"></a><span data-ttu-id="8773a-103">ICorDebugThread4::HadUnhandledException メソッド</span><span class="sxs-lookup"><span data-stu-id="8773a-103">ICorDebugThread4::HadUnhandledException Method</span></span>

<span data-ttu-id="8773a-104">スレッドで未処理の例外が発生したかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="8773a-104">Indicates whether the thread has ever had an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8773a-105">構文</span><span class="sxs-lookup"><span data-stu-id="8773a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="8773a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8773a-106">Parameters</span></span>  

 `ppBlockingObjectEnum`  
 <span data-ttu-id="8773a-107">入出力 [CorDebugBlockingObject](cordebugblockingobject-structure.md) 構造体の順序付けられた列挙体のアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8773a-107">[out] A pointer to the address of an ordered enumeration of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8773a-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="8773a-108">Return Value</span></span>  

 <span data-ttu-id="8773a-109">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="8773a-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="8773a-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8773a-110">HRESULT</span></span>|<span data-ttu-id="8773a-111">説明</span><span class="sxs-lookup"><span data-stu-id="8773a-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8773a-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="8773a-112">S_OK</span></span>|<span data-ttu-id="8773a-113">スレッドの作成以降、ハンドルされない例外が発生しました。</span><span class="sxs-lookup"><span data-stu-id="8773a-113">The thread has had an unhandled exception since its creation.</span></span>|  
|<span data-ttu-id="8773a-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="8773a-114">S_FALSE</span></span>|<span data-ttu-id="8773a-115">スレッドでハンドルされない例外が発生していません。</span><span class="sxs-lookup"><span data-stu-id="8773a-115">The thread has never had an unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8773a-116">解説</span><span class="sxs-lookup"><span data-stu-id="8773a-116">Remarks</span></span>  

 <span data-ttu-id="8773a-117">このメソッドは、スレッドにハンドルされない例外が発生したかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="8773a-117">This method indicates whether the thread has ever had an unhandled exception.</span></span> <span data-ttu-id="8773a-118">未処理の例外のコールバックがトリガーされるか、ネイティブ JIT アタッチが開始されるまで、このメソッドは S_OK を返すことが保証されます。</span><span class="sxs-lookup"><span data-stu-id="8773a-118">By the time the unhandled exception callback is triggered or native JIT-attach is initiated, this method is guaranteed to return S_OK.</span></span> <span data-ttu-id="8773a-119">処理不能な例外が返されるという保証はありませ [ん。](icordebugthread-getcurrentexception-method.md) ただし、ハンドルされない例外コールバックを取得した後、またはネイティブ JIT アタッチによってプロセスがまだ続行されていない場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="8773a-119">There is no guarantee that the [ICorDebugThread.GetCurrentException](icordebugthread-getcurrentexception-method.md) method will return the unhandled exception; however, it will if the process has not yet been continued after getting the unhandled exception callback or upon native JIT-attach.</span></span> <span data-ttu-id="8773a-120">また、ネイティブ JIT アタッチがトリガーされたときに、ハンドルされない例外を持つ複数のスレッドを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="8773a-120">Furthermore, it is possible (although unlikely) to have more than one thread with an unhandled exception at the time native JIT-attach is triggered.</span></span> <span data-ttu-id="8773a-121">このような場合は、どの例外が JIT アタッチをトリガーしたかを判断する方法はありません。</span><span class="sxs-lookup"><span data-stu-id="8773a-121">In such a case there is no way to determine which exception triggered the JIT-attach.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8773a-122">要件</span><span class="sxs-lookup"><span data-stu-id="8773a-122">Requirements</span></span>  

 <span data-ttu-id="8773a-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8773a-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8773a-124">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8773a-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8773a-125">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8773a-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8773a-126">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8773a-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8773a-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="8773a-127">See also</span></span>

- [<span data-ttu-id="8773a-128">ICorDebugThread4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8773a-128">ICorDebugThread4 Interface</span></span>](icordebugthread4-interface.md)
- [<span data-ttu-id="8773a-129">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="8773a-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="8773a-130">デバッグ</span><span class="sxs-lookup"><span data-stu-id="8773a-130">Debugging</span></span>](index.md)
