---
title: 破壊的変更:リモート API は旧型式
description: Core .NET ライブラリにおける .NET 5 の破壊的変更について学習します。一部のリモート処理関連の API は古いものとしてマークされており、カスタム診断 ID を含む警告が生成されます。
ms.date: 11/01/2020
ms.openlocfilehash: 3c4f7cd200cadd11321da60f2b4a0d191497aae8
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257170"
---
# <a name="remoting-apis-are-obsolete"></a><span data-ttu-id="fd4ae-103">リモート API は旧型式</span><span class="sxs-lookup"><span data-stu-id="fd4ae-103">Remoting APIs are obsolete</span></span>

<span data-ttu-id="fd4ae-104">一部のリモート処理関連の API は古いものとしてマークされており、コンパイル時に `SYSLIB0010` 警告が生成されます。</span><span class="sxs-lookup"><span data-stu-id="fd4ae-104">Some remoting-related APIs are marked as obsolete and generate a `SYSLIB0010` warning at compile time.</span></span> <span data-ttu-id="fd4ae-105">これらの API は、将来のバージョンの .NET で削除される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fd4ae-105">These APIs may be removed in a future version of .NET.</span></span>

## <a name="change-description"></a><span data-ttu-id="fd4ae-106">変更内容</span><span class="sxs-lookup"><span data-stu-id="fd4ae-106">Change description</span></span>

<span data-ttu-id="fd4ae-107">次のリモート API は、古いものとしてマークされています。</span><span class="sxs-lookup"><span data-stu-id="fd4ae-107">The following remoting APIs are marked obsolete.</span></span>

| <span data-ttu-id="fd4ae-108">API</span><span class="sxs-lookup"><span data-stu-id="fd4ae-108">API</span></span> | <span data-ttu-id="fd4ae-109">古いものとしてマークされる対象</span><span class="sxs-lookup"><span data-stu-id="fd4ae-109">Marked obsolete in...</span></span> |
| - | - |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="fd4ae-110">5.0 RC1</span><span class="sxs-lookup"><span data-stu-id="fd4ae-110">5.0 RC1</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="fd4ae-111">5.0 RC1</span><span class="sxs-lookup"><span data-stu-id="fd4ae-111">5.0 RC1</span></span> |

<span data-ttu-id="fd4ae-112">.NET Framework 2.x から 4.x では、<xref:System.MarshalByRefObject.GetLifetimeService> および <xref:System.MarshalByRefObject.InitializeLifetimeService> メソッドによって、.NET リモート処理に関するインスタンスの有効期間が制御されます。</span><span class="sxs-lookup"><span data-stu-id="fd4ae-112">In .NET Framework 2.x - 4.x, the <xref:System.MarshalByRefObject.GetLifetimeService> and <xref:System.MarshalByRefObject.InitializeLifetimeService> methods control the lifetime of instances involved with .NET remoting.</span></span> <span data-ttu-id="fd4ae-113">.NET Core 2.x から 3.x では、これらのメソッドによって常に、実行時に <xref:System.PlatformNotSupportedException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="fd4ae-113">In .NET Core 2.x- 3.x, these methods always throw a <xref:System.PlatformNotSupportedException> at run time.</span></span>

<span data-ttu-id="fd4ae-114">.NET 5 以降のバージョンでは、<xref:System.MarshalByRefObject.GetLifetimeService> および <xref:System.MarshalByRefObject.InitializeLifetimeService> メソッドは古いものとしてマークされ、警告が示されますが、実行時には引き続き <xref:System.PlatformNotSupportedException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="fd4ae-114">In .NET 5 and later versions, the <xref:System.MarshalByRefObject.GetLifetimeService> and <xref:System.MarshalByRefObject.InitializeLifetimeService> methods are marked obsolete as warning, but continue to throw a <xref:System.PlatformNotSupportedException> at run time.</span></span>

```csharp
// MemoryStream, like all Stream instances, subclasses MarshalByRefObject.
MemoryStream stream = new MemoryStream();
// Throws PlatformNotSupportedException; also produces warning SYSLIB0010.
obj.InitializeLifetimeService();
```

<span data-ttu-id="fd4ae-115">これは、コンパイル時のみの変更です。</span><span class="sxs-lookup"><span data-stu-id="fd4ae-115">This is a compile-time only change.</span></span> <span data-ttu-id="fd4ae-116">実行時については、以前のバージョンの .NET Core からの変更はありません。</span><span class="sxs-lookup"><span data-stu-id="fd4ae-116">There is no run-time change from previous versions of .NET Core.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="fd4ae-117">変更理由</span><span class="sxs-lookup"><span data-stu-id="fd4ae-117">Reason for change</span></span>

<span data-ttu-id="fd4ae-118">[.NET リモート処理](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71))はレガシ テクノロジです。</span><span class="sxs-lookup"><span data-stu-id="fd4ae-118">[.NET remoting](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71)) is a legacy technology.</span></span> <span data-ttu-id="fd4ae-119">これにより、(異なるコンピューター上にある可能性があっても) 別のプロセスでオブジェクトをインスタンス化し、通常のインプロセス .NET オブジェクト インスタンスの場合と同じように、そのオブジェクトとやりとりすることができます。</span><span class="sxs-lookup"><span data-stu-id="fd4ae-119">It allows instantiating an object in another process (potentially even on a different machine) and interacting with that object as if it were an ordinary, in-process .NET object instance.</span></span> <span data-ttu-id="fd4ae-120">.NET リモート処理インフラストラクチャは .NET Framework 2.x から 4.x にのみ存在します。</span><span class="sxs-lookup"><span data-stu-id="fd4ae-120">The .NET remoting infrastructure only exists in .NET Framework 2.x - 4.x.</span></span> <span data-ttu-id="fd4ae-121">.NET Core および .NET 5 以降のバージョンで .NET リモート処理はサポートされておらず、リモート API が存在しないか、常にこれらのランタイムで例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="fd4ae-121">.NET Core and .NET 5 and later versions don't have support for .NET remoting, and the remoting APIs either don't exist or always throw exceptions on these runtimes.</span></span>

<span data-ttu-id="fd4ae-122">開発者がこれらの API を使用しないようにするために、選択されたリモート処理関連の API を古いものと見なしています。</span><span class="sxs-lookup"><span data-stu-id="fd4ae-122">To help steer developers away from these APIs, we are obsoleting selected remoting-related APIs.</span></span> <span data-ttu-id="fd4ae-123">これらの API は、将来のバージョンの .NET で完全に削除される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fd4ae-123">These APIs may be removed entirely in a future version of .NET.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="fd4ae-124">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="fd4ae-124">Version introduced</span></span>

<span data-ttu-id="fd4ae-125">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="fd4ae-125">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="fd4ae-126">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="fd4ae-126">Recommended action</span></span>

- <span data-ttu-id="fd4ae-127">他のアプリケーションの、または複数のコンピューターのオブジェクトと通信する場合は、WCF または HTTP ベースの REST サービスの使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="fd4ae-127">Consider using WCF or HTTP-based REST services to communicate with objects in other applications or across machines.</span></span> <span data-ttu-id="fd4ae-128">詳細については、[.NET Core で使用できない .NET Framework テクノロジ](../../../porting/net-framework-tech-unavailable.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd4ae-128">For more information, see [.NET Framework technologies unavailable on .NET Core](../../../porting/net-framework-tech-unavailable.md).</span></span>

- <span data-ttu-id="fd4ae-129">古い API を引き続き使用する必要がある場合は、コードで `SYSLIB0010` 警告を抑制することができます。</span><span class="sxs-lookup"><span data-stu-id="fd4ae-129">If you must continue to use the obsolete APIs, you can suppress the `SYSLIB0010` warning in code.</span></span>

  ```csharp
  MarshalByRefObject obj = GetMarshalByRefObj();
  #pragma warning disable SYSLIB0010 // Disable the warning.
  obj.InitializeLifetimeService(); // Still throws PNSE.
  obj.GetLifetimeService(); // Still throws PNSE.
  #pragma warning restore SYSLIB0010 // Reenable the warning.
  ```

  <span data-ttu-id="fd4ae-130">プロジェクト ファイルで警告を抑制することもできます。これにより、プロジェクト内のすべてのソース ファイルに対して警告が無効になります。</span><span class="sxs-lookup"><span data-stu-id="fd4ae-130">You can also suppress the warning in your project file, which disables the warning for all source files in the project.</span></span>

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- NoWarn below will suppress SYSLIB0010 project-wide -->
     <NoWarn>$(NoWarn);SYSLIB0010</NoWarn>
    </PropertyGroup>
  </Project>
  ```

  <span data-ttu-id="fd4ae-131">`SYSLIB0010` を抑制すると、リモート API が古いという警告のみが無効になります。</span><span class="sxs-lookup"><span data-stu-id="fd4ae-131">Suppressing `SYSLIB0010` disables only the remoting API obsoletion warnings.</span></span> <span data-ttu-id="fd4ae-132">それ以外の警告は無効になりません。</span><span class="sxs-lookup"><span data-stu-id="fd4ae-132">It does not disable any other warnings.</span></span> <span data-ttu-id="fd4ae-133">また、常に <xref:System.PlatformNotSupportedException> をスローするハードコーディングされた実行時の動作は変更されません。</span><span class="sxs-lookup"><span data-stu-id="fd4ae-133">Additionally, it doesn't change the hardcoded run-time behavior of always throwing <xref:System.PlatformNotSupportedException>.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="fd4ae-134">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="fd4ae-134">Affected APIs</span></span>

- <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=fullName>
- <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `M:System.MarshalByRefObject.GetLifetimeService`
- `M:System.MarshalByRefObject.InitializeLifetimeService`

-->
