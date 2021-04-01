---
title: System.Text.Json で変更できない型と非パブリック アクセサーを使用する方法
description: .NET で JSON との間のシリアル化および逆シリアル化を行うときに、変更できない型と非パブリック アクセサーを使用する方法について説明します。
ms.date: 02/08/2021
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
dev_langs:
- csharp
- vb
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 188ed6a5582f4677eb60963af72036963b5fe821
ms.sourcegitcommit: bdbf6472de867a0a11aaa5b9384a2506c24f27d2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2021
ms.locfileid: "102206675"
---
# <a name="how-to-use-immutable-types-and-non-public-accessors-with-systemtextjson"></a>System.Text.Json で変更できない型と非パブリック アクセサーを使用する方法

この記事では、`System.Text.Json` 名前空間で不変の型、パラメーター化されたパブリック コンストラクター、および非パブリック アクセサーを使用する方法について説明します。

## <a name="immutable-types-and-records"></a>不変の型とレコード

::: zone pivot="dotnet-5-0"
`System.Text.Json` ではパラメーター化されたパブリック コンストラクターを使用できるので、不変のクラスまたは構造体を逆シリアル化できます。 クラスの場合、パラメーター化されたコンストラクターしかない場合は、そのコンストラクターが使用されます。 構造体または複数のコンストラクターを持つクラスの場合は、[[JsonConstructor]](xref:System.Text.Json.Serialization.JsonConstructorAttribute) 属性を適用することにより、使用するコンストラクターを指定します。 その属性を使用しないと、パラメーターなしのパブリック コンストラクターが存在する場合は常にそれが使用されます。 その属性は、パブリック コンストラクターでのみ使用できます。 次の例では、`[JsonConstructor]` 属性が使用されています。

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/ImmutableTypes.cs" highlight="13":::
:::code language="vb" source="snippets/system-text-json-how-to-5-0/vb/ImmutableTypes.vb" :::

パラメーター化されたコンストラクターのパラメーター名は、プロパティ名と一致している必要があります。 一致では大文字と小文字は区別されません。また、[[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) を使用してプロパティの名前を変更する場合でも、コンストラクター パラメーターは実際のプロパティ名と一致している必要があります。 次の例では、`TemperatureC` プロパティの名前は、JSON では `celsius` に変更されていますが、コンストラクター パラメーターには引き続き `temperatureC` の名前が付けられます。

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/ImmutableTypesCtorParms.cs" highlight="10,14-16":::

`[JsonPropertyName]` に加え、次の属性でもパラメーター化されたコンストラクターでの逆シリアル化がサポートされています。

* [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute)
* [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute)
* [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute)
* [[JsonNumberHandling]](xref:System.Text.Json.Serialization.JsonNumberHandlingAttribute)

次の例で示されているように、C# 9 のレコードもサポートされています。

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/Records.cs":::

すべてのプロパティ セッターが非パブリックであるために不変の型の場合は、次のセクションを参照してください。
::: zone-end

::: zone pivot="dotnet-core-3-1"
`JsonConstructorAttribute` と C# 9 のレコードのサポートは、.NET Core 3.1 では使用できません。
::: zone-end

## <a name="non-public-property-accessors"></a>パブリックでないプロパティ アクセサー

::: zone pivot="dotnet-5-0"
パブリックでないプロパティ アクセサーを使用できるようにするには、次の例で示されているように、[[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) 属性を使用します。

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/NonPublicAccessors.cs" highlight="12,15":::
:::code language="vb" source="snippets/system-text-json-how-to-5-0/vb/NonPublicAccessors.vb" :::
::: zone-end

::: zone pivot="dotnet-core-3-1"
パブリックでないプロパティ アクセサーは、.NET Core 3.1 ではサポートされていません。 詳細については、[Newtonsoft.Json からの移行の記事](system-text-json-migrate-from-newtonsoft-how-to.md#non-public-property-setters-and-getters)を参照してください。
::: zone-end

## <a name="see-also"></a>関連項目

* [System.Text.Json の概要](system-text-json-overview.md)
* [JSON をシリアル化および逆シリアル化する方法](system-text-json-how-to.md)
* [JsonSerializerOptions インスタンスのインスタンスを作成する](system-text-json-configure-options.md)
* [大文字と小文字を区別しない一致を有効にする](system-text-json-character-casing.md)
* [プロパティの名前と値をカスタマイズする](system-text-json-customize-properties.md)
* [プロパティを無視する](system-text-json-ignore-properties.md)
* [無効な JSON を許可する](system-text-json-invalid-json.md)
* [オーバーフロー JSON の処理](system-text-json-handle-overflow.md)
* [参照を保持する](system-text-json-preserve-references.md)
* [ポリモーフィックなシリアル化](system-text-json-polymorphism.md)
* [Newtonsoft.Json から System.Text.Json に移行する](system-text-json-migrate-from-newtonsoft-how-to.md)
* [文字エンコードをカスタマイズする](system-text-json-character-encoding.md)
* [カスタム シリアライザーと逆シリアライザーを作成する](write-custom-serializer-deserializer.md)
* [JSON シリアル化のためのカスタム コンバーターの作成](system-text-json-converters-how-to.md)
* [DateTime および DateTimeOffset のサポート](../datetime/system-text-json-support.md)
* [System.Text.Json API リファレンス](xref:System.Text.Json)
* [System.Text.Json.Serialization API リファレンス](xref:System.Text.Json.Serialization)
