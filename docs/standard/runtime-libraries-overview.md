---
title: ランタイム ライブラリの概要
description: 目次の「ランタイム ライブラリ」セクションに含まれる内容について学習します。
author: tdykstra
ms.date: 11/12/2020
ms.openlocfilehash: 5a8f888e1778553e2968277738cfef5134f11589
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "103412170"
---
# <a name="runtime-libraries-overview"></a>ランタイム ライブラリの概要

[フレームワークに依存するアプリ](../core/introduction.md#deployment-models)で使用するためにコンピューターにインストールされている [.NET ランタイム](../core/introduction.md#sdk-and-runtimes)には、[ランタイム ライブラリ](glossary.md#runtime)、[フレームワーク ライブラリ](glossary.md#framework-libraries)、または[基本クラス ライブラリ (BCL)](glossary.md#bcl)と呼ばれるクラス ライブラリの包括的な標準セットがあります。 また、NuGet パッケージで提供されているランタイム ライブラリの拡張機能もあります。

これらのライブラリでは、多くの汎用およびアプリ固有の型、アルゴリズム、ユーティリティの機能の実装が提供されます。

## <a name="runtime-libraries"></a>ランタイム ライブラリ

これらのライブラリでは、基本的な型およびユーティリティの機能が提供され、他のすべての .NET クラス ライブラリの基本となります。 たとえば、<xref:System.String?displayProperty=nameWithType> クラスで、これにより文字列を操作するための API が提供されます。 別の例としては、[シリアル化ライブラリ](serialization/index.md)があります。

## <a name="extensions-to-the-runtime-libraries"></a>ランタイム ライブラリの拡張機能

一部のライブラリは、ランタイムの[共有フレームワーク](glossary.md#shared-framework)に含まれるのではなく、NuGet パッケージで提供されます。 次に例を示します。

* [Logging](../core/extensions/logging.md)
* [依存関係の挿入](../core/extensions/dependency-injection.md)
* [Configuration](../core/extensions/configuration.md)

## <a name="see-also"></a>関連項目

* [.NET の概要](../core/introduction.md)
* [.NET SDK またはランタイムのインストール](../core/install/index.yml)
* [インストールされている .NET SDK または使用するランタイムのバージョンを選択する](../core/versions/selection.md)
* [フレームワークに依存するアプリの発行](../core/deploying/index.md#publish-framework-dependent)
