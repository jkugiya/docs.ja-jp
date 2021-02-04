---
description: '#pragma warning - C# リファレンス'
title: '#pragma warning - C# リファレンス'
ms.date: 07/20/2015
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
ms.openlocfilehash: 16582a74bd34f2c0d89950280f1d5fde25435eea
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2021
ms.locfileid: "99215993"
---
# <a name="pragma-warning-c-reference"></a><span data-ttu-id="e48d2-103">#pragma 警告 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="e48d2-103">#pragma warning (C# Reference)</span></span>

<span data-ttu-id="e48d2-104">`#pragma warning` を使用すると、特定の警告を有効または無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="e48d2-104">`#pragma warning` can enable or disable certain warnings.</span></span>

## <a name="syntax"></a><span data-ttu-id="e48d2-105">構文</span><span class="sxs-lookup"><span data-stu-id="e48d2-105">Syntax</span></span>

```csharp
#pragma warning disable warning-list
#pragma warning restore warning-list
```

## <a name="parameters"></a><span data-ttu-id="e48d2-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e48d2-106">Parameters</span></span>

 <span data-ttu-id="e48d2-107">`warning-list` 警告番号のコンマ区切りのリスト。</span><span class="sxs-lookup"><span data-stu-id="e48d2-107">`warning-list` A comma-separated list of warning numbers.</span></span> <span data-ttu-id="e48d2-108">"CS" というプレフィックスは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="e48d2-108">The "CS" prefix is optional.</span></span>

 <span data-ttu-id="e48d2-109">警告番号が指定されていないと、`disable` はすべての警告を無効にし、`restore` はすべての警告を有効にします。</span><span class="sxs-lookup"><span data-stu-id="e48d2-109">When no warning numbers are specified, `disable` disables all warnings and `restore` enables all warnings.</span></span>

> [!NOTE]
> <span data-ttu-id="e48d2-110">Visual Studio で警告番号を調べるには、プロジェクトをビルドし、**[出力]** ウィンドウで警告番号を探してください。</span><span class="sxs-lookup"><span data-stu-id="e48d2-110">To find warning numbers in Visual Studio, build your project and then look for the warning numbers in the **Output** window.</span></span>

## <a name="example"></a><span data-ttu-id="e48d2-111">例</span><span class="sxs-lookup"><span data-stu-id="e48d2-111">Example</span></span>

```csharp
// pragma_warning.cs
using System;

#pragma warning disable 414, CS3021
[CLSCompliant(false)]
public class C
{
    int i = 1;
    static void Main()
    {
    }
}
#pragma warning restore CS3021
[CLSCompliant(false)]  // CS3021
public class D
{
    int i = 1;
    public static void F()
    {
    }
}
```

## <a name="see-also"></a><span data-ttu-id="e48d2-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="e48d2-112">See also</span></span>

- [<span data-ttu-id="e48d2-113">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="e48d2-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e48d2-114">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="e48d2-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e48d2-115">C# プリプロセッサ ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="e48d2-115">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="e48d2-116">C# コンパイラ エラー</span><span class="sxs-lookup"><span data-stu-id="e48d2-116">C# Compiler Errors</span></span>](../compiler-messages/index.md)
- [<span data-ttu-id="e48d2-117">コード分析の警告を抑制する方法</span><span class="sxs-lookup"><span data-stu-id="e48d2-117">How to suppress code analysis warnings</span></span>](../../../fundamentals/code-analysis/suppress-warnings.md)
