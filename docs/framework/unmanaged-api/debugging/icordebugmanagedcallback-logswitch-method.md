---
description: 詳細については、次を参照
title: ICorDebugManagedCallback::LogSwitch メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LogSwitch
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LogSwitch
helpviewer_keywords:
- LogSwitch method [.NET Framework debugging]
- ICorDebugManagedCallback::LogSwitch method [.NET Framework debugging]
ms.assetid: 0ac59d27-783f-4a87-b7a8-baa3ccc54582
topic_type:
- apiref
ms.openlocfilehash: 658b2afbe7074062910670c6748dc579973715f8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660467"
---
# <a name="icordebugmanagedcallbacklogswitch-method"></a><span data-ttu-id="09855-103">ICorDebugManagedCallback::LogSwitch メソッド</span><span class="sxs-lookup"><span data-stu-id="09855-103">ICorDebugManagedCallback::LogSwitch Method</span></span>

<span data-ttu-id="09855-104">共通言語ランタイム (CLR) マネージスレッドが、 <xref:System.Diagnostics.Switch> デバッグ/トレーススイッチを作成、変更、または削除するために、クラスのメソッドを呼び出したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="09855-104">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.Switch> class to create, modify, or delete a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09855-105">構文</span><span class="sxs-lookup"><span data-stu-id="09855-105">Syntax</span></span>  
  
```cpp  
HRESULT LogSwitch (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] ULONG                ulReason,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pParentName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09855-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="09855-106">Parameters</span></span>  

 `PAppDomain`  
 <span data-ttu-id="09855-107">からデバッグ/トレーススイッチを作成、変更、または削除したマネージスレッドを含むアプリケーションドメインを表す、コードのオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="09855-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that created, modified, or deleted a debugging/tracing switch.</span></span>  
  
 `pThread`  
 <span data-ttu-id="09855-108">からマネージスレッドを表す、コードスレッドオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="09855-108">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="09855-109">からイベントログに書き込まれた説明メッセージの重大度レベルを示す値。</span><span class="sxs-lookup"><span data-stu-id="09855-109">[in] A value that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `ulReason`  
 <span data-ttu-id="09855-110">からデバッグ/トレーススイッチで実行された操作を示す [Logswitchcallreason](logswitchcallreason-enumeration.md) 列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="09855-110">[in] A value of the [LogSwitchCallReason](logswitchcallreason-enumeration.md) enumeration that indicates the operation performed on the debugging/tracing switch.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="09855-111">からデバッグ/トレーススイッチの名前へのポインター。</span><span class="sxs-lookup"><span data-stu-id="09855-111">[in] A pointer to the name of the debugging/tracing switch.</span></span>  
  
 `pParentName`  
 <span data-ttu-id="09855-112">からデバッグ/トレーススイッチの親の名前へのポインター。</span><span class="sxs-lookup"><span data-stu-id="09855-112">[in] A pointer to the name of the parent of the debugging/tracing switch.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09855-113">要件</span><span class="sxs-lookup"><span data-stu-id="09855-113">Requirements</span></span>  

 <span data-ttu-id="09855-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="09855-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09855-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="09855-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="09855-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="09855-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="09855-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09855-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09855-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="09855-118">See also</span></span>

- [<span data-ttu-id="09855-119">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="09855-119">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
