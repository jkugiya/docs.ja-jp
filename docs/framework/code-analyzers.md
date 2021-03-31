---
title: .NET Framework 用のコード アナライザー
titleSuffix: ''
description: .NET Framework Analyzers パッケージ内のアナライザーを使用し、コードの問題を見つけて対処する方法について学習します。
author: billwagner
ms.author: wiwagn
ms.date: 10/23/2020
ms.openlocfilehash: 69dfbc9f9645c7f602ffbce46308b241c119fd96
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2020
ms.locfileid: "103412164"
---
# <a name="code-analysis"></a>コード分析

コード アナライザーを使用すると、.NET Framework アプリケーション コードの潜在的な問題を見つけることができます。 アナライザーによって、潜在的な問題が検出され、その修正が提案されます。

コードを書くとき、あるいは CI ビルドの一部として、Roslyn ベースのコード アナライザーは、Visual Studio で対話的に動作します。 開発サイクルのできるだけ早い段階で、プロジェクトにアナライザーを追加する必要があります。 コードに潜む問題を見つけるのが早ければ早いほど、修正が簡単になります。 アナライザーによって、既存のコードの問題にフラグが設定され、開発を続けると、新しい問題に関する警告が表示されます。

## <a name="install-and-configure-analyzers"></a>アナライザーのインストールと構成

.NET Framework Analyzer は [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet パッケージで配布されます。 このパッケージには、.NET Framework API に固有のアナライザーが用意されており、これにはセキュリティ アナライザーが含まれています。 このパッケージは [Microsoft.CodeAnalysis.FxCopAnalyzers パッケージ](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)に含まれているので、パッケージをインストールする場合は、.NET Framework アナライザーを個別にインストールする必要はありません。

アナライザーを実行するすべてのプロジェクトに NuGet パッケージをインストールします。 1 人の開発者がそれをプロジェクトに追加すれば十分です。 アナライザー パッケージはプロジェクト依存関係であり、更新済みのソリューションが与えられると、あらゆる開発者のコンピューターで実行されます。

このパッケージをインストールするには、プロジェクトを右クリックし、[依存関係の管理] を選択します。 NuGet エクスプローラーで、"Microsoft.NetFramework.Analyzers" を検索します。 ソリューションのすべてのプロジェクトで安定した最新のバージョンをインストールします。

## <a name="use-the-analyzers"></a>アナライザーの使用

NuGet パッケージがインストールされたら、ソリューションをビルドします。 アナライザーは、コードベースで見つかった問題を報告します。 問題は Visual Studio の [エラー一覧] ウィンドウに警告として表示されます。次の画像をご覧ください。

![.NET Framework アナライザーによって報告される問題](./media/framework-analyzers-2.png)

コードを記述しているとき、コードに潜在的な問題があれば、その部分に波線が表示されます。
次の画像に示すように、問題をポイントすると、詳細情報が表示され、考えられる修正候補が表示されます。

![コード アナライザーによって検出された問題の対話型レポート。](./media/framework-analyzers-1.png)

詳細については、[Visual Studio のコード分析](/visualstudio/code-quality/roslyn-analyzers-overview)に関するページを参照してください。

## <a name="types-of-rules"></a>規則の種類

アナライザーによって、ソリューション内のコードが検査され、`CA` プレフィックスと共に警告が表示されます。 可能性のあるすべての警告の一覧については、「[コード品質規則](../fundamentals/code-analysis/quality-rules/index.md)」を参照してください。 .NET Framework の API に適用されるのは、次のような一部の警告のみです。

- [CA1058:型は、一定の基本型を拡張することはできません](../fundamentals/code-analysis/quality-rules/ca1058.md)

- [CA2153: 破損状態例外はキャッチしないでください](../fundamentals/code-analysis/quality-rules/ca2153.md)

- [CA2229:シリアル化コンストラクターを実装します](../fundamentals/code-analysis/quality-rules/ca2229.md)

- [CA2235:すべてのシリアル化不可能なフィールドを設定します](../fundamentals/code-analysis/quality-rules/ca2235.md)

- [CA2237: ISerializable 型を Serializable に設定します](../fundamentals/code-analysis/quality-rules/ca2237.md)

- [CA3075: XML の安全ではない DTD の処理](../fundamentals/code-analysis/quality-rules/ca3075.md)

- [CA5350: 脆弱な暗号アルゴリズムを使用しないでください](../fundamentals/code-analysis/quality-rules/ca5350.md)

- [CA5351 破られた暗号アルゴリズムを使用しないでください](../fundamentals/code-analysis/quality-rules/ca5351.md)

## <a name="see-also"></a>関連項目

- [Visual Studio でのコード分析](/visualstudio/code-quality/roslyn-analyzers-overview)
- [.NET SDK でのコード分析](../fundamentals/code-analysis/overview.md)
