---
title: .NET でカスタム構成プロバイダーを実装する
description: .NET アプリケーションにカスタム構成プロバイダーを実装する方法について説明します。
author: IEvangelist
ms.author: dapine
ms.date: 12/04/2020
ms.topic: how-to
ms.openlocfilehash: 22e46b7df8b02421633d6be251d990879baa8b2b
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2020
ms.locfileid: "102402023"
---
# <a name="implement-a-custom-configuration-provider-in-net"></a>.NET でカスタム構成プロバイダーを実装する

JSON、XML、INI ファイルなどの一般的な構成ソースに使用できる[構成プロバイダー](configuration-providers.md)は多数あります。 使用できるプロバイダーの 1 つがアプリケーションのニーズに合わない場合は、必要に応じてカスタム構成プロバイダーを実装します。 この記事では、構成ソースとしてデータベースに依存するカスタム構成プロバイダーを実装する方法について説明します。

## <a name="custom-configuration-provider"></a>カスタム構成プロバイダー

このサンプル アプリは、[Entity Framework (EF) Core](/ef/core) を使用してデータベースから構成のキーと値のペアを読み取る、基本的な構成プロバイダーを作成する方法を示します。

プロバイダーの特徴は次のとおりです。

- EF のメモリ内データベースは、デモンストレーションのために使用されます。 接続文字列を必要とするデータベースを使用するには、第 2 の `ConfigurationBuilder` を実装して、別の構成プロバイダーからの接続文字列を指定します。
- プロバイダーは、起動時に、構成にデータベース テーブルを読み取ります。 プロバイダーは、キー単位でデータベースを照会しません。
- 変更時に再度読み込む機能は実装されていません。このため、アプリの起動後にデータベースを更新しても、アプリの構成には影響がありません。

データベースに構成値を格納するための `Settings` レコード型のエンティティを定義します。 たとえば、*Models* フォルダーに *Settings.cs* ファイルを追加できます。

:::code language="csharp" source="snippets/configuration/custom-provider/Models/Settings.cs":::

レコード型については、[C# 9 でのレコード型](../../csharp/whats-new/csharp-9.md#record-types)に関する記事を参照してください。

構成した値を格納し、その値にアクセスするための `EntityConfigurationContext` を追加します。

*Providers/EntityConfigurationContext.cs*:

:::code language="csharp" source="snippets/configuration/custom-provider/Providers/EntityConfigurationContext.cs":::

<xref:Microsoft.Extensions.Configuration.IConfigurationSource> を実装するクラスを作成します。

*Providers/EntityConfigurationSource.cs*:

:::code language="csharp" source="snippets/configuration/custom-provider/Providers/EntityConfigurationSource.cs":::

<xref:Microsoft.Extensions.Configuration.ConfigurationProvider> から継承して、カスタム構成プロバイダーを作成します。 データベースが空だった場合、構成プロバイダーはこれを初期化します。 構成キーでは大文字と小文字が区別されないため、データベースの初期化に使用されるディクショナリは、大文字と小文字を区別しない比較子 ([StringComparer.OrdinalIgnoreCase](xref:System.StringComparer.OrdinalIgnoreCase)) を使用して作成されます。

*Providers/EntityConfigurationProvider.cs*:

:::code language="csharp" source="snippets/configuration/custom-provider/Providers/EntityConfigurationProvider.cs":::

`AddEntityConfiguration` 拡張メソッドを使用すると、<xref:Microsoft.Extensions.Configuration.IConfigurationBuilder> インスタンスに構成ソースを追加できます。

*Extensions/ConfigurationBuilderExtensions.cs*:

:::code language="csharp" source="snippets/configuration/custom-provider/Extensions/ConfigurationBuilderExtensions.cs":::

次のコードでは、*Program.cs* でカスタムの `EntityConfigurationProvider` を使用する方法を示します。

:::code language="csharp" source="snippets/configuration/custom-provider/Program.cs" highlight="27-28":::

## <a name="see-also"></a>関連項目

- [.NET での構成](configuration.md)
- [.NET の構成プロバイダー](configuration-providers.md)
