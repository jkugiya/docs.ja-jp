---
description: '詳細情報: _EFN_GetManagedObjectFieldInfo 関数'
title: _EFN_GetManagedObjectFieldInfo 関数
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedObjectFieldInfo
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedObjectFieldInfo
helpviewer_keywords:
- _EFN_GetManagedObjectFieldInfo function [.NET Framework debugging]
ms.assetid: 3b93bcff-62a4-47b2-babc-6bcf4216119a
topic_type:
- apiref
ms.openlocfilehash: 749ab286a86db07c1b66ff2b61ff073d15334800
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637888"
---
# <a name="_efn_getmanagedobjectfieldinfo-function"></a>\_EFN\_GetManagedObjectFieldInfo 関数

指定したオブジェクト ポインターとフィールド名を使用して、オブジェクトの先頭からフィールドまでのオフセットとフィールドの値を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT _EFN_GetManagedObjectFieldInfo(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       objAddr,  
    [in]  __out_ecount (mdNameLen) PSTR szFieldName,  
    [out] PULONG64      pValue,  
    [out] PULONG        pOffset  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `Client`  
 [in] デバッグ クライアントへのポインター。  
  
 `objAddr`  
 [in] マネージド オブジェクト ポインター。  
  
 szFieldName  
 [in] フィールド名へのマネージド オブジェクト ポインター。  
  
 `pValue`  
 [out] フィールド値。 このパラメーターには、null を指定できます。  
  
 `pOffset`  
 [out] `objAddr` からフィールドまでのオフセット。 このパラメーターには、null を指定できます。  
  
## <a name="remarks"></a>解説  

 オフセットが 0 の場合、オフセットは書き込まれません。  
  
 現在コンテキスト内にあるスレッドにマネージド コードがない場合、この関数では、ファシリティ値が 0xa0 でエラー コードが 0x1000 の HRESULT SOS_E_NOMANAGEDCODE が返されます。  
  
## <a name="requirements"></a>必要条件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** SOS_Stacktrace.h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ グローバル静的関数](debugging-global-static-functions.md)
