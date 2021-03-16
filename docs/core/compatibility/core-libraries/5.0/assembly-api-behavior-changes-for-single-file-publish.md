---
title: 破壊的変更:単一ファイル発行形式のアセンブリ関連 API 動作の変更
description: Core .NET ライブラリにおける .NET 5 の破壊的変更について学習します。アセンブリのファイルの場所に関連する複数の API は、単一ファイルの公開形式で呼び出されたときに動作が変更されます。
ms.date: 11/01/2020
ms.openlocfilehash: 3810a71fac481a42ccf2c8e64149d171f31c6821
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257688"
---
# <a name="assembly-related-api-behavior-changes-for-single-file-publishing-format"></a>単一ファイル発行形式のアセンブリ関連 API 動作の変更

アセンブリのファイルの場所に関連する複数の API は、単一ファイルの公開形式で呼び出されたときに動作が変更されます。

## <a name="change-description"></a>変更内容

.NET 5 以降のバージョンの単一ファイル公開では、バンドルされたアセンブリは、ディスクに展開されるのではなく、メモリから読み込まれます。 単一ファイルで公開されたアプリの場合、これは、特定の場所関連の API が .NET 5 以降で以前のバージョンの .NET とは異なる値を返すことを意味します。 変更点は次のとおりです。

| API | 以前のバージョン | .NET 5 以降 |
| - | - | - |
| <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> | 展開された DLL ファイル パスを返します | バンドルされたアセンブリに対して空の文字列を返します |
| <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType> | 展開された DLL ファイル パスを返します | バンドルされたアセンブリの例外をスローします |
| <xref:System.Reflection.Assembly.GetFile(System.String)?displayProperty=nameWithType> | バンドルされたアセンブリの `null` を返します | バンドルされたアセンブリの例外をスローします |
| `Environment.GetCommandLineArgs()[0]` | 値はエントリ ポイント DLL の名前です | 値はホストの実行可能ファイルの名前です |
| <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType> | 値は一時的な展開ディレクトリです | 値は、ホストの実行可能ファイルの格納ディレクトリです。 |

## <a name="version-introduced"></a>導入されたバージョン

5.0

## <a name="recommended-action"></a>推奨アクション

1 つのファイルとして公開する場合は、アセンブリのファイルの場所に依存しないようにします。

## <a name="affected-apis"></a>影響を受ける API

- <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.GetFile(System.String)?displayProperty=nameWithType>
- <xref:System.Environment.GetCommandLineArgs?displayProperty=nameWithType>
- <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Reflection.Assembly.Location`
- `P:System.Reflection.Assembly.CodeBase`
- `M:System.Reflection.Assembly.GetFile(System.String)`
- `M:System.Environment.GetCommandLineArgs`
- `P:System.AppContext.BaseDirectory`

-->
