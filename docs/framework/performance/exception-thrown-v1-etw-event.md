---
title: Exception Thrown_V1 ETW イベント
description: ExceptionThrown_V1 ETW イベントに関する詳細情報を表示します。 スローされた例外に対して、フィールド名、データ型、説明などのイベント データが提供されます。
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
ms.openlocfilehash: c1ba994b291bd278a95e34beb0b02ed6581786e8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263478"
---
# <a name="exception-thrown_v1-etw-event"></a>Exception Thrown_V1 ETW イベント

このイベントは、スローされる例外に関する情報をキャプチャします。  
  
 イベントが発生するキーワードとイベントのレベルを次の表に示します  (詳細については、「 [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md)」を参照してください)。  
  
|イベントを発生させるキーワード|レベル|  
|-----------------------------------|-----------|  
|`ExceptionKeyword` (0x8000)|警告 (2)|  
  
 次の表にイベント情報を示します。  
  
|イベント|イベント ID|いつ発生するか|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|80|マネージド例外がスローされます。|  
  
 次の表にイベント データを示します。  
  
|フィールド名|データ型|説明|  
|----------------|---------------|-----------------|  
|例外の種類|win:UnicodeString|例外の種類 (`System.NullReferenceException` など)。|  
|例外メッセージ|win:UnicodeString|実際の例外メッセージ。|  
|EIPCodeThrow|win:Pointer|例外が発生した命令ポインター。|  
|ExceptionHR|win:UInt32|例外 [HRESULT](/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a)。|  
|ExceptionFlags|win:UInt16|0x01: HasInnerException (Visual Basic のドキュメントで「[CLR ETW イベント](clr-etw-events.md)」を参照)。<br /><br /> 0x02: IsNestedException。<br /><br /> 0x04: IsRethrownException。<br /><br /> 0x08: IsCorruptedStateException (プロセスの状態が破損していることを示す。「[破損状態例外を処理する](/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)」を参照)。<br /><br /> 0x10: IsCLSCompliant (<xref:System.Exception> から派生した例外は CLS 準拠で、それ以外は CLS 非準拠)。|  
|ClrInstanceID|win:UInt16|CLR または CoreCLR のインスタンスの一意の ID。|  
  
## <a name="see-also"></a>関連項目

- [CLR ETW イベント](clr-etw-events.md)
