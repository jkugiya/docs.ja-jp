---
description: '詳細情報: Model-View-View Model を利用したポータブル クラス ライブラリの使用'
title: Model-View-View Model を利用した汎用性のあるクラス ライブラリの使用
ms.date: 07/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Portable Class Library [.NET Framework], and MVVM
- MVVM, and Portable Class Library
ms.assetid: 41a0b9f8-15a2-431a-bc35-e310b2953b03
ms.openlocfilehash: 4eea099aaa515c2b7d9874fd6c6d5c4132c5e7a2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "102402289"
---
# <a name="using-portable-class-library-with-model-view-view-model"></a>Model-View-View Model を利用した汎用性のあるクラス ライブラリの使用

.NET Framework [ポータブル クラス ライブラリ](portable-class-library.md)を使用して Model-View-View Model (MVVM) パターンを実装し、複数のプラットフォーム間でアセンブリを共有できます。

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 MVVM は、基になるビジネス ロジックからユーザー インターフェイスを分離するアプリケーション パターンです。 Visual Studio 2012 のポータブル クラス ライブラリ プロジェクトでモデル クラスとビュー モデル クラスを実装した後、さまざまなプラットフォーム向けにカスタマイズされたビューを作成できます。 この方法を使用すると、次の図に示すように、データ モデルとビジネス ロジックを 1 回だけ記述し、.NET Framework、Silverlight、Windows Phone、および Windows 8.x Store アプリからそのコードを使用できます。

 ![プラットフォーム間でアセンブリを共有する MVVM を使用したポータブル クラス ライブラリが示されています。](./media/using-portable-class-library-with-model-view-view-model/mvvm-share-assemblies-across-platforms.png)

 このトピックでは、MVVM パターンに関する一般的な情報については説明しません。 ここではポータブル クラス ライブラリを使用して MVVM を実装する方法についてのみ説明します。 MVVM の詳細については、「[WPF 用 Prism ライブラリ 5.0 を使用した MVVM クイック スタート](/previous-versions/msp-n-p/gg430857(v=pandp.40))」を参照してください。

## <a name="classes-that-support-mvvm"></a>MVVM がサポートされているクラス

 ポータブル クラス ライブラリ プロジェクトで .NET Framework 4.5、Windows 8.x Store アプリ用 .NET、Silverlight、または Windows Phone 7.5 をターゲットとする場合、MVVM パターンを実装するために次のクラスを使用できます。

- <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> クラス

- <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> クラス

- <xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType> クラス

- <xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType> クラス

- <xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType> クラス

- <xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType> クラス

- <xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType> クラス

- <xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType> クラス

- <xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType> クラス

- <xref:System.Windows.Input.ICommand?displayProperty=nameWithType> クラス

- <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType> 名前空間に含まれるすべてのクラス

## <a name="implementing-mvvm"></a>MVVM の実装

 MVVM を実装するには、通常、ポータブル クラス ライブラリ プロジェクトでモデルとビュー モデルの両方を作成します。ポータブル クラス ライブラリ プロジェクトではポータブルでないプロジェクトを参照できないためです。 モデルとビュー モデルは、同じプロジェクトに含めても、別々のプロジェクトに含めてもかまいません。 別々のプロジェクトを使用する場合は、ビュー モデル プロジェクトからモデル プロジェクトへの参照を追加します。

 モデルとビュー モデルのプロジェクトをコンパイルした後、ビューが含まれるアプリでそれらのアセンブリを参照します。 ビューがビュー モデルとのみ対話する場合は、ビュー モデルが含まれるアセンブリを参照するだけで済みます。

### <a name="model"></a>モデル

 次の例は、ポータブル クラス ライブラリ プロジェクトに配置できる簡略化されたモデル クラスを示しています。

 [!code-csharp[PortableClassLibraryMVVM#1](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customer.cs#1)]
 [!code-vb[PortableClassLibraryMVVM#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customer.vb#1)]

 次の例は、ポータブル クラス ライブラリ プロジェクトのデータを設定、取得、および更新するための簡単な方法を示しています。 実際のアプリでは、Windows Communication Foundation (WCF) サービスなどのソースからデータを取得します。

 [!code-csharp[PortableClassLibraryMVVM#2](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customerrepository.cs#2)]
 [!code-vb[PortableClassLibraryMVVM#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerrepository.vb#2)]

### <a name="view-model"></a>ビュー モデル

 多くの場合、ビュー モデルの基底クラスは MVVM パターンを実装する際に追加されます。 基底クラスの例を次に示します。

 [!code-csharp[PortableClassLibraryMVVM#3](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/viewmodelbase.cs#3)]
 [!code-vb[PortableClassLibraryMVVM#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/viewmodelbase.vb#3)]

 <xref:System.Windows.Input.ICommand> インターフェイスの実装は、MVVM パターンと共によく使用されます。 <xref:System.Windows.Input.ICommand> インターフェイスを実装する例を次に示します。

 [!code-csharp[PortableClassLibraryMVVM#4](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/relaycommand.cs#4)]
 [!code-vb[PortableClassLibraryMVVM#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/relaycommand.vb#4)]

 簡略化されたビュー モデルの例を次に示します。

 [!code-csharp[PortableClassLibraryMVVM#5](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainpageviewmodel.cs#5)]
 [!code-vb[PortableClassLibraryMVVM#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerviewmodel.vb#5)]  
  
### <a name="view"></a>表示  

 .NET Framework 4.5 アプリ、Windows 8.x Store アプリ、Silverlight ベースのアプリ、または Windows Phone 7.5 アプリから、モデルとビュー モデルのプロジェクトが含まれるアセンブリを参照できます。  その後、ビュー モデルと対話するビューを作成します。 次の例は、ビュー モデルからデータを取得して更新する簡素化された Windows Presentation Foundation (WPF) アプリを示しています。 Silverlight、Windows Phone、または Windows 8.x Store アプリでも同様のビューを作成できます。  
  
 [!code-xaml[PortableClassLibraryMVVM#6](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainwindow.xaml#6)]  
  
## <a name="see-also"></a>関連項目

- [ポータブル クラス ライブラリ](portable-class-library.md)
