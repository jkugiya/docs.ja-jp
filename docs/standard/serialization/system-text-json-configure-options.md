---
title: System.Text.Json で JsonSerializerOptions をインスタンス化する方法
description: パフォーマンスの問題を回避する方法と、JsonSerializerOptions インスタンスで使用可能なコンストラクターを使用する方法について説明します。
ms.date: 01/19/2021
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
ms.openlocfilehash: a74f4e0aa286f182906033e34be7bad63a72503f
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/17/2021
ms.locfileid: "100583233"
---
# <a name="how-to-instantiate-jsonserializeroptions-instances-with-systemtextjson"></a>System.Text.Json で JsonSerializerOptions インスタンスをインスタンス化する方法

この記事では、<xref:System.Text.Json.JsonSerializerOptions> の使用時にパフォーマンスの問題を回避する方法について説明します。 また、使用可能なパラメーター化コンストラクターの使用方法についても説明します。

## <a name="reuse-jsonserializeroptions-instances"></a>JsonSerializerOptions インスタンスの再利用

同じオプションで `JsonSerializerOptions` を繰り返し使用する場合、使用のたびに新しい `JsonSerializerOptions` インスタンスを作成しないでください。 すべての呼び出しで同じインスタンスを再利用します。 ここでは、カスタム コンバーター用に作成し、<xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> または <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> を呼び出すコードに関して説明しています。

次のコードでは、新しいオプションのインスタンスを使用する場合にパフォーマンスが低下することを示しています。

:::code language="csharp" source="snippets/system-text-json-configure-options/csharp/ReuseOptionsInstances.cs":::

上のコードでは、同じオプション インスタンスを使用して、小さいオブジェクトを 100,000 回シリアル化しています。 その後、同じ回数だけ同じオブジェクトがシリアル化され、毎回新しいオプション インスタンスが作成されます。 実行時の典型的な差は、40,140 ミリ秒と比較し 190 です。 イテレーションの回数を増やすと、この差はさらに広がります。

新しいオプション インスタンスが渡されると、オブジェクト グラフ内の各型の最初のシリアル化時にシリアライザーはウォームアップ フェーズになります。 このウォームアップには、シリアル化に必要なメタデータのキャッシュの作成が含まれます。 メタデータには、プロパティのゲッター、セッター、コンストラクターの引数、指定した属性などに対するデリゲートが含まれています。 このメタデータ キャッシュは、オプションのインスタンスに格納されています。 同じウォームアップ プロセスとキャッシュは逆シリアル化にも該当します。

`JsonSerializerOptions` インスタンスのメタデータのキャッシュのサイズは、シリアル化される型の数によって異なります。 動的に生成された型など、多数の型をシリアライザーに渡すと、キャッシュのサイズは増加し続け、最終的に `OutOfMemoryException` が発生する可能性があります。

## <a name="copy-jsonserializeroptions"></a>JsonSerializerOptions をコピーする

::: zone pivot="dotnet-5-0"
次の例で示されているように、既存のインスタンスと同じオプションを使用して新しいインスタンスを作成できる [JsonSerializerOptions コンストラクター](xref:System.Text.Json.JsonSerializerOptions.%23ctor(System.Text.Json.JsonSerializerOptions))があります。

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CopyOptions.cs" highlight="29":::
:::code language="vb" source="snippets/system-text-json-how-to-5-0/vb/CopyOptions.vb" :::
::: zone-end

::: zone pivot="dotnet-core-3-1"
既存のインスタンスを受け取る `JsonSerializerOptions` コンストラクターは、.NET Core 3.1 では使用できません。
::: zone-end

## <a name="web-defaults-for-jsonserializeroptions"></a>JsonSerializerOptions の Web の既定値

::: zone pivot="dotnet-5-0"
Web アプリ用に異なる既定値があるオプションは次のとおりです。

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>
* <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A> = <xref:System.Text.Json.Serialization.JsonNumberHandling.AllowReadingFromString>

次の例で示されているように、ASP.NET Core によって Web アプリ用に使用される既定のオプションで新しいインスタンスを作成できる [JsonSerializerOptions コンストラクター](xref:System.Text.Json.JsonSerializerOptions.%23ctor(System.Text.Json.JsonSerializerDefaults)?view=net-5.0&preserve-view=true)があります。

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/OptionsDefaults.cs" highlight="24":::
:::code language="vb" source="snippets/system-text-json-how-to-5-0/vb/OptionsDefaults.vb" :::
::: zone-end

::: zone pivot="dotnet-core-3-1"
Web アプリ用に異なる既定値があるオプションは次のとおりです。

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>

既定値のセットを指定する `JsonSerializerOptions` コンストラクターは、.NET Core 3.1 では使用できません。
::: zone-end

## <a name="see-also"></a>関連項目

* [System.Text.Json の概要](system-text-json-overview.md)
* [JSON をシリアル化および逆シリアル化する方法](system-text-json-how-to.md)
* [大文字と小文字を区別しない一致を有効にする](system-text-json-character-casing.md)
* [プロパティの名前と値をカスタマイズする](system-text-json-customize-properties.md)
* [プロパティを無視する](system-text-json-ignore-properties.md)
* [無効な JSON を許可する](system-text-json-invalid-json.md)
* [オーバーフロー JSON の処理](system-text-json-handle-overflow.md)
* [参照を保持する](system-text-json-preserve-references.md)
* [変更できない型と非パブリック アクセサー](system-text-json-immutability.md)
* [ポリモーフィックなシリアル化](system-text-json-polymorphism.md)
* [Newtonsoft.Json から System.Text.Json に移行する](system-text-json-migrate-from-newtonsoft-how-to.md)
* [文字エンコードをカスタマイズする](system-text-json-character-encoding.md)
* [カスタム シリアライザーと逆シリアライザーを作成する](write-custom-serializer-deserializer.md)
* [JSON シリアル化のためのカスタム コンバーターの作成](system-text-json-converters-how-to.md)
* [DateTime および DateTimeOffset のサポート](../datetime/system-text-json-support.md)
* [System.Text.Json API リファレンス](xref:System.Text.Json)
* [System.Text.Json.Serialization API リファレンス](xref:System.Text.Json.Serialization)
