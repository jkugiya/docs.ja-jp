---
title: 破壊的変更:PublishDepsFilePath の動作の変更
description: PublishDepsFilePath MSBuild プロパティがシングルファイル アプリケーションに対して空になるという、.NET 5 の破壊的変更について学習します。
ms.date: 09/17/2020
ms.openlocfilehash: 845073e73ec6bdf820f28ace487d9ae4d04d0790
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872926"
---
# <a name="publishdepsfilepath-behavior-change"></a>PublishDepsFilePath の動作の変更

`PublishDepsFilePath` MSBuild プロパティは、単一ファイル アプリケーションの場合は空です。 また、非単一ファイル アプリケーションの場合は、ビルドの後半まで、*deps. json* ファイルを出力ディレクトリにコピーすることはできません。

## <a name="version-introduced"></a>導入されたバージョン

5.0

## <a name="change-description"></a>変更の説明

以前のバージョンの .NET での `PublishDepsFilePath` MSBuild プロパティは、非単一ファイル アプリケーションの場合は出力ディレクトリ内にあるアプリの *deps. json* ファイルへのパス、単一ファイル アプリの場合は中間ディレクトリ内のパスです。

.NET 5 以降では、単一ファイル アプリケーションの場合は `PublishDepsFilePath` が空になり、新しい `IntermediateDepsFilePath` プロパティによって中間ディレクトリ内に *deps.json* の場所が指定されます。 また、非単一ファイル アプリケーションの場合は、ビルドの後半まで、*deps. json* ファイルを出力ディレクトリ (すなわち、`PublishDepsFilePath` によって指定されるパス) にコピーすることはできません。

## <a name="reason-for-change"></a>変更理由

この変更は、次の 2 つの理由で行われました。

- .NET 5 で[機能強化された単一ファイル アプリ](https://github.com/dotnet/designs/blob/main/accepted/2020/single-file/design.md)をサポートするための発行ロジックのリファクタリングに起因します。

- 単一ファイル アプリでは、*deps.json* がバンドルされた後に *deps.json* ファイルの書き換えを試行するターゲットに対する保護を支援するためです。これにより、アプリは、通知なしで影響を受けることがありません。 このため、単一ファイル アプリケーションの場合、`PublishDepsFilePath` が空になります。

## <a name="recommended-action"></a>推奨アクション

*deps. json* ファイルを書き換えるターゲットは通常、`IntermediateDepsFilePath` プロパティを使用して書き換えを行います。

## <a name="affected-apis"></a>影響を受ける API

N/A

<!--

### Affected APIs

Not detectable via API analysis.

### Category

MSBuild

-->
