---
description: '詳細情報: AddFile2 メソッド'
title: AddFile2 メソッド
ms.date: 03/30/2017
api_name:
- AddFile2
- IALink2.AddFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddFile2
helpviewer_keywords:
- AddFile2 method
ms.assetid: 03bc49bf-a89b-4fb6-a88d-97482e061195
topic_type:
- apiref
ms.openlocfilehash: d53527ecf7e8b3a99a11ea99512fbc812125de3e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638614"
---
# <a name="addfile2-method"></a>AddFile2 メソッド

アセンブリにファイルを追加します。 バインドされていないモジュールの作成にも使用できます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT AddFile2(  
    mdAssembly AssemblyID,  
    LPCWSTR pszFilename,  
    DWORD dwFlags,  
    IMetaDataEmit2* pEmitter,  
    mdFile* pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a>パラメーター  

 `AssemblyID`  
 ファイルが追加されるアセンブリの ID。  
  
 `pszFilename`  
 追加するファイルの名前。  
  
 `dwFlags`  
 `ffContainsNoMetaData` や `ffWriteable` などの COM+ `FileDef` フラグ。 `dwFlags` は [DefineFile メソッド](../metadata/imetadataassemblyemit-definefile-method.md)に渡されます。  
  
 `pEmitter`  
 [IMetaDataEmit2 インターフェイス](../metadata/imetadataemit2-interface.md)へのインターフェイス。  
  
 `pFileToken`  
 追加するファイルの ID を受け取ります。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は、S_OK が返されます。  
  
## <a name="requirements"></a>必要条件  

 alink.h を必要とします。  
  
## <a name="see-also"></a>関連項目

- [IALink2 インターフェイス](ialink2-interface.md)
- [IALink インターフェイス](ialink-interface.md)
- [ALink API](index.md)
