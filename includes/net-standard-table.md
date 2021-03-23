---
ms.openlocfilehash: c690f2f1dcdee9d34a2a82435c3562fc7dfae04a
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104879664"
---
| .NET Standard              | [1.0]  | [1.1]  | [1.2] | [1.3] | [1.4] | [1.5]              | [1.6]              | [2.0]               | [2.1] |
|----------------------------|--------|--------|-------|-------|-------|--------------------|--------------------|---------------------|---------------------
| .NET                       | 5.0    | 5.0    | 5.0   | 5.0   | 5.0   | 5.0                | 5.0                | 5.0                 | 5.0 |
| .NET Core                  | 1.0    | 1.0    | 1.0   | 1.0   | 1.0   | 1.0                | 1.0                | 2.0                 | 3.0 |
| .NET Framework <sup>1</sup>| 4.5    | 4.5    | 4.5.1 | 4.6   | 4.6.1 | 4.6.1 <sup>2</sup> | 4.6.1 <sup>2</sup> | 4.6.1 <sup>2</sup>  | 該当なし<sup>3</sup> |
| Mono                       | 4.6    | 4.6    | 4.6   | 4.6   | 4.6   | 4.6                | 4.6                | 5.4                 | 6.4 |
| Xamarin.iOS                | 10.0   | 10.0   | 10.0  | 10.0  | 10.0  | 10.0               | 10.0               | 10.14               | 12.16 |
| Xamarin.Mac                | 3.0    | 3.0    | 3.0   | 3.0   | 3.0   | 3.0                | 3.0                | 3.8                 | 5.16 |
| Xamarin.Android            | 7.0    | 7.0    | 7.0   | 7.0   | 7.0   | 7.0                | 7.0                | 8.0                 | 10.0 |
| ユニバーサル Windows プラットフォーム | 10.0   | 10.0   | 10.0  | 10.0  | 10.0  | 10.0.16299         | 10.0.16299         | 10.0.16299          | TBD |
| Unity                      | 2018.1 | 2018.1 | 2018.1| 2018.1| 2018.1| 2018.1             |  2018.1            | 2018.1              | TBD |

<sup>1 .NET Framework のバージョン リストは、.NET Core 2.0 SDK 以降のバージョンのツールに適用されます。以前のバージョンでは、.NET Standard 1.5 以降で別のマッピングが使用されます。Visual Studio 2017 以降にアップグレードできない場合は、[Visual Studio 2015 用の .NET Core のツールをダウンロード](https://github.com/dotnet/core/blob/main/release-notes/download-archive.md)できます。</sup>

<sup>2 ここに挙げたバージョンは、特定の .NET Standard ライブラリを適用できるかどうかの判断で NuGet が使用する規則を表します。NuGet では .NET Framework 4.6.1 が .NET Standard 1.5 から 2.0 をサポートすると見なしますが、.NET Framework 4.6.1 プロジェクトのそれらのバージョンでビルドされた .NET Standard ライブラリを使用する際にいくつかの問題が発生します。そのようなライブラリを使用する必要がある .NET Framework プロジェクトでは、.NET Framework 4.7.2 以降を対象とするプロジェクトにアップグレードすることをお勧めします。</sup>

<sup>3 .NET Framework により .NET Standard 2.1 はサポートされていません。詳細については、[.NET Standard 2.1 のお知らせ](https://devblogs.microsoft.com/dotnet/announcing-net-standard-2-1/)に関するページを参照してください。</sup>

- 列は .NET Standard バージョンです。 各見出しセルは、そのバージョンの .NET Standard に追加された API に関するドキュメントのリンクになっています。
- 行は、各 .NET 実装です。
- 各セルのバージョン番号は、その .NET Standard バージョンをターゲットにするために必要な *最小* バージョンの実装です。
- 対話型のテーブルについては、「[.NET Standard バージョン](https://dotnet.microsoft.com/platform/dotnet-standard#versions)」を参照してください。

[1.0]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.0.md
[1.1]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.1.md
[1.2]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.2.md
[1.3]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.3.md
[1.4]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.4.md
[1.5]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.5.md
[1.6]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.6.md
[2.0]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard2.0.md
[2.1]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard2.1.md
