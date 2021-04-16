---
description: '詳細情報: ICLRHostProtectionManager::SetProtectedCategories メソッド'
title: ICLRHostProtectionManager::SetProtectedCategories メソッド
ms.date: 03/30/2017
api_name:
- ICLRHostProtectionManager.SetProtectedCategories
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostProtectionManager::SetProtectedCategories
helpviewer_keywords:
- SetProtectedCategories method [.NET Framework hosting]
- ICLRHostProtectionManager::SetProtectedCategories method [.NET Framework hosting]
ms.assetid: fa21dc7b-5da7-440b-b59e-9180e5181f9d
topic_type:
- apiref
ms.openlocfilehash: 9138c31ea1a2d9b7ebeaeac8ef5ef9305eabef8d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637535"
---
# <a name="iclrhostprotectionmanagersetprotectedcategories-method"></a>ICLRHostProtectionManager::SetProtectedCategories メソッド

部分的に信頼されたコードでの実行をブロックする必要があるのは、どのカテゴリのマネージド型とメンバーかを指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetProtectedCategories (  
    [in] EApiCategories  categories  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `categories`  
 [in] [EApiCategories](eapicategories-enumeration.md) の組み合わせ。部分的に信頼されたコードでの実行をブロックする必要があるのは、どのカテゴリのマネージド型とメンバーかを示します。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`SetProtectedCategories` が正常に返されました。|  
|HOST_E_CLRNOTAVAILABLE|共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージド コードを実行できないまたは呼び出しを正常に処理できない状態です。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトしました。|  
|HOST_E_NOT_OWNER|呼び出し元はロックを所有していません。|  
|HOST_E_ABANDONED|ブロックされたスレッドまたはファイバーが待機しているイベントがキャンセルされました。|  
|E_FAIL|不明な壊滅的なエラーが発生しました。 メソッドにより E_FAIL が返された後、そのプロセス内で CLR が使用できなくなります。 ホスト メソッドに対する後続の呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。|  
  
## <a name="remarks"></a>解説  

 各 `EApiCategories` 値では、マネージド型とメンバーの一覧が参照されます。 `EApiCategories` 列挙型と `SetProtectedCategories` メソッドは、マネージド <xref:System.Security.Permissions.HostProtectionAttribute> クラスに直接関連付けられます。このクラスは、`EApiCategories` によって記述されたカテゴリに対応する機能を公開するマネージド型とメンバーをマークするために使用されます。 詳細については、`EApiCategories` に直接対応する <xref:System.Security.Permissions.HostProtectionAttribute> および <xref:System.Security.Permissions.HostProtectionResource> 列挙型を参照してください。  
  
## <a name="requirements"></a>必要条件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** リソースとして MSCorEE.dll に含まれている  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Security.Permissions.HostProtectionAttribute>
- <xref:System.Security.Permissions.HostProtectionResource>
- [EApiCategories 列挙型](eapicategories-enumeration.md)
- [ICLRControl インターフェイス](iclrcontrol-interface.md)
- [ICLRHostProtectionManager インターフェイス](iclrhostprotectionmanager-interface.md)
