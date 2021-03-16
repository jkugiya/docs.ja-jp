---
title: '破壊的変更:CA2014: stackalloc はループ内で使用しないでください。'
description: コード分析ルール CA2014 の有効化によって発生する .NET 5 での破壊的変更について学習します。
ms.date: 09/03/2020
ms.openlocfilehash: ac17c8ee588576947e21618a55c0eea883aa37ad
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257779"
---
# <a name="warning-ca2014-do-not-use-stackalloc-in-loops"></a>警告 CA2014:stackalloc はループ内で使用しないでください。

.NET コード アナライザー ルール [CA2014](/visualstudio/code-quality/ca2014) は、.NET 5.0 以降では既定で有効になっています。 [stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) 式がループ内で使用される C# コードに対して、ビルドの警告が生成されます。

## <a name="change-description"></a>変更内容

.NET 5 以降、.NET SDK には [.NET ソース コード アナライザー](../../../../fundamentals/code-analysis/overview.md)が含まれています。 これらのルールのいくつかは、[CA2014](/visualstudio/code-quality/ca2014) を含め、既定で有効になっています。 このルールに違反し、警告をエラーとして扱うように構成されているコードがプロジェクトに含まれている場合、この変更によってビルドが破損する可能性があります。

[stackalloc 式](../../../../csharp/language-reference/operators/stackalloc.md)がループ内で使用されるルール CA2014 によって、C# コードが検索されます。 [stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) によって、現在のスタック フレームからメモリが割り当てられます。 現在のメソッド呼び出しが戻るまでメモリは解放されません。これにより、スタック オーバーフローにつながる可能性があります。 スタック オーバーフローの例外をキャッチできないため、スタック オーバーフローが発生した場合はアプリが終了します。

## <a name="version-introduced"></a>導入されたバージョン

5.0

## <a name="recommended-action"></a>推奨アクション

- ループ内での [stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) の使用を避けます。 ループの外側でメモリ ブロックを割り当て、それをループ内で再利用してください。 詳細については、[CA2014](/visualstudio/code-quality/ca2014) に関する記事を参照してください。

- コード分析を完全に無効にするには、プロジェクト ファイルで `EnableNETAnalyzers` を `false` に設定します。 詳細については、「[EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers)」を参照してください。

## <a name="affected-apis"></a>影響を受ける API

API 分析では検出できません。

<!--

### Affected APIs

Not detectable via API analysis.

### Category

Code analysis

-->
