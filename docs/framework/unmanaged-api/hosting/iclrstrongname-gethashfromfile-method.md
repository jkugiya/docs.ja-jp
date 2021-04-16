---
description: '詳細情報: ICLRStrongName::GetHashFromFile メソッド'
title: ICLRStrongName::GetHashFromFile メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromFile method [.NET Framework hosting]
- GetHashFromFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 9e50480a-8ada-4044-b2a5-97bb14ed3525
topic_type:
- apiref
ms.openlocfilehash: e930f1c21e5b0be441fe44ad352b2ef2f43d0f67
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637054"
---
# <a name="iclrstrongnamegethashfromfile-method"></a>ICLRStrongName::GetHashFromFile メソッド

指定したファイルの内容に対してハッシュが生成されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,
    [out] BYTE     *pbHash,
    [in]  DWORD    cchHash,
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `szFilePath`  
 [in] ハッシュするファイルの名前。  
  
 `piHashAlg`  
 [in、out] ハッシュを生成するときに使用するアルゴリズム。 有効なアルゴリズムは、Win32 CryptoAPI によって定義されているものです。 `piHashAlg` が 0 に設定されている場合は、既定のアルゴリズム CALG_SHA-1 が使用されます。  
  
 `pbHash`  
 [out] 生成されたハッシュを格納しているバイト配列。  
  
 `cchHash`  
 [in] `pbHash` が指すバッファーの最大サイズ。  
  
 `pchHash`  
 [out] 返された `pbHash` のサイズ (バイト単位)。  
  
## <a name="return-value"></a>戻り値  

 メソッドが正常に完了した場合は `S_OK`、それ以外の場合は失敗を示す HRESULT 値 (リストについては、[一般的な HRESULT 値](/windows/win32/seccrypto/common-hresult-values)に関するページを参照)。  
  
## <a name="remarks"></a>解説  

 このメソッドは [ICLRStrongName::GetHashFromFileW](iclrstrongname-gethashfromfilew-method.md) メソッドと基本的に同じですが、ファイル名の指定が Unicode ではなく ANSI である点が異なります。  
  
## <a name="requirements"></a>必要条件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** MetaHost.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [GetHashFromFileW メソッド](iclrstrongname-gethashfromfilew-method.md)
- [ICLRStrongName インターフェイス](iclrstrongname-interface.md)
