---
description: '詳細情報: StrongNameTokenFromAssemblyEx 関数'
title: StrongNameTokenFromAssemblyEx 関数
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromAssemblyEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameTokenFromAssemblyEx
helpviewer_keywords:
- StrongNameTokenFromAssemblyEx function [.NET Framework strong naming]
ms.assetid: 67a8a9f2-dee3-44b2-a1c0-f307a3bdf90f
topic_type:
- apiref
ms.openlocfilehash: 4ca08c8cfa90415723fc2632e32aa8f45c334db3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636281"
---
# <a name="strongnametokenfromassemblyex-function"></a>StrongNameTokenFromAssemblyEx 関数

指定したアセンブリ ファイルから厳密な名前のトークンが作成され、トークンが表す公開キーが返されます。  
  
 この関数は非推奨とされています。 代わりに、[ICLRStrongName::StrongNameTokenFromAssemblyEx](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) メソッドを使用してください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
BOOLEAN StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `wszFilePath`  
 [in] アセンブリの移植可能な実行可能ファイル (PE) のパス。  
  
 `ppbStrongNameToken`  
 [out] 返された厳密な名前トークン。  
  
 `pcbStrongNameToken`  
 [out] 厳密な名前トークンのサイズ (バイト単位)。  
  
 `ppbPublicKeyBlob`  
 [out] 返された公開キー。  
  
 `pcbPublicKeyBlob`  
 [out] 公開キーのサイズ (バイト単位)。  
  
## <a name="return-value"></a>戻り値  

 正常に完了した場合は `true`。それ以外の場合は `false`。  
  
## <a name="remarks"></a>解説  

 厳密な名前トークンは、公開キーの短縮形です。 トークンは、アセンブリの署名に使用される公開キーから作成された 64 ビットのハッシュです。 トークンはアセンブリの厳密な名前の一部であり、アセンブリ メタデータから読み取ることができます。  
  
 キーが取得されてトークンが作成されたら、[StrongNameFreeBuffer](strongnamefreebuffer-function.md) 関数を呼び出し、割り当てられてメモリを解放してください。  
  
 `StrongNameTokenFromAssemblyEx` 関数が正常に完了しない場合、[StrongNameErrorInfo](strongnameerrorinfo-function.md) 関数を呼び出し、最後に生成されたエラーを取得します。  
  
## <a name="requirements"></a>必要条件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** StrongName.h  
  
 **ライブラリ:** mscoree.dll にリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [StrongNameTokenFromAssemblyEx メソッド](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [StrongNameTokenFromAssembly メソッド](../hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [ICLRStrongName インターフェイス](../hosting/iclrstrongname-interface.md)
