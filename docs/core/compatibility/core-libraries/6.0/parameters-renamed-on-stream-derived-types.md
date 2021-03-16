---
title: '破壊的変更: ストリーム派生型でのパラメーター名の変更'
description: ストリーム派生型のメソッドの一部のパラメーター名が変更されたという、Core .NET ライブラリでの .NET 6.0 の破壊的変更について説明します。
ms.date: 03/04/2021
ms.openlocfilehash: c685fae6a7ed20ea47815d5f89a4e066c75e1178
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102260006"
---
# <a name="some-parameters-in-stream-derived-types-are-renamed"></a><span data-ttu-id="294e4-103">ストリーム派生型での一部のパラメーター名の変更</span><span class="sxs-lookup"><span data-stu-id="294e4-103">Some parameters in Stream-derived types are renamed</span></span>

<span data-ttu-id="294e4-104">.NET 6 では、<xref:System.IO.Stream?displayProperty=fullName> から派生した型のメソッドの一部のパラメーター名が、基底クラスと一致するように変更されました。</span><span class="sxs-lookup"><span data-stu-id="294e4-104">In .NET 6, some parameters of methods on types derived from <xref:System.IO.Stream?displayProperty=fullName> have been renamed to match the base class.</span></span>

## <a name="change-description"></a><span data-ttu-id="294e4-105">変更内容</span><span class="sxs-lookup"><span data-stu-id="294e4-105">Change description</span></span>

<span data-ttu-id="294e4-106">以前の .NET バージョンでは、<xref:System.IO.Stream> から派生したいくつかの型では、メソッドがオーバーライドされますが、使用されるパラメーター名は基本型で使用されているものとは異なっています。</span><span class="sxs-lookup"><span data-stu-id="294e4-106">In previous .NET versions, several types derived from <xref:System.IO.Stream> override methods but use different parameter names than those used by the base type.</span></span> <span data-ttu-id="294e4-107">たとえば、<xref:System.IO.Compression.DeflateStream.Read(System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType> のバイト配列パラメーターには `array` という名前が付けられていますが、基底クラス メソッド内のそれに対応する引数には `buffer` という名前が付けられています。</span><span class="sxs-lookup"><span data-stu-id="294e4-107">For example, the byte array parameter of <xref:System.IO.Compression.DeflateStream.Read(System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType> is named `array` while the corresponding argument in the base class method is named `buffer`.</span></span>

<span data-ttu-id="294e4-108">.NET 6 では、パラメーター名が一致していない <xref:System.IO.Stream?displayProperty=fullName> から派生する型はすべて、基本型と同じパラメーター名を使用することにより基本型に準拠するようになりました。</span><span class="sxs-lookup"><span data-stu-id="294e4-108">In .NET 6, all types that derive from <xref:System.IO.Stream?displayProperty=fullName> that had mismatched parameter names have been brought into conformance with the base type by using the same parameter names as the base type.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="294e4-109">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="294e4-109">Version introduced</span></span>

<span data-ttu-id="294e4-110">6.0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="294e4-110">6.0 Preview 1</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="294e4-111">変更理由</span><span class="sxs-lookup"><span data-stu-id="294e4-111">Reason for change</span></span>

<span data-ttu-id="294e4-112">この変更にはいくつかの理由があります。</span><span class="sxs-lookup"><span data-stu-id="294e4-112">There are several reasons for the change:</span></span>

- <span data-ttu-id="294e4-113">無効な引数が渡され例外がスローされた場合、その例外には、実装に応じて、基本パラメーターの名前が含まれることもあれば、派生パラメーターの名前が含まれることもありました。</span><span class="sxs-lookup"><span data-stu-id="294e4-113">If an invalid argument was passed and an exception was thrown, that exception might have contained the base parameter's name or the derived parameter's name, depending on the implementation.</span></span> <span data-ttu-id="294e4-114">呼び出し元では、基本として型指定された参照または派生型として型指定された参照のいずれも使用されている可能性があるので、例外の引数名が常に正しいとは限りません。</span><span class="sxs-lookup"><span data-stu-id="294e4-114">Since the caller may have been using a reference typed as the base or as the derived type, it's impossible for the argument name in the exception to always be correct.</span></span>
- <span data-ttu-id="294e4-115">パラメーター名が異なると、すべての <xref:System.IO.Stream> 実装にわたって動作を一貫して検証することが難しくなります。</span><span class="sxs-lookup"><span data-stu-id="294e4-115">Having different parameter names makes it harder to consistently validate behavior across all <xref:System.IO.Stream> implementations.</span></span>
- <span data-ttu-id="294e4-116">.NET 6 では、引数を検証するために <xref:System.IO.Stream> に対してパブリック メソッドが追加されました。このメソッドでは使用するパラメーター名に一貫性を持たせる必要があります。</span><span class="sxs-lookup"><span data-stu-id="294e4-116">.NET 6 adds a public method on <xref:System.IO.Stream> for validating arguments, and that methods needs to have a consistent parameter name to use.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="294e4-117">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="294e4-117">Recommended action</span></span>

<span data-ttu-id="294e4-118">この破壊的変更の影響はごくわずかです。</span><span class="sxs-lookup"><span data-stu-id="294e4-118">The effect of this breaking change is minimal:</span></span>

- <span data-ttu-id="294e4-119">既存のバイナリの場合、その影響は、影響を受ける派生型のパラメーターの名前を調べるためにリフレクションを使用するコードに限定されます。</span><span class="sxs-lookup"><span data-stu-id="294e4-119">For existing binaries, its impact is limited to code that uses reflection to examine the names of parameters on the affected derived types.</span></span>
- <span data-ttu-id="294e4-120">ソース コードの場合、その影響は、派生ストリーム型に対してその派生型として型指定された変数を使用してメソッドを呼び出すために名前付きパラメーターを使用するコードに限定されます。</span><span class="sxs-lookup"><span data-stu-id="294e4-120">For source code, its impact is limited to code that uses named parameters to invoke methods on the derived stream type using a variable typed as that derived type.</span></span>

<span data-ttu-id="294e4-121">どちらの場合も、基本パラメーター名を一貫して使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="294e4-121">In both cases, the recommended action is to consistently use the base parameter name.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="294e4-122">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="294e4-122">Affected APIs</span></span>

- <xref:System.IO.BufferedStream.Read(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>
- <xref:System.IO.BufferedStream.Write(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>
- <xref:System.IO.Compression.DeflateStream.BeginWrite(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)?displayProperty=fullName>
- <xref:System.IO.Compression.DeflateStream.Read(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>
- <xref:System.IO.Compression.DeflateStream.ReadAsync(System.Byte[],System.Int32,System.Int32,System.Threading.CancellationToken)?displayProperty=fullName>
- <xref:System.IO.Compression.DeflateStream.Write(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>
- <xref:System.IO.Compression.DeflateStream.WriteAsync(System.Byte[],System.Int32,System.Int32,System.Threading.CancellationToken)?displayProperty=fullName>
- <xref:System.IO.Compression.GZipStream.BeginRead(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)?displayProperty=fullName>
- <xref:System.IO.Compression.GZipStream.BeginWrite(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)?displayProperty=fullName>
- <xref:System.IO.Compression.GZipStream.Read(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>
- <xref:System.IO.Compression.GZipStream.ReadAsync(System.Byte[],System.Int32,System.Int32,System.Threading.CancellationToken)?displayProperty=fullName>
- <xref:System.IO.Compression.GZipStream.Write(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>
- <xref:System.IO.Compression.GZipStream.WriteAsync(System.Byte[],System.Int32,System.Int32,System.Threading.CancellationToken)?displayProperty=fullName>
- <xref:System.IO.FileStream.BeginRead(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)?displayProperty=fullName>
- <xref:System.IO.FileStream.BeginWrite(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)?displayProperty=fullName>
- <xref:System.IO.FileStream.Read(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>
- <xref:System.IO.FileStream.Write(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>
- <xref:System.Net.Sockets.NetworkStream.BeginRead(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)?displayProperty=fullName>
- <xref:System.Net.Sockets.NetworkStream.BeginWrite(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)?displayProperty=fullName>
- <xref:System.Net.Sockets.NetworkStream.Read(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>
- <xref:System.Net.Sockets.NetworkStream.ReadAsync(System.Byte[],System.Int32,System.Int32,System.Threading.CancellationToken)?displayProperty=fullName>
- <xref:System.Net.Sockets.NetworkStream.Write(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>
- <xref:System.Net.Sockets.NetworkStream.WriteAsync(System.Byte[],System.Int32,System.Int32,System.Threading.CancellationToken)?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `M:System.IO.Compression.DeflateStream.BeginWrite(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)`
- `M:System.IO.Compression.DeflateStream.Read(System.Byte[],System.Int32,System.Int32)`
- `M:System.IO.Compression.DeflateStream.ReadAsync(System.Byte[],System.Int32,System.Int32,System.Threading.CancellationToken)`
- `M:System.IO.Compression.DeflateStream.Write(System.Byte[],System.Int32,System.Int32)`
- `M:System.IO.Compression.DeflateStream.WriteAsync(System.Byte[],System.Int32,System.Int32,System.Threading.CancellationToken)`
- `M:System.IO.Compression.GZipStream.BeginRead(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)`
- `M:System.IO.Compression.GZipStream.BeginWrite(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)`
- `M:System.IO.Compression.GZipStream.Read(System.Byte[],System.Int32,System.Int32)`
- `M:System.IO.Compression.GZipStream.ReadAsync(System.Byte[],System.Int32,System.Int32,System.Threading.CancellationToken)`
- `M:System.IO.Compression.GZipStream.Write(System.Byte[],System.Int32,System.Int32)`
- `M:System.IO.Compression.GZipStream.WriteAsync(System.Byte[],System.Int32,System.Int32,System.Threading.CancellationToken)`
- `M:System.IO.BufferedStream.Read(System.Byte[],System.Int32,System.Int32)`
- `M:System.IO.BufferedStream.Write(System.Byte[],System.Int32,System.Int32)`
- `M:System.IO.FileStream.BeginRead(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)`
- `M:System.IO.FileStream.BeginWrite(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)`
- `M:System.IO.FileStream.Read(System.Byte[],System.Int32,System.Int32)`
- `M:System.IO.FileStream.Write(System.Byte[],System.Int32,System.Int32)`
- `M:System.Net.Sockets.NetworkStream.BeginRead(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)`
- `M:System.Net.Sockets.NetworkStream.BeginWrite(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)`
- `M:System.Net.Sockets.NetworkStream.Read(System.Byte[],System.Int32,System.Int32)`
- `M:System.Net.Sockets.NetworkStream.ReadAsync(System.Byte[],System.Int32,System.Int32,System.Threading.CancellationToken)`
- `M:System.Net.Sockets.NetworkStream.Write(System.Byte[],System.Int32,System.Int32)`
- `M:System.Net.Sockets.NetworkStream.WriteAsync(System.Byte[],System.Int32,System.Int32,System.Threading.CancellationToken)`

-->
