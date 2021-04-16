---
description: '詳細情報: AssemblyOptions 列挙型'
title: AssemblyOptions 列挙体
ms.date: 03/30/2017
api_name:
- AssemblyOptions
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AssemblyOptions
helpviewer_keywords:
- Alink API, AssemblyOptions enumeration
- AssemblyOptions enumeration
ms.assetid: 84f83921-64cb-49e3-ac8b-22a0b77b18a8
topic_type:
- apiref
ms.openlocfilehash: aba9ecb3176f533e2d53e2e45fef3d1dc4e55077
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638419"
---
# <a name="assemblyoptions-enumeration"></a>AssemblyOptions 列挙体

アセンブリ オプションを列挙します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum _AssemblyOptions {  
    optAssemTitle = 0,  
    optAssemDescription,  
    optAssemConfig,  
    optAssemOS,  
    optAssemProcessor,  
    optAssemLocale,  
    optAssemVersion,  
    optAssemCompany,  
    optAssemProduct,  
    optAssemProductVersion,  
    optAssemCopyright,  
    optAssemTrademark,  
    optAssemKeyFile,  
    optAssemKeyName,  
    optAssemAlgID,  
    optAssemFlags,  
    optAssemHalfSign,  
    optAssemFileVersion,  
    optAssemSatelliteVer,  
    optLastAssemOption  
}   AssemblyOptions;  
```  
  
## <a name="fields"></a>フィールド  
  
|フィールド|説明|  
|-----------|-----------------|  
|optAssemTitle|String - アセンブリのタイトルを表します。|  
|optAssemDescription|String - アセンブリの説明を格納します。|  
|optAssemConfig|String - アセンブリ構成を格納します。|  
|optAssemOS|String - 次のようにエンコードされます: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion"。|  
|optAssemProcessor|ULONG|  
|optAssemLocale|String - アセンブリ ロケールを格納します。|  
|optAssemVersion|String - 次のようにエンコードされます: "Major.Minor.Build.Revision"。|  
|optAssemCompany|String - 会社名を格納します。|  
|optAssemProduct|String - 製品名を格納します。|  
|optAssemProductVersion|String (InformationalVersion とも呼ばれます)。|  
|optAssemCopyright|String - 著作権情報を格納します。|  
|optAssemTrademark|String - 商標情報を格納します。|  
|optAssemKeyFile|String (ファイル名)。|  
|optAssemKeyName|String (キー名)。|  
|optAssemAlgID|ULONG|  
|optAssemFlags|ULONG|  
|optAssemHalfSign|Bool (DelaySign とも呼ばれます)。|  
|optAssemFileVersion|String - 次のようにエンコードされます: "Major.Minor.Build.Revision"。ProductVersion と同じです。|  
|optAssemSatelliteVer|String - "Major.Minor.Build.Revision" としてエンコードされます。|  
|optLastAssemOption|要素数のカウンター。|  
  
## <a name="requirements"></a>必要条件  

 **ヘッダー:** alink.h  
  
 **ライブラリ**: alink.dll  
  
## <a name="see-also"></a>関連項目

- [Al.exe (アセンブリ リンカー)](../../tools/al-exe-assembly-linker.md)
