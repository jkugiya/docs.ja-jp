---
title: 破壊的変更:UTF-7 コード パスが古い形式に
description: Core .NET ライブラリでの .NET 5 の破壊的変更について学習します。この変更後、UTF7 と UTF7Encoding コンストラクターは古い形式となりました。
ms.date: 11/01/2020
ms.openlocfilehash: 7a0ba771e0fac2908ca37f16afb10118e1537161
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256986"
---
# <a name="utf-7-code-paths-are-obsolete"></a>UTF-7 コード パスが古い形式に

UTF-7 エンコードがアプリケーション間で広く使用されることはなくなりました。多くの仕様では、現在インターチェンジでの[使用が禁止されています](https://security.stackexchange.com/a/68609/3573)。 また、UTF-7 でエンコードされたデータの使用を予測していないアプリケーションでは、[攻撃ベクトルとして使用される](https://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=utf-7)こともあります。 Microsoft では、<xref:System.Text.UTF7Encoding?displayProperty=nameWithType> の使用に対して警告が行われます。エラー検出が提供されないためです。

その結果、<xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> プロパティと <xref:System.Text.UTF7Encoding.%23ctor%2A> コンストラクターは古い形式になりました。 さらに、<xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> と <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=nameWithType> では、`UTF-7` を指定できなくなりました。

## <a name="change-description"></a>変更の説明

以前は、<xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> API を使用して、UTF-7 エンコードのインスタンスを作成できました。 次に例を示します。

```csharp
Encoding enc1 = Encoding.GetEncoding("utf-7"); // By name.
Encoding enc2 = Encoding.GetEncoding(65000); // By code page.
```

また、UTF-7 エンコードを表すインスタンスが <xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType> メソッドによって列挙されていました。これは、システムに登録されているすべての <xref:System.Text.Encoding> インスタンスを列挙します。

.NET 5 以降では、<xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> プロパティと <xref:System.Text.UTF7Encoding.%23ctor%2A> コンストラクターは古くなり、警告 `SYSLIB0001` (プレビュー バージョンでは `MSLIB0001`) が生成されます。 ただし、<xref:System.Text.UTF7Encoding> クラスを使用しているときに呼び出し元が受け取る警告の数を減らすために、<xref:System.Text.UTF7Encoding> 型自体は古い形式に設定されていません。

```csharp
// The next line generates warning SYSLIB0001.
UTF7Encoding enc = new UTF7Encoding();
// The next line does not generate a warning.
byte[] bytes = enc.GetBytes("Hello world!");
```

また、<xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> メソッドでは、エンコード名 `utf-7` とコード ページ `65000` が `unknown` として扱われます。 エンコードを `unknown` として扱うと、メソッドによって <xref:System.ArgumentException> がスローされます。

```csharp
// Throws ArgumentException, same as calling Encoding.GetEncoding("unknown").
Encoding enc = Encoding.GetEncoding("utf-7");
```

最後に、<xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType> メソッドでは、返される <xref:System.Text.EncodingInfo> 配列に UTF-7 エンコードが含まれません。 このエンコードはインスタンス化できないため、除外されます。

```csharp
foreach (EncodingInfo encInfo in Encoding.GetEncodings())
{
    // The next line would throw if GetEncodings included UTF-7.
    Encoding enc = Encoding.GetEncoding(encInfo.Name);
}
```

## <a name="reason-for-change"></a>変更理由

多くのアプリケーションでは、信頼できないソースから提供されるエンコード名の値と共に `Encoding.GetEncoding("encoding-name")` が呼び出されます。 たとえば、Web クライアントまたはサーバーでは、`Content-Type` ヘッダーの `charset` の部分を受け取り、その値を検証せずに `Encoding.GetEncoding` に直接渡すかもしれません。 これにより、悪意のあるエンドポイントが `Content-Type: ...; charset=utf-7` を指定できるようになり、受信側のアプリケーションが不適切な動作をする可能性があります。

さらに、UTF-7 コード パスを無効にすると、コンパイラ (Blazor で使用されるものなど) の最適化が可能になり、生成されたアプリケーションからこれらのコード パスを完全に削除できるようになります。 その結果、コンパイルされたアプリケーションはより効率的に実行され、使用されるディスク領域は少なくなります。

## <a name="version-introduced"></a>導入されたバージョン

5.0

## <a name="recommended-action"></a>推奨アクション

ほとんどの場合、お客様が何らかのアクションを実行する必要はありません。 ただし、以前に UTF-7 関連のコード パスをアクティブにしていたアプリについては、以下のガイダンスを考慮してください。

- お使いのアプリで、信頼できないソースから提供される不明なエンコード名を使用して <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> が呼び出される場合:

  代わりに、エンコード名を構成可能な許可リストと比較します。 構成可能な許可リストには、最低でも業界標準の "utf-8" が含まれている必要があります。 お客様のクライアントと規制の要件によっては、"GB18030" などの地域固有のエンコードを許可することが必要になる場合もあります。

  許可リストを実装しない場合、<xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> では、システムに組み込まれている、またはカスタム <xref:System.Text.EncodingProvider> を介して登録されている <xref:System.Text.Encoding> が返されます。 サービスの要件を監査して、これが目的の動作であることを検証します。 アプリケーションで、この記事の後半で説明する互換性スイッチを再度有効にしない限り、UTF-7 は引き続き既定で無効になります。

- 独自のプロトコルまたはファイル形式内で <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> または <xref:System.Text.UTF7Encoding> を使用している場合:

  <xref:System.Text.Encoding.UTF8?displayProperty=nameWithType> または <xref:System.Text.UTF8Encoding> の使用に切り替えます。 UTF-8 は業界標準であり、各言語、オペレーティング システム、およびランタイム間で広くサポートされています。 UTF-8 を使用すると、将来のコードの保守が容易になり、エコシステムの他の部分との相互運用性が高まります。

- <xref:System.Text.Encoding> インスタンスを <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> と比較している場合:

  代わりに、既知の UTF-7 コード ページ (`65000`) に対してチェックを実行することを検討してください。 コード ページと比較することによって、警告を回避し、一部のエッジ ケースを処理することもできます。たとえば、他のユーザーが `new UTF7Encoding()` を呼び出した場合や、型をサブクラス化した場合などです。

  ```csharp
  void DoSomething(Encoding enc)
  {
      // Don't perform the check this way.
      // It produces a warning and misses some edge cases.
      if (enc == Encoding.UTF7)
      {
          // Encoding is UTF-7.
      }

      // Instead, perform the check this way.
      if (enc != null && enc.CodePage == 65000)
      {
          // Encoding is UTF-7.
      }
  }
  ```

- <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> または <xref:System.Text.UTF7Encoding> を使用する必要がある場合:

  コード内で、またはプロジェクトの *.csproj* ファイル内で、`SYSLIB0001` 警告を抑制することができます。

  ```csharp
  #pragma warning disable SYSLIB0001 // Disable the warning.
  Encoding enc = Encoding.UTF7;
  #pragma warning restore SYSLIB0001 // Re-enable the warning.
  ```

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- NoWarn below suppresses SYSLIB0001 project-wide -->
     <NoWarn>$(NoWarn);SYSLIB0001</NoWarn>
    </PropertyGroup>
  </Project>
  ```

  > [!NOTE]
  > `SYSLIB0001` の抑制によって無効になるのは、古い <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> と <xref:System.Text.UTF7Encoding> に関する警告のみです。 他の警告が無効になったり、<xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> などの API の動作が変更されたりすることはありません。

- `Encoding.GetEncoding("utf-7", ...)` をサポートする必要がある場合:

  互換性スイッチを使用して、このサポートを再度有効にすることができます。 次の例に示すように、この互換性スイッチは、アプリケーションの *.csproj* ファイル、または [ランタイム構成ファイル](../../../run-time-config/index.md)で指定できます。

  アプリケーションの *.csproj* ファイル:

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- Re-enable support for UTF-7 -->
     <EnableUnsafeUTF7Encoding>true</EnableUnsafeUTF7Encoding>
    </PropertyGroup>
  </Project>
  ```

  アプリケーションの *runtimeconfig.template.json* ファイル:

  ```json
  {
    "configProperties": {
      "System.Text.Encoding.EnableUnsafeUTF7Encoding": true
    }
  }
  ```

  > [!TIP]
  > UTF-7 のサポートを再度有効にする場合は、<xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> を呼び出すコードのセキュリティ レビューを実行する必要があります。

## <a name="affected-apis"></a>影響を受ける API

- <xref:System.Text.Encoding.UTF7?displayProperty=fullName>
- <xref:System.Text.UTF7Encoding.%23ctor>
- <xref:System.Text.UTF7Encoding.%23ctor(System.Boolean)>
- <xref:System.Text.Encoding.GetEncoding(System.Int32)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncoding(System.String)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncoding(System.Int32,System.Text.EncoderFallback,System.Text.DecoderFallback)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncodings?displayProperty=fullName>

<!--

#### Category

- Core .NET libraries
- Security

### Affected APIs

- `System.Text.Encoding.UTF7`
- `System.Text.UTF7Encoding.#ctor`
- `System.Text.UTF7Encoding.#ctor(System.Boolean)`
- `System.Text.Encoding.GetEncoding(System.Int32)`
- `System.Text.Encoding.GetEncoding(System.String)`
- `System.Text.Encoding.GetEncoding(System.Int32,System.Text.EncoderFallback,System.Text.DecoderFallback)`
- `System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)`
- `System.Text.Encoding.GetEncodings`

-->
