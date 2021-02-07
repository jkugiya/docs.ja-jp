---
description: '詳細情報: ICorDebugManagedCallback3:: CustomNotification メソッド'
title: ICorDebugManagedCallback3::CustomNotification メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback3.CustomNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback3::CustomNotification
helpviewer_keywords:
- ICorDebugManagedCallback3::CustomNotification method [.NET Framework debugging]
- CustomNotification method [.NET Framework debugging]
ms.assetid: 5e5422ac-afa1-403d-a894-2d7348673e38
topic_type:
- apiref
ms.openlocfilehash: 18210e9c65afa0655374fb038d30516cfed02052
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691719"
---
# <a name="icordebugmanagedcallback3customnotification-method"></a><span data-ttu-id="a5f9b-103">ICorDebugManagedCallback3::CustomNotification メソッド</span><span class="sxs-lookup"><span data-stu-id="a5f9b-103">ICorDebugManagedCallback3::CustomNotification Method</span></span>

<span data-ttu-id="a5f9b-104">カスタムデバッガー通知が発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="a5f9b-104">Indicates that a custom debugger notification has been raised.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5f9b-105">構文</span><span class="sxs-lookup"><span data-stu-id="a5f9b-105">Syntax</span></span>  
  
```cpp  
HRESULT CustomNotification(ICorDebugThread *    pThread,  
                           ICorDebugAppDomain * pAppDomain);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5f9b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a5f9b-106">Parameters</span></span>  

 `pThread`  
 <span data-ttu-id="a5f9b-107">から通知を発生させたスレッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="a5f9b-107">[in] A pointer to the thread that raised the notification.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="a5f9b-108">から通知を発生させたスレッドを含むアプリケーションドメインへのポインター。</span><span class="sxs-lookup"><span data-stu-id="a5f9b-108">[in] A pointer to the application domain that contains the thread that raised the notification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a5f9b-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="a5f9b-109">Return Value</span></span>  

 <span data-ttu-id="a5f9b-110">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="a5f9b-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a5f9b-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a5f9b-111">HRESULT</span></span>|<span data-ttu-id="a5f9b-112">説明</span><span class="sxs-lookup"><span data-stu-id="a5f9b-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a5f9b-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="a5f9b-113">S_OK</span></span>|<span data-ttu-id="a5f9b-114">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="a5f9b-114">The method completed successfully.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="a5f9b-115">例外</span><span class="sxs-lookup"><span data-stu-id="a5f9b-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5f9b-116">解説</span><span class="sxs-lookup"><span data-stu-id="a5f9b-116">Remarks</span></span>  

 <span data-ttu-id="a5f9b-117">後続の [ICorDebugThread4:: Getcurrentcustomデバッガ通知](icordebugthread4-getcurrentcustomdebuggernotification-method.md) メソッドの呼び出しでは、メソッドに渡されたスレッドオブジェクトを取得し <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="a5f9b-117">A subsequent call to the [ICorDebugThread4::GetCurrentCustomDebuggerNotification](icordebugthread4-getcurrentcustomdebuggernotification-method.md) method retrieves the thread object that was passed to the <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a5f9b-118">スレッドオブジェクトの型は、 [ICorDebugProcess3:: SetEnableCustomNotification](icordebugprocess3-setenablecustomnotification-method.md) メソッドを呼び出すことによって既に有効になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5f9b-118">The thread object's type must have been previously enabled by calling the [ICorDebugProcess3::SetEnableCustomNotification](icordebugprocess3-setenablecustomnotification-method.md) method.</span></span> <span data-ttu-id="a5f9b-119">デバッガーは、スレッドオブジェクトのフィールドから型固有のパラメーターを読み取ることができ、応答をフィールドに格納できます。</span><span class="sxs-lookup"><span data-stu-id="a5f9b-119">The debugger can read type-specific parameters from the fields of the thread object, and can store responses into fields.</span></span>  
  
 <span data-ttu-id="a5f9b-120">[ICorDebug](icordebug-interface.md)インターフェイスでは、通知の種類やその内容にポリシーは適用されません。また、通知のセマンティクスは、厳密にはデバッガー、アプリケーション、および .NET Framework 間のコントラクトになります。</span><span class="sxs-lookup"><span data-stu-id="a5f9b-120">The [ICorDebug](icordebug-interface.md) interface imposes no policy on the types of notifications or their contents, and the semantics of the notifications are strictly a contract between debuggers, applications, and the .NET Framework.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5f9b-121">要件</span><span class="sxs-lookup"><span data-stu-id="a5f9b-121">Requirements</span></span>  

 <span data-ttu-id="a5f9b-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5f9b-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5f9b-123">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a5f9b-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a5f9b-124">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5f9b-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5f9b-125">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5f9b-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5f9b-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="a5f9b-126">See also</span></span>

- [<span data-ttu-id="a5f9b-127">ICorDebugManagedCallback3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a5f9b-127">ICorDebugManagedCallback3 Interface</span></span>](icordebugmanagedcallback3-interface.md)
- [<span data-ttu-id="a5f9b-128">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="a5f9b-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="a5f9b-129">デバッグ</span><span class="sxs-lookup"><span data-stu-id="a5f9b-129">Debugging</span></span>](index.md)
