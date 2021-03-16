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
# <a name="utf-7-code-paths-are-obsolete"></a><span data-ttu-id="f281f-103">UTF-7 コード パスが古い形式に</span><span class="sxs-lookup"><span data-stu-id="f281f-103">UTF-7 code paths are obsolete</span></span>

<span data-ttu-id="f281f-104">UTF-7 エンコードがアプリケーション間で広く使用されることはなくなりました。多くの仕様では、現在インターチェンジでの[使用が禁止されています](https://security.stackexchange.com/a/68609/3573)。</span><span class="sxs-lookup"><span data-stu-id="f281f-104">The UTF-7 encoding is no longer in wide use among applications, and many specs now [forbid its use](https://security.stackexchange.com/a/68609/3573) in interchange.</span></span> <span data-ttu-id="f281f-105">また、UTF-7 でエンコードされたデータの使用を予測していないアプリケーションでは、[攻撃ベクトルとして使用される](https://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=utf-7)こともあります。</span><span class="sxs-lookup"><span data-stu-id="f281f-105">It's also occasionally [used as an attack vector](https://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=utf-7) in applications that don't anticipate encountering UTF-7-encoded data.</span></span> <span data-ttu-id="f281f-106">Microsoft では、<xref:System.Text.UTF7Encoding?displayProperty=nameWithType> の使用に対して警告が行われます。エラー検出が提供されないためです。</span><span class="sxs-lookup"><span data-stu-id="f281f-106">Microsoft warns against use of <xref:System.Text.UTF7Encoding?displayProperty=nameWithType> because it doesn't provide error detection.</span></span>

<span data-ttu-id="f281f-107">その結果、<xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> プロパティと <xref:System.Text.UTF7Encoding.%23ctor%2A> コンストラクターは古い形式になりました。</span><span class="sxs-lookup"><span data-stu-id="f281f-107">Consequently, the <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> property and <xref:System.Text.UTF7Encoding.%23ctor%2A> constructors are now obsolete.</span></span> <span data-ttu-id="f281f-108">さらに、<xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> と <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=nameWithType> では、`UTF-7` を指定できなくなりました。</span><span class="sxs-lookup"><span data-stu-id="f281f-108">Additionally, <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> and <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=nameWithType> no longer allow you to specify `UTF-7`.</span></span>

## <a name="change-description"></a><span data-ttu-id="f281f-109">変更の説明</span><span class="sxs-lookup"><span data-stu-id="f281f-109">Change description</span></span>

<span data-ttu-id="f281f-110">以前は、<xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> API を使用して、UTF-7 エンコードのインスタンスを作成できました。</span><span class="sxs-lookup"><span data-stu-id="f281f-110">Previously, you could create an instance of the UTF-7 encoding by using the <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> APIs.</span></span> <span data-ttu-id="f281f-111">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="f281f-111">For example:</span></span>

```csharp
Encoding enc1 = Encoding.GetEncoding("utf-7"); // By name.
Encoding enc2 = Encoding.GetEncoding(65000); // By code page.
```

<span data-ttu-id="f281f-112">また、UTF-7 エンコードを表すインスタンスが <xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType> メソッドによって列挙されていました。これは、システムに登録されているすべての <xref:System.Text.Encoding> インスタンスを列挙します。</span><span class="sxs-lookup"><span data-stu-id="f281f-112">Additionally, an instance that represents the UTF-7 encoding was enumerated by the <xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType> method, which enumerates all the <xref:System.Text.Encoding> instances registered on the system.</span></span>

<span data-ttu-id="f281f-113">.NET 5 以降では、<xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> プロパティと <xref:System.Text.UTF7Encoding.%23ctor%2A> コンストラクターは古くなり、警告 `SYSLIB0001` (プレビュー バージョンでは `MSLIB0001`) が生成されます。</span><span class="sxs-lookup"><span data-stu-id="f281f-113">Starting in .NET 5, the <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> property and <xref:System.Text.UTF7Encoding.%23ctor%2A> constructors are obsolete and produce warning `SYSLIB0001` (or `MSLIB0001` in preview versions).</span></span> <span data-ttu-id="f281f-114">ただし、<xref:System.Text.UTF7Encoding> クラスを使用しているときに呼び出し元が受け取る警告の数を減らすために、<xref:System.Text.UTF7Encoding> 型自体は古い形式に設定されていません。</span><span class="sxs-lookup"><span data-stu-id="f281f-114">However, to reduce the number of warnings that callers receive when using the <xref:System.Text.UTF7Encoding> class, the <xref:System.Text.UTF7Encoding> type itself is not marked obsolete.</span></span>

```csharp
// The next line generates warning SYSLIB0001.
UTF7Encoding enc = new UTF7Encoding();
// The next line does not generate a warning.
byte[] bytes = enc.GetBytes("Hello world!");
```

<span data-ttu-id="f281f-115">また、<xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> メソッドでは、エンコード名 `utf-7` とコード ページ `65000` が `unknown` として扱われます。</span><span class="sxs-lookup"><span data-stu-id="f281f-115">Additionally, the <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> methods treat the encoding name `utf-7` and the code page `65000` as `unknown`.</span></span> <span data-ttu-id="f281f-116">エンコードを `unknown` として扱うと、メソッドによって <xref:System.ArgumentException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="f281f-116">Treating the encoding as `unknown` causes the method to throw an <xref:System.ArgumentException>.</span></span>

```csharp
// Throws ArgumentException, same as calling Encoding.GetEncoding("unknown").
Encoding enc = Encoding.GetEncoding("utf-7");
```

<span data-ttu-id="f281f-117">最後に、<xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType> メソッドでは、返される <xref:System.Text.EncodingInfo> 配列に UTF-7 エンコードが含まれません。</span><span class="sxs-lookup"><span data-stu-id="f281f-117">Finally, the <xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType> method doesn't include the UTF-7 encoding in the <xref:System.Text.EncodingInfo> array that it returns.</span></span> <span data-ttu-id="f281f-118">このエンコードはインスタンス化できないため、除外されます。</span><span class="sxs-lookup"><span data-stu-id="f281f-118">The encoding is excluded because it cannot be instantiated.</span></span>

```csharp
foreach (EncodingInfo encInfo in Encoding.GetEncodings())
{
    // The next line would throw if GetEncodings included UTF-7.
    Encoding enc = Encoding.GetEncoding(encInfo.Name);
}
```

## <a name="reason-for-change"></a><span data-ttu-id="f281f-119">変更理由</span><span class="sxs-lookup"><span data-stu-id="f281f-119">Reason for change</span></span>

<span data-ttu-id="f281f-120">多くのアプリケーションでは、信頼できないソースから提供されるエンコード名の値と共に `Encoding.GetEncoding("encoding-name")` が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="f281f-120">Many applications call `Encoding.GetEncoding("encoding-name")` with an encoding name value that's provided by an untrusted source.</span></span> <span data-ttu-id="f281f-121">たとえば、Web クライアントまたはサーバーでは、`Content-Type` ヘッダーの `charset` の部分を受け取り、その値を検証せずに `Encoding.GetEncoding` に直接渡すかもしれません。</span><span class="sxs-lookup"><span data-stu-id="f281f-121">For example, a web client or server might take the `charset` portion of the `Content-Type` header and pass the value directly to `Encoding.GetEncoding` without validating it.</span></span> <span data-ttu-id="f281f-122">これにより、悪意のあるエンドポイントが `Content-Type: ...; charset=utf-7` を指定できるようになり、受信側のアプリケーションが不適切な動作をする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f281f-122">This could allow a malicious endpoint to specify `Content-Type: ...; charset=utf-7`, which could cause the receiving application to misbehave.</span></span>

<span data-ttu-id="f281f-123">さらに、UTF-7 コード パスを無効にすると、コンパイラ (Blazor で使用されるものなど) の最適化が可能になり、生成されたアプリケーションからこれらのコード パスを完全に削除できるようになります。</span><span class="sxs-lookup"><span data-stu-id="f281f-123">Additionally, disabling UTF-7 code paths allows optimizing compilers, such as those used by Blazor, to remove these code paths entirely from the resulting application.</span></span> <span data-ttu-id="f281f-124">その結果、コンパイルされたアプリケーションはより効率的に実行され、使用されるディスク領域は少なくなります。</span><span class="sxs-lookup"><span data-stu-id="f281f-124">As a result, the compiled applications run more efficiently and take less disk space.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="f281f-125">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="f281f-125">Version introduced</span></span>

<span data-ttu-id="f281f-126">5.0</span><span class="sxs-lookup"><span data-stu-id="f281f-126">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="f281f-127">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="f281f-127">Recommended action</span></span>

<span data-ttu-id="f281f-128">ほとんどの場合、お客様が何らかのアクションを実行する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="f281f-128">In most cases, you don't need to take any action.</span></span> <span data-ttu-id="f281f-129">ただし、以前に UTF-7 関連のコード パスをアクティブにしていたアプリについては、以下のガイダンスを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="f281f-129">However, for apps that have previously activated UTF-7-related code paths, consider the guidance that follows.</span></span>

- <span data-ttu-id="f281f-130">お使いのアプリで、信頼できないソースから提供される不明なエンコード名を使用して <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> が呼び出される場合:</span><span class="sxs-lookup"><span data-stu-id="f281f-130">If your app calls <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> with unknown encoding names provided by an untrusted source:</span></span>

  <span data-ttu-id="f281f-131">代わりに、エンコード名を構成可能な許可リストと比較します。</span><span class="sxs-lookup"><span data-stu-id="f281f-131">Instead, compare the encoding names against a configurable allow list.</span></span> <span data-ttu-id="f281f-132">構成可能な許可リストには、最低でも業界標準の "utf-8" が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="f281f-132">The configurable allow list should at minimum include the industry-standard "utf-8".</span></span> <span data-ttu-id="f281f-133">お客様のクライアントと規制の要件によっては、"GB18030" などの地域固有のエンコードを許可することが必要になる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="f281f-133">Depending on your clients and regulatory requirements, you may also need to allow region-specific encodings, such as "GB18030".</span></span>

  <span data-ttu-id="f281f-134">許可リストを実装しない場合、<xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> では、システムに組み込まれている、またはカスタム <xref:System.Text.EncodingProvider> を介して登録されている <xref:System.Text.Encoding> が返されます。</span><span class="sxs-lookup"><span data-stu-id="f281f-134">If you don't implement an allow list, <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> will return any <xref:System.Text.Encoding> that's built into the system or that's registered via a custom <xref:System.Text.EncodingProvider>.</span></span> <span data-ttu-id="f281f-135">サービスの要件を監査して、これが目的の動作であることを検証します。</span><span class="sxs-lookup"><span data-stu-id="f281f-135">Audit your service's requirements to validate that this is the desired behavior.</span></span> <span data-ttu-id="f281f-136">アプリケーションで、この記事の後半で説明する互換性スイッチを再度有効にしない限り、UTF-7 は引き続き既定で無効になります。</span><span class="sxs-lookup"><span data-stu-id="f281f-136">UTF-7 continues to be disabled by default unless your application re-enables the compatibility switch mentioned later in this article.</span></span>

- <span data-ttu-id="f281f-137">独自のプロトコルまたはファイル形式内で <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> または <xref:System.Text.UTF7Encoding> を使用している場合:</span><span class="sxs-lookup"><span data-stu-id="f281f-137">If you're using <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> or <xref:System.Text.UTF7Encoding> within your own protocol or file format:</span></span>

  <span data-ttu-id="f281f-138"><xref:System.Text.Encoding.UTF8?displayProperty=nameWithType> または <xref:System.Text.UTF8Encoding> の使用に切り替えます。</span><span class="sxs-lookup"><span data-stu-id="f281f-138">Switch to using <xref:System.Text.Encoding.UTF8?displayProperty=nameWithType> or <xref:System.Text.UTF8Encoding>.</span></span> <span data-ttu-id="f281f-139">UTF-8 は業界標準であり、各言語、オペレーティング システム、およびランタイム間で広くサポートされています。</span><span class="sxs-lookup"><span data-stu-id="f281f-139">UTF-8 is an industry standard and is widely supported across languages, operating systems, and runtimes.</span></span> <span data-ttu-id="f281f-140">UTF-8 を使用すると、将来のコードの保守が容易になり、エコシステムの他の部分との相互運用性が高まります。</span><span class="sxs-lookup"><span data-stu-id="f281f-140">Using UTF-8 eases future maintenance of your code and makes it more interoperable with the rest of the ecosystem.</span></span>

- <span data-ttu-id="f281f-141"><xref:System.Text.Encoding> インスタンスを <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> と比較している場合:</span><span class="sxs-lookup"><span data-stu-id="f281f-141">If you're comparing an <xref:System.Text.Encoding> instance against <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType>:</span></span>

  <span data-ttu-id="f281f-142">代わりに、既知の UTF-7 コード ページ (`65000`) に対してチェックを実行することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="f281f-142">Instead, consider performing a check against the well-known UTF-7 code page, which is `65000`.</span></span> <span data-ttu-id="f281f-143">コード ページと比較することによって、警告を回避し、一部のエッジ ケースを処理することもできます。たとえば、他のユーザーが `new UTF7Encoding()` を呼び出した場合や、型をサブクラス化した場合などです。</span><span class="sxs-lookup"><span data-stu-id="f281f-143">By comparing against the code page, you avoid the warning and also handle some edge cases, such as if somebody called `new UTF7Encoding()` or subclassed the type.</span></span>

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

- <span data-ttu-id="f281f-144"><xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> または <xref:System.Text.UTF7Encoding> を使用する必要がある場合:</span><span class="sxs-lookup"><span data-stu-id="f281f-144">If you must use <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> or <xref:System.Text.UTF7Encoding>:</span></span>

  <span data-ttu-id="f281f-145">コード内で、またはプロジェクトの *.csproj* ファイル内で、`SYSLIB0001` 警告を抑制することができます。</span><span class="sxs-lookup"><span data-stu-id="f281f-145">You can suppress the `SYSLIB0001` warning in code or within your project's *.csproj* file.</span></span>

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
  > <span data-ttu-id="f281f-146">`SYSLIB0001` の抑制によって無効になるのは、古い <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> と <xref:System.Text.UTF7Encoding> に関する警告のみです。</span><span class="sxs-lookup"><span data-stu-id="f281f-146">Suppressing `SYSLIB0001` only disables the <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> and <xref:System.Text.UTF7Encoding> obsoletion warnings.</span></span> <span data-ttu-id="f281f-147">他の警告が無効になったり、<xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> などの API の動作が変更されたりすることはありません。</span><span class="sxs-lookup"><span data-stu-id="f281f-147">It doesn't disable any other warnings or change the behavior of APIs like <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="f281f-148">`Encoding.GetEncoding("utf-7", ...)` をサポートする必要がある場合:</span><span class="sxs-lookup"><span data-stu-id="f281f-148">If you must support `Encoding.GetEncoding("utf-7", ...)`:</span></span>

  <span data-ttu-id="f281f-149">互換性スイッチを使用して、このサポートを再度有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="f281f-149">You can re-enable support for this via a compatibility switch.</span></span> <span data-ttu-id="f281f-150">次の例に示すように、この互換性スイッチは、アプリケーションの *.csproj* ファイル、または [ランタイム構成ファイル](../../../run-time-config/index.md)で指定できます。</span><span class="sxs-lookup"><span data-stu-id="f281f-150">This compatibility switch can be specified in the application's *.csproj* file or in a [run-time configuration file](../../../run-time-config/index.md), as shown in the following examples.</span></span>

  <span data-ttu-id="f281f-151">アプリケーションの *.csproj* ファイル:</span><span class="sxs-lookup"><span data-stu-id="f281f-151">In the application's *.csproj* file:</span></span>

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- Re-enable support for UTF-7 -->
     <EnableUnsafeUTF7Encoding>true</EnableUnsafeUTF7Encoding>
    </PropertyGroup>
  </Project>
  ```

  <span data-ttu-id="f281f-152">アプリケーションの *runtimeconfig.template.json* ファイル:</span><span class="sxs-lookup"><span data-stu-id="f281f-152">In the application's *runtimeconfig.template.json* file:</span></span>

  ```json
  {
    "configProperties": {
      "System.Text.Encoding.EnableUnsafeUTF7Encoding": true
    }
  }
  ```

  > [!TIP]
  > <span data-ttu-id="f281f-153">UTF-7 のサポートを再度有効にする場合は、<xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> を呼び出すコードのセキュリティ レビューを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f281f-153">If you re-enable support for UTF-7, you should perform a security review of code that calls <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType>.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="f281f-154">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="f281f-154">Affected APIs</span></span>

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
