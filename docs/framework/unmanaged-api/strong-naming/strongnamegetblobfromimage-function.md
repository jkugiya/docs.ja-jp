---
description: '詳細情報: StrongNameGetBlobFromImage 関数'
title: StrongNameGetBlobFromImage 関数
ms.date: 03/30/2017
api_name:
- StrongNameGetBlobFromImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetBlobFromImage
helpviewer_keywords:
- StrongNameGetBlobFromImage function [.NET Framework strong naming]
ms.assetid: 1de658e6-da32-4d01-9097-6f43c92222e1
topic_type:
- apiref
ms.openlocfilehash: c68d6914d47fbb711c49c1e8432cae1bf33e771f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636352"
---
# <a name="strongnamegetblobfromimage-function"></a>StrongNameGetBlobFromImage 関数

指定したメモリ アドレスにあるアセンブリ イメージのバイナリ表現が取得されます。  
  
 この関数は非推奨とされています。 代わりに、[ICLRStrongName::StrongNameGetBlobFromImage](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md) メソッドを使用してください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
BOOLEAN StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pbBase`  
 [in] マップされたアセンブリ マニフェストのメモリ アドレス。  
  
 `dwLength`  
 [in] `pbBase` にあるイメージのサイズ (バイト単位)。  
  
 `pbBlob`  
 [in] イメージのバイナリ表現を格納するバッファー。  
  
 `pcbBlob`  
 [in、out] 要求された `pbBlob` の最大サイズ (バイト単位)。 返されたときの `pbBlob` の実際のサイズ (バイト単位)。  
  
## <a name="return-value"></a>戻り値  

 正常に完了した場合は `true`。それ以外の場合は `false`。  
  
## <a name="remarks"></a>解説  

 `StrongNameGetBlobFromImage` 関数が正常に完了しない場合、[StrongNameErrorInfo](strongnameerrorinfo-function.md) 関数を呼び出し、最後に生成されたエラーを取得します。  
  
## <a name="requirements"></a>必要条件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** StrongName.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [StrongNameGetBlobFromImage メソッド](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [StrongNameGetBlob メソッド](../hosting/iclrstrongname-strongnamegetblob-method.md)
- [ICLRStrongName インターフェイス](../hosting/iclrstrongname-interface.md)
