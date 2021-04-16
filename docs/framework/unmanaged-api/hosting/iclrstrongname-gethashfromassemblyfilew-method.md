---
description: '詳細情報: ICLRStrongName::GetHashFromAssemblyFileW メソッド'
title: ICLRStrongName::GetHashFromAssemblyFileW メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromAssemblyFileW
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromAssemblyFileW
helpviewer_keywords:
- ICLRStrongName::GetHashFromAssemblyFileW method [.NET Framework hosting]
- GetHashFromAssemblyFileW method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5d0b44a2-5a14-44a2-9a0e-e8682fd4e106
topic_type:
- apiref
ms.openlocfilehash: 27123ed8217d49765fe3fd7c19efc92f4e770722
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637080"
---
# <a name="iclrstrongnamegethashfromassemblyfilew-method"></a>ICLRStrongName::GetHashFromAssemblyFileW メソッド

Unicode 文字列で指定されたファイルの内容に対してハッシュが作成されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `wszFilePath`  
 [in] ハッシュ化されるファイルへのパス。 このパラメーターは、Unicode 文字列である必要があります。  
  
 `piHashAlg`  
 [in、out] ハッシュ アルゴリズムを指定する定数。 既定のハッシュ アルゴリズムでは、ゼロを使用します。  
  
 `pbHash`  
 [out] 返されたハッシュ バッファー。  
  
 `cchHash`  
 [in] 要求された `pbHash` の最大サイズ。  
  
 `pchHash`  
 [out] `pbHash` の返されたサイズ (バイト単位)。  
  
## <a name="return-value"></a>戻り値  

 メソッドが正常に完了した場合は `S_OK`、それ以外の場合は失敗を示す HRESULT 値 (リストについては、[一般的な HRESULT 値](/windows/win32/seccrypto/common-hresult-values)に関するページを参照)。  
  
## <a name="requirements"></a>必要条件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** MetaHost.h  
  
 **ライブラリ:** リソースとして MSCorEE.dll に含まれている  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [GetHashFromAssemblyFile メソッド](iclrstrongname-gethashfromassemblyfile-method.md)
- [ICLRStrongName インターフェイス](iclrstrongname-interface.md)
