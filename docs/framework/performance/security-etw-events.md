---
title: セキュリティ ETW イベント
description: .NET での厳密な名前の検証と Authenticode の検証中に発生するセキュリティ ETW イベントについて説明します。
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
ms.openlocfilehash: 4402bf5690a53ce518077268a3e20a95aeb14e8a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272515"
---
# <a name="security-etw-events"></a>セキュリティ ETW イベント

セキュリティ イベントは、厳密な名前の検証時と Authenticode の検証時に発生します。  

## <a name="strongnameverificationstart_v1-and-strongnameverificationstop_v1-events"></a>StrongNameVerificationStart_V1 イベントと StrongNameVerificationStop_V1 イベント  

 次の表に、キーワードとレベルを示します。 (詳細については、「 [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md)」を参照してください)。  
  
|イベントを発生させるキーワード|レベル|  
|-----------------------------------|-----------|  
|`SecurityKeyword` (0x400)|情報通知 (4)|  
  
 次の表に、イベント情報を示します。  
  
|イベント|イベント ID|いつ発生するか|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|181|厳密な名前の検証の開始。|  
|`StrongNameVerificationStop_V1`|182|厳密な名前の検証の終了。|  
  
 次の表に、イベント データを示します。  
  
|フィールド名|データ型|説明|  
|----------------|---------------|-----------------|  
|VerificationFlags|win:UInt32|検証フラグ。|  
|ErrorCode|win:UInt32|HResult エラー コード。|  
|FullyQualifiedAssemblyName|win:UnicodeString|完全修飾アセンブリ名。|  
|ClrInstanceID|win:UInt16|CLR または CoreCLR のインスタンスの一意の ID。|  

## <a name="authenticodeverificationstart_v1-and-authenticodeverificationstop_v1-events"></a>AuthenticodeVerificationStart_V1 イベントと AuthenticodeVerificationStop_V1 イベント  

 次の表に、キーワードとレベルを示します。  
  
|イベントを発生させるキーワード|レベル|  
|-----------------------------------|-----------|  
|`SecurityKeyword` (0x400)|情報通知 (4)|  
  
 次の表に、イベント情報を示します。  
  
|イベント|イベント ID|いつ発生するか|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|183|Authenticode 検証の開始。|  
|`AuthenticodeVerificationStop_V1`|184|Authenticode 検証の終了。|  
  
 次の表に、イベント データを示します。  
  
|フィールド名|データ型|説明|  
|----------------|---------------|-----------------|  
|VerificationFlags|win:UInt32|検証フラグ。|  
|ErrorCode|win:UInt32|HResult エラー コード。|  
|ModulePath|win:UnicodeString|モジュール パス|  
|ClrInstanceID|win:UInt16|CLR または CoreCLR のインスタンスの一意の ID。|  
  
## <a name="see-also"></a>関連項目

- [CLR ETW イベント](clr-etw-events.md)
