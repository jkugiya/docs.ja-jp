---
description: '詳細情報: ICLRTask::Reset メソッド'
title: ICLRTask::Reset メソッド
ms.date: 03/30/2017
api_name:
- ICLRTask.Reset
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::Reset
helpviewer_keywords:
- ICLRTask::Reset method [.NET Framework hosting]
- Reset method, ICLRTask interface [.NET Framework hosting]
ms.assetid: 1bfb5d3a-0ffd-4bb4-9bf6-aec00cb675b7
topic_type:
- apiref
ms.openlocfilehash: d30738b98003e0543c1a2a31c7471b15811efe5f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636989"
---
# <a name="iclrtaskreset-method"></a>ICLRTask::Reset メソッド

ホストでタスクを完了したことを共通言語ランタイム (CLR) に通知し、CLR で現在の [ICLRTask](iclrtask-interface.md) インスタンスを再利用して別のタスクを表すことができるようにします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Reset (  
    [in] BOOL fFull  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `fFull`  
 [in] ランタイムで、現在の `ICLRTask` インスタンスに関連するセキュリティおよびロケール情報に加えて、スレッドに関連するすべての静的な値をリセットする必要がある場合は `true`。それ以外の場合は `false`。  
  
 値が `true` の場合、ランタイムでは、<xref:System.Threading.Thread.AllocateDataSlot%2A> または <xref:System.Threading.Thread.AllocateNamedDataSlot%2A> を使用して格納されたデータがリセットされます。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`Reset` が正常に返されました。|  
|HOST_E_CLRNOTAVAILABLE|CLR がプロセスに読み込まれていないか、CLR がマネージド コードを実行できないまたは呼び出しを処理できない状態です。 成功|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトしました。|  
|HOST_E_NOT_OWNER|呼び出し元はロックを所有していません。|  
|HOST_E_ABANDONED|ブロックされたスレッドまたはファイバーが待機しているイベントがキャンセルされました。|  
|E_FAIL|不明な壊滅的なエラーが発生しました。 メソッドにより E_FAIL が返されると、そのプロセス内で CLR が使用できなくなります。 ホスト メソッドに対する後続の呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。|  
  
## <a name="remarks"></a>解説  

 CLR では、以前に作成された `ICLRTask` インスタンスをリサイクルして、新しいタスクが必要になるたびに新しいインスタンスを繰り返し作成するオーバーヘッドを回避することができます。 ホストでは、タスクを完了したときに [ICLRTask::ExitTask](iclrtask-exittask-method.md) ではなく `ICLRTask::Reset` を呼び出すことで、この機能が有効にされます。 `ICLRTask` インスタンスの通常のライフサイクルの概要を次に示します。  
  
1. ランタイムで新しい `ICLRTask` インスタンスが作成されます。  
  
2. ランタイムで [IHostTaskManager::GetCurrentTask](ihosttaskmanager-getcurrenttask-method.md) が呼び出され、現在のホスト タスクへの参照が取得されます。  
  
3. ランタイムで、新しいインスタンスをホスト タスクに関連付けるために、[IHostTask::SetCLRTask](ihosttask-setclrtask-method.md) が呼び出されます。  
  
4. タスクが実行され、完了します。  
  
5. ホストで、`ICLRTask::ExitTask` を呼び出すことによってタスクが破棄されます。  
  
 `Reset` では、このシナリオが次の 2 つの方法で変更されます。 上記の手順 5 では、ホストで `Reset` が呼び出されてタスクがクリーンな状態にリセットされた後、関連する [IHostTask](ihosttask-interface.md) インスタンスから `ICLRTask` インスタンスが切り離されます。 必要であれば、ホストで `IHostTask` インスタンスをキャッシュして再利用することもできます。 上記の手順 1 では、ランタイムで新しいインスタンスを作成する代わりに、キャッシュからリサイクルされた `ICLRTask` が取得されます。  
  
 この方法は、ホストに再利用可能なワーカー タスクのプールがある場合に適しています。 ホストでは、`IHostTask` インスタンスの 1 つが破棄されると、`ExitTask` を呼び出すことによって、対応する `ICLRTask` が破棄されます。  
  
## <a name="requirements"></a>必要条件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRTask インターフェイス](iclrtask-interface.md)
- [ICLRTaskManager インターフェイス](iclrtaskmanager-interface.md)
- [IHostTask インターフェイス](ihosttask-interface.md)
- [IHostTaskManager インターフェイス](ihosttaskmanager-interface.md)
