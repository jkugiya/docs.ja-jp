---
description: '詳細について: IMetaDataAssemblyEmit::D efineExportedType メソッド'
title: IMetaDataAssemblyEmit::DefineExportedType メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineExportedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineExportedType
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineExportedType method [.NET Framework metadata]
- DefineExportedType method [.NET Framework metadata]
ms.assetid: fad01d7a-3178-4c8c-9f0a-4641e3701c9b
topic_type:
- apiref
ms.openlocfilehash: 0da1b1eb0880b0ba9df0ba9ad70b460163dffc39
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671114"
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a>IMetaDataAssemblyEmit::DefineExportedType メソッド

指定してエクスポートした型のメタデータが含まれる `ExportedType` 構造体を作成し、関連付けられたメタデータ トークンを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DefineExportedType (  
    [in]  LPCWSTR             szName,  
    [in]  mdToken             tkImplementation,
    [in]  mdTypeDef           tkTypeDef,  
    [in]  DWORD               dwExportedTypeFlags,  
    [out] mdExportedType      *pmdct  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `szName`  
 からエクスポートする型の名前。 共通言語ランタイムのバージョン1.1 では、エクスポートされた型の名前が、型ので指定された名前と完全に一致している必要があり `TypeDef` ます。  
  
 `tkImplementation`  
 からエクスポートされた型を実装する場所を指定するトークン。 有効な値とそれに関連付けられている意味は次のとおりです。  
  
- `mdFile` この型は、このアセンブリ内の別のファイルに実装されています。  
  
- `mdAssemblyRef` 型が別のアセンブリに実装されています。  
  
- `mdExportedTYpe` 型が他の型の中で入れ子になっています。  
  
- `mdFileNil` この型はマニフェストと同じファイル内にあり、入れ子にされた型ではありません。  
  
 `tkTypeDef`  
 からエクスポートする型を指定するメタデータのトークン。 この値は、型を実装するファイルのテーブルに入力され、 `TypeDef` そのファイルがこのアセンブリ内にある場合にのみ関連します。  
  
 `dwExportedTypeFlags`  
 からエクスポートされた型のプロパティ設定を定義する [Cortypeattr](cortypeattr-enumeration.md) 列挙値のビットごとの組み合わせ。  
  
 `pmdct`  
 入出力エクスポートされた型を示す、返されたメタデータトークンへのポインター。  
  
## <a name="remarks"></a>解説  

 `ExportedType`このアセンブリによって公開され、マニフェストを含むモジュール以外のモジュールで実装される型ごとに、メタデータ構造を定義する必要があります。  
  
## <a name="requirements"></a>要件  

 **プラットフォーム:** 「 [システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataAssemblyEmit インターフェイス](imetadataassemblyemit-interface.md)
