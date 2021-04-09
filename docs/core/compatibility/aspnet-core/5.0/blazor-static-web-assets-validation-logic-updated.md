---
title: '破壊的変更:Blazor: 静的な Web アセットの検証ロジックの更新'
description: 'ASP.NET Core 5.0 での破壊的変更について学習します。タイトル: Blazor:静的な Web アセットの検証ロジックの更新'
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: b6fb8e9a10157a97119fa07a95fb3dbb8b207214
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498153"
---
# <a name="blazor-updated-validation-logic-for-static-web-assets"></a>Blazor: 静的な Web アセットの検証ロジックの更新

ASP.NET Core 3.1 と Blazor WebAssembly 3.2 の静的な Web アセットの競合の検証で問題が発生しました。 問題は次のとおりです。

* ホストのアセットと、Razor クラスライブラリ (RCL) および Blazor WebAssembly アプリからのアセット間の適切な競合検出が阻止されました。
* ほとんどの場合、Blazor WebAssembly アプリに影響します。既定では、RCL の静的な Web 資産は `_content/$(PackageId)` プレフィックス付きで提供されるためです。

## <a name="version-introduced"></a>導入されたバージョン

5.0

## <a name="old-behavior"></a>以前の動作

開発中、RCL の静的な Web アセットは、同じホスト パス上にあるホスト プロジェクトのアセットで警告なしでオーバーライドされる可能性があります。 */folder/file.txt* で提供される静的な Web アセットを定義した RCL を考えてみましょう。 ホストによって *wwwroot/folder/file.txt* にファイルが配置された場合、RCL または Blazor WebAssembly アプリ上のファイルがこのサーバー上のファイルで警告なしでオーバーライドされます。

## <a name="new-behavior"></a>新しい動作

この問題が発生すると、ASP.NET Core によって正しく検出されます。 適切な操作を実行できるように、競合があることがユーザーに通知されます。

## <a name="reason-for-change"></a>変更理由

静的 Web アセットは、プロジェクトの *wwwroot* ホスト上のファイルによってオーバーライド可能なものとは想定されていませんでした。 これらのファイルをオーバーライドできるようにすると、診断が困難なエラーが発生するおそれがあります。 結果として、発行されたアプリで未定義の動作変更が発生する可能性があります。

## <a name="recommended-action"></a>推奨アクション

既定では、RCL ファイルがホスト上のファイルと競合する理由はありません。 RCL ファイルには `_content/${PackageId}` がプレフィックスとして付けられます。 Blazor WebAssembly ファイルはホストの URL 空間のルートに配置されるため、競合が起きやすくなります。 たとえば、Blazor WebAssembly アプリには *favicon.ico* ファイルが含まれており、これはホストもその *wwwroot* フォルダーに配置している場合があります。

競合のソースが RCL ファイルの場合、多くの場合、コードによってライブラリからプロジェクトの *wwwroot* フォルダーにアセットがコピーされていることを意味します。 ファイルをコピーするコードを記述することにより、静的な Web 資産の主な目的が損なわれます。 この目的は、新しいコンパイルをトリガーすることなくコンテンツが更新されるときに、ブラウザーで更新プログラムを取得するための基本となります。

この動作を維持し、ホスト上のファイルを維持することを選択できます。 これを行うには、カスタム MSBuild ターゲットを使用して静的 Web アセットの一覧からそのファイルを削除します。

ホスト プロジェクトのファイルではなく、RCL のファイルまたは Blazor WebAssembly アプリのファイルを使用するには、ホスト プロジェクトからそのファイルを削除します。

## <a name="affected-apis"></a>影響を受ける API

なし

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
