---
title: 例外ランタイム イベント
description: 例外と例外処理に固有の診断情報を収集する .NET ランタイム イベントを確認します。
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- exception events (CoreCLR)
- exception handling events (CoreCLR)
- ETW, EventPipe, LTTng exception events (CoreCLR)
ms.openlocfilehash: f4f63c8469f9c734b872ddaec8d1d7f7f0427576
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "96594103"
---
# <a name="net-runtime-exception-events"></a>.NET ランタイム例外イベント

これらのランタイム イベントは、スローされる例外に関する情報をキャプチャします。 診断のためにこれらのイベントを使用する方法の詳細については、[.NET アプリケーションのログ記録とトレース](../../core/diagnostics/logging-tracing.md)に関するページを参照してください。

## <a name="exceptionthrown_v1-event"></a>ExceptionThrown_V1 イベント

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`ExceptionKeyword` (0x8000)|エラー (1)|

 次の表にイベント情報を示します。

|Event|イベント ID|いつ発生するか|
|-----------|--------------|-----------------|
|`ExceptionThrown_V1`|80|マネージド例外がスローされます。|

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`ExceptionType`|`win:UnicodeString`|例外の種類 (`System.NullReferenceException` など)。|
|`ExceptionMessage`|`win:UnicodeString`|実際の例外メッセージ。|
|`EIPCodeThrow`|`win:Pointer`|例外が発生した命令ポインター。|
|`ExceptionHR`|`win:UInt32`|例外 [HRESULT](/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a)。|
|`ExceptionFlags`|`win:UInt16`|`0x01`: HasInnerException。<br /><br /> `0x02`: IsNestedException。<br /><br /> `0x04`: IsRethrownException。<br /><br /> `0x08`: IsCorruptedStateException (プロセスの状態が破損していることを示す。「[破損状態例外を処理する](/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)」を参照)。<br /><br /> `0x10`: IsCLSCompliant (<xref:System.Exception> から派生した例外は CLS 準拠で、それ以外は CLS 非準拠)。|
|`ClrInstanceID`|`win:UInt16`|CLR または CoreCLR のインスタンスの一意の ID。|

## <a name="exceptioncatchstart-event"></a>ExceptionCatchStart イベント

このイベントは、マネージ例外の catch ハンドラーが開始したときに生成されます。

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`ExceptionKeyword` (0x8000)|情報提供 (4)|

 次の表にイベント情報を示します。

|Event|イベント ID|いつ発生するか|
|-----------|--------------|-----------------|
|`ExceptionCatchStart`|250|マネージ例外は、ランタイムによって処理されます。|

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`EIPCodeThrow`|`win:Pointer`|例外が発生した命令ポインター。|
|`MethodID`|`win:Pointer`|例外が発生したメソッドのメソッド記述子へのポインター。|
|`MethodName`|`win:UnicodeString`|例外が発生したメソッドの名前。|
|`ClrInstanceID`|`win:UInt16`|CLR または CoreCLR のインスタンスの一意の ID。|

## <a name="exceptioncatchstop-event"></a>ExceptionCatchStop イベント

このイベントは、マネージ例外の catch ハンドラーが終了したときに生成されます。

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`ExceptionKeyword` (0x8000)|情報提供 (4)|

 次の表にイベント情報を示します。

|Event|イベント ID|いつ発生するか|
|-----------|--------------|-----------------|
|`ExceptionCatchStop`|251|マネージ例外の catch ハンドラーが完了したとき。|

## <a name="exceptionfinallystart-event"></a>ExceptionFinallyStart イベント

このイベントは、マネージ例外の finally ハンドラーが開始したときに生成されます。

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`ExceptionKeyword` (0x8000)|情報提供 (4)|

 次の表にイベント情報を示します。

|Event|イベント ID|いつ発生するか|
|-----------|--------------|-----------------|
|`ExceptionFinallyStart`|252|マネージ例外は、ランタイムによって処理されます。|

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`EIPCodeThrow`|`win:Pointer`|例外が発生した命令ポインター。|
|`MethodID`|`win:Pointer`|例外が発生したメソッドのメソッド記述子へのポインター。|
|`MethodName`|`win:UnicodeString`|例外が発生したメソッドの名前。|
|`ClrInstanceID`|`win:UInt16`|CLR または CoreCLR のインスタンスの一意の ID。|

## <a name="exceptionfinallystop-event"></a>ExceptionFinallyStop イベント

このイベントは、マネージ例外の catch ハンドラーが終了したときに生成されます。

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`ExceptionKeyword` (0x8000)|情報提供 (4)|

 次の表にイベント情報を示します。

|Event|イベント ID|いつ発生するか|
|-----------|--------------|-----------------|
|`ExceptionFinallyStop`|253|マネージ例外の finally ハンドラーが完了したとき。|

## <a name="exceptionfilterstart-event"></a>ExceptionFilterStart イベント

このイベントは、マネージ例外のフィルター処理が開始したときに生成されます。

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`ExceptionKeyword` (0x8000)|情報提供 (4)|

 次の表にイベント情報を示します。

|Event|イベント ID|いつ発生するか|
|-----------|--------------|-----------------|
|`ExceptionFilterStart`|254|マネージ例外のフィルター処理が開始したとき。|

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`EIPCodeThrow`|`win:Pointer`|例外が発生した命令ポインター。|
|`MethodID`|`win:Pointer`|例外が発生したメソッドのメソッド記述子へのポインター。|
|`MethodName`|`win:UnicodeString`|例外が発生したメソッドの名前。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR のインスタンスの一意の ID。|

## <a name="exceptionfilterstop-event"></a>ExceptionFilterStop イベント

このイベントは、マネージ例外のフィルター処理が終了したときに生成されます。

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`ExceptionKeyword` (0x8000)|情報提供 (4)|

 次の表にイベント情報を示します。

|Event|イベント ID|いつ発生するか|
|-----------|--------------|-----------------|
|`ExceptionFilteringStart`|255|マネージ例外のフィルター処理が終了したとき。|

## <a name="exceptionthrownstop-event"></a>ExceptionThrownStop イベント

このイベントは、スローされたマネージ例外の処理がランタイムによって完了したときに生成されます。

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`ExceptionKeyword` (0x8000)|情報提供 (4)|
  
 次の表にイベント情報を示します。

|Event|イベント ID|いつ発生するか|
|-----------|--------------|-----------------|
|`ExceptionThrownStop`|256|マネージ例外のフィルター処理が終了したとき。|
