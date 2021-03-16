---
description: '詳細情報: 複数のプラットフォームを対象とするライブラリのアプリ リソース'
title: 複数のプラットフォームを対象とするライブラリのアプリケーション リソース
ms.date: 07/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- multiple platforms, resources for
- resources [.NET Framework]
- .NET Framework, resources when targeting multiple platforms
- resources, for multiple platforms
- targeting multiple platforms, resources for
ms.assetid: 72c76f0b-7255-4576-9261-3587f949669c
ms.openlocfilehash: c6d1a8d19c58174e4b08842c4965dfbe3389d1e8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "102402294"
---
# <a name="app-resources-for-libraries-that-target-multiple-platforms"></a>複数のプラットフォームを対象とするライブラリのアプリケーション リソース

.NET Framework の[ポータブル クラス ライブラリ](portable-class-library.md) プロジェクトの種類を使用すると、複数のプラットフォームからクラス ライブラリのリソースにアクセスできることを保証できます。 このプロジェクトの種類は Visual Studio 2012 で利用でき、.NET Framework クラス ライブラリの移植性の高いサブセットを対象としています。 ポータブル クラス ライブラリを使用すると、デスクトップ アプリ、Silverlight アプリ、Windows Phone アプリ、Windows 8.x ストア アプリからライブラリにアクセスできるようになります。

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 ポータブル クラス ライブラリ プロジェクトでは、アプリケーションで使用できるのは <xref:System.Resources> 名前空間内の非常に限られた型のサブセットのみですが、<xref:System.Resources.ResourceManager> クラスを使用してリソースを取得することはできます。 ただし、Visual Studio を使用してアプリケーションを作成する場合は、<xref:System.Resources.ResourceManager> クラス ライブラリを使用するのではなく、Visual Studio によって作成された厳密に型指定されたラッパーを使用する必要があります。

 Visual Studio で厳密に型指定されたラッパーを作成するには、Visual Studio リソース デザイナーでメイン リソース ファイルの **[アクセス修飾子]** を **[パブリック]** に設定します。 これにより、厳密に型指定された ResourceManager ラッパーを含む [resourceFileName].designer.cs または [resourceFileName].designer.vb ファイルが作成されます。 厳密に型指定されたリソース ラッパーの使用方法の詳細については、トピック「[Resgen.exe (リソース ファイル ジェネレーター)](../../framework/tools/resgen-exe-resource-file-generator.md)」の「厳密に型指定されたリソース クラスの生成」を参照してください。

## <a name="resource-manager-in-the-portable-class-library"></a>ポータブル クラス ライブラリの Resource Manager

 ポータブル クラス ライブラリ プロジェクトでは、リソースへのすべてのアクセスは <xref:System.Resources.ResourceManager> クラスによって処理されます。 <xref:System.Resources.ResourceReader> や <xref:System.Resources.ResourceSet> などの <xref:System.Resources> 名前空間の型にはポータブル クラス ライブラリ プロジェクトからアクセスできないため、これらはリソースへのアクセスには使用できません。

 ポータブル クラス ライブラリ プロジェクトには、以下の表に示す 4 つの <xref:System.Resources.ResourceManager> メンバーが含まれています。 これらのコンストラクターおよびメソッドを使用すると、<xref:System.Resources.ResourceManager> オブジェクトをインスタンス化して文字列リソースを取得できます。

|`ResourceManager` のメンバー|説明|
|------------------------------|-----------------|
|<xref:System.Resources.ResourceManager.%23ctor%28System.String%2CSystem.Reflection.Assembly%29>|<xref:System.Resources.ResourceManager> インスタンスを作成し、指定されたアセンブリ内にある、名前の指定されたリソース ファイルにアクセスします。|
|<xref:System.Resources.ResourceManager.%23ctor%28System.Type%29>|指定された型に対応する <xref:System.Resources.ResourceManager> インスタンスを作成します。|
|<xref:System.Resources.ResourceManager.GetString%28System.String%29>|現在のカルチャに対する、名前の指定されたリソースを取得します。|
|<xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>|指定されたカルチャに属する、名前の指定されたリソースを取得します。|

 ポータブル クラス ライブラリの他の <xref:System.Resources.ResourceManager> メンバーを除外すると、シリアル化されたオブジェクト、文字列以外のデータ、およびイメージはリソース ファイルから取得できなくなります。 ポータブル クラス ライブラリからリソースを使用するには、すべてのオブジェクト データを文字列形式で格納する必要があります。 たとえば、数値を文字列に変換してリソース ファイルに格納し、これらを取得して、数値データ型の `Parse` メソッドまたは `TryParse` メソッドを使用して数値に戻すことができます。 イメージや他のバイナリ データを文字列形式に変換するには <xref:System.Convert.ToBase64String%2A?displayProperty=nameWithType> メソッドを呼び出し、バイト配列に戻すには <xref:System.Convert.FromBase64String%2A?displayProperty=nameWithType> メソッドを呼び出します。

## <a name="the-portable-class-library-and-windows-store-apps"></a>ポータブル クラス ライブラリと Windows ストア アプリ

 ポータブル クラス ライブラリ プロジェクトでは、リソースを .resx ファイルに格納します。これらのファイルはその後 .resources ファイルにコンパイルされ、コンパイル時にメイン アセンブリまたはサテライト アセンブリに埋め込まれます。 一方、Windows 8.x ストア アプリでは、リソースを .resw ファイルに格納する必要があります。このファイルはその後、単一のパッケージ リソース インデックス (PRI) ファイルにコンパイルされます。 ただし、ファイル形式に互換性がないにもかかわらず、ポータブル クラス ライブラリは Windows 8.x ストア アプリで機能します。

 クラス ライブラリを Windows 8.x ストア アプリで使用するには、Windows ストア アプリケーション プロジェクトでその参照を追加します。 Visual Studio によりアセンブリのリソースが .resw ファイルに透過的に抽出され、それを使用して PRI ファイルが生成されて、そこから Windows ランタイムでリソースを抽出できます。 実行時に Windows ランタイムによりポータブル クラス ライブラリ内のコードが実行されますが、ポータブル クラス ライブラリのリソースは PRI ファイルから取得されます。

 ローカライズされたリソースがポータブル クラス ライブラリ プロジェクトに含まれている場合は、デスクトップ アプリケーション内のライブラリの場合と同様に、ハブ アンド スポーク モデルを使用してこれらを配置します。 メイン リソース ファイルおよびローカライズされたリソース ファイルを Windows 8.x ストア アプリで使用するには、参照をメイン アセンブリに追加します。 コンパイル時に、Visual Studio はメイン リソース ファイルとローカライズされているリソース ファイルからリソースを個別の .resw ファイルに抽出します。 次に、実行時に Windows ランタイムによってアクセスされる単一の PRI ファイルに .resw ファイルをコンパイルします。

<a name="NonLoc"></a>

## <a name="example-non-localized-portable-class-library"></a>例: ローカライズされていないポータブル クラス ライブラリ

 以下の単純なローカライズされていないポータブル クラス ライブラリの例では、リソースを使用して列名が格納され、表形式データ用に予約する文字数が決定されます。 この例では LibResources.resx という名前のファイルを使用して、次の表に示す文字列リソースを格納します。

|リソース名|リソースの値|
|-------------------|--------------------|
|Born|Birthdate|
|BornLength|12|
|Hired|Hire Date|
|HiredLength|12|
|id|id|
|ID.Length|12|
|名前|名前|
|NameLength|25|
|タイトル|従業員データベース|

 次のコードにより、ファイルの **[アクセス修飾子]** が **[パブリック]** に変更されると Visual Studio によって生成される `resources` という名前の Resource Manager ラッパーを使用する `UILibrary` クラスが定義されます。 UILibrary クラスは必要に応じて文字列データを解析します。 . このクラスは `MyCompany.Employees` 名前空間にあることに注意してください。

 [!code-csharp[Conceptual.Resources.Portable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/uilibrary.cs#1)]
 [!code-vb[Conceptual.Resources.Portable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/uilibrary.vb#1)]

 次のコードは、`UILibrary` クラスとそのリソースをコンソールモード アプリケーションからアクセスする方法を示します。 コンソール アプリケーションのプロジェクトに追加するには UILibrary.dll への参照が必要です。

 [!code-csharp[Conceptual.Resources.Portable#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program.cs#2)]
 [!code-vb[Conceptual.Resources.Portable#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module1.vb#2)]

 次のコードでは、`UILibrary` クラスとそのリソースを Windows 8.x ストア アプリからアクセスする方法が示されています。 Windows ストア アプリケーション プロジェクトに追加するには UILibrary.dll への参照が必要です。

 [!code-csharp[Conceptual.Resources.PortableMetro#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetro/cs/blankpage.xaml.cs#1)]

## <a name="example-localized-portable-class-library"></a>例: ローカライズされたポータブル クラス ライブラリ

 以下のローカライズされているポータブル クラス ライブラリの例には、フランス語 (フランス) と英語 (米国) のカルチャのリソースが含まれています。 英語 (米国) のカルチャはアプリケーションの既定のカルチャです。そのリソースは[前のセクション](app-resources-for-libraries-that-target-multiple-platforms.md#NonLoc)の表に示されています。 フランス語 (フランス) のカルチャのリソース ファイルは LibResources.fr-FR.resx という名前で、以下の表に示す文字列リソースで構成されています。 `UILibrary` クラスのソース コードは前のセクションに示すものと同じです。

|リソース名|リソースの値|
|-------------------|--------------------|
|Born|Date de naissance|
|BornLength|20|
|Hired|Date embauché|
|HiredLength|16|
|id|id|
|名前|Nom|
|タイトル|Base de données des employés|

 次のコードは、`UILibrary` クラスとそのリソースをコンソールモード アプリケーションからアクセスする方法を示します。 コンソール アプリケーションのプロジェクトに追加するには UILibrary.dll への参照が必要です。

 [!code-csharp[Conceptual.Resources.Portable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program2.cs#3)]
 [!code-vb[Conceptual.Resources.Portable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module2.vb#3)]

 次のコードでは、`UILibrary` クラスとそのリソースを Windows 8.x ストア アプリからアクセスする方法が示されています。 Windows ストア アプリケーション プロジェクトに追加するには UILibrary.dll への参照が必要です。 静的な `ApplicationLanguages.PrimaryLanguageOverride` プロパティを使用してアプリケーションの優先言語をフランス語に設定します。

 [!code-csharp[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetroloc/cs/blankpage.xaml.cs#1)]
 [!code-vb[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portablemetroloc/vb/blankpage.xaml.vb#1)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Resources.ResourceManager>
- [デスクトップ アプリケーションのリソース](../../framework/resources/index.md)
- [リソースのパッケージ化と配置](../../framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
