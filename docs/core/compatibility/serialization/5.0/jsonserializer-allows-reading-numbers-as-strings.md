---
title: 破壊的変更:ASP.NET Core アプリで、引用符で囲まれた数値を逆シリアル化できる
description: .NET 5 の破壊的変更について学習します。この変更後、例外がスローされるのではなく、JSON 文字列として表される数値が ASP.NET Core アプリによって正常に逆シリアル化されるようになります。
ms.date: 10/21/2020
ms.openlocfilehash: f541af5bf5f0a519fd5205f44d68a9b401569909
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256310"
---
# <a name="aspnet-core-apps-allow-deserializing-quoted-numbers"></a>ASP.NET Core アプリで、引用符で囲まれた数値を逆シリアル化できる

.NET 5 以降では、ASP.NET Core アプリによって、<xref:System.Text.Json.JsonSerializerDefaults.Web?displayProperty=nameWithType> で指定された既定の逆シリアル化オプションが使用されます。 <xref:System.Text.Json.JsonSerializerDefaults.Web> オプション セットには、<xref:System.Text.Json.Serialization.JsonNumberHandling.AllowReadingFromString?displayProperty=nameWithType>への <xref:System.Text.Json.JsonSerializerOptions.NumberHandling> の設定が含まれます。 この変更は、例外がスローされるのではなく、JSON 文字列として表される数値が ASP.NET Core アプリによって正常に逆シリアル化されることを意味します。

## <a name="change-description"></a>変更内容

.NET Core 3.0 から 3.1 では、JSON ペイロードで引用符で囲まれた数値が検出された場合、逆シリアル化中に <xref:System.Text.Json.JsonSerializer> によって <xref:System.Text.Json.JsonException> がスローされます。 引用符で囲まれた数値は、オブジェクト グラフの数値プロパティとマップするために使用されます。 .NET Core 3.0 から 3.1 では、数値は <xref:System.Text.Json.JsonTokenType.Number?displayProperty=nameWithType> トークンからのみ読み取られます。

.NET 5 以降では、JSON ペイロードの引用符で囲まれた数値は、既定で ASP.NET Core アプリに対して有効と見なされます。 引用符で囲まれた数値の逆シリアル化中に例外はスローされません。

> [!TIP]
>
> - 既定のスタンドアロンの <xref:System.Text.Json.JsonSerializer> や <xref:System.Text.Json.JsonSerializerOptions> の動作変更はありません。
> - これは厳密には破壊的変更ではありません。これにより、シナリオがより制限の厳しいものになるのではなく、より制限の少ないものになるためです (つまり、例外をスローするのではなく、JSON 文字列からの数値の強制変換が正常に行われます)。 しかし、これは多くの ASP.NET Core アプリに影響する重要な動作変更であるため、ここに記載されています。
> - <xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> および <xref:System.Net.Http.Json.HttpContentJsonExtensions.ReadFromJsonAsync%2A?displayProperty=nameWithType> 拡張メソッドで <xref:System.Text.Json.JsonSerializerDefaults.Web> シリアル化オプション セットも使用されます。

## <a name="version-introduced"></a>導入されたバージョン

5.0

## <a name="reason-for-change"></a>変更理由

複数のユーザーから、<xref:System.Text.Json.JsonSerializer> でのより制限の少ない数値処理のためのオプションを求められました。 このフィードバックは、多くの JSON プロデューサー (たとえば、Web 全体のサービス) によって引用符で囲まれた数値が生成されることを示しています。 引用符で囲まれた数値の読み取り (逆シリアル化) を許可することにより、.NET アプリでこれらのペイロードを既定で Web コンテキストで正常に解析できます。 この構成は <xref:System.Text.Json.JsonSerializerDefaults.Web?displayProperty=nameWithType> を介して公開されるので、クライアント、サーバー、および共有など、異なるアプリケーション層全体で同じオプションを指定することができます。

## <a name="recommended-action"></a>推奨される操作

この変更が破壊的なものである場合、たとえば、検証のために厳密な数値の処理に依存している場合は、以前の動作を再び有効にすることができます。 <xref:System.Text.Json.JsonSerializerOptions.NumberHandling?displayProperty=nameWithType> オプションを <xref:System.Text.Json.Serialization.JsonNumberHandling.Strict?displayProperty=nameWithType> に設定します。

ASP.NET Core MVC および Web API アプリの場合は、次のコードを使用して `Startup` でオプションを構成できます。

```csharp
services.AddControllers()
   .AddJsonOptions(options.NumberHandling = JsonNumberHandling.Strict);
```

## <a name="affected-apis"></a>影響を受ける API

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=fullName>

<!--

### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

### Category

- ASP.NET Core
- Serialization

-->
