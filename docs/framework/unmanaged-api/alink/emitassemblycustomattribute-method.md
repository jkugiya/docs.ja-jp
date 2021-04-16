---
description: '詳細情報: EmitAssemblyCustomAttribute メソッド'
title: EmitAssemblyCustomAttribute メソッド
ms.date: 03/30/2017
api_name:
- IALink.EmitAssemblyCustomAttribute
- EmitAssemblyCustomAttribute
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitAssemblyCustomAttribute
helpviewer_keywords:
- EmitAssemblyCustomAttribute method
ms.assetid: b72f5409-79af-4fa7-90a7-7630eec170f1
topic_type:
- apiref
ms.openlocfilehash: c91eb563c14b442a22db8f328287c10e5cc9a63c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638328"
---
# <a name="emitassemblycustomattribute-method"></a>EmitAssemblyCustomAttribute メソッド

アセンブリ レベルのカスタム属性を設定するために呼び出します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EmitAssemblyCustomAttribute(  
    mdAssembly   AssemblyID,  
    mdToken      FileToken,  
    mdToken      tkType,  
    void const*  pCustomValue,  
    DWORD        cbCustomValue,  
    BOOL         bSecurity,  
    BOOL         bAllowMulti  
) PURE;  
```  
  
## <a name="parameters"></a>パラメーター  

 `AssemblyID`  
 アセンブリの ID。  
  
 `FileToken`  
 属性を定義するファイル。 `AssemblyID` がバインドされていない netmodule を示していない場合は、NULL にすることができます。  
  
 `tkType`  
 カスタム属性の型。  
  
 `pCustomValue`  
 カスタム値データ。  
  
 `cbCustomValue`  
 カスタム値データの長さ。  
  
 `bSecurity`  
 カスタム属性がアセンブリ署名に関連付けられている場合は TRUE。  
  
 `bAllowMulti`  
 複数の属性を出力する場合は TRUE。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は、S_OK が返されます。  
  
## <a name="requirements"></a>必要条件  

 alink.h を必要とします  
  
## <a name="see-also"></a>関連項目

- [IALink インターフェイス](ialink-interface.md)
- [IALink2 インターフェイス](ialink2-interface.md)
- [ALink API](index.md)
