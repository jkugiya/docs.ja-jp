---
title: 相互運用ランタイム イベント
description: 相互運用に固有の診断情報を収集する .NET ランタイム イベントに関するページを参照してください。
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- Interop events (CoreCLR)
- ETW, EventPipe, LTTng interop events (CoreCLR)
ms.openlocfilehash: 5635fb55b3a6ffa3f5611da80cdb2909e226e2ea
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "96594048"
---
# <a name="net-runtime-interop-events"></a>.NET ランタイム相互運用イベント

これらのランタイム イベントは、共通中間言語 (CIL) のスタブ生成に関する情報をキャプチャします。 診断のためにこれらのイベントを使用する方法の詳細については、[.NET アプリケーションのログ記録とトレース](../../core/diagnostics/logging-tracing.md)に関するページを参照してください。

## <a name="ilstubgenerated-event"></a>ILStubGenerated イベント

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`InteropKeyword` (0x2000)|情報通知 (4)|
  
|Event|イベント ID|いつ発生するか|
|-----------|--------------|-----------------|
|`ILStubGenerated`|88|IL スタブが生成されます。|

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`ModuleID`|`win:UInt16`|モジュールの ID です。|
|`StubMethodID`|`win:UInt64`|スタブのメソッド識別子。|
|`StubFlags`|`win:UInt32`|スタブのフラグ:<br /><br /> `0x1` - 逆方向の相互運用。<br /><br /> `0x2` - COM 相互運用。<br /><br /> `0x4` - NGen.exe で生成されたスタブ。<br /><br /> `0x8` - デリゲート。<br /><br /> `0x10` - 可変個引数。<br /><br /> `0x20` - アンマネージ呼び出し先。<br /><br /> `0x40` -構造体マーシャル|
|`ManagedInteropMethodToken`|`win:UInt32`|マネージド相互運用メソッドのトークンです。|
|`ManagedInteropMethodNameSpace`|`win:UnicodeString`|マネージ相互運用メソッドの名前空間とそれを囲む型。|
|`ManagedInteropMethodName`|`win:UnicodeString`|マネージド相互運用メソッドの名前。|
|`ManagedInteropMethodSignature`|`win:UnicodeString`|マネージド相互運用メソッドのシグネチャ。|
|`NativeMethodSignature`|`win:UnicodeString`|ネイティブ メソッド シグネチャ。|
|`StubMethodSignature`|`win:UnicodeString`|スタブ メソッド シグネチャ。|
|`StubMethodILCode`|`win:UnicodeString`|スタブ メソッドの共通中間言語 (CIL) コード。|
|`ClrInstanceID`|`win:UInt16`|CLR または CoreCLR のインスタンスの一意の ID。|
