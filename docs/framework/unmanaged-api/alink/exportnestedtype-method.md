---
description: '詳細情報: ExportNestedType メソッド'
title: ExportNestedType メソッド
ms.date: 03/30/2017
api_name:
- IALink.ExportNestedType
- ExportNestedType
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportNestedType
helpviewer_keywords:
- ExportNestedType method
ms.assetid: dec7df60-4d30-47c8-99db-72e0419e5f76
topic_type:
- apiref
ms.openlocfilehash: 66cf4c3572857a0e7e99efa966cdb0b9ae2be673
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638145"
---
# <a name="exportnestedtype-method"></a>ExportNestedType メソッド

入れ子にされた型をエクスポート可能として指定します。 入れ子になった型のエクスポートは [ExportType メソッド](exporttype-method.md)でもできますが、このメソッドの方が高速です。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ExportNestedType(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    mdExportedType  ParentType,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;
```  
  
## <a name="parameters"></a>パラメーター  

 `AssemblyID`  
 エクスポート元のアセンブリの ID。  
  
 `FileToken`  
 エクスポート可能にする型を定義するファイルのファイル トークンまたはアセンブリ。  
  
 `TypeToken`  
 エクスポート可能にする型の型トークン。  
  
 `ParentType`  
 親の型のトークン。  
  
 `pszTypename`  
 エクスポートする完全修飾型名。  
  
 `dwFlags`  
 `tdPublic` や `tdNested` などの `ComType` フラグ。 この値は、[DefineExportedType メソッド](../metadata/imetadataassemblyemit-defineexportedtype-method.md)に渡すことができます。  
  
 `pType`  
 エクスポートされた型のトークンを受け取ります。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は、S_OK が返されます。  
  
## <a name="requirements"></a>必要条件  

 alink.h を必要とします  
  
## <a name="see-also"></a>関連項目

- [IALink インターフェイス](ialink-interface.md)
- [IALink2 インターフェイス](ialink2-interface.md)
- [ALink API](index.md)
