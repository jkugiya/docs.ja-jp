---
title: .NET 5 以降の古い機能
description: SYSLIB コンパイラの警告を発生させる、.NET 5 以降のバージョンで古いものとしてマークされた API について説明します。
ms.date: 10/20/2020
ms.openlocfilehash: d6563f21624456d74801242268ecf72652fc4f88
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256284"
---
# <a name="obsolete-features-in-net-5"></a><span data-ttu-id="9f7a8-103">.NET 5 の古い機能</span><span class="sxs-lookup"><span data-stu-id="9f7a8-103">Obsolete features in .NET 5</span></span>

<span data-ttu-id="9f7a8-104">.NET 5 以降、新たに、古いものとしてマークされた一部の API によって、<xref:System.ObsoleteAttribute> の 2 つの新しいプロパティが使用されます。</span><span class="sxs-lookup"><span data-stu-id="9f7a8-104">Starting in .NET 5, some APIs that are newly marked as obsolete make use of two new properties on <xref:System.ObsoleteAttribute>.</span></span>

- <span data-ttu-id="9f7a8-105"><xref:System.ObsoleteAttribute.DiagnosticId?displayProperty=nameWithType> プロパティは、カスタム診断 ID を使用してビルド警告を生成するようにコンパイラに指示します。</span><span class="sxs-lookup"><span data-stu-id="9f7a8-105">The <xref:System.ObsoleteAttribute.DiagnosticId?displayProperty=nameWithType> property tells the compiler to generate build warnings using a custom diagnostic ID.</span></span> <span data-ttu-id="9f7a8-106">カスタム ID を使用すると、旧型式であるという警告を明確に個別に分けて非表示にすることができます。</span><span class="sxs-lookup"><span data-stu-id="9f7a8-106">The custom ID allows for obsoletion warning to be suppressed specifically and separately from one another.</span></span> <span data-ttu-id="9f7a8-107">.NET 5 以降の旧型式の場合、カスタム診断 ID の形式は `SYSLIBxxxx` です。</span><span class="sxs-lookup"><span data-stu-id="9f7a8-107">In the case of the .NET 5+ obsoletions, the format for the custom diagnostic ID is `SYSLIBxxxx`.</span></span>

- <span data-ttu-id="9f7a8-108"><xref:System.ObsoleteAttribute.UrlFormat?displayProperty=nameWithType> プロパティは、旧型式の詳細について確認するために URL リンクを含めるようにコンパイラに指示します。</span><span class="sxs-lookup"><span data-stu-id="9f7a8-108">The <xref:System.ObsoleteAttribute.UrlFormat?displayProperty=nameWithType> property tells the compiler to include a URL link to learn more about the obsoletion.</span></span>

<span data-ttu-id="9f7a8-109">古い API の使用によってビルドの警告またはエラーが発生した場合は、「[リファレンス](#reference)」セクションに記載されている診断 ID に関する具体的なガイダンスに従ってください。</span><span class="sxs-lookup"><span data-stu-id="9f7a8-109">If you encounter build warnings or errors due to usage of an obsolete API, follow the specific guidance provided for the diagnostic ID listed in the [Reference](#reference) section.</span></span> <span data-ttu-id="9f7a8-110">これらの古い警告またはエラーは、古い型またはメンバーに対して [標準診断 ID (CS0618)](../../csharp/language-reference/compiler-messages/cs0618.md) を使用して非表示にすることは "*できません*"。代わりに、カスタム `SYSLIBxxxx` 診断 ID の値を使用してください。</span><span class="sxs-lookup"><span data-stu-id="9f7a8-110">Warnings or errors for these obsoletions *can't* be suppressed using the [standard diagnostic ID (CS0618)](../../csharp/language-reference/compiler-messages/cs0618.md) for obsolete types or members; use the custom `SYSLIBxxxx` diagnostic ID values instead.</span></span> <span data-ttu-id="9f7a8-111">詳細については、「[警告を表示しない](#suppress-warnings)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9f7a8-111">For more information, see [Suppress warnings](#suppress-warnings).</span></span>

## <a name="reference"></a><span data-ttu-id="9f7a8-112">リファレンス</span><span class="sxs-lookup"><span data-stu-id="9f7a8-112">Reference</span></span>

<span data-ttu-id="9f7a8-113">次の表は、.NET 5 以降の `SYSLIBxxxx` 旧型式のインデックスを示しています。</span><span class="sxs-lookup"><span data-stu-id="9f7a8-113">The following table provides an index to the `SYSLIBxxxx` obsoletions in .NET 5+.</span></span>

| <span data-ttu-id="9f7a8-114">診断 ID</span><span class="sxs-lookup"><span data-stu-id="9f7a8-114">Diagnostic ID</span></span> | <span data-ttu-id="9f7a8-115">Description</span><span class="sxs-lookup"><span data-stu-id="9f7a8-115">Description</span></span> |
| - | - |
| [<span data-ttu-id="9f7a8-116">SYSLIB0001</span><span class="sxs-lookup"><span data-stu-id="9f7a8-116">SYSLIB0001</span></span>](syslib-warnings/syslib0001.md) | <span data-ttu-id="9f7a8-117">UTF-7 エンコードは安全ではないため、使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="9f7a8-117">The UTF-7 encoding is insecure and should not be used.</span></span> <span data-ttu-id="9f7a8-118">代わりに UTF-8 を使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="9f7a8-118">Consider using UTF-8 instead.</span></span> |
| [<span data-ttu-id="9f7a8-119">SYSLIB0002</span><span class="sxs-lookup"><span data-stu-id="9f7a8-119">SYSLIB0002</span></span>](syslib-warnings/syslib0002.md) | <span data-ttu-id="9f7a8-120"><xref:System.Security.Permissions.PrincipalPermissionAttribute> はランタイムによって受け入れられず、使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="9f7a8-120"><xref:System.Security.Permissions.PrincipalPermissionAttribute> is not honored by the runtime and must not be used.</span></span> |
| [<span data-ttu-id="9f7a8-121">SYSLIB0003</span><span class="sxs-lookup"><span data-stu-id="9f7a8-121">SYSLIB0003</span></span>](syslib-warnings/syslib0003.md) | <span data-ttu-id="9f7a8-122">コード アクセス セキュリティ (CAS) はサポートされていないか、ランタイムによって受け入れられていません。</span><span class="sxs-lookup"><span data-stu-id="9f7a8-122">Code access security (CAS) is not supported or honored by the runtime.</span></span> |
| [<span data-ttu-id="9f7a8-123">SYSLIB0004</span><span class="sxs-lookup"><span data-stu-id="9f7a8-123">SYSLIB0004</span></span>](syslib-warnings/syslib0004.md) | <span data-ttu-id="9f7a8-124">制約された実行領域 (CER) 機能はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="9f7a8-124">The constrained execution region (CER) feature is not supported.</span></span> |
| [<span data-ttu-id="9f7a8-125">SYSLIB0005</span><span class="sxs-lookup"><span data-stu-id="9f7a8-125">SYSLIB0005</span></span>](syslib-warnings/syslib0005.md) | <span data-ttu-id="9f7a8-126">グローバル アセンブリ キャッシュ (GAC) はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="9f7a8-126">The global assembly cache (GAC) is not supported.</span></span> |
| [<span data-ttu-id="9f7a8-127">SYSLIB0006</span><span class="sxs-lookup"><span data-stu-id="9f7a8-127">SYSLIB0006</span></span>](syslib-warnings/syslib0006.md) | <span data-ttu-id="9f7a8-128"><xref:System.Threading.Thread.Abort?displayProperty=nameWithType> はサポートされていません。<xref:System.PlatformNotSupportedException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="9f7a8-128"><xref:System.Threading.Thread.Abort?displayProperty=nameWithType> is not supported and throws <xref:System.PlatformNotSupportedException>.</span></span> |
| [<span data-ttu-id="9f7a8-129">SYSLIB0007</span><span class="sxs-lookup"><span data-stu-id="9f7a8-129">SYSLIB0007</span></span>](syslib-warnings/syslib0007.md) | <span data-ttu-id="9f7a8-130">この暗号化アルゴリズムの既定の実装はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="9f7a8-130">The default implementation of this cryptography algorithm is not supported.</span></span> |
| [<span data-ttu-id="9f7a8-131">SYSLIB0008</span><span class="sxs-lookup"><span data-stu-id="9f7a8-131">SYSLIB0008</span></span>](syslib-warnings/syslib0008.md) | <span data-ttu-id="9f7a8-132"><xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator> API はサポートされていません。<xref:System.PlatformNotSupportedException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="9f7a8-132">The <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator> API is not supported and throws <xref:System.PlatformNotSupportedException>.</span></span> |
| [<span data-ttu-id="9f7a8-133">SYSLIB0009</span><span class="sxs-lookup"><span data-stu-id="9f7a8-133">SYSLIB0009</span></span>](syslib-warnings/syslib0009.md) | <span data-ttu-id="9f7a8-134"><xref:System.Net.AuthenticationManager.Authenticate%2A?displayProperty=nameWithType> および <xref:System.Net.AuthenticationManager.PreAuthenticate%2A?displayProperty=nameWithType> メソッドはサポートされていません。<xref:System.PlatformNotSupportedException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="9f7a8-134">The <xref:System.Net.AuthenticationManager.Authenticate%2A?displayProperty=nameWithType> and <xref:System.Net.AuthenticationManager.PreAuthenticate%2A?displayProperty=nameWithType> methods are not supported and throw <xref:System.PlatformNotSupportedException>.</span></span> |
| [<span data-ttu-id="9f7a8-135">SYSLIB0010</span><span class="sxs-lookup"><span data-stu-id="9f7a8-135">SYSLIB0010</span></span>](syslib-warnings/syslib0010.md) | <span data-ttu-id="9f7a8-136">一部のリモート処理 API はサポートされていません。<xref:System.PlatformNotSupportedException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="9f7a8-136">Some remoting APIs are not supported and throw <xref:System.PlatformNotSupportedException>.</span></span> |
| [<span data-ttu-id="9f7a8-137">SYSLIB0011</span><span class="sxs-lookup"><span data-stu-id="9f7a8-137">SYSLIB0011</span></span>](syslib-warnings/syslib0011.md) | <span data-ttu-id="9f7a8-138"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> シリアル化は古いので使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="9f7a8-138"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> serialization is obsolete and should not be used.</span></span> |
| [<span data-ttu-id="9f7a8-139">SYSLIB0012</span><span class="sxs-lookup"><span data-stu-id="9f7a8-139">SYSLIB0012</span></span>](syslib-warnings/syslib0012.md) | <span data-ttu-id="9f7a8-140"><xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType> と <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType> は .NET Framework との互換性のためだけに含まれています。</span><span class="sxs-lookup"><span data-stu-id="9f7a8-140"><xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType> and <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType> are only included for .NET Framework compatibility.</span></span> <span data-ttu-id="9f7a8-141">代わりに、<xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> を使用してください。</span><span class="sxs-lookup"><span data-stu-id="9f7a8-141">Use <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> instead.</span></span> |

## <a name="suppress-warnings"></a><span data-ttu-id="9f7a8-142">警告を表示しない</span><span class="sxs-lookup"><span data-stu-id="9f7a8-142">Suppress warnings</span></span>

<span data-ttu-id="9f7a8-143">古い API を使用する必要があり、`SYSLIBxxxx` 診断がエラーとして表示されない場合は、コードまたはプロジェクト ファイルで警告を非表示にすることができます。</span><span class="sxs-lookup"><span data-stu-id="9f7a8-143">If you must use the obsolete APIs and the `SYSLIBxxxx` diagnostic does not surface as an error, you can suppress the warning in code or in your project file.</span></span>

<span data-ttu-id="9f7a8-144">コードは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="9f7a8-144">In code:</span></span>

```csharp
// Disable the warning.
#pragma warning disable SYSLIB0001
// Code that uses obsolete API.
...
// Re-enable the warning.
#pragma warning restore SYSLIB0001
```

<span data-ttu-id="9f7a8-145">プロジェクト ファイル:</span><span class="sxs-lookup"><span data-stu-id="9f7a8-145">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
   <TargetFramework>net5.0</TargetFramework>
   <!-- NoWarn below suppresses SYSLIB0001 project-wide -->
   <NoWarn>$(NoWarn);SYSLIB0001</NoWarn>
   <!-- To suppress multiple warnings, you can use multiple NoWarn elements -->
   <NoWarn>$(NoWarn);SYSLIB0002</NoWarn>
   <NoWarn>$(NoWarn);SYSLIB0003</NoWarn>
   <!-- Alternatively, you can suppress multiple warnings by using a semicolon-delimited list -->
   <NoWarn>$(NoWarn);SYSLIB0001;SYSLIB0002;SYSLIB0003</NoWarn>
  </PropertyGroup>
</Project>
```

> [!NOTE]
> <span data-ttu-id="9f7a8-146">このように警告を非表示にすると、指定した非推奨警告だけが無効になります。</span><span class="sxs-lookup"><span data-stu-id="9f7a8-146">Suppressing warnings in this way only disables the obsoletion warnings you specify.</span></span> <span data-ttu-id="9f7a8-147">診断 ID の異なる非推奨警告を含め、その他の警告は無効になりません。</span><span class="sxs-lookup"><span data-stu-id="9f7a8-147">It doesn't disable any other warnings, including obsoletion warnings with different diagnostic IDs.</span></span>
