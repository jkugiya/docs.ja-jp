---
description: '詳細情報: COR_NATIVE_LINK 構造'
title: COR_NATIVE_LINK 構造体
ms.date: 03/30/2017
api_name:
- COR_NATIVE_LINK
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_NATIVE_LINK
helpviewer_keywords:
- COR_NATIVE_LINK structure [.NET Framework metadata]
ms.assetid: 6ef78d3c-1c69-4141-b687-dcb065b7a74d
topic_type:
- apiref
ms.openlocfilehash: 09c715af698a0614fd4a9a17679df6908a1497a6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678576"
---
# <a name="cor_native_link-structure"></a>COR_NATIVE_LINK 構造体

ネイティブ コードのリンクに使用される情報が含まれます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct
{  
    BYTE        m_linkType;  
    BYTE        m_flags;  
    mdMemberRef m_entryPoint;  
} COR_NATIVE_LINK;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`m_linkType`|ネイティブコードでリンクされる型。 この値は、 [CorNativeLinkType](cornativelinktype-enumeration.md) 値の1つです。|  
|`m_flags`|ネイティブコードをリンクするときにリンカーによって使用されるフラグ。 この値は、 [CorNativeLinkFlags](cornativelinkflags-enumeration.md) 値の1つです。|  
|`m_entryPoint`|エントリポイントを表す MemberRef メタデータトークン。 形式は `lib:entrypoint` です。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ構造体](metadata-structures.md)
- [CorNativeLinkType 列挙型](cornativelinktype-enumeration.md)
- [CorNativeLinkFlags 列挙型](cornativelinkflags-enumeration.md)
