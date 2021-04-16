---
description: '詳細情報: StrongNameSignatureVerification 関数'
title: StrongNameSignatureVerification 関数
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerification
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerification
helpviewer_keywords:
- StrongNameSignatureVerification function [.NET Framework strong naming]
ms.assetid: 933758dd-231e-4382-8819-242c0a13a4b7
topic_type:
- apiref
ms.openlocfilehash: 74130cda96f38218d2fd296ff8804f86a9a18cd8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636259"
---
# <a name="strongnamesignatureverification-function"></a>StrongNameSignatureVerification 関数

指定したパスにあるアセンブリ マニフェストに厳密な名前の署名が含まれるかどうかを示す値が取得されます。これは指定したフラグに従って確認されます。  
  
 この関数は非推奨とされています。 代わりに、[ICLRStrongName::StrongNameSignatureVerification](../hosting/iclrstrongname-strongnamesignatureverification-method.md) メソッドを使用してください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
BOOLEAN StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `wszFilePath`  
 [in] 検証するアセンブリの移植可能な実行可能ファイル (.dll または .exe) のパス。  
  
 `dwInFlags`  
 [in] 検証動作を変更するフラグ。 サポートされている値を次に示します。  
  
- `SN_INFLAG_FORCE_VER` (0x00000001) - レジストリ設定を上書きする必要がある場合でも、検証を実行します。  
  
- `SN_INFLAG_INSTALL` (0x00000002) - マニフェストを初めて検証するときに指定します。  
  
- `SN_INFLAG_ADMIN_ACCESS` (0x00000004) - キャッシュで、管理者特権を持つユーザーのみにアクセスを許可することを指定します。  
  
- `SN_INFLAG_USER_ACCESS` (0x00000008) - 現在のユーザーのみがアセンブリにアクセスできるように指定します。  
  
- `SN_INFLAG_ALL_ACCESS` (0x00000010) - キャッシュでアクセス制限の保証を提供しないことを指定します。  
  
- `SN_INFLAG_RUNTIME` (0x80000000) - 内部デバッグ用に予約されています。  
  
 `pdwOutFlags`  
 [out] 厳密な名前のシグネチャが検証されたかどうかを示すフラグ。 サポートされている値を次に示します。  
  
- `SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - この値は、レジストリ設定によって検証が成功したことを指定するために、`false` に設定されます。  
  
## <a name="return-value"></a>戻り値  

 検証が正常に実行された場合は `true`。それ以外の場合は `false`。  
  
## <a name="requirements"></a>必要条件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** StrongName.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [StrongNameSignatureVerification メソッド](../hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [StrongNameSignatureVerificationEx メソッド](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [ICLRStrongName インターフェイス](../hosting/iclrstrongname-interface.md)
