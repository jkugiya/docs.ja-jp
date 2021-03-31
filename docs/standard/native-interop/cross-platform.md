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
# <a name="writing-cross-platform-pinvoke-code"></a>クロス プラットフォーム P/Invoke コードの作成

## <a name="library-name-variations"></a>ライブラリ名のバリエーション

クロス プラットフォームの P/Invoke コードをさらに単純にするために、正規の共有ライブラリ拡張機能 (`.dll`、`.so` または `.dylib`) が、ランタイムによってネイティブ ライブラリ名に追加されます。 また、Linux と macOS では、ランタイムによって `lib` の付加が試みられます。 これらのライブラリ名のバリエーションは、アンマネージド ライブラリを読み込む API (<xref:System.Runtime.InteropServices.DllImportAttribute> など) を使用すると、自動的に検索されます。

> [!NOTE]
> ライブラリ名の絶対パス (`/usr/lib/libc` など) はそのままの状態で扱われ、バリエーションは検索されません。

P/Invoke を使用する次の例を考えてみましょう。

```csharp
[DllImport("nativedep")]
static extern int ExportedFunction();
```

Windows で実行している場合、DLL は次の順序で検索されます。

1. `nativedep`
1. `nativedep.dll` (ライブラリ名の末尾が `.dll` または .`exe` ではない場合)

Linux または macOS で実行されている場合、ランタイムによって、`lib` の付加、および正規の共有ライブラリ拡張機能の追加が試みられます。 これらの OS では、ライブラリ名のバリエーションは次の順序で試行されます。

1. `nativedep.so` / `nativedep.dylib`
1. `libnativedep.so` / `libnativedep.dylib` <sup>1</sup>
1. `nativedep`
1. `libnativedep` <sup>1</sup>

Linux では、ライブラリ名の末尾が `.so`、またはライブラリ名に `.so.` (末尾の `.` に注意) が含まれている場合に、検索の順序が異なります。 次の例を確認してください。

```csharp
[DllImport("nativedep.so.6")]
static extern int ExportedFunction();
```

この場合、ライブラリ名のバリエーションは、次の順序で試みられます。

1. `nativedep.so.6`
1. `libnativedep.so.6` <sup>1</sup>
1. `nativedep.so.6.so`
1. `libnativedep.so.6.so` <sup>1</sup>

<sup>1</sup> パスは、ライブラリ名にディレクトリの区切り文字 (`/`) が含まれていない場合にのみ確認されます。

## <a name="custom-import-resolver"></a>カスタム インポート リゾルバー

より複雑なシナリオでは、実行時に DLL インポートを解決するには、<xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver%2A> を使用します。 次の例では、CPU がサポートする場合に、`nativedep` が `nativedep_avx2` に解決されます。

> [!TIP]
> この機能は、.NET 5 以降、および .NET Core 3.1 以降でのみ使用できます。

[!code-csharp[import resolver](~/samples/snippets/standard/interop/pinvoke/import-resolver/Program.cs)]

## <a name="see-also"></a>関連項目

- [プラットフォーム呼び出し (P/Invoke)](pinvoke.md)
