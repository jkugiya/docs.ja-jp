---
title: .NET でのツールと診断
author: IEvangelist
description: .NET 開発者が使用できる開発ツールと診断ツールについて説明します。
ms.author: dapine
ms.date: 10/21/2020
ms.topic: overview
ms.openlocfilehash: 07c1a161a0bb429403db6852fe77749d83c19ec0
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "96593833"
---
# <a name="tools-and-diagnostics-in-net"></a>.NET でのツールと診断

この記事では、.NET 開発者が使用できるさまざまなツールについて説明します。 .NET には、コマンドライン インターフェイス (CLI) を備えた堅牢なソフトウェア開発キット (SDK) があります。 .NET CLI では、.NET 対応の統合開発環境 (IDE) 全体で多くの機能が有効になります。 この記事では、パフォーマンスの問題、メモリ リーク、高 CPU、デッドロックを診断するための NET CLI ツール、コード分析のためのツール サポートなどの生産性機能に関するリソースも提供します。

## <a name="net-sdk"></a>.NET SDK

.NET SDK には、.NET ランタイムと .NET CLI の両方が含まれています。 Windows、Linux、macOS、または Docker 用の [.NET SDK](https://dotnet.microsoft.com/download) をダウンロードできます。 詳細については、[.NET SDK の概要](../core/sdk.md)に関するページを参照してください。

## <a name="net-cli"></a>.NET CLI

.NET CLI は、.NET アプリケーションを開発、ビルド、実行、発行するためのクロスプラットフォーム ツールチェーンです。 .NET CLI は、.NET SDK に含まれています。 詳細については、[.NET CLI の概要](../core/tools/index.md)に関するページを参照してください。

## <a name="ides"></a>IDE

.NET アプリケーションは、[Visual Studio Code](https://code.visualstudio.com/docs)、 [Visual Studio](/visualstudio/windows)、または [Visual Studio for Mac](/visualstudio/mac) で作成できます。 クラウドを利用した開発環境の詳細については、[Visual Studio Codespaces](/visualstudio/codespaces/overview/what-is-vsonline)に関するページを参照してください。

## <a name="additional-tools"></a>その他のツール

.NET では、より一般的なツールだけでなく、特定のシナリオ用のツールも用意されています。 ユース ケースの一部には、.NET SDK または .NET ランタイムのアンインストール、Windows Communication Foundation (WCF) メタデータの取得、プロキシ ソース コードの生成、XML のシリアル化などがあります。 詳細については、「[.NET の追加ツールの概要](../core/additional-tools/index.md)」を参照してください。

## <a name="diagnostics-and-instrumentation"></a>診断とインストルメンテーション

.NET 開発者は、一般的なパフォーマンス診断ツールを利用して、アプリのパフォーマンスの監視、トレースによるアプリのプロファイリング、パフォーマンス メトリックの収集、およびダンプ ファイルの分析を行うことができます。 イベント カウンターを使用してパフォーマンス メトリックを収集し、プロファイリング ツールを使用して、アプリの動作についての分析情報を得ることができます。 詳細については、[.NET 診断ツール](../core/diagnostics/index.md)に関するページを参照してください。

## <a name="code-analysis"></a>コード分析

.NET のコンパイラ プラットフォーム (Roslyn) アナライザーでは、お使いの C# または Visual Basic コードについて、コード品質やコード スタイルに関する問題を検査できます。 詳細については、「[.NET ソース コード分析の概要](code-analysis/overview.md)」を参照してください。
