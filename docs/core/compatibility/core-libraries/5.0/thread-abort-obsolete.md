---
title: 破壊的変更:Thread.Abort は古い形式
description: Core .NET ライブラリでの .NET 5 の破壊的変更について学習します。この変更後、Thread.Abort API は古い形式となりました。
ms.date: 11/01/2020
ms.openlocfilehash: 29c688250593801bab9b32b9e787911e561ec000
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257064"
---
# <a name="threadabort-is-obsolete"></a><span data-ttu-id="d545b-103">Thread.Abort は古い形式</span><span class="sxs-lookup"><span data-stu-id="d545b-103">Thread.Abort is obsolete</span></span>

<span data-ttu-id="d545b-104"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> API は非推奨になっています。</span><span class="sxs-lookup"><span data-stu-id="d545b-104">The <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> APIs are obsolete.</span></span> <span data-ttu-id="d545b-105">.NET 5 以降のバージョンを対象とするプロジェクトでは、これらのメソッドが呼び出されると、コンパイル時の警告 `SYSLIB0006` が発生します。</span><span class="sxs-lookup"><span data-stu-id="d545b-105">Projects that target .NET 5 or a later version will encounter compile-time warning `SYSLIB0006` if these methods are called.</span></span>

## <a name="change-description"></a><span data-ttu-id="d545b-106">変更内容</span><span class="sxs-lookup"><span data-stu-id="d545b-106">Change description</span></span>

<span data-ttu-id="d545b-107">以前は、<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> を呼び出したときにコンパイル時の警告は生成されませんでしたが、このメソッドによって実行時に <xref:System.PlatformNotSupportedException> がスローされていました。</span><span class="sxs-lookup"><span data-stu-id="d545b-107">Previously, calls to <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> did not produce compile-time warnings, however, the method did throw a <xref:System.PlatformNotSupportedException> at run time.</span></span>

<span data-ttu-id="d545b-108">.NET 5 以降、<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> は警告として古い形式を示すマークが付けられるようになりました。</span><span class="sxs-lookup"><span data-stu-id="d545b-108">Starting in .NET 5, <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> is marked obsolete as warning.</span></span> <span data-ttu-id="d545b-109">このメソッドを呼び出すと、コンパイラの警告 `SYSLIB0006` が生成されます。</span><span class="sxs-lookup"><span data-stu-id="d545b-109">Calling this method produces compiler warning `SYSLIB0006`.</span></span> <span data-ttu-id="d545b-110">メソッドの実装は変更されず、引き続き <xref:System.PlatformNotSupportedException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="d545b-110">The implementation of the method is unchanged, and it continues to throw a <xref:System.PlatformNotSupportedException>.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="d545b-111">変更理由</span><span class="sxs-lookup"><span data-stu-id="d545b-111">Reason for change</span></span>

<span data-ttu-id="d545b-112"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> により、.NET Framework を除くすべての .NET 実装で常に <xref:System.PlatformNotSupportedException> がスローされることを考慮して、呼び出される場所に注意を促すためにメソッドに <xref:System.ObsoleteAttribute> が追加されました。</span><span class="sxs-lookup"><span data-stu-id="d545b-112">Given that <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> always throws a <xref:System.PlatformNotSupportedException> on all .NET implementations except .NET Framework, <xref:System.ObsoleteAttribute> was added to the method to draw attention to places where it's called.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="d545b-113">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="d545b-113">Version introduced</span></span>

<span data-ttu-id="d545b-114">5.0</span><span class="sxs-lookup"><span data-stu-id="d545b-114">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="d545b-115">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="d545b-115">Recommended action</span></span>

- <span data-ttu-id="d545b-116"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> を呼び出す代わりに、<xref:System.Threading.CancellationToken> を使用して作業単位の処理を中止します。</span><span class="sxs-lookup"><span data-stu-id="d545b-116">Use a <xref:System.Threading.CancellationToken> to abort processing of a unit of work instead of calling <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d545b-117">次の例は、<xref:System.Threading.CancellationToken>の使用方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="d545b-117">The following example illustrates the use of <xref:System.Threading.CancellationToken>.</span></span>

  ```csharp
  void ProcessPendingWorkItemsNew(CancellationToken cancellationToken)
  {
      if (QueryIsMoreWorkPending())
      {
          // If the CancellationToken is marked as "needs to cancel",
          // this will throw the appropriate exception.
          cancellationToken.ThrowIfCancellationRequested();

          WorkItem work = DequeueWorkItem();
          ProcessWorkItem(work);
      }
  }
  ```

  <span data-ttu-id="d545b-118">詳細については、「[マネージド スレッドのキャンセル](../../../../standard/threading/cancellation-in-managed-threads.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d545b-118">For more information, see [Cancellation in managed threads](../../../../standard/threading/cancellation-in-managed-threads.md).</span></span>

- <span data-ttu-id="d545b-119">コンパイル時の警告が表示されないようにするには、警告コード `SYSLIB0006` を抑制します。</span><span class="sxs-lookup"><span data-stu-id="d545b-119">To suppress the compile-time warning, suppress warning code `SYSLIB0006`.</span></span> <span data-ttu-id="d545b-120">警告コードは <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> に固有であり、これを抑制しても、コード内の他の非推奨警告は抑制されません。</span><span class="sxs-lookup"><span data-stu-id="d545b-120">The warning code is specific to <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> and suppressing it doesn't suppress other obsoletion warnings in your code.</span></span> <span data-ttu-id="d545b-121">しかし、警告を抑制するのではなく、<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> の呼び出しを削除することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d545b-121">However, we recommend that you remove calls to <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> instead of suppressing the warning.</span></span>

  ```csharp
  void MyMethod()
  {
  #pragma warning disable SYSLIB0006
      Thread.CurrentThread.Abort();
  #pragma warning restore SYSLIB0006
  }
  ```

  <span data-ttu-id="d545b-122">また、プロジェクト ファイルで警告を抑制することもできます。</span><span class="sxs-lookup"><span data-stu-id="d545b-122">You can also suppress the warning in the project file.</span></span>

  ```xml
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Disable "Thread.Abort is obsolete" warnings for entire project. -->
    <NoWarn>$(NoWarn);SYSLIB0006</NoWarn>
  </PropertyGroup>
  ```

## <a name="affected-apis"></a><span data-ttu-id="d545b-123">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="d545b-123">Affected APIs</span></span>

- <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `Overload:System.Threading.Thread.Abort`

-->
