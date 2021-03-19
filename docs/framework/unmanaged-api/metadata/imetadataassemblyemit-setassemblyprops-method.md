---
description: '詳細について: IMetaDataAssemblyEmit:: SetAssemblyProps メソッド'
title: IMetaDataAssemblyEmit::SetAssemblyProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetAssemblyProps
helpviewer_keywords:
- SetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyProps method [.NET Framework metadata]
ms.assetid: 91b633d7-9e75-43c3-a8d2-2144984e5f9e
topic_type:
- apiref
ms.openlocfilehash: d5dfb5fa472bb83863c8e4909998deeb2b9fc53b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678199"
---
# <a name="imetadataassemblyemitsetassemblyprops-method"></a>IMetaDataAssemblyEmit::SetAssemblyProps メソッド

指定された `Assembly` メタデータ構造体を変更します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetAssemblyProps (  
    [in] mdAssembly               pma,  
    [in] const void               *pbPublicKey,  
    [in] ULONG                    cbPublicKey,  
    [in] ULONG                    ulHashAlgId,  
    [in] LPCWSTR                  szName,  
    [in] const ASSEMBLYMETADATA   *pMetaData,  
    [in] DWORD                    dwAssemblyFlags  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pma`  
 から変更するメタデータ構造を指定するメタデータトークン `Assembly` 。  
  
 `pbPublicKey`  
 からアセンブリの発行者の公開キーへのポインター。  
  
 `cbPublicKey`  
 からのサイズ (バイト単位) `pbPublicKey` 。  
  
 `ulHashAlgId`  
 からアセンブリファイルのハッシュに使用されるハッシュアルゴリズムの識別子。  
  
 `szName`  
 からユーザーが判読できる、アセンブリのテキスト名。  
  
 `pMetaData`  
 からアセンブリのバージョン、プラットフォーム、およびロケール情報を格納している ASSEMBLYMETADATA へのポインター。  
  
 `dwAssemblyFlags`  
 からアセンブリのさまざまな属性を指定する [Assemblyflags](assemblyflags-enumeration.md) 値のビットごとの組み合わせ。  
  
## <a name="remarks"></a>解説  

 メタデータ構造を作成するには `Assembly` 、 [IMetaDataAssemblyEmit::D efineAssembly](imetadataassemblyemit-defineassembly-method.md) メソッドを使用します。  
  
## <a name="requirements"></a>要件  

 **プラットフォーム:** 「 [システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataAssemblyEmit インターフェイス](imetadataassemblyemit-interface.md)
