---
title: GetDemultiplexedStub 関数 (アンマネージド API リファレンス)
description: GetDemultiplexedStub 関数では、Windows 管理から非同期呼び出しを受信する際にクライアントを支援するオブジェクト転送シンクが作成されます。
ms.date: 11/06/2017
api_name:
- GetDemultiplexedStub
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetDemultiplexedStub
helpviewer_keywords:
- GetDemultiplexedStub function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: f8f9b56268168bb16c476a9366facd17e8ac44e5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730631"
---
# <a name="getdemultiplexedstub-function"></a><span data-ttu-id="9b3e9-103">GetDemultiplexedStub 関数</span><span class="sxs-lookup"><span data-stu-id="9b3e9-103">GetDemultiplexedStub function</span></span>

<span data-ttu-id="9b3e9-104">Windows 管理から非同期呼び出しを受信する際にクライアントを支援するオブジェクト転送シンクが作成されます。</span><span class="sxs-lookup"><span data-stu-id="9b3e9-104">Creates an object forwarder sink to assist a client in receiving asynchronous calls from Windows Management.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="9b3e9-105">構文</span><span class="sxs-lookup"><span data-stu-id="9b3e9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDemultiplexedStub (
   [in] IUnknown*    pObject,
   [in] boolean      isLocal,
   [out] IUnknown**  ppObject
);
```  

## <a name="parameters"></a><span data-ttu-id="9b3e9-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9b3e9-106">Parameters</span></span>

`pObject`  
<span data-ttu-id="9b3e9-107">[in] [IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink) のクライアントのインプロセス実装へのポインター。</span><span class="sxs-lookup"><span data-stu-id="9b3e9-107">[in] A pointer to the client's in-process implementation of [IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink).</span></span>

`isLocal`  
<span data-ttu-id="9b3e9-108">[in] イベントがローカル (`true`) であるか、それ以外であるか (`false`) を示すフラグ。</span><span class="sxs-lookup"><span data-stu-id="9b3e9-108">[in] A flag that indicates whether the event is local (`true`); otherwise, `false`.</span></span>

`ppObject`  
<span data-ttu-id="9b3e9-109">[out] Windows 管理から非同期呼び出しを受信する際にクライアントを支援するオブジェクト転送シンク。</span><span class="sxs-lookup"><span data-stu-id="9b3e9-109">[out] A object forwarder sink to assist a client in receiving asynchronous calls from Windows Management.</span></span>

## <a name="return-value"></a><span data-ttu-id="9b3e9-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="9b3e9-110">Return value</span></span>

<span data-ttu-id="9b3e9-111">関数が成功した場合の戻り値は `S_OK` (0) です。</span><span class="sxs-lookup"><span data-stu-id="9b3e9-111">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="9b3e9-112">関数が失敗した場合の戻り値はゼロ以外のエラー コードです。</span><span class="sxs-lookup"><span data-stu-id="9b3e9-112">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="9b3e9-113">拡張されたエラー情報を取得するには、[GetErrorInfo](geterrorinfo.md) 関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="9b3e9-113">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="9b3e9-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="9b3e9-114">Requirements</span></span>  

 <span data-ttu-id="9b3e9-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b3e9-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b3e9-116">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="9b3e9-116">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="9b3e9-117">**.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9b3e9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b3e9-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="9b3e9-118">See also</span></span>

- [<span data-ttu-id="9b3e9-119">WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="9b3e9-119">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
