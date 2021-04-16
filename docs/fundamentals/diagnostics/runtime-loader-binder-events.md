---
title: ローダーおよびバインダー ランタイム イベント
description: アセンブリ ローダーとバインダーに関する情報を収集するローダーおよびバインダー ETW イベントに固有の診断情報を収集する .NET ランタイム イベントを参照してください。
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- Assembly Loader events (CoreCLR)
- Assembly Binder events (CoreCLR)
- ETW, EventPipe, LTTng assembly loader and binder events (CoreCLR)
ms.openlocfilehash: 2284c580482f6b93a77f44649225ff7e5485666a
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "96594109"
---
# <a name="net-runtime-loader-and-binder-events"></a>.NET ランタイム ローダーとバインダー イベント

これらのイベントは、アセンブリ、およびモジュールのロードとアンロードに関連する情報を収集します。 診断のためにこれらのイベントを使用する方法の詳細については、[.NET アプリケーションのログ記録とトレース](../../core/diagnostics/logging-tracing.md)に関するページを参照してください。

|イベントを発生させるキーワード|Event|Level|
|-----------------------------------|-----------|-----------|
|`LoaderKeyword` (0x8)|`DomainModuleLoad_V1`|情報提供 (4)|

|Event|イベント ID|説明|
|-----------|--------------|-----------------|
|`DomainModuleLoad_V1`|151|モジュールがアプリケーション ドメインに読み込まれるときに発生します。|

## <a name="moduleload_v2-event"></a>ModuleLoad_V2 イベント

|イベントを発生させるキーワード|Event|Level|
|-----------------------------------|-----------|-----------|
|`LoaderKeyword` (0x8)|`DomainModuleLoad_V1`|情報提供 (4)|

|Event|イベント ID|説明|
|-----------|--------------|-----------------|
|`ModuleLoad_V2`|152|プロセスの有効期間中にモジュールが読み込まれるときに発生します。|

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`ModuleID`|`win:UInt64`|モジュールの一意な ID。|
|`AssemblyID`|`win:UInt64`|このモジュールが存在するアセンブリの ID。|
|`ModuleFlags`|`win:UInt32`|0x1: ドメインに中立的なモジュール。<br /><br /> 0x2: モジュールにネイティブ イメージがある。<br /><br /> 0x4: 動的モジュール。<br /><br /> 0x8: マニフェスト モジュール。|
|`Reserved1`|`win:UInt32`|予約済みのフィールド。|
|`ModuleILPath`|`win:UnicodeString`|モジュールの Common Intermediate Language (CIL) のイメージのパス、またはそれが動的アセンブリ (null で終わる) である場合は動的モジュール名。|
|`ModuleNativePath`|`win:UnicodeString`|モジュール ネイティブ イメージがある場合、そのパス (null で終わる)。|
|`ClrInstanceID`|`win:UInt16`|CLR または CoreCLR のインスタンスの一意の ID。|
|`ManagedPdbSignature`|`win:GUID`|このモジュールに一致するマネージド プログラム データベース (PDB) の GUID の署名。|
|`ManagedPdbAge`|`win:UInt32`|このモジュールに一致する管理対象 PDB に書き込まれた期間を表す数値。|
|`ManagedPdbBuildPath`|`win:UnicodeString`|このモジュールに一致する管理対象の PDB が構成されている場所へのパス。 これは、ファイル名だけの場合もあります。|
|`NativePdbSignature`|`win:GUID`|このモジュールに一致するネイティブ イメージ ジェネレーター (NGen) PDB の GUID の署名 (該当する場合)。|
|`NativePdbAge`|`win:UInt32`|このモジュールに一致する NGen PDB に書き込まれた期間を表す数値 (該当する場合)。|
|`NativePdbBuildPath`|`win:UnicodeString`|このモジュールに一致する管理対象の NGen PDB が構成されている場所へのパス (該当する場合)。 これは、ファイル名だけの場合もあります。|

## <a name="moduleunload_v2-event"></a>ModuleUnload_V2 イベント

|イベントを発生させるキーワード|Event|Level|
|-----------------------------------|-----------|-----------|
|`LoaderKeyword` (0x8)|`DomainModuleLoad_V1`|情報提供 (4)|

|Event|イベント ID|説明|
|-----------|--------------|-----------------|
|`ModuleUnload_V2`|153|プロセスの有効期間中にモジュールがアンロードされるときに発生します。|

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`ModuleID`|`win:UInt64`|モジュールの一意な ID。|
|`AssemblyID`|`win:UInt64`|このモジュールが存在するアセンブリの ID。|
|`ModuleFlags`|`win:UInt32`|0x1: ドメインに中立的なモジュール。<br /><br /> 0x2: モジュールにネイティブ イメージがある。<br /><br /> 0x4: 動的モジュール。<br /><br /> 0x8: マニフェスト モジュール。|
|`Reserved1`|`win:UInt32`|予約済みのフィールド。|
|`ModuleILPath`|`win:UnicodeString`|モジュールの Common Intermediate Language (CIL) のイメージのパス、またはそれが動的アセンブリ (null で終わる) である場合は動的モジュール名。|
|`ModuleNativePath`|`win:UnicodeString`|モジュール ネイティブ イメージがある場合、そのパス (null で終わる)。|
|`ClrInstanceID`|``win:UInt16``|CLR または CoreCLR のインスタンスの一意の ID。|
|`ManagedPdbSignature`|`win:GUID`|このモジュールに一致するマネージド プログラム データベース (PDB) の GUID の署名。|
|`ManagedPdbAge`|`win:UInt32`|このモジュールに一致する管理対象 PDB に書き込まれた期間を表す数値。|
|`ManagedPdbBuildPath`|`win:UnicodeString`|このモジュールに一致する管理対象の PDB が構成されている場所へのパス。 これは、ファイル名だけの場合もあります。|
|`NativePdbSignature`|`win:GUID`|このモジュールに一致するネイティブ イメージ ジェネレーター (NGen) PDB の GUID の署名 (該当する場合)。|
|`NativePdbAge`|`win:UInt32`|このモジュールに一致する NGen PDB に書き込まれた期間を表す数値 (該当する場合)。|
|`NativePdbBuildPath`|`win:UnicodeString`|このモジュールに一致する管理対象の NGen PDB が構成されている場所へのパス (該当する場合)。 これは、ファイル名だけの場合もあります。|

## <a name="moduledcstart_v2-event"></a>ModuleDCStart_V2 イベント

|イベントを発生させるキーワード|Event|Level|
|-----------------------------------|-----------|-----------|
|`LoaderKeyword` (0x8)|`DomainModuleLoad_V1`|情報提供 (4)

|Event|イベント ID|説明
|-----------|--------------|-----------------|
|`ModuleDCStart_V2`|153|開始ランダウン中にモジュールを列挙します。|

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`ModuleID`|`win:UInt64`|モジュールの一意な ID。|
|`AssemblyID`|`win:UInt64`|このモジュールが存在するアセンブリの ID。|
|`ModuleFlags`|`win:UInt32`|0x1: ドメインに中立的なモジュール。<br /><br /> 0x2: モジュールにネイティブ イメージがある。<br /><br /> 0x4: 動的モジュール。<br /><br /> 0x8: マニフェスト モジュール。|
|`Reserved1`|`win:UInt32`|予約済みのフィールド。|
|`ModuleILPath`|`win:UnicodeString`|モジュールの Common Intermediate Language (CIL) のイメージのパス、またはそれが動的アセンブリ (null で終わる) である場合は動的モジュール名。|
|`ModuleNativePath`|`win:UnicodeString`|モジュール ネイティブ イメージがある場合、そのパス (null で終わる)。|
|`ClrInstanceID`|`win:UInt16`|CLR または CoreCLR のインスタンスの一意の ID。|
|`ManagedPdbSignature`|`win:GUID`|このモジュールに一致するマネージド プログラム データベース (PDB) の GUID の署名。|
|`ManagedPdbAge`|`win:UInt32`|このモジュールに一致する管理対象 PDB に書き込まれた期間を表す数値。|
|`ManagedPdbBuildPath`|`win:UnicodeString`|このモジュールに一致する管理対象の PDB が構成されている場所へのパス。 これは、ファイル名だけの場合もあります。|
|`NativePdbSignature`|`win:GUID`|このモジュールに一致するネイティブ イメージ ジェネレーター (NGen) PDB の GUID の署名 (該当する場合)。|
|`NativePdbAge`|`win:UInt32`|このモジュールに一致する NGen PDB に書き込まれた期間を表す数値 (該当する場合)。|
|`NativePdbBuildPath`|`win:UnicodeString`|このモジュールに一致する管理対象の NGen PDB が構成されている場所へのパス (該当する場合)。 これは、ファイル名だけの場合もあります。|

## <a name="moduledcend_v2-event"></a>ModuleDCEnd_V2 イベント

|イベントを発生させるキーワード|Event|Level|
|-----------------------------------|-----------|-----------|
|`LoaderKeyword` (0x8)|`DomainModuleLoad_V1`|情報提供 (4)|

|Event|イベント ID|説明|
|-----------|--------------|-----------------|
|`ModuleDCEnd_V2`|154|終了ランダウン中にモジュールを列挙します。|

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`ModuleID`|`win:UInt64`|モジュールの一意な ID。|
|`AssemblyID`|`win:UInt64`|このモジュールが存在するアセンブリの ID。|
|`ModuleFlags`|`win:UInt32`|0x1: ドメインに中立的なモジュール。<br /><br /> 0x2: モジュールにネイティブ イメージがある。<br /><br /> 0x4: 動的モジュール。<br /><br /> 0x8: マニフェスト モジュール。|
|`Reserved1`|`win:UInt32`|予約済みのフィールド。|
|`ModuleILPath`|`win:UnicodeString`|モジュールの Common Intermediate Language (CIL) のイメージのパス、またはそれが動的アセンブリ (null で終わる) である場合は動的モジュール名。|
|`ModuleNativePath`|`win:UnicodeString`|モジュール ネイティブ イメージがある場合、そのパス (null で終わる)。|
|`ClrInstanceID`|`win:UInt16`|CLR または CoreCLR のインスタンスの一意の ID。|
|`ManagedPdbSignature`|`win:GUID`|このモジュールに一致するマネージド プログラム データベース (PDB) の GUID の署名。|
|`ManagedPdbAge`|`win:UInt32`|このモジュールに一致する管理対象 PDB に書き込まれた期間を表す数値。|
|`ManagedPdbBuildPath`|`win:UnicodeString`|このモジュールに一致する管理対象の PDB が構成されている場所へのパス。 これは、ファイル名だけの場合もあります。|
|`NativePdbSignature`|`win:GUID`|このモジュールに一致するネイティブ イメージ ジェネレーター (NGen) PDB の GUID の署名 (該当する場合)。|
|`NativePdbAge`|`win:UInt32`|このモジュールに一致する NGen PDB に書き込まれた期間を表す数値 (該当する場合)。|
|`NativePdbBuildPath`|`win:UnicodeString`|このモジュールに一致する管理対象の NGen PDB が構成されている場所へのパス (該当する場合)。 これは、ファイル名だけの場合もあります。|

## <a name="assemblyload_v1-event"></a>AssemblyLoad_V1 イベント

|イベントを発生させるキーワード|Event|Level|
|-----------------------------------|-----------|-----------|
|`LoaderKeyword` (0x8)|`DomainModuleLoad_V1`|情報提供 (4)|

|Event|イベント ID|説明|
|-----------|--------------|-----------------|
|`AssemblyLoad_V1`|154|アセンブリが読み込まれたときに発生します。|

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`AssemblyID`|`win:UInt64`|アセンブリの一意の ID。|
|`AppDomainID`|`win:UInt64`|このアセンブリのドメインの ID。|
|`BindingID`|`win:UInt64`|アセンブリ バインディングを一意に識別する ID。|
|`AssemblyFlags`|`win:UInt32`|0x1: ドメインに中立的なアセンブリ。<br /><br /> 0x2: 動的アセンブリ。<br /><br /> 0x4: アセンブリにネイティブ イメージがある。<br /><br /> 0x8: 収集可能なアセンブリ。|
|`AssemblyName`|`win:UnicodeString`|完全修飾アセンブリ名。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR のインスタンスの一意の ID。

## <a name="assemblyunload_v1-event"></a>AssemblyUnload_V1 イベント

|イベントを発生させるキーワード|Event|Level|
|-----------------------------------|-----------|-----------|
|`LoaderKeyword` (0x8)|`DomainModuleLoad_V1`|情報提供 (4)|

|Event|イベント ID|説明|
|-----------|--------------|-----------------|
|`FireAssemblyUnload_V1`|155|アセンブリが読み込まれたときに発生します。|

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`AssemblyID`|`win:UInt64`|アセンブリの一意の ID。|
|`AppDomainID`|`win:UInt64`|このアセンブリのドメインの ID。|
|`BindingID`|`win:UInt64`|アセンブリ バインディングを一意に識別する ID。|
|`AssemblyFlags`|`win:UInt32`|0x1: ドメインに中立的なアセンブリ。<br /><br /> 0x2: 動的アセンブリ。<br /><br /> 0x4: アセンブリにネイティブ イメージがある。<br /><br /> 0x8: 収集可能なアセンブリ。|
|`AssemblyName`|`win:UnicodeString`|完全修飾アセンブリ名。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR のインスタンスの一意の ID。|

## <a name="assemblydcstart_v1-event"></a>AssemblyDCStart_V1 イベント

|イベントを発生させるキーワード|Event|Level|
|-----------------------------------|-----------|-----------|
|`LoaderKeyword` (0x8)|`DomainModuleLoad_V1`|情報提供 (4)|

|Event|イベント ID|説明|
|-----------|--------------|-----------------|
|`AssemblyDCStart_V1`|155|開始ランダウン中にアセンブリを列挙します。|

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`AssemblyID`|`win:UInt64`|アセンブリの一意の ID。|
|`AppDomainID`|`win:UInt64`|このアセンブリのドメインの ID。|
|`BindingID`|`win:UInt64`|アセンブリ バインディングを一意に識別する ID。|
|`AssemblyFlags`|`win:UInt32`|0x1: ドメインに中立的なアセンブリ。<br /><br /> 0x2: 動的アセンブリ。<br /><br /> 0x4: アセンブリにネイティブ イメージがある。<br /><br /> 0x8: 収集可能なアセンブリ。|
|`AssemblyName`|`win:UnicodeString`|完全修飾アセンブリ名。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR のインスタンスの一意の ID。|

## <a name="assemblyloadstart-event"></a>AssemblyLoadStart イベント

|イベントを発生させるキーワード|Event|Level|
|-----------------------------------|-----------|-----------|
|`Binder` (0x4)|`AssemblyLoadStart`|情報提供 (4)|

|Event|イベント ID|説明|
|-----------|--------------|-----------------|
|`AssemblyLoadStart`|290|アセンブリの読み込みが要求されました。

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`AssemblyName`|`win:UnicodeString`|アセンブリ名の名前。|
|`AssemblyPath`|`win:UnicodeString`|アセンブリ名のパス。|
|`RequestingAssembly`|`win:UnicodeString`|要求している ("親") アセンブリの名前。|
|`AssemblyLoadContext`|`win:UnicodeString`|アセンブリの読み込みコンテキスト。|
|`RequestingAssemblyLoadContext`|`win:UnicodeString`|要求している ("親") アセンブリの読み込みコンテキスト。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR のインスタンスの一意の ID。|

## <a name="assemblyloadstop-event"></a>AssemblyLoadStop イベント

|イベントを発生させるキーワード|Event|Level|
|-----------------------------------|-----------|-----------|
|`Binder` (0x4)|`AssemblyLoadStart`|情報提供 (4)|

|Event|イベント ID|説明|
|-----------|--------------|-----------------|
|`AssemblyLoadStart`|291|アセンブリの読み込みが要求されました。

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`AssemblyName`|`win:UnicodeString`|アセンブリ名の名前。|
|`AssemblyPath`|`win:UnicodeString`|アセンブリ名のパス。|
|`RequestingAssembly`|`win:UnicodeString`|要求している ("親") アセンブリの名前。|
|`AssemblyLoadContext`|`win:UnicodeString`|アセンブリの読み込みコンテキスト。|
|`RequestingAssemblyLoadContext`|`win:UnicodeString`|要求している ("親") アセンブリの読み込みコンテキスト。|
|`Success`|`win:Boolean`|アセンブリの読み込みが成功したかどうか。|
|`ResultAssemblyName`|`win:UnicodeString`|読み込まれたアセンブリの名前。|
|`ResultAssemblyPath`|`win:UnicodeString`|読み込まれたアセンブリのパス。|
|`Cached`|`win:UnicodeString`|読み込みがキャッシュされたかどうか。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR のインスタンスの一意の ID。|

## <a name="resolutionattempted-event"></a>ResolutionAttempted イベント

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|-----------|
|`Binder` (0x4)|情報提供 (4)|

|Event|イベント ID|説明|
|-----------|--------------|-----------------|
|`ResolutionAttempted`|292|アセンブリの読み込みが要求されました。

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`AssemblyName`|`win:UnicodeString`|アセンブリ名の名前。|
|`Stage`|`win:UInt16`|解決段階。<br/><br/>0: 読み込み中の検索。<br/><br/>1: アセンブリの読み込みコンテキスト</br><br/>2: アプリケーション アセンブリ。<br/><br/>3: 既定のアセンブリ読み込みコンテキストのフォールバック。 <br/><br/>4: サテライト アセンブリの解決。 <br/><br/>5: アセンブリの読み込みコンテキストの解決中。<br/><br/>6: AppDomain アセンブリの解決中。
|`AssemblyLoadContext`|`win:UnicodeString`|アセンブリの読み込みコンテキスト。|
|`Result`|`win:UInt16`|解決の試行結果。<br/><br/>0: 成功<br/><br/>1: アセンブリ非検出<br/><br/>2: 互換性のないバージョン<br/><br/>3: アセンブリ名不一致<br/><br/>4: 失敗<br/><br/>5: 例外|
|`ResultAssemblyName`|`win:UnicodeString`|解決されたアセンブリの名前。|
|`ResultAssemblyPath`|`win:UnicodeString`|解決されたアセンブリのパス。|
|`ErrorMessage`|`win:UnicodeString`|例外が発生した場合のエラー メッセージ。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR のインスタンスの一意の ID。|

## <a name="assemblyloadcontextresolvinghandlerinvoked-event"></a>AssemblyLoadContextResolvingHandlerInvoked イベント

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|-----------|
|`Binder` (0x4)|情報提供 (4)|

|Event|イベント ID|説明|
|-----------|--------------|-----------------|
|`AssemblyLoadContextResolvingHandlerInvoked`|293|[AssemblyLoadContext.Resolving](xref:System.Runtime.Loader.AssemblyLoadContext.Resolving) ハンドラーが呼び出された。|

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`AssemblyName`|`win:UnicodeString`|アセンブリ名の名前。|
|`HandlerName`|`win:UnicodeString`|呼び出されたハンドラーの名前。|
|`AssemblyLoadContext`|`win:UnicodeString`|アセンブリの読み込みコンテキスト。|
|`ResultAssemblyName`|`win:UnicodeString`|解決されたアセンブリの名前。|
|`ResultAssemblyPath`|`win:UnicodeString`|解決されたアセンブリのパス。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR のインスタンスの一意の ID。|

## <a name="appdomainassemblyresolvehandlerinvoked-event"></a>AppDomainAssemblyResolveHandlerInvoked イベント

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|-----------|
|`Binder` (0x4)|情報提供 (4)|

|Event|イベント ID|説明|
|-----------|--------------|-----------------|
|`AppDomainAssemblyResolveHandlerInvoked`|294|<xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> ハンドラーが呼び出された。|

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`AssemblyName`|`win:UnicodeString`|アセンブリ名の名前。|
|`HandlerName`|`win:UnicodeString`|呼び出されたハンドラーの名前。|
|`ResultAssemblyName`|`win:UnicodeString`|解決されたアセンブリの名前。|
|`ResultAssemblyPath`|`win:UnicodeString`|解決されたアセンブリのパス。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR のインスタンスの一意の ID。|

## <a name="assemblyloadfromresolvehandlerinvoked-event"></a>AssemblyLoadFromResolveHandlerInvoked イベント

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|-----------|
|`Binder` (0x4)|情報提供 (4)|

|Event|イベント ID|説明|
|-----------|--------------|-----------------|
|`AssemblyLoadFromResolveHandlerInvoked`|295|<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> ハンドラーが呼び出された。|

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`AssemblyName`|`win:UnicodeString`|アセンブリ名の名前。|
|`IsTrackedLoad`|`win:Boolean`|アセンブリの読み込みを追跡するかどうか。|
|`RequestingAssemblyPath`|`win:UnicodeString`|要求しているアセンブリのパス。|
|`ComputedRequestedAssemblyPath`|`win:UnicodeString`|要求されたアセンブリのパス。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR のインスタンスの一意の ID。|

## <a name="knownpathprobed-event"></a>KnownPathProbed イベント

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|-----------|
|`Binder` (0x4)|情報提供 (4)|

|Event|イベント ID|説明|
|-----------|--------------|-----------------|
|`KnownPathProbed`|296|既知のパスがアセンブリのためにプローブされた。|

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`FilePath`|`win:UnicodeString`|プローブされたパス。|
|`Source`|`win:UInt16`|プローブされたパスのソース。<br/><br/>0x0: アプリケーション アセンブリ。<br/><br/>0x1: アプリ ネイティブ イメージ パス。<br/><br/>0x2: アプリのパス。</br><br/>0x3: プラットフォーム リソース ルート。<br/><br/>0x4: サテライト サブディレクトリ。</br>|
|`Result`|`win:UInt32`|プローブの HRESULT。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR のインスタンスの一意の ID。|
