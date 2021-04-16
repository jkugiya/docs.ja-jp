---
description: '詳細情報: StrongNameTokenFromPublicKey 関数'
title: StrongNameTokenFromPublicKey 関数
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- COM
f1_keywords:
- StrongNameTokenFromPublicKey
helpviewer_keywords:
- StrongNameTokenFromPublicKey function [.NET Framework strong naming]
ms.assetid: 997e9e57-abb2-4217-bf20-1df621a75add
topic_type:
- apiref
ms.openlocfilehash: f978c9b2727db4b293b9c92a8789fbf9ba749d41
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636282"
---
# <a name="strongnametokenfrompublickey-function"></a>StrongNameTokenFromPublicKey 関数

公開キーを表すトークンが取得されます。 厳密な名前トークンは、公開キーの短縮形です。  
  
 この関数は非推奨とされています。 代わりに、[ICLRStrongName::StrongNameTokenFromPublicKey](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md) メソッドを使用してください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
BOOLEAN StrongNameTokenFromPublicKey (
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pbPublicKeyBlob`  
 [in] 厳密な名前のシグネチャを生成するために使用されるキーの組の公開部分を格納する [PublicKeyBlob](publickeyblob-structure.md) 型の構造体。  
  
 `cbPublicKeyBlob`  
 [in] `pbPublicKeyBlob` のサイズ (バイト単位)。  
  
 `ppbStrongNameToken`  
 [out] `pbPublicKeyBlob` に渡されたキーに対応する厳密な名前トークン。 共通言語ランタイムで、トークンが返されるメモリが割り当てられます。 呼び出し元では、[StrongNameFreeBuffer](strongnamefreebuffer-function.md) 関数を使用して、このメモリを解放する必要があります。  
  
 `pcbStrongNameToken`  
 [out] 返された厳密な名前トークンのサイズ (バイト単位)。  
  
## <a name="return-value"></a>戻り値  

 正常に完了した場合は `true`。それ以外の場合は `false`。  
  
## <a name="remarks"></a>解説  

 厳密な名前トークンは、キー情報をメタデータに格納する際に領域を節約するために使用される公開キーの短縮形です。 具体的には、厳密な名前トークンは、依存アセンブリを参照するためにアセンブリ参照で使用されます。  
  
 `StrongNameTokenFromPublicKey` 関数が正常に完了しない場合、[StrongNameErrorInfo](strongnameerrorinfo-function.md) 関数を呼び出し、最後に生成されたエラーを取得します。  
  
## <a name="requirements"></a>必要条件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** StrongName.h  
  
 **ライブラリ**: mscoree.dll にリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [StrongNameTokenFromPublicKey メソッド](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [StrongNameGetPublicKey メソッド](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [PublicKeyBlob 構造体](publickeyblob-structure.md)
