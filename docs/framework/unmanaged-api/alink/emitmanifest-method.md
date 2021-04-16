---
description: '詳細情報: EmitManifest メソッド'
title: EmitManifest メソッド
ms.date: 03/30/2017
api_name:
- EmitManifest
- IALink.EmitManifest
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitManifest
helpviewer_keywords:
- EmitManifest method
ms.assetid: fdebc1f3-b62e-4d9e-b775-8ccaa8ecb250
topic_type:
- apiref
ms.openlocfilehash: 770631864c030c067feb0b02d2f00c36076aa44c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638276"
---
# <a name="emitmanifest-method"></a>EmitManifest メソッド

最終的なマニフェストを出力します。 このメソッドは、他のすべてのファイルをインポートし、すべてのオプションを設定した後に呼び出します。 バインドされていないモジュールに対しては、このメソッドを呼び出さないでください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EmitManifest(  
    mdAssembly   AssemblyID,  
    DWORD*       pdwReserveSize,  
    mdAssembly*  ptkManifest  
) PURE;  
```  
  
## <a name="parameters"></a>パラメーター  

 `AssemblyID`  
 アセンブリの ID。  
  
 `pdwReserveSize`  
 [StrongNameSignatureSize 関数](../strong-naming/strongnamesignaturesize-function.md)から取得した、アセンブリ ファイルで予約するサイズを受け取ります。  
  
 `ptkManifest`  
 必要に応じて、アセンブリ マニフェスト トークンを受け取ります。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は、S_OK が返されます。  
  
## <a name="requirements"></a>必要条件  

 alink.h を必要とします。  
  
## <a name="see-also"></a>関連項目

- [IALink インターフェイス](ialink-interface.md)
- [IALink2 インターフェイス](ialink2-interface.md)
- [ALink API](index.md)
