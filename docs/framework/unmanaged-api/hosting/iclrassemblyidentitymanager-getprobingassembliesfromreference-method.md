---
description: '詳細情報: ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference メソッド'
title: ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference メソッド
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetProbingAssembliesFromReference
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference method [.NET Framework hosting]
- GetProbingAssembliesFromReference method [.NET Framework hosting]
ms.assetid: aec05744-e8d4-44c6-b4a8-e583229ac34e
topic_type:
- apiref
ms.openlocfilehash: 38fcea460537ebed0e54103b460a48c2e58d8173
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100431426"
---
# <a name="iclrassemblyidentitymanagergetprobingassembliesfromreference-method"></a>ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference メソッド

指定された ID 型を使用してアセンブリによって参照されるアセンブリ ID の [ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md) 列挙子を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetProbingAssembliesFromReference (  
    [in] DWORD   dwMachineType,  
    [in] DWORD   dwFlags,  
    [in] LPCWSTR pwzReferenceIdentity,  
    [out] ICLRProbingAssemblyEnum **ppProbingAssemblyEnum  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `dwMachineType`  
 [in] WinNT.h に定義されたとおりにプロセッサ アーキテクチャを指定する有効な値。  
  
 `dwFlags`  
 [in] 将来の拡張用に用意されています。 CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT は、共通言語ランタイム (CLR) の現在のバージョンでサポートされている唯一の値です。  
  
 `pwzReferenceIdentity`  
 [in] 不透明なアセンブリ バインド ID。通常は、[ICLRAssemblyIdentityManager::GetBindingIdentityFromFile](iclrassemblyidentitymanager-getbindingidentityfromfile-method.md) メソッドまたは [ICLRAssemblyIdentityManager::GetBindingIdentityFromStream](iclrassemblyidentitymanager-getbindingidentityfromstream-method.md) メソッドの呼び出しから返されます。  
  
 `ppProbingAssemblyEnum`  
 [out] `pwzReferenceIdentity` によって識別されるアセンブリで参照されるアセンブリへの参照を含む `ICLRProbingAssemblyEnum` 列挙子のインターフェイス ポインター。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|メソッドから正常に値が返されました。|  
|HOST_E_CLRNOTAVAILABLE|CLR がプロセスに読み込まれていない、または CLR が、マネージド コードを実行したり呼び出しを正常に処理したりできない状態にあります。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトしました。|  
|HOST_E_NOT_OWNER|呼び出し元はロックを所有していません。|  
|HOST_E_ABANDONED|ブロックされたスレッドまたはファイバーが待機しているイベントがキャンセルされました。|  
|E_FAIL|不明な壊滅的なエラーが発生しました。 メソッドで E_FAIL が返される場合、CLR をプロセス内で使用することはできなくなります。 ホスト メソッドに対する後続の呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。|  
  
## <a name="requirements"></a>必要条件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** リソースとして MSCorEE.dll に含まれている  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRAssemblyIdentityManager インターフェイス](iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList インターフェイス](iclrassemblyreferencelist-interface.md)
- [ICLRProbingAssemblyEnum インターフェイス](iclrprobingassemblyenum-interface.md)
