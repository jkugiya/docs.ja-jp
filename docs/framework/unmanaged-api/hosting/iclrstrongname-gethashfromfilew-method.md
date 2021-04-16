---
description: '詳細情報: ICLRStrongName::GetHashFromFileW メソッド'
title: ICLRStrongName::GetHashFromFileW メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromFileW
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromFileW
helpviewer_keywords:
- GetHashFromFileW method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::GetHashFromFileW method [.NET Framework hosting]
ms.assetid: c6ff45fc-905d-4c6e-b00c-97c6c7c55d99
topic_type:
- apiref
ms.openlocfilehash: 6145a044f490ef3827de6db8d84d16222306642d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636976"
---
# <a name="iclrstrongnamegethashfromfilew-method"></a>ICLRStrongName::GetHashFromFileW メソッド

Unicode 文字列で指定されたファイルの内容に対してハッシュが作成されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetHashFromFileW (
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);
```  
  
## <a name="parameters"></a>パラメーター  

 `wszFilePath`  
 [in] ハッシュするファイルの Unicode 名。  
  
 `piHashAlg`  
 [in、out] ハッシュを生成するときに使用するアルゴリズム。 有効なアルゴリズムは、Win32 CryptoAPI によって定義されているものです。 `piHashAlg` が 0 に設定されている場合は、既定のアルゴリズム CALG_SHA-1 が使用されます。  
  
 `pbHash`  
 [out] 生成されたハッシュを格納しているバイト配列。  
  
 `cchHash`  
 [in] `pbHash` が指すバッファーの最大サイズ。  
  
 `pchHash`  
 [out] `pbHash` のバイト単位のサイズ。  
  
## <a name="return-value"></a>戻り値  

 メソッドが正常に完了した場合は `S_OK`、それ以外の場合は失敗を示す HRESULT 値 (リストについては、[一般的な HRESULT 値](/windows/win32/seccrypto/common-hresult-values)に関するページを参照)。  
  
## <a name="remarks"></a>解説  

 このメソッドは [ICLRStrongName::GetHashFromFile](iclrstrongname-gethashfromfile-method.md) メソッドと基本的に同じですが、ファイル名の指定が ANSI ではなく Unicode である点が異なります。  
  
## <a name="requirements"></a>必要条件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** MetaHost.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [GetHashFromFile メソッド](iclrstrongname-gethashfromfile-method.md)
- [ICLRStrongName インターフェイス](iclrstrongname-interface.md)
