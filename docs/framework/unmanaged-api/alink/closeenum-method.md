---
description: '詳細情報: CloseEnum メソッド'
title: CloseEnum メソッド
ms.date: 03/30/2017
api_name:
- CloseEnum
- IALink.CloseEnum
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- CloseEnum
helpviewer_keywords:
- CloseEnum method
ms.assetid: aa4a091e-13fe-4264-91de-e12f1c767c87
topic_type:
- apiref
ms.openlocfilehash: 700c54de5af2e5c0be6940d4045019092655d46f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638380"
---
# <a name="closeenum-method"></a>CloseEnum メソッド

指定された列挙型を閉じ、関連付けられているリソースを解放します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CloseEnum(  
    HALINKENUM hEnum  
) PURE;  
```  
  
## <a name="parameters"></a>パラメーター  

 `hEnum`  
 閉じられる列挙型のハンドル。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は、S_OK が返されます。  
  
## <a name="requirements"></a>必要条件  

 alink.h を必要とします  
  
## <a name="see-also"></a>関連項目

- [IALink インターフェイス](ialink-interface.md)
- [IALink2 インターフェイス](ialink2-interface.md)
- [ALink API](index.md)
