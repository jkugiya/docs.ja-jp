---
title: 汎用性のあるクラス ライブラリを使用したプラットフォーム間の開発
description: .NET のポータブル クラスライブラリ プロジェクト タイプを使用すれば、Microsoft プラットフォーム向けのクロスプラットフォーム アプリやライブラリをすばやく簡単に構築できます。
ms.date: 09/17/2018
helpviewer_keywords:
- Portable Class Library [.NET Framework]
- targeting multiple platforms
- multiple platforms, targeting
ms.assetid: c31e1663-c164-4e65-b66d-d3aa8750a154
ms.openlocfilehash: ced595f62249609f4524d0b4b7bf734929619bfd
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2020
ms.locfileid: "102402287"
---
# <a name="cross-platform-development-with-the-portable-class-library"></a>ポータブル クラス ライブラリを使用したクロスプラットフォームの開発

Visual Studio のポータブル クラス ライブラリ プロジェクト タイプを使用すれば、Microsoft プラットフォーム向けのクロスプラットフォーム アプリやライブラリをすばやく簡単に構築できます。

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

ポータブル クラス ライブラリにより、コードの開発とテストにかかる時間とコストを削減できます。 このプロジェクト タイプを使用してポータブル .NET Framework アセンブリを記述およびビルドしてから、.NET Framework、iOS、Mac などの複数のプラットフォームをターゲットとしたアプリから、それらのアセンブリを参照します。

Visual Studio でポータブル クラス ライブラリ プロジェクトを作成し、プロジェクトの開発を開始した後でも、ターゲット プラットフォームを変更できます。 Visual Studio では新しいアセンブリを使用してライブラリをコンパイルするので、コード内で行う必要がある変更を確認できます。

## <a name="create-a-portable-class-library-project"></a>ポータブル クラス ライブラリ プロジェクトを作成する

ポータブル クラス ライブラリを作成するには、Visual Studio に用意されているテンプレートを使用します。 新しいプロジェクトを作成し ( **[ファイル]**  >  **[新しいプロジェクト]** )、 **[新しいプロジェクト]** ダイアログ ボックスで、使用するプログラミング言語 (Visual C# または Visual Basic) を選択します。 次に、 **[クラス ライブラリ (レガシ ポータブル)]** テンプレートを選択します。 プロジェクトの名前を入力し、 **[OK]** を選択します。

**[ポータブル クラス ライブラリの追加]** ダイアログ ボックスが表示されます。 2 つ以上のターゲットを選択してから、 **[OK]** を選択します。

![Visual Studio でポータブル クラス ライブラリ ターゲットを追加する](media/add-portable-class-library.png)

## <a name="change-targets"></a>ターゲットを変更する

ポータブル クラス ライブラリ プロジェクトのターゲット プラットフォームは、それを作成するときでも、開発を開始してからでも変更できます。 プロジェクトの作成後にターゲットを変更するには、**ソリューション エクスプローラー** で、(ソリューションではなく) ポータブル クラス ライブラリ プロジェクトのショートカット メニューを開き、 **[プロパティ]** を選択します。 プロジェクトのプロパティ ページの **[ライブラリ]** タブに、プロジェクトの現在のターゲット プラットフォームが表示されます。

![Visual Studio でのポータブル クラス ライブラリのプロジェクト プロパティ](media/pcl-project-properties.png)

ターゲットを追加または削除するには、 **[変更]** ボタンをクリックして、適切なチェック ボックスをオンまたはオフにします。

ターゲットを変更すると、変更後のターゲットに合わせて、プロジェクトの開発に使用できる API が変更されます。 Visual Studio は、ターゲットを変更したことで発生する可能性があるエラーと警告を報告します。

Visual Studio で変更を行う前にアセンブリの移植性を評価する場合は、[.NET 移植性アナライザー](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)を使用できます。

## <a name="supported-types-and-members"></a>サポートされている型とメンバー

ポータブル クラス ライブラリのプロジェクトで使用できる型とメンバーは、互換性に関するいくつかの要因による制約を受けます。

- 選択したターゲット間で共有される必要があります。

- それらのターゲット間で同様に動作する必要があります。

- 廃止候補であってはなりません。

- 特にサポートしているメンバーがポータブルでない場合は、ポータブルな環境に意味がある必要があります。

メンバーがポータブル クラス ライブラリでサポートされており、選択したターゲットのメンバーである場合、IntelliSense でプロジェクトにこのメンバーが表示されます。 ただし、API がポータブル クラス ライブラリでサポートされている可能性があります。API を使用できるかどうかは、選択したターゲットによって異なります。

## <a name="api-differences-in-the-portable-class-library"></a>ポータブル クラス ライブラリでの API の相違点

サポートされるすべてのプラットフォームでポータブル クラス ライブラリ アセンブリの互換性を確保するために、ポータブル クラス ライブラリでは一部のメンバーが若干変更されています。

## <a name="use-the-portable-class-library"></a>ポータブル クラス ライブラリを使用する

ポータブル クラス ライブラリ プロジェクトをビルドしたら、他のプロジェクトからそのプロジェクトを参照します。 プロジェクトを参照することも、アクセスする必要のあるクラスを含む特定のアセンブリを参照することもできます。

ポータブル クラス ライブラリ アセンブリを参照するアプリを実行するには、ターゲット プラットフォームの必要なバージョン (またはそれ以上のバージョン) がコンピューターにインストールされている必要があります。 Visual Studio には必要なすべてのフレームワークが含まれるため、さらに変更を加えることなく、アプリケーションの開発に使用したコンピューターでアプリケーションを実行できます。

### <a name="deploy-a-universal-windows-app"></a>ユニバーサル Windows アプリを配置する

ポータブル クラス ライブラリ アセンブリを参照するユニバーサル Windows アプリを作成する場合、そのアプリを配置するために必要なすべての機能はアプリ パッケージに含まれており、追加の作業は不要です。

### <a name="deploy-a-net-framework-app"></a>.NET Framework アプリを配置する

ポータブル クラス ライブラリ アセンブリを参照する .NET Framework アプリを配置するときは、.NET Framework の正しいバージョンに対する依存関係を指定する必要があります。 この依存関係を指定することで、必要なバージョンがアプリケーションと共に確実にインストールされます。

- ClickOnce 配置で依存関係を作成するには、**ソリューション エクスプローラー** で、発行するプロジェクトのプロジェクト ノードを選択します (これは、ポータブル クラス ライブラリ プロジェクトを参照するプロジェクトです)。メニュー バーで **[プロジェクト]**  >  **[プロパティ]** の順に選択してから、 **[発行]** タブを選択します。 **[発行]** ページで、 **[必須コンポーネント]** をクリックします。 必須コンポーネントとして、必要な .NET Framework のバージョンを選択します。

- セットアップ プロジェクトで依存関係を作成するには、**ソリューション エクスプローラー** で、セットアップ プロジェクトを選択します。 メニュー バーで、 **[プロジェクト]**  >  **[プロパティ]**  >  **[必須コンポーネント]** の順に選択します。 必須コンポーネントとして、必要な .NET Framework のバージョンを選択します。

.NET Framework アプリの配置の詳細については、[開発者向けの配置ガイド](../../framework/deployment/deployment-guide-for-developers.md)を参照してください。

## <a name="see-also"></a>関連項目

- [MVVM を利用した汎用性のあるクラス ライブラリの使用](using-portable-class-library-with-model-view-view-model.md)
- [複数のプラットフォームを対象とするライブラリのアプリ リソース](app-resources-for-libraries-that-target-multiple-platforms.md)
- [.NET Portability Analyzer](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)
- [Windows ストア アプリおよび Windows ランタイムのための .NET Framework サポート](support-for-windows-store-apps-and-windows-runtime.md)
- [配置](../../framework/deployment/net-framework-applications.md)
