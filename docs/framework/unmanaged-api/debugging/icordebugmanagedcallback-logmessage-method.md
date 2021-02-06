---
description: 詳細については、次を参照
title: ICorDebugManagedCallback::LogMessage メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LogMessage
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LogMessage
helpviewer_keywords:
- ICorDebugManagedCallback::LogMessage method [.NET Framework debugging]
- LogMessage method [.NET Framework debugging]
ms.assetid: d218554a-bf42-4d88-833d-ede30de67a53
topic_type:
- apiref
ms.openlocfilehash: 199f1f5dca7889a62ef351b4a2731fdb360768d3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660519"
---
# <a name="icordebugmanagedcallbacklogmessage-method"></a><span data-ttu-id="d635e-103">ICorDebugManagedCallback::LogMessage メソッド</span><span class="sxs-lookup"><span data-stu-id="d635e-103">ICorDebugManagedCallback::LogMessage Method</span></span>

<span data-ttu-id="d635e-104">共通言語ランタイム (CLR) マネージスレッドが、 <xref:System.Diagnostics.EventLog> イベントを記録するためにクラスのメソッドを呼び出したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="d635e-104">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.EventLog> class to log an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d635e-105">構文</span><span class="sxs-lookup"><span data-stu-id="d635e-105">Syntax</span></span>  
  
```cpp  
HRESULT LogMessage (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pMessage  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d635e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d635e-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="d635e-107">からイベントを記録したマネージスレッドを含むアプリケーションドメインを表す、コードのオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d635e-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that logged the event.</span></span>  
  
 `pThread`  
 <span data-ttu-id="d635e-108">からマネージスレッドを表す、コードスレッドオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d635e-108">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="d635e-109">からイベントログに書き込まれた説明メッセージの重大度レベルを示す、ログ記録 [Levelenum](logginglevelenum-enumeration.md) 列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="d635e-109">[in] A value of the [LoggingLevelEnum](logginglevelenum-enumeration.md) enumeration that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="d635e-110">からトレーススイッチの名前へのポインター。</span><span class="sxs-lookup"><span data-stu-id="d635e-110">[in] A pointer to the name of the tracing switch.</span></span>  
  
 `pMessage`  
 <span data-ttu-id="d635e-111">からイベントログに書き込まれたメッセージへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d635e-111">[in] A pointer to the message that was written to the event log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d635e-112">要件</span><span class="sxs-lookup"><span data-stu-id="d635e-112">Requirements</span></span>  

 <span data-ttu-id="d635e-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d635e-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d635e-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d635e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d635e-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d635e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d635e-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d635e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d635e-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="d635e-117">See also</span></span>

- [<span data-ttu-id="d635e-118">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d635e-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
