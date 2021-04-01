---
title: System.Text.Json で参照を保持する方法
description: .NET で JSON との間のシリアル化および逆シリアル化を行うときに、参照を保持し、循環参照を処理する方法について説明します。
ms.date: 01/12/2021
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
ms.openlocfilehash: 0dda695c7e21090f68703309da03d5158fc858f1
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/17/2021
ms.locfileid: "100584057"
---
# <a name="how-to-preserve-references-and-handle-circular-references-with-systemtextjson"></a>System.Text.Json で参照を保持して循環参照を処理する

::: zone pivot="dotnet-5-0"

参照を保持し、循環参照を処理するには、<xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler%2A> を <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A> に設定します。 これを設定すると、次のような動作になります。

* シリアル化のとき:

  複合型を書き込むとき、シリアライザーによってメタデータのプロパティ (`$id`、`$values`、`$ref`) も書き込まれます。

* 逆シリアル化のとき:

  メタデータが想定され (必須ではありません)、逆シリアライザーによってその理解が試みられます。

次のコードでは、`Preserve` 設定の使用方法を示します。

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/PreserveReferences.cs" highlight="34":::
:::code language="vb" source="snippets/system-text-json-how-to-5-0/vb/PreserveReferences.vb" :::

この機能を使用して、値型または不変型を保持することはできません。 逆シリアル化のとき、不変型のインスタンスは、ペイロード全体が読み取られた後で作成されます。 そのため、同じインスタンスへの参照が JSON ペイロード内に含まれている場合、それを逆シリアル化することはできません。

値型、不変型、配列の場合、参照メタデータはシリアル化されません。 逆シリアル化では、`$ref` または `$id` が検出されると例外がスローされます。 ただし、Newtonsoft.Json を使用してシリアル化されたペイロードを逆シリアル化できるようにするため、`$id` (および、コレクションの場合は `$values`) は値型で無視されます。  Newtonsoft.Json の場合は、そのような型のメタデータがシリアル化されます。

オブジェクトが等しいかどうかを判断するために System.Text.Json によって使用される <xref:System.Collections.Generic.ReferenceEqualityComparer.Instance%2A?displayProperty=nameWithType> では、2 つのオブジェクト インスタンスを比較するときに、値の等価性 (<xref:System.Object.Equals(System.Object)?displayProperty=nameWithType>) ではなく参照の等価性 (<xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=nameWithType>) が使用されます。

参照がシリアル化および逆シリアル化される方法の詳細については、<xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A?displayProperty=nameWithType> に関するページを参照してください。

シリアル化および逆シリアル化で参照を維持するための動作は、<xref:System.Text.Json.Serialization.ReferenceResolver> クラスによって定義されます。 カスタム動作を指定するには、派生クラスを作成します。 例については、[GuidReferenceResolver](https://github.com/dotnet/docs/blob/9d5e88edbd7f12be463775ffebbf07ac8415fe18/docs/standard/serialization/snippets/system-text-json-how-to-5-0/csharp/GuidReferenceResolverExample.cs) に関するページを参照してください。

## <a name="persist-reference-metadata-across-multiple-serialization-and-deserialization-calls"></a>複数のシリアル化および逆シリアル化呼び出し間で参照メタデータを保持する

既定では、参照データは <xref:System.Text.Json.JsonSerializer.Serialize%2A> または <xref:System.Text.Json.JsonSerializer.Deserialize%2A> への呼び出しごとにキャッシュされます。 ある `Serialize`/`Deserialize` 呼び出しから別の呼び出しへの参照を保持するには、`Serialize`/`Deserialize` の呼び出しサイトで <xref:System.Text.Json.Serialization.ReferenceResolver> インスタンスをルート化します。 このスクリプトの例を次のコードに示します。

* `Employee` のリストがあり、それぞれを個別にシリアル化する必要がある。
* `ReferenceHandler` のリゾルバーに保存されている参照を利用したい。

ここでは `Employee` クラスです。

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/PreserveReferencesMultipleCalls.cs" id="Employee":::

<xref:System.Text.Json.Serialization.ReferenceResolver> から派生するクラスは、参照をディクショナリに格納します。

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/PreserveReferencesMultipleCalls.cs" id="MyReferenceResolver":::

<xref:System.Text.Json.Serialization.ReferenceHandler> から派生するクラスは、`MyReferenceResolver` のインスタンスを保持し、必要な場合にのみ新しいインスタンスを作成します (この例では `Reset` という名前のメソッド)。

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/PreserveReferencesMultipleCalls.cs" id="MyReferenceHandler":::

このサンプル コードは、シリアライザーを呼び出すときに、<xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler> プロパティが `MyReferenceHandler` のインスタンスに設定されている <xref:System.Text.Json.JsonSerializerOptions> インスタンスを使用します。 このパターンに従う場合は、シリアル化が終了したときに必ず `ReferenceResolver` ディクショナリをリセットして、継続的に拡大しないようにしてください。

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/PreserveReferencesMultipleCalls.cs" id="CallSerializer" highlight = "3-4,14":::

::: zone-end

::: zone pivot="dotnet-core-3-1"
.NET Core 3.1 の System.Text.Json でサポートされているのは値によるシリアル化のみであり、循環参照の場合は例外がスローされます。
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
* [変更できない型と非パブリック アクセサー](system-text-json-immutability.md)
* [ポリモーフィックなシリアル化](system-text-json-polymorphism.md)
* [Newtonsoft.Json から System.Text.Json に移行する](system-text-json-migrate-from-newtonsoft-how-to.md)
* [文字エンコードをカスタマイズする](system-text-json-character-encoding.md)
* [カスタム シリアライザーと逆シリアライザーを作成する](write-custom-serializer-deserializer.md)
* [JSON シリアル化のためのカスタム コンバーターの作成](system-text-json-converters-how-to.md)
* [DateTime および DateTimeOffset のサポート](../datetime/system-text-json-support.md)
* [System.Text.Json API リファレンス](xref:System.Text.Json)
* [System.Text.Json.Serialization API リファレンス](xref:System.Text.Json.Serialization)
