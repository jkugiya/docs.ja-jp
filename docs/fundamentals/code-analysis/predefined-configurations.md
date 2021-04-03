---
title: 定義済み構成ファイル (コード分析)
description: 定義済み editorconfig ファイルとルール セット ファイルを使用して、特定の種類のコード分析をターゲットとする方法について説明します。
ms.date: 09/24/2020
ms.topic: conceptual
ms.openlocfilehash: 748ab8a9ddfcfcadeb33da877769cedac901655a
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104876592"
---
# <a name="predefined-configuration-files"></a>定義済み構成ファイル

定義済み EditorConfig ファイルと[ルール セット](/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules) ファイルを利用して、セキュリティ ルールやデザイン ルールなどのコード品質ルールのカテゴリをすばやく簡単に有効にできます。 特定のカテゴリのルールを有効にすることにより、ターゲットとなる問題や特定の条件を識別できます。 これらの定義済みファイルにアクセスするには、[Microsoft.CodeAnalysis.NetAnalyzers](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) NuGet アナライザー パッケージをインストールします。

[Microsoft.CodeAnalysis.NetAnalyzers](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) には、定義済み EditorConfig ファイルと、次のルール カテゴリのルール セットが含まれています。

- すべてのルール
- データフロー
- デザイン
- ドキュメント
- グローバリゼーション
- 相互運用性
- 保守容易性
- 名前を付ける
- パフォーマンス
- FxCop からの移植
- [信頼性]
- Security
- 使用法

これらのルールの各カテゴリには、次のための EditorConfig ファイルまたはルール セット ファイルがあります。

- カテゴリ内のすべてのルールを有効にする (および他のすべてのルールを無効にする)
- 各ルールの既定の重要度、および既定の設定で有効になっているものを使用する (および他のすべてのルールを無効にする)

> [!TIP]
> "すべてのルール" カテゴリには、すべてのルールを無効にするための追加の EditorConfig ファイルまたはルール セット ファイルがあります。 このファイルを使用すると、プロジェクト内のアナライザーの警告やエラーすべてをすぐに除去できます。

## <a name="predefined-editorconfig-files"></a>定義済み EditorConfig ファイル

Microsoft.CodeAnalysis.NetAnalyzers アナライザー パッケージ用の定義済み EditorConfig ファイルは、NuGet パッケージがインストールされた場所の *editorconfig* サブディレクトリにあります。 たとえば、すべてのセキュリティ ルールを有効にする EditorConfig ファイルは、*editorconfig/SecurityRulesEnabled/.editorconfig* にあります。

選択した *.editorconfig* ファイルを、プロジェクトのルート ディレクトリにコピーします。

## <a name="predefined-rule-sets"></a>定義済みの規則セット

Microsoft.CodeAnalysis.NetAnalyzers アナライザー パッケージ用の定義済みルール セット ファイルは、NuGet パッケージがインストールされた場所の *rulesets* サブディレクトリにあります。 たとえば、すべてのセキュリティ ルールを有効にするルール セット ファイルは、*rulesets/SecurityRulesEnabled.ruleset* にあります。 このルール セットの中の 1 つまたは複数をコピーし、プロジェクトが格納されているディレクトリに貼り付けます。

## <a name="see-also"></a>関連項目

- [アナライザーの構成](https://github.com/dotnet/roslyn-analyzers/blob/main/docs/Analyzer%20Configuration.md)
- [EditorConfig 用 .NET コード スタイル ルール オプション](code-style-rule-options.md)
