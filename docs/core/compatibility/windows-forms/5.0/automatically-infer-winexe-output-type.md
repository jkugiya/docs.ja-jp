---
title: '破壊的変更: WPF アプリと WinForms アプリで OutputType が WinExe に設定されている'
description: .NET SDK 5.0.100 での破壊的変更について学習します。Windows フォーム アプリで OutputType が自動的に WinExe に設定されます。
ms.date: 02/08/2021
ms.openlocfilehash: 565007e9ce6be289456afc9facbd4c555a1110bd
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256180"
---
# <a name="outputtype-set-to-winexe-for-wpf-and-winforms-apps"></a>WPF アプリと WinForms アプリで OutputType が WinExe に設定されている

`OutputType` は、Windows Presentation Foundation (WPF) アプリと Windows フォーム アプリでは、自動的に `WinExe` に設定されます。 `OutputType` が `WinExe` に設定されている場合、アプリの実行時にコンソール ウィンドウは開きません。

## <a name="change-description"></a>変更内容

以前のバージョンの .NET SDK では、プロジェクト ファイルで `OutputType` に指定されている値が使用されます。 次に例を示します。

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

.NET SDK の 5.0.100 バージョンからは、`OutputType` を `Exe` に設定すると、.NET Framework を含むあらゆるフレームワーク バージョンを対象にする WPF アプリと Windows フォーム アプリの場合、自動的に `WinExe` に変更されます。

```xml
<PropertyGroup>
  <OutputType>WinExe</OutputType>
</PropertyGroup>
```

 `OutputType` がプロジェクト ファイルで指定されていない場合は、既定値の `Library` になり、その値は変更されません。

## <a name="reason-for-change"></a>変更理由

WPF アプリまたは Windows フォーム アプリの実行時に、ほとんどのユーザーがコンソール ウィンドウを開かないことを前提としています。 さらに、[これらの種類のアプリケーションでは .NET SDK が使用され](sdk-and-target-framework-change.md) (Windows Desktop SDK が使用されるのではなく)、正しい既定値が設定されるようになります。 さらに、iOS と Android を対象としたサポートが追加されると、これらすべてで同じ出力の種類が使用される場合に、複数のプラットフォーム間で複数のターゲットを指定することが容易になります。

## <a name="version-introduced"></a>導入されたバージョン

.NET 5.0.100

## <a name="recommended-action"></a>推奨アクション

ユーザー側の対応は必要ありません。 ただし、以前の動作に戻す場合は、プロジェクト ファイルの `DisableWinExeOutputInference` プロパティを `true` に設定します。

```xml
<DisableWinExeOutputInference>true</DisableWinExeOutputInference>
```

## <a name="affected-apis"></a>影響を受ける API

API 分析では検出できません。

<!--

### Affected APIs

Not detectable via API analysis.

### Category

- Windows Forms
- Windows Presentation Framework (WPF)

-->
