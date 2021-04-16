---
description: '詳細情報: EnumImportTypes メソッド'
title: EnumImportTypes メソッド
ms.date: 03/30/2017
api_name:
- EnumImportTypes
- IALink.EnumImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EnumImportTypes
helpviewer_keywords:
- EnumImportTypes method
ms.assetid: 83a0e4e7-ec06-40cb-9b63-700b9695bb04
topic_type:
- apiref
ms.openlocfilehash: 39570740f3560f5bfef8ba80b95c0eb2aca41f59
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638120"
---
# <a name="enumimporttypes-method"></a>EnumImportTypes メソッド

各スコープ内の各型を列挙します。

## <a name="syntax"></a>構文

```cpp
HRESULT EnumImportTypes(
    HALINKENUM   hEnum,
    DWORD        dwMax,
    mdTypeDef    aTypeDefs[],
    DWORD*       pdwCount
) PURE;
```

## <a name="parameters"></a>パラメーター

`hEnum`\
列挙子のハンドル。

`dwMax`\
取得する型の最大数。

`aTypeDefs`\
型トークンを受け取ります (`dwMax` を超えることはできません)。

`pdwCount`\
`aTypeDefs` 内の実際の型数を受け取ります。

## <a name="return-value"></a>戻り値

メソッドが成功した場合は、S_OK が返されます。

## <a name="requirements"></a>必要条件

alink.h を必要とします

## <a name="see-also"></a>関連項目

- [IALink インターフェイス](ialink-interface.md)
- [IALink2 インターフェイス](ialink2-interface.md)
- [ALink API](index.md)
