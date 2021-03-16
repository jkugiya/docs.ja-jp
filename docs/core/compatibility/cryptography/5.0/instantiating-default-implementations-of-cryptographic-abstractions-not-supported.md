---
title: '破壊的変更: 暗号抽象化の既定の実装のインスタンス化はサポートされていない'
description: .NET 5 の破壊的変更について学習します。この変更により、暗号抽象化に対するパラメーターなしの Create() オーバーロードは古い機能となります。
ms.date: 10/16/2020
ms.openlocfilehash: b75f3568317d1db8ae1bb629f760aaec7e69776a
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256791"
---
# <a name="instantiating-default-implementations-of-cryptographic-abstractions-is-not-supported"></a>暗号抽象化の既定の実装のインスタンス化はサポートされていない

暗号抽象化に対するパラメーターなしの `Create()` のオーバーロードは、.NET 5.0 においては警告になる古い機能です。

## <a name="change-description"></a>変更内容

.NET Framework 2.0 から 4.8 の場合、<xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> などの抽象暗号プリミティブ ファクトリは、異なるアルゴリズムを返すように構成できます。 たとえば、.NET Framework 4.8 の既定のインストールにおいては、次のスニペットに示すように、パラメーターなしの静的メソッド <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> から、SHA-1 アルゴリズムのインスタンスが返されます。

**.NET Framework のみ**

```csharp
// Return an instance of the default hash algorithm (SHA1).
HashAlgorithm alg = HashAlgorithm.Create();
// Prints 'System.Security.Cryptography.SHA1CryptoServiceProvider'.
Console.WriteLine(alg.GetType());

// Change the default algorithm to be SHA256, not SHA1.
CryptoConfig.AddAlgorithm(typeof(SHA256CryptoServiceProvider), typeof(HashAlgorithm).FullName);
alg = HashAlgorithm.Create();
// Prints 'System.Security.Cryptography.SHA256CryptoServiceProvider'.
Console.WriteLine(alg.GetType());
```

[コンピューター全体の構成](../../../../framework/configure-apps/map-algorithm-names-to-cryptography-classes.md)を使用して、プログラムで `CryptoConfig` を呼び出すことなく、既定のアルゴリズムを変更することもできます。

.NET Core 2.0 から 3.1 の場合、<xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> などの抽象暗号プリミティブ ファクトリからは、<xref:System.PlatformNotSupportedException> が常にスローされます。

```csharp
// Throws PlatformNotSupportedException on .NET Core.
HashAlgorithm alg = HashAlgorithm.Create();
```

.NET 5 以降のバージョンにおいては、<xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> などの抽象暗号プリミティブ ファクトリは、古い形式としてマークされ、ID `SYSLIB0007` のコンパイル時警告が生成されます。 実行時には、これらのメソッドからは引き続き <xref:System.PlatformNotSupportedException> がスローされます。

```csharp
// Throws PlatformNotSupportedException.
// Also produces compile-time warning SYSLIB0007 on .NET 5+.
HashAlgorithm alg = HashAlgorithm.Create();
```

これは、コンパイル時のみの変更です。 実行時については、以前のバージョンの .NET Core からの変更はありません。

> [!NOTE]
>
> - `Create()` メソッドのパラメーターなしのオーバーロードだけが古くなっています。 パラメーター化されたオーバーロードは古くなく、適切に機能します。
>
>   ```csharp
>   // Call Create(string), providing an explicit algorithm family name.
>   // Works in .NET Framework, .NET Core, and .NET 5.0+.
>   HashAlgorithm hashAlg = HashAlgorithm.Create("SHA256");
>   ```
>
> - "*特定の*" (抽象化されていない) アルゴリズム ファミリのパラメーターなしのオーバーロードは古くなく、引き続き適切に機能します。
>
>   ```csharp
>   // Call a specific algorithm family's parameterless Create() ctor.
>   // Works in .NET Framework, .NET Core, and .NET 5.0+.
>   Aes aesAlg = Aes.Create();
>   ```

## <a name="reason-for-change"></a>変更理由

.NET Framework に存在していた暗号構成システムは、.NET Core および .NET 5.0 以降には存在しなくなっているため、レガシ システムは適切な暗号アジリティに対応しません。 また、.NET の下位互換性の要件のため、暗号の進歩に対応してフレームワークで特定の暗号化 API を更新することもできません。 たとえば、<xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> メソッドは、SHA-1 ハッシュ アルゴリズムが最新であった .NET Framework 1.0 のときに導入されました。 20 年が経過し、現在、SHA-1 は破られたものと見なされていますが、<xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> によって別のアルゴリズムが返されるように変更することはできません。 それを行うと、使用しているアプリケーションに許容できない破壊的変更が発生します。

ベスト プラクティスとしては、暗号プリミティブを使用しているライブラリ (AES、SHA-*、RSA など) で、これらのプリミティブの使用方法を完全に制御する必要があることが示されています。 将来の保証が必要とされるアプリケーションの場合、これらのプリミティブがラップされている上位レベルのライブラリを使用し、キー管理と暗号アジリティの機能を追加する必要があります。 これらのライブラリは、多くの場合、ホスティング環境によって提供されます。 1 つの例として [ASP.NET のデータ保護ライブラリ](/aspnet/core/security/data-protection/)があり、呼び出し元のアプリケーションに代わってこれらの問題を処理します。

## <a name="version-introduced"></a>導入されたバージョン

5.0

## <a name="recommended-action"></a>推奨アクション

- 推奨される対応は、現在は古くなった API の呼び出しを、特定のアルゴリズム用のファクトリ メソッド (<xref:System.Security.Cryptography.Aes.Create?displayProperty=nameWithType> など) の呼び出しに置き換えることです。 これにより、インスタンス化されるアルゴリズムを完全に制御できます。

- 古くなった API を使用している .NET Framework アプリによって生成された既存のペイロードとの互換性を維持する必要がある場合は、次の表で推奨されている代わりのものを使用します。 次の表は、.NET Framework の既定のアルゴリズムから .NET 5 以降の同等のアルゴリズムへのマッピングを示したものです。

  | .NET Framework | .NET Core および .NET 5.0 以降で互換性のある代替機能 | 注釈 |
  | - | - | - |
  | <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.RSA.Create?displayProperty=nameWithType> | |
  | <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.SHA1.Create?displayProperty=nameWithType> | SHA-1 アルゴリズムは、破られたものと見なされています。 可能であれば、より強力なアルゴリズムを使用することを検討してください。 詳細については、セキュリティ アドバイザーに相談してください。 |
  | <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.HMACSHA1.%23ctor> | ほとんどの最新のアプリケーションに対しては、HMACSHA1 アルゴリズムは推奨されません。 可能であれば、より強力なアルゴリズムを使用することを検討してください。 詳細については、セキュリティ アドバイザーに相談してください。 |
  | <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.HMACSHA1.%23ctor> | ほとんどの最新のアプリケーションに対しては、HMACSHA1 アルゴリズムは推奨されません。 可能であれば、より強力なアルゴリズムを使用することを検討してください。 詳細については、セキュリティ アドバイザーに相談してください。 |
  | <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.Aes.Create?displayProperty=nameWithType> |

- 古いパラメーターなしの `Create()` のオーバーロードを引き続き呼び出す必要がある場合は、コードで警告 `SYSLIB0007` を抑制できます。

  ```csharp
  #pragma warning disable SYSLIB0007 // Disable the warning.
  HashAlgorithm alg = HashAlgorithm.Create(); // Still throws PNSE.
  #pragma warning restore SYSLIB0007 // Re-enable the warning.
  ```

  また、プロジェクト ファイルで警告を抑制することもできます。 そのようにすると、プロジェクト内のすべてのソース ファイルで警告が無効になります。

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- NoWarn below suppresses SYSLIB0007 project-wide -->
     <NoWarn>$(NoWarn);SYSLIB0007</NoWarn>
    </PropertyGroup>
  </Project>
  ```

  > [!NOTE]
  > `SYSLIB0007` を抑制すると、ここで示した暗号 API が古いという警告のみが無効になります。 それ以外の警告は無効になりません。 また、警告を抑制しても、実行時にはこれらの古い API から <xref:System.PlatformNotSupportedException> がスローされます。

## <a name="affected-apis"></a>影響を受ける API

- <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.HMAC.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=fullName>

<!--

### Affected APIs

- `M:System.Security.Cryptography.AsymmetricAlgorithm.Create`
- `M:System.Security.Cryptography.HashAlgorithm.Create`
- `M:System.Security.Cryptography.HMAC.Create`
- `M:System.Security.Cryptography.KeyedHashAlgorithm.Create`
- `M:System.Security.Cryptography.SymmetricAlgorithm.Create`

### Category

- Cryptography

-->
