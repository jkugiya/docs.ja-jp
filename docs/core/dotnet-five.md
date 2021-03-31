---
title: .NET 5 の新機能
description: .Net Core の次世代のクロス プラットフォームおよびオープンソースの開発プラットフォームである .NET 5 について説明します。
ms.date: 11/30/2020
ms.topic: overview
ms.author: dapine
author: IEvangelist
ms.openlocfilehash: 7984f235044db5dfc7533343e7d43cd7745fba33
ms.sourcegitcommit: 88fbb019b84c2d044d11fb4f6004aec07f2b25b1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2021
ms.locfileid: "103412178"
---
# <a name="whats-new-in-net-5"></a>.NET 5 の新機能

.NET 5.0 は、.NET Core 3.1 の次のメジャー リリースです。 この新しいリリースは、次の 2 つの理由から .NET Core 4.0 ではなく、.NET 5.0 と名付けられています。

- バージョン番号 4.x は、NET Framework 4.x との混同を避けるために省略しました。
- 以降の .NET の主要な実装であることを強調するために、名前から "Core" を削除しました。 .NET 5.0 では、.NET Core または .NET Framework よりも多くの種類のアプリと多くのプラットフォームをサポートしています。

ASP.NET Core 5.0 は .NET 5.0 に基づいていますが、ASP.NET MVC 5 との混同を避けるために、"Core" という名前を引き続き使用しています。 同様に、Entity Framework Core 5.0 も、Entity Framework 5 および 6 との混同を避けるために、"Core" という名前を引き続き使用しています。

.NET 5.0 には、.NET Core 3.1 と比較し、次の機能強化と新機能があります。

- [C# の更新](#c-updates)
- [F# の更新](#f-updates)
- [Visual Basic の更新](#visual-basic-updates)
- [System.Text.Json の新機能](#systemtextjson-new-features)
- [単一ファイル アプリ](deploying/single-file.md)
- [アプリのトリミング](https://devblogs.microsoft.com/dotnet/app-trimming-in-net-5)
- Windows ARM64 および ARM64 組み込み
- ダンプ デバッグでのツールのサポート
- ランタイム ライブラリの 80% に、[null 許容参照型](../csharp/nullable-references.md)の注釈が付けられています
- パフォーマンスの向上:
  - [ガベージ コレクション (GC)](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5/#gc)
  - [System.Text.Json](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5/#json)
  - [System.Text.RegularExpressions](https://devblogs.microsoft.com/dotnet/regex-performance-improvements-in-net-5)
  - [Async ValueTask プール](https://devblogs.microsoft.com/dotnet/async-valuetask-pooling-in-net-5)
  - [コンテナー サイズの最適化](https://github.com/dotnet/dotnet-docker/issues/1814#issuecomment-625294750)
  - [その他の多数の領域](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5)

## <a name="net-50-doesnt-replace-net-framework"></a>.NET 5.0 は .NET Framework の後継ではない

.Net 5.0 は今後の .NET の主要な実装であり、.NET Framework 4.x は引き続きサポートされます。

次のテクノロジを .NET Framework から .NET 5.0 に移植する予定はありませんが、.NET 5.0 には代替手段があります。

| テクノロジ            | 推奨される代替手段                                                                         |
|-----------------------|-------------------------------------------------------------------------------------------------|
| Web フォーム             | ASP.NET Core [Blazor](/aspnet/core/blazor) または [Razor Pages](/aspnet/core/tutorials/razor-pages) |
| Windows Workflow (WF) | [オープンソース CoreWF](https://github.com/UiPath-Open/corewf) または [Elsa ワークフロー](https://github.com/elsa-workflows/elsa-core) |

### <a name="windows-communication-foundation"></a>Windows Communication Foundation

元の [Windows Communication Foundation (WCF)](../framework/wcf/index.md) の実装は、Windows でのみサポートされていました。 ただし、クライアント ポートが .NET Foundation から提供されています。 これは、完全に[オープンソース](https://github.com/dotnet/wcf)であり、クロス プラットフォームで、Microsoft でサポートされています。 コア NuGet パッケージの一覧は次のとおりです。

- [System.ServiceModel.Duplex](https://www.nuget.org/packages/System.ServiceModel.Duplex)
- [System.ServiceModel.Federation](https://www.nuget.org/packages/System.ServiceModel.Federation)
- [System.ServiceModel.Http](https://www.nuget.org/packages/System.ServiceModel.Http)
- [System.ServiceModel.NetTcp](https://www.nuget.org/packages/System.ServiceModel.NetTcp)
- [System.ServiceModel.Primitives](https://www.nuget.org/packages/System.ServiceModel.Primitives)
- [System.ServiceModel.Security](https://www.nuget.org/packages/System.ServiceModel.Security)

前述のクライアント ライブラリを補完するサーバー コンポーネントは、コミュニティで管理されています。 この GitHub リポジトリは、[Corewcf](https://github.com/CoreWCF/CoreWCF) にあります。 このサーバー コンポーネントは、Microsoft では正式にサポートされて _いません_。 WCF の代わりに、[gRPC](/aspnet/core/grpc) を使用することを検討してください。

## <a name="net-50-doesnt-replace-net-standard"></a>.NET 5.0 は .NET Standard の後継ではない

新しいアプリケーションを開発する場合、`net5.0` ターゲット フレームワーク モニカー (TFM) を、クラス ライブラリを含むすべての種類のプロジェクトに指定できます。 `net5.0` TFM を使用するだけで、簡単に .NET 5 とワークロードを共有できます。

.NET 5.0 アプリおよびライブラリでは、`netcoreapp` と `netstandard` の TFM の組みが `net5.0` ターゲット フレームワーク モニカー (TFM) に置き換わっています。 ただし、.NET Framework、.NET Core、および .NET 5 の各ワークロードと同じコードを使用する予定の場合は、`netstandard2.0` をお使いの TFM として指定します。 詳細については、「[.NET Standard](../standard/net-standard.md)」をご覧ください。

## <a name="c-updates"></a>C# の更新

.NET 5 アプリを記述する開発者は、C# の最新バージョンと機能を使用できます。 .NET 5 は、この言語に多数の新機能が取り入れられた C# 9 とペアになっています。 次にいくつか主要なものを紹介します。

- レコード: 値ベースの等値セマンティクスを使用する参照型と、新しい `with` 式でサポートされる非破壊的な変化。
- リレーショナル パターン マッチング: 論理パターン (`and`、`or`、`not` の新しいキーワード) を含む比較評価および式のための、パターン マッチング機能の関係演算子への拡張。
- 最上位レベルのステートメント: C# の採用と学習を加速するために、`Main` メソッドを省略でき、次のような単純なアプリケーションが許可されています。

   ```csharp
   System.Console.Write("Hello world!");
   ```

- 関数ポインター: `ldftn` および `calli` の中間言語 (IL) オペコードを公開する言語構成要素。

利用可能な C# 9 の機能の詳細については、「[C# 9 の新機能](../csharp/whats-new/csharp-9.md)」を参照してください。

### <a name="source-generators"></a>ソース ジェネレーター

開発者のプロジェクトでは、C# のいくつかの主要な新機能に加え、ソース ジェネレーターが使用されるようになっています。 ソース ジェネレーターを使用すると、コンパイル時に実行されるコードでお使いのプログラムを検査して、お使いのコードの残りの部分と共にコンパイルされる追加のファイルを生成できます。

ソース ジェネレーターの詳細については、「[Introducing C# source generators](https://devblogs.microsoft.com/dotnet/introducing-c-source-generators)」 (C# のソース ジェネレーターの概要)、および [C# のソース ジェネレーターのサンプル](https://devblogs.microsoft.com/dotnet/new-c-source-generator-samples)に関するページを参照してください。

## <a name="f-updates"></a>F# の更新

F# は .NET の関数型のプログラミング言語であり、.NET 5 で開発者は、F# 5 を使用できます。 F# 5 の新機能をいくつか紹介します。

### <a name="interpolated-strings"></a>挿入文字列

C# の補間文字列と同様に、また JavaScript でも、F# で基本の文字列補間がサポートされています。

```fsharp
let name = "David"
let age = 36
let message = $"{name} is {age} years old."
```

基本の文字列補間に加え、型指定の補間があります。 型指定の補間では、指定した型が書式指定子と一致する必要があります。

```fsharp
let name = "David"
let age = 36
let message = $"%s{name} is %d{age} years old."
```

これは、タイプセーフな入力に基づいて文字列を書式設定する [`sprintf`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-printfmodule.html#sprintf) 関数と似ています。 <!-- For more information, see [What's new in F# 5](fsharp/whats-new/fsharp-50.md). -->

## <a name="visual-basic-updates"></a>Visual Basic の更新

.NET 5 の Visual Basic には、新しい言語機能がありません。 しかし、.NET 5 の Visual Basic では、次もサポートしています。

| 説明                            | `dotnet new` パラメーター |
|----------------------------------------|------------------------|
| コンソール アプリケーション                    | `console`              |
| クラス ライブラリ                          | `classlib`             |
| WPF アプリケーション                        | `wpf`                  |
| WPF クラス ライブラリ                      | `wpflib`               |
| WPF カスタム コントロール ライブラリ             | `wpfcustomcontrollib`  |
| WPF ユーザー コントロール ライブラリ               | `wpfusercontrollib`    |
| Windows フォーム (WinForms) アプリケーション   | `winforms`             |
| Windows フォーム (WinForms) クラス ライブラリ | `winformslib`          |
| 単体テスト プロジェクト                      | `mstest`               |
| NUnit 3 テスト プロジェクト                   | `nunit`                |
| NUnit 3 テスト項目                      | `nunit-test`           |
| xUnit テスト プロジェクト                     | `xunit`                |

.NET CLI のプロジェクト テンプレートの詳細については、「[`dotnet new`](tools/dotnet-new.md)」を参照してください。

## <a name="systemtextjson-new-features"></a>System.Text.Json の新機能

[System.Text.Js](../standard/serialization/system-text-json-overview.md) に、またこれを対象とした新機能があります。

- [参照を保持し、循環参照を処理する](../standard/serialization/system-text-json-preserve-references.md)
- [HttpClient と HttpContent の拡張メソッド](../standard/serialization/system-text-json-how-to.md#httpclient-and-httpcontent-extension-methods)
- [引用符で囲まれた数値を許可または記述する](../standard/serialization/system-text-json-invalid-json.md#allow-or-write-numbers-in-quotes)
- [不変の型と C# 9 レコードのサポート](../standard/serialization/system-text-json-immutability.md)
- [パブリックでないプロパティ アクセサーのサポート](../standard/serialization/system-text-json-immutability.md)
- [フィールドのサポート](../standard/serialization/system-text-json-how-to.md#include-fields)
- [プロパティの条件付きでの無視](../standard/serialization/system-text-json-ignore-properties.md)
- [ディクショナリでの文字列以外のキーのサポート](../standard/serialization/system-text-json-migrate-from-newtonsoft-how-to.md#dictionary-with-non-string-key)
- [カスタム コンバーターによる null の処理の許可](../standard/serialization/system-text-json-converters-how-to.md#handle-null-values)
- [JsonSerializerOptions をコピーする](../standard/serialization/system-text-json-configure-options.md#copy-jsonserializeroptions)
- [Web の既定値を使用した JsonSerializerOptions の作成](../standard/serialization/system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)

## <a name="see-also"></a>関連項目

- [1 つの .NET への道のり](https://channel9.msdn.com/Events/Build/2020/BOD106)
- [.NET 5 のパフォーマンスの向上](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5)
- [.NET SDK をダウンロードする](https://dotnet.microsoft.com/download)
