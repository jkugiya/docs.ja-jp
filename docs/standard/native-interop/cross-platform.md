---
title: クロス プラットフォーム P/Invoke
description: P/Invoke を使用してネイティブ ライブラリを読み込むときにランタイムによって検索されるパスについて説明します。 また、SetDllImportResolver の使用方法についても説明します。
author: saul
ms.date: 01/31/2021
ms.openlocfilehash: 40ad87fe537ad043a488e4086814a58ef8e0211e
ms.sourcegitcommit: 38999dc0ec4f7c4404de5ce0951b64c55997d9ab
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/02/2021
ms.locfileid: "99427469"
---
# <a name="writing-cross-platform-pinvoke-code"></a><span data-ttu-id="aa9bf-104">クロス プラットフォーム P/Invoke コードの作成</span><span class="sxs-lookup"><span data-stu-id="aa9bf-104">Writing cross platform P/Invoke code</span></span>

## <a name="library-name-variations"></a><span data-ttu-id="aa9bf-105">ライブラリ名のバリエーション</span><span class="sxs-lookup"><span data-stu-id="aa9bf-105">Library name variations</span></span>

<span data-ttu-id="aa9bf-106">クロス プラットフォームの P/Invoke コードをさらに単純にするために、正規の共有ライブラリ拡張機能 (`.dll`、`.so` または `.dylib`) が、ランタイムによってネイティブ ライブラリ名に追加されます。</span><span class="sxs-lookup"><span data-stu-id="aa9bf-106">To facilitate simpler cross platform P/Invoke code, the runtime adds the canonical shared library extension (`.dll`, `.so` or `.dylib`) to native library names.</span></span> <span data-ttu-id="aa9bf-107">また、Linux と macOS では、ランタイムによって `lib` の付加が試みられます。</span><span class="sxs-lookup"><span data-stu-id="aa9bf-107">On Linux and macOS, the runtime will also try prepending `lib`.</span></span> <span data-ttu-id="aa9bf-108">これらのライブラリ名のバリエーションは、アンマネージド ライブラリを読み込む API (<xref:System.Runtime.InteropServices.DllImportAttribute> など) を使用すると、自動的に検索されます。</span><span class="sxs-lookup"><span data-stu-id="aa9bf-108">These library names variations are automatically searched when you use APIs that load unmanaged libraries (e.g., <xref:System.Runtime.InteropServices.DllImportAttribute>).</span></span>

> [!NOTE]
> <span data-ttu-id="aa9bf-109">ライブラリ名の絶対パス (`/usr/lib/libc` など) はそのままの状態で扱われ、バリエーションは検索されません。</span><span class="sxs-lookup"><span data-stu-id="aa9bf-109">Absolute paths in library names (e.g., `/usr/lib/libc`) are treated as-is and no variations will be searched.</span></span>

<span data-ttu-id="aa9bf-110">P/Invoke を使用する次の例を考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="aa9bf-110">Consider the following example of using P/Invoke:</span></span>

```csharp
[DllImport("nativedep")]
static extern int ExportedFunction();
```

<span data-ttu-id="aa9bf-111">Windows で実行している場合、DLL は次の順序で検索されます。</span><span class="sxs-lookup"><span data-stu-id="aa9bf-111">When running on Windows, the DLL is searched for in the following order:</span></span>

1. `nativedep`
1. <span data-ttu-id="aa9bf-112">`nativedep.dll` (ライブラリ名の末尾が `.dll` または .`exe` ではない場合)</span><span class="sxs-lookup"><span data-stu-id="aa9bf-112">`nativedep.dll` (if the library name does not already end with `.dll` or .`exe`)</span></span>

<span data-ttu-id="aa9bf-113">Linux または macOS で実行されている場合、ランタイムによって、`lib` の付加、および正規の共有ライブラリ拡張機能の追加が試みられます。</span><span class="sxs-lookup"><span data-stu-id="aa9bf-113">When running on Linux or macOS, the runtime will try prepending `lib` and appending the canonical shared library extension.</span></span> <span data-ttu-id="aa9bf-114">これらの OS では、ライブラリ名のバリエーションは次の順序で試行されます。</span><span class="sxs-lookup"><span data-stu-id="aa9bf-114">On these OSes, library name variations are tried in the following order:</span></span>

1. `nativedep.so` / `nativedep.dylib`
1. <span data-ttu-id="aa9bf-115">`libnativedep.so` / `libnativedep.dylib` <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="aa9bf-115">`libnativedep.so` / `libnativedep.dylib` <sup>1</sup></span></span>
1. `nativedep`
1. <span data-ttu-id="aa9bf-116">`libnativedep` <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="aa9bf-116">`libnativedep` <sup>1</sup></span></span>

<span data-ttu-id="aa9bf-117">Linux では、ライブラリ名の末尾が `.so`、またはライブラリ名に `.so.` (末尾の `.` に注意) が含まれている場合に、検索の順序が異なります。</span><span class="sxs-lookup"><span data-stu-id="aa9bf-117">On Linux, the search order is different if the library name ends with `.so` or contains `.so.` (note the trailing `.`).</span></span> <span data-ttu-id="aa9bf-118">次の例を確認してください。</span><span class="sxs-lookup"><span data-stu-id="aa9bf-118">Consider the following example:</span></span>

```csharp
[DllImport("nativedep.so.6")]
static extern int ExportedFunction();
```

<span data-ttu-id="aa9bf-119">この場合、ライブラリ名のバリエーションは、次の順序で試みられます。</span><span class="sxs-lookup"><span data-stu-id="aa9bf-119">In this case, the library name variations are tried in the following order:</span></span>

1. `nativedep.so.6`
1. <span data-ttu-id="aa9bf-120">`libnativedep.so.6` <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="aa9bf-120">`libnativedep.so.6` <sup>1</sup></span></span>
1. `nativedep.so.6.so`
1. <span data-ttu-id="aa9bf-121">`libnativedep.so.6.so` <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="aa9bf-121">`libnativedep.so.6.so` <sup>1</sup></span></span>

<span data-ttu-id="aa9bf-122"><sup>1</sup> パスは、ライブラリ名にディレクトリの区切り文字 (`/`) が含まれていない場合にのみ確認されます。</span><span class="sxs-lookup"><span data-stu-id="aa9bf-122"><sup>1</sup> Path is checked only if the library name does not contain a directory separator character (`/`).</span></span>

## <a name="custom-import-resolver"></a><span data-ttu-id="aa9bf-123">カスタム インポート リゾルバー</span><span class="sxs-lookup"><span data-stu-id="aa9bf-123">Custom import resolver</span></span>

<span data-ttu-id="aa9bf-124">より複雑なシナリオでは、実行時に DLL インポートを解決するには、<xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver%2A> を使用します。</span><span class="sxs-lookup"><span data-stu-id="aa9bf-124">In more complex scenarios, you can use <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver%2A> to resolve DLL imports at runtime.</span></span> <span data-ttu-id="aa9bf-125">次の例では、CPU がサポートする場合に、`nativedep` が `nativedep_avx2` に解決されます。</span><span class="sxs-lookup"><span data-stu-id="aa9bf-125">In the following example, `nativedep` is resolved to `nativedep_avx2` if the CPU supports it.</span></span>

> [!TIP]
> <span data-ttu-id="aa9bf-126">この機能は、.NET 5 以降、および .NET Core 3.1 以降でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="aa9bf-126">This functionality is only available in .NET 5 and .NET Core 3.1 or later.</span></span>

[!code-csharp[import resolver](~/samples/snippets/standard/interop/pinvoke/import-resolver/Program.cs)]

## <a name="see-also"></a><span data-ttu-id="aa9bf-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="aa9bf-127">See also</span></span>

- [<span data-ttu-id="aa9bf-128">プラットフォーム呼び出し (P/Invoke)</span><span class="sxs-lookup"><span data-stu-id="aa9bf-128">Platform Invoke (P/Invoke)</span></span>](pinvoke.md)
