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
# <a name="instantiating-default-implementations-of-cryptographic-abstractions-is-not-supported"></a><span data-ttu-id="2475d-103">暗号抽象化の既定の実装のインスタンス化はサポートされていない</span><span class="sxs-lookup"><span data-stu-id="2475d-103">Instantiating default implementations of cryptographic abstractions is not supported</span></span>

<span data-ttu-id="2475d-104">暗号抽象化に対するパラメーターなしの `Create()` のオーバーロードは、.NET 5.0 においては警告になる古い機能です。</span><span class="sxs-lookup"><span data-stu-id="2475d-104">The parameterless `Create()` overloads on cryptographic abstractions are obsolete as warning as of .NET 5.0.</span></span>

## <a name="change-description"></a><span data-ttu-id="2475d-105">変更内容</span><span class="sxs-lookup"><span data-stu-id="2475d-105">Change description</span></span>

<span data-ttu-id="2475d-106">.NET Framework 2.0 から 4.8 の場合、<xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> などの抽象暗号プリミティブ ファクトリは、異なるアルゴリズムを返すように構成できます。</span><span class="sxs-lookup"><span data-stu-id="2475d-106">In .NET Framework 2.0 - 4.8, abstract cryptographic primitive factories such as <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> can be configured to return different algorithms.</span></span> <span data-ttu-id="2475d-107">たとえば、.NET Framework 4.8 の既定のインストールにおいては、次のスニペットに示すように、パラメーターなしの静的メソッド <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> から、SHA-1 アルゴリズムのインスタンスが返されます。</span><span class="sxs-lookup"><span data-stu-id="2475d-107">For example, on a default install of .NET Framework 4.8, the parameterless, static method <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> returns an instance of the SHA1 algorithm, as shown in the following snippet.</span></span>

<span data-ttu-id="2475d-108">**.NET Framework のみ**</span><span class="sxs-lookup"><span data-stu-id="2475d-108">**.NET Framework only**</span></span>

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

<span data-ttu-id="2475d-109">[コンピューター全体の構成](../../../../framework/configure-apps/map-algorithm-names-to-cryptography-classes.md)を使用して、プログラムで `CryptoConfig` を呼び出すことなく、既定のアルゴリズムを変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="2475d-109">You can also use [machine-wide configuration](../../../../framework/configure-apps/map-algorithm-names-to-cryptography-classes.md) to change the default algorithm without needing to call into `CryptoConfig` programmatically.</span></span>

<span data-ttu-id="2475d-110">.NET Core 2.0 から 3.1 の場合、<xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> などの抽象暗号プリミティブ ファクトリからは、<xref:System.PlatformNotSupportedException> が常にスローされます。</span><span class="sxs-lookup"><span data-stu-id="2475d-110">In .NET Core 2.0 - 3.1, abstract cryptographic primitive factories such as <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> always throw a <xref:System.PlatformNotSupportedException>.</span></span>

```csharp
// Throws PlatformNotSupportedException on .NET Core.
HashAlgorithm alg = HashAlgorithm.Create();
```

<span data-ttu-id="2475d-111">.NET 5 以降のバージョンにおいては、<xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> などの抽象暗号プリミティブ ファクトリは、古い形式としてマークされ、ID `SYSLIB0007` のコンパイル時警告が生成されます。</span><span class="sxs-lookup"><span data-stu-id="2475d-111">In .NET 5 and later versions, abstract cryptographic primitive factories such as <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> are marked obsolete and produce a compile-time warning with ID `SYSLIB0007`.</span></span> <span data-ttu-id="2475d-112">実行時には、これらのメソッドからは引き続き <xref:System.PlatformNotSupportedException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="2475d-112">At run time, these methods continue to throw a <xref:System.PlatformNotSupportedException>.</span></span>

```csharp
// Throws PlatformNotSupportedException.
// Also produces compile-time warning SYSLIB0007 on .NET 5+.
HashAlgorithm alg = HashAlgorithm.Create();
```

<span data-ttu-id="2475d-113">これは、コンパイル時のみの変更です。</span><span class="sxs-lookup"><span data-stu-id="2475d-113">This is a compile-time only change.</span></span> <span data-ttu-id="2475d-114">実行時については、以前のバージョンの .NET Core からの変更はありません。</span><span class="sxs-lookup"><span data-stu-id="2475d-114">There is no run-time change from previous versions of .NET Core.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="2475d-115">`Create()` メソッドのパラメーターなしのオーバーロードだけが古くなっています。</span><span class="sxs-lookup"><span data-stu-id="2475d-115">Only the parameterless overloads of the `Create()` methods are obsolete.</span></span> <span data-ttu-id="2475d-116">パラメーター化されたオーバーロードは古くなく、適切に機能します。</span><span class="sxs-lookup"><span data-stu-id="2475d-116">Parameterized overloads are not obsolete and still function as expected.</span></span>
>
>   ```csharp
>   // Call Create(string), providing an explicit algorithm family name.
>   // Works in .NET Framework, .NET Core, and .NET 5.0+.
>   HashAlgorithm hashAlg = HashAlgorithm.Create("SHA256");
>   ```
>
> - <span data-ttu-id="2475d-117">"*特定の*" (抽象化されていない) アルゴリズム ファミリのパラメーターなしのオーバーロードは古くなく、引き続き適切に機能します。</span><span class="sxs-lookup"><span data-stu-id="2475d-117">Parameterless overloads of *specific* algorithm families (not abstractions) are not obsolete, and will continue to function as expected.</span></span>
>
>   ```csharp
>   // Call a specific algorithm family's parameterless Create() ctor.
>   // Works in .NET Framework, .NET Core, and .NET 5.0+.
>   Aes aesAlg = Aes.Create();
>   ```

## <a name="reason-for-change"></a><span data-ttu-id="2475d-118">変更理由</span><span class="sxs-lookup"><span data-stu-id="2475d-118">Reason for change</span></span>

<span data-ttu-id="2475d-119">.NET Framework に存在していた暗号構成システムは、.NET Core および .NET 5.0 以降には存在しなくなっているため、レガシ システムは適切な暗号アジリティに対応しません。</span><span class="sxs-lookup"><span data-stu-id="2475d-119">The cryptographic configuration system present in .NET Framework is no longer present in .NET Core and .NET 5.0+, since that legacy system doesn't allow for proper cryptographic agility.</span></span> <span data-ttu-id="2475d-120">また、.NET の下位互換性の要件のため、暗号の進歩に対応してフレームワークで特定の暗号化 API を更新することもできません。</span><span class="sxs-lookup"><span data-stu-id="2475d-120">.NET's backward-compatibility requirements also prohibit the framework from updating certain cryptographic APIs to keep up with advances in cryptography.</span></span> <span data-ttu-id="2475d-121">たとえば、<xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> メソッドは、SHA-1 ハッシュ アルゴリズムが最新であった .NET Framework 1.0 のときに導入されました。</span><span class="sxs-lookup"><span data-stu-id="2475d-121">For example, the <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> method was introduced in .NET Framework 1.0, when the SHA-1 hash algorithm was state-of-the-art.</span></span> <span data-ttu-id="2475d-122">20 年が経過し、現在、SHA-1 は破られたものと見なされていますが、<xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> によって別のアルゴリズムが返されるように変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="2475d-122">Twenty years have passed, and now SHA-1 is considered broken, but we cannot change <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> to return a different algorithm.</span></span> <span data-ttu-id="2475d-123">それを行うと、使用しているアプリケーションに許容できない破壊的変更が発生します。</span><span class="sxs-lookup"><span data-stu-id="2475d-123">Doing so would introduce an unacceptable breaking change in consuming applications.</span></span>

<span data-ttu-id="2475d-124">ベスト プラクティスとしては、暗号プリミティブを使用しているライブラリ (AES、SHA-\*、RSA など) で、これらのプリミティブの使用方法を完全に制御する必要があることが示されています。</span><span class="sxs-lookup"><span data-stu-id="2475d-124">Best practice dictates that libraries that consume cryptographic primitives (such as AES, SHA-\*, and RSA) should be in full control over how they consume these primitives.</span></span> <span data-ttu-id="2475d-125">将来の保証が必要とされるアプリケーションの場合、これらのプリミティブがラップされている上位レベルのライブラリを使用し、キー管理と暗号アジリティの機能を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2475d-125">Applications that require future-proofing should utilize higher-level libraries that wrap these primitives and add key management and cryptographic agility capabilities.</span></span> <span data-ttu-id="2475d-126">これらのライブラリは、多くの場合、ホスティング環境によって提供されます。</span><span class="sxs-lookup"><span data-stu-id="2475d-126">These libraries are often provided by the hosting environment.</span></span> <span data-ttu-id="2475d-127">1 つの例として [ASP.NET のデータ保護ライブラリ](/aspnet/core/security/data-protection/)があり、呼び出し元のアプリケーションに代わってこれらの問題を処理します。</span><span class="sxs-lookup"><span data-stu-id="2475d-127">One example is [ASP.NET's Data Protection library](/aspnet/core/security/data-protection/), which handles these concerns on behalf of the calling application.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="2475d-128">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="2475d-128">Version introduced</span></span>

<span data-ttu-id="2475d-129">5.0</span><span class="sxs-lookup"><span data-stu-id="2475d-129">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="2475d-130">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="2475d-130">Recommended action</span></span>

- <span data-ttu-id="2475d-131">推奨される対応は、現在は古くなった API の呼び出しを、特定のアルゴリズム用のファクトリ メソッド (<xref:System.Security.Cryptography.Aes.Create?displayProperty=nameWithType> など) の呼び出しに置き換えることです。</span><span class="sxs-lookup"><span data-stu-id="2475d-131">The recommended course of action is to replace calls to the now-obsolete APIs with calls to factory methods for specific algorithms, for example, <xref:System.Security.Cryptography.Aes.Create?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2475d-132">これにより、インスタンス化されるアルゴリズムを完全に制御できます。</span><span class="sxs-lookup"><span data-stu-id="2475d-132">This gives you full control over which algorithms are instantiated.</span></span>

- <span data-ttu-id="2475d-133">古くなった API を使用している .NET Framework アプリによって生成された既存のペイロードとの互換性を維持する必要がある場合は、次の表で推奨されている代わりのものを使用します。</span><span class="sxs-lookup"><span data-stu-id="2475d-133">If you need to maintain compatibility with existing payloads generated by .NET Framework apps that use the now-obsolete APIs, use the replacements suggested in the following table.</span></span> <span data-ttu-id="2475d-134">次の表は、.NET Framework の既定のアルゴリズムから .NET 5 以降の同等のアルゴリズムへのマッピングを示したものです。</span><span class="sxs-lookup"><span data-stu-id="2475d-134">The table provides a mapping from .NET Framework default algorithms to their .NET 5+ equivalents.</span></span>

  | <span data-ttu-id="2475d-135">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="2475d-135">.NET Framework</span></span> | <span data-ttu-id="2475d-136">.NET Core および .NET 5.0 以降で互換性のある代替機能</span><span class="sxs-lookup"><span data-stu-id="2475d-136">.NET Core / .NET 5.0+ compatible replacement</span></span> | <span data-ttu-id="2475d-137">注釈</span><span class="sxs-lookup"><span data-stu-id="2475d-137">Remarks</span></span> |
  | - | - | - |
  | <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.RSA.Create?displayProperty=nameWithType> | |
  | <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.SHA1.Create?displayProperty=nameWithType> | <span data-ttu-id="2475d-138">SHA-1 アルゴリズムは、破られたものと見なされています。</span><span class="sxs-lookup"><span data-stu-id="2475d-138">The SHA-1 algorithm is considered broken.</span></span> <span data-ttu-id="2475d-139">可能であれば、より強力なアルゴリズムを使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="2475d-139">Consider using a stronger algorithm if possible.</span></span> <span data-ttu-id="2475d-140">詳細については、セキュリティ アドバイザーに相談してください。</span><span class="sxs-lookup"><span data-stu-id="2475d-140">Consult your security advisor for further guidance.</span></span> |
  | <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.HMACSHA1.%23ctor> | <span data-ttu-id="2475d-141">ほとんどの最新のアプリケーションに対しては、HMACSHA1 アルゴリズムは推奨されません。</span><span class="sxs-lookup"><span data-stu-id="2475d-141">The HMACSHA1 algorithm is discouraged for most modern applications.</span></span> <span data-ttu-id="2475d-142">可能であれば、より強力なアルゴリズムを使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="2475d-142">Consider using a stronger algorithm if possible.</span></span> <span data-ttu-id="2475d-143">詳細については、セキュリティ アドバイザーに相談してください。</span><span class="sxs-lookup"><span data-stu-id="2475d-143">Consult your security advisor for further guidance.</span></span> |
  | <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.HMACSHA1.%23ctor> | <span data-ttu-id="2475d-144">ほとんどの最新のアプリケーションに対しては、HMACSHA1 アルゴリズムは推奨されません。</span><span class="sxs-lookup"><span data-stu-id="2475d-144">The HMACSHA1 algorithm is discouraged for most modern applications.</span></span> <span data-ttu-id="2475d-145">可能であれば、より強力なアルゴリズムを使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="2475d-145">Consider using a stronger algorithm if possible.</span></span> <span data-ttu-id="2475d-146">詳細については、セキュリティ アドバイザーに相談してください。</span><span class="sxs-lookup"><span data-stu-id="2475d-146">Consult your security advisor for further guidance.</span></span> |
  | <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.Aes.Create?displayProperty=nameWithType> |

- <span data-ttu-id="2475d-147">古いパラメーターなしの `Create()` のオーバーロードを引き続き呼び出す必要がある場合は、コードで警告 `SYSLIB0007` を抑制できます。</span><span class="sxs-lookup"><span data-stu-id="2475d-147">If you must continue to call the obsolete parameterless `Create()` overloads, you can suppress the `SYSLIB0007` warning in code.</span></span>

  ```csharp
  #pragma warning disable SYSLIB0007 // Disable the warning.
  HashAlgorithm alg = HashAlgorithm.Create(); // Still throws PNSE.
  #pragma warning restore SYSLIB0007 // Re-enable the warning.
  ```

  <span data-ttu-id="2475d-148">また、プロジェクト ファイルで警告を抑制することもできます。</span><span class="sxs-lookup"><span data-stu-id="2475d-148">You can also suppress the warning in your project file.</span></span> <span data-ttu-id="2475d-149">そのようにすると、プロジェクト内のすべてのソース ファイルで警告が無効になります。</span><span class="sxs-lookup"><span data-stu-id="2475d-149">Doing so disables the warning for all source files within the project.</span></span>

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
  > <span data-ttu-id="2475d-150">`SYSLIB0007` を抑制すると、ここで示した暗号 API が古いという警告のみが無効になります。</span><span class="sxs-lookup"><span data-stu-id="2475d-150">Suppressing `SYSLIB0007` disables only the obsoletion warnings for the cryptography APIs listed here.</span></span> <span data-ttu-id="2475d-151">それ以外の警告は無効になりません。</span><span class="sxs-lookup"><span data-stu-id="2475d-151">It does not disable any other warnings.</span></span> <span data-ttu-id="2475d-152">また、警告を抑制しても、実行時にはこれらの古い API から <xref:System.PlatformNotSupportedException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="2475d-152">Additionally, even if you suppress the warning, these obsoleted APIs will still throw a <xref:System.PlatformNotSupportedException> at run time.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="2475d-153">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="2475d-153">Affected APIs</span></span>

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
