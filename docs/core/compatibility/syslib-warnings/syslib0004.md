---
title: SYSLIB0004 警告
description: コンパイル時の警告 SYSLIB0004 が生成される旧型式について説明します。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 76726e233e2900c82dce1b0872533e5356e91c8c
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256369"
---
# <a name="syslib0004-the-constrained-execution-region-cer-feature-is-not-supported"></a><span data-ttu-id="93e91-103">SYSLIB0004: 制約された実行領域 (CER) 機能はサポートされていません</span><span class="sxs-lookup"><span data-stu-id="93e91-103">SYSLIB0004: The constrained execution region (CER) feature is not supported</span></span>

<span data-ttu-id="93e91-104">[制約された実行領域 (CER)](../../../framework/performance/constrained-execution-regions.md) 機能は、.NET Framework でのみサポートされています。</span><span class="sxs-lookup"><span data-stu-id="93e91-104">The [Constrained execution regions (CER)](../../../framework/performance/constrained-execution-regions.md) feature is supported only in .NET Framework.</span></span> <span data-ttu-id="93e91-105">そのため、さまざまな CER 関連 API は、.NET 5.0 以降、古いものとしてマークされています。</span><span class="sxs-lookup"><span data-stu-id="93e91-105">As such, various CER-related APIs are marked obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="93e91-106">これらの API を使用すると、コンパイル時に警告 `SYSLIB0004` が生成されます。</span><span class="sxs-lookup"><span data-stu-id="93e91-106">Using these APIs generates warning `SYSLIB0004` at compile time.</span></span>

<span data-ttu-id="93e91-107">次の CER 関連の API は旧型式です。</span><span class="sxs-lookup"><span data-stu-id="93e91-107">The following CER-related APIs are obsolete:</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup(System.Runtime.CompilerServices.RuntimeHelpers.TryCode,System.Runtime.CompilerServices.RuntimeHelpers.CleanupCode,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegionsNoOP?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareContractedDelegate(System.Delegate)?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.ProbeForSufficientStack?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.Cer?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.Consistency?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.PrePrepareMethodAttribute?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute?displayProperty=nameWithType>

## <a name="workarounds"></a><span data-ttu-id="93e91-108">回避策</span><span class="sxs-lookup"><span data-stu-id="93e91-108">Workarounds</span></span>

- <span data-ttu-id="93e91-109">CER 属性をメソッドに適用している場合、その属性を削除します。</span><span class="sxs-lookup"><span data-stu-id="93e91-109">If you have applied a CER attribute to a method, remove the attribute.</span></span> <span data-ttu-id="93e91-110">そのような属性は、.NET 5 以降のバージョンで効果がありません。</span><span class="sxs-lookup"><span data-stu-id="93e91-110">These attributes have no effect in .NET 5 and later versions.</span></span>

  ```csharp
  // REMOVE the attribute below.
  [ReliabilityContract(Consistency.WillNotCorruptState, Cer.Success)]
  public void DoSomething()
  {
  }

  // REMOVE the attribute below.
  [PrePrepareMethod]
  public void DoSomething()
  {
  }
  ```

- <span data-ttu-id="93e91-111">`RuntimeHelpers.ProbeForSufficientStack` または `RuntimeHelpers.PrepareContractedDelegate` を呼び出している場合、呼び出しを削除します。</span><span class="sxs-lookup"><span data-stu-id="93e91-111">If you are calling `RuntimeHelpers.ProbeForSufficientStack` or `RuntimeHelpers.PrepareContractedDelegate`, remove the call.</span></span> <span data-ttu-id="93e91-112">そのような呼び出しは、.NET 5 以降のバージョンで効果がありません。</span><span class="sxs-lookup"><span data-stu-id="93e91-112">These calls have no effect in .NET 5 and later versions.</span></span>

  ```csharp
  public void DoSomething()
  {
      // REMOVE the call below.
      RuntimeHelpers.ProbeForSufficientStack();

      // (Remainder of your method logic here.)
  }
  ```

- <span data-ttu-id="93e91-113">`RuntimeHelpers.PrepareConstrainedRegions` を呼び出している場合、呼び出しを削除します。</span><span class="sxs-lookup"><span data-stu-id="93e91-113">If you are calling `RuntimeHelpers.PrepareConstrainedRegions`, remove the call.</span></span> <span data-ttu-id="93e91-114">この呼び出しは、.NET 5 以降のバージョンで効果がありません。</span><span class="sxs-lookup"><span data-stu-id="93e91-114">This call has no effect in .NET 5 and later versions.</span></span>

  ```csharp
  public void DoSomething_Old()
  {
      // REMOVE the call below.
      RuntimeHelpers.PrepareConstrainedRegions();
      try
      {
          // try code
      }
      finally
      {
          // cleanup code
      }
  }

  public void DoSomething_Corrected()
  {
      // There is no call to PrepareConstrainedRegions. It's a normal try / finally block.

      try
      {
          // try code
      }
      finally
      {
          // cleanup code
      }
  }
  ```

- <span data-ttu-id="93e91-115">`RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup` を呼び出している場合、呼び出しを標準の _try / catch / finally_ ブロックに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="93e91-115">If you are calling `RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup`, replace the call with a standard _try / catch / finally_ block.</span></span>

  ```csharp
  // The sample below produces warning SYSLIB0004.
  public void DoSomething_Old()
  {
      RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup(MyTryCode, MyCleanupCode, null);
  }
  public void MyTryCode(object state) { /* try code */ }
  public void MyCleanupCode(object state, bool exceptionThrown) { /* cleanup code */ }

  // The corrected sample below does not produce warning SYSLIB0004.
  public void DoSomething_Corrected()
  {
      try
      {
          // try code
      }
      catch (Exception ex)
      {
          // exception handling code
      }
      finally
      {
          // cleanup code
      }
  }
  ```

[!INCLUDE [suppress-syslib-warning](../../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a><span data-ttu-id="93e91-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="93e91-116">See also</span></span>

- [<span data-ttu-id="93e91-117">制約された実行領域</span><span class="sxs-lookup"><span data-stu-id="93e91-117">Constrained execution regions</span></span>](../../../framework/performance/constrained-execution-regions.md)
