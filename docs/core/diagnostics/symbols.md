---
title: .NET でのシンボル
description: .NET でのシンボルとポータブル PDB の概要
ms.date: 02/08/2021
ms.openlocfilehash: 8f217bf8b62ff12a6ea1dc6a5b14b34d8037dd2d
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759899"
---
# <a name="symbols"></a>Symbols

シンボルは、デバッグや他の診断ツールに役立ちます。 シンボル ファイルの内容は、言語、コンパイラ、およびプラットフォームによって異なります。 非常に高いレベルのシンボルは、ソース コードとコンパイラによって生成されるバイナリとの間のマッピングです。 これらのマッピングは、[Visual Studio](/visualstudio/debugger/what-is-debugging) や [Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging) などのツールによって、ソースの行番号の情報またはローカル変数名を解決するために使用されます。

[シンボルに関する Windows のドキュメント](/windows/win32/dxtecharts/debugging-with-symbols)には、Windows のシンボルに関する詳細な情報が含まれていますが、多くの概念は他のプラットフォームにも当てはまります。

## <a name="learn-about-nets-portable-pdb-format"></a>.NET のポータブル PDB 形式について学習する

.NET Core には、新しいシンボル ファイル (PDB) の形式であるポータブル PDB が導入されています。 Windows 専用である従来の PDB とは異なり、ポータブル PDB を作成すると、すべてのプラットフォームで読み取ることができます。

### <a name="what-is-a-pdb"></a>PDB とは

PDB ファイルは、コンパイラによって生成される補助ファイルであり、他のツール (特にデバッガー) に、メインの実行可能ファイルの内容、およびその生成方法に関する情報を提供します。 たとえば、デバッガーによって PDB が読み取られ、foo.cs の 12 行目が実行可能ファイルの適切な場所にマップされて、ブレークポイントを設定できるようになります。 Windows PDB 形式はかなり長い時間が経過しており、さらに古い他のネイティブ デバッグ シンボル形式から進化したものです。 最初は、ネイティブ (C/C++) プログラム用の形式でした。 .NET Framework の最初のリリースで、Windows PDB 形式は .NET をサポートするように拡張されました。

## <a name="use-the-correct-pdb-format-for-your-scenario"></a>シナリオに適した PDB 形式を使用する

ポータブル PDB も Windows PDB も、すべての場所でサポートされているわけではないため、使用する形式を決定するには、プロジェクトを使用およびデバッグする場所を検討する必要があります。 両方の形式で使用およびデバッグできるようにしたいプロジェクトがある場合は、異なるビルド構成を使用して、プロジェクトを 2 回ビルドし、両方の種類のコンシューマーをサポートできます。

### <a name="support-for-portable-pdbs"></a>ポータブル PDB のサポート

ポータブル PDB は、どのオペレーティング システムでも読み取ることができ、マネージド コードで推奨されるシンボル形式ですが、それがサポートされていないレガシ ツールとアプリケーションがいくつかあります。

* .NET Framework 4.7.1 以前を対象とするアプリケーション: 行番号に戻るマッピングが含まれるスタック トレースの出力 (ASP.NET のエラー ページなど)。 メソッドの名前は影響を受けません。ソース ファイル名と行番号のみがサポートされていません。

* ildasm や .NET Reflector などの .NET 逆コンパイラを使用して、ソース行マッピングまたはローカル パラメーター名の表示を予想します。

* 最新バージョンの [DIA](/visualstudio/debugger/debug-interface-access/debug-interface-access-sdk) と、シンボルの読み取りにそれを使用するツール (WinDBG など) ではポータブル PDB がサポートされますが、古いバージョンではサポートされません。

* 古いバージョンのプロファイラーで、ポータブル PDB がサポートされていない場合があります。

ポータブル PDB をサポートしていないツールでそれらを使用するには、ポータブル PDB と Windows PDB 間で変換する [Pdb2Pdb](https://github.com/dotnet/symreader-converter#pdb2pdb) を使用してみることができます。

### <a name="support-for-windows-pdbs"></a>Windows PDB のサポート

Windows PDB の書き込みまたは読み取りは、Windows 上でのみ可能です。 マネージド コードへの Windows PDB の使用は廃止されており、レガシ ツールでのみ必要です。 一部の新しいコンパイラ機能はポータブル PDB 専用に実装されているので、Windows PDB ではなくポータブル PDB を使用することをお勧めします。

## <a name="see-also"></a>関連項目

* [dotnet-symbol](./dotnet-symbol.md) を使用して、フレームワーク バイナリ用のシンボル ファイルをダウンロードできます

* [シンボルに関する Windows のドキュメント](/windows/win32/dxtecharts/debugging-with-symbols)
