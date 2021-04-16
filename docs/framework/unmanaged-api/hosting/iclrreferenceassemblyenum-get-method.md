---
description: '詳細情報: ICLRReferenceAssemblyEnum::Get メソッド'
title: ICLRReferenceAssemblyEnum::Get メソッド
ms.date: 03/30/2017
api_name:
- ICLRReferenceAssemblyEnum.Get
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRReferenceAssemblyEnum::Get
helpviewer_keywords:
- ICLRReferenceAssemblyEnum::Get method [.NET Framework hosting]
- Get method, ICLRReferenceAssemblyEnum interface [.NET Framework hosting]
ms.assetid: f21c1612-9c5d-4abc-a337-577086d29c17
topic_type:
- apiref
ms.openlocfilehash: ea4e71631a9ebb381f721b78f17507603891a032
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637301"
---
# <a name="iclrreferenceassemblyenumget-method"></a>ICLRReferenceAssemblyEnum::Get メソッド

指定されたインデックス位置にあるアセンブリ ID を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `dwIndex`  
 [in] 返されるアセンブリ ID の、0 から始まるインデックス。  
  
 `pwzBuffer`  
 [out] アセンブリ ID データが含まれるバッファー。  
  
 `pcchBufferSize`  
 [in、out] `pwzBuffer` バッファーのサイズ。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`Get` が正常に返されました。|  
|ERROR_INSUFFICIENT_BUFFER|`pwzBuffer` が小さすぎます。|  
|ERROR_NO_MORE_ITEMS|列挙型には、これ以上項目が含まれていません。|  
|HOST_E_CLRNOTAVAILABLE|共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージド コードを実行できないまたは呼び出しを正常に処理できない状態です。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトしました。|  
|HOST_E_NOT_OWNER|呼び出し元はロックを所有していません。|  
|HOST_E_ABANDONED|ブロックされたスレッドまたはファイバーが待機しているイベントがキャンセルされました。|  
|E_FAIL|不明な壊滅的なエラーが発生しました。 メソッドで E_FAIL が返される場合、CLR をプロセス内で使用することはできなくなります。 ホスト メソッドに対する後続の呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。|  
  
## <a name="remarks"></a>解説  

 通常、`Get` は 2 回呼び出されます。 最初の呼び出しでは、`pwzBuffer` に null 値を指定し、`pcchBufferSize` を `pwzBuffer` に適したサイズに設定します。 2 番目の呼び出しでは、適切なサイズの `pwzBuffer` が供給され、完了時に正規のアセンブリ ID データが格納されます。  
  
## <a name="requirements"></a>必要条件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** リソースとして MSCorEE.dll に含まれている  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRAssemblyReferenceList インターフェイス](iclrassemblyreferencelist-interface.md)
- [ICLRReferenceAssemblyEnum インターフェイス](iclrreferenceassemblyenum-interface.md)
