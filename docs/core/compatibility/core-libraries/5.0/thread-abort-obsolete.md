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
# <a name="threadabort-is-obsolete"></a>Thread.Abort は古い形式

<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> API は非推奨になっています。 .NET 5 以降のバージョンを対象とするプロジェクトでは、これらのメソッドが呼び出されると、コンパイル時の警告 `SYSLIB0006` が発生します。

## <a name="change-description"></a>変更内容

以前は、<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> を呼び出したときにコンパイル時の警告は生成されませんでしたが、このメソッドによって実行時に <xref:System.PlatformNotSupportedException> がスローされていました。

.NET 5 以降、<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> は警告として古い形式を示すマークが付けられるようになりました。 このメソッドを呼び出すと、コンパイラの警告 `SYSLIB0006` が生成されます。 メソッドの実装は変更されず、引き続き <xref:System.PlatformNotSupportedException> がスローされます。

## <a name="reason-for-change"></a>変更理由

<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> により、.NET Framework を除くすべての .NET 実装で常に <xref:System.PlatformNotSupportedException> がスローされることを考慮して、呼び出される場所に注意を促すためにメソッドに <xref:System.ObsoleteAttribute> が追加されました。

## <a name="version-introduced"></a>導入されたバージョン

5.0

## <a name="recommended-action"></a>推奨アクション

- <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> を呼び出す代わりに、<xref:System.Threading.CancellationToken> を使用して作業単位の処理を中止します。 次の例は、<xref:System.Threading.CancellationToken>の使用方法を示しています。

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

  詳細については、「[マネージド スレッドのキャンセル](../../../../standard/threading/cancellation-in-managed-threads.md)」を参照してください。

- コンパイル時の警告が表示されないようにするには、警告コード `SYSLIB0006` を抑制します。 警告コードは <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> に固有であり、これを抑制しても、コード内の他の非推奨警告は抑制されません。 しかし、警告を抑制するのではなく、<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> の呼び出しを削除することをお勧めします。

  ```csharp
  void MyMethod()
  {
  #pragma warning disable SYSLIB0006
      Thread.CurrentThread.Abort();
  #pragma warning restore SYSLIB0006
  }
  ```

  また、プロジェクト ファイルで警告を抑制することもできます。

  ```xml
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Disable "Thread.Abort is obsolete" warnings for entire project. -->
    <NoWarn>$(NoWarn);SYSLIB0006</NoWarn>
  </PropertyGroup>
  ```

## <a name="affected-apis"></a>影響を受ける API

- <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `Overload:System.Threading.Thread.Abort`

-->
