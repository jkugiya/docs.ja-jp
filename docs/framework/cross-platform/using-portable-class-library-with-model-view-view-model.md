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
# <a name="using-portable-class-library-with-model-view-view-model"></a><span data-ttu-id="a2482-103">Model-View-View Model を利用した汎用性のあるクラス ライブラリの使用</span><span class="sxs-lookup"><span data-stu-id="a2482-103">Using Portable Class Library with Model-View-View Model</span></span>

<span data-ttu-id="a2482-104">.NET Framework [ポータブル クラス ライブラリ](portable-class-library.md)を使用して Model-View-View Model (MVVM) パターンを実装し、複数のプラットフォーム間でアセンブリを共有できます。</span><span class="sxs-lookup"><span data-stu-id="a2482-104">You can use the .NET Framework [Portable Class Library](portable-class-library.md) to implement the Model-View-View Model (MVVM) pattern and share assemblies across multiple platforms.</span></span>

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 <span data-ttu-id="a2482-105">MVVM は、基になるビジネス ロジックからユーザー インターフェイスを分離するアプリケーション パターンです。</span><span class="sxs-lookup"><span data-stu-id="a2482-105">MVVM is an application pattern that isolates the user interface from the underlying business logic.</span></span> <span data-ttu-id="a2482-106">Visual Studio 2012 のポータブル クラス ライブラリ プロジェクトでモデル クラスとビュー モデル クラスを実装した後、さまざまなプラットフォーム向けにカスタマイズされたビューを作成できます。</span><span class="sxs-lookup"><span data-stu-id="a2482-106">You can implement the model and view model classes in a Portable Class Library project in Visual Studio 2012, and then create views that are customized for different platforms.</span></span> <span data-ttu-id="a2482-107">この方法を使用すると、次の図に示すように、データ モデルとビジネス ロジックを 1 回だけ記述し、.NET Framework、Silverlight、Windows Phone、および Windows 8.x Store アプリからそのコードを使用できます。</span><span class="sxs-lookup"><span data-stu-id="a2482-107">This approach enables you to write the data model and business logic only once, and use that code from .NET Framework, Silverlight, Windows Phone, and Windows 8.x Store apps, as shown in the following illustration.</span></span>

 ![プラットフォーム間でアセンブリを共有する MVVM を使用したポータブル クラス ライブラリが示されています。](./media/using-portable-class-library-with-model-view-view-model/mvvm-share-assemblies-across-platforms.png)

 <span data-ttu-id="a2482-109">このトピックでは、MVVM パターンに関する一般的な情報については説明しません。</span><span class="sxs-lookup"><span data-stu-id="a2482-109">This topic does not provide general information about the MVVM pattern.</span></span> <span data-ttu-id="a2482-110">ここではポータブル クラス ライブラリを使用して MVVM を実装する方法についてのみ説明します。</span><span class="sxs-lookup"><span data-stu-id="a2482-110">It only provides information about how to use Portable Class Library to implement MVVM.</span></span> <span data-ttu-id="a2482-111">MVVM の詳細については、「[WPF 用 Prism ライブラリ 5.0 を使用した MVVM クイック スタート](/previous-versions/msp-n-p/gg430857(v=pandp.40))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2482-111">For more information about MVVM, see the [MVVM Quickstart Using the Prism Library 5.0 for WPF](/previous-versions/msp-n-p/gg430857(v=pandp.40)).</span></span>

## <a name="classes-that-support-mvvm"></a><span data-ttu-id="a2482-112">MVVM がサポートされているクラス</span><span class="sxs-lookup"><span data-stu-id="a2482-112">Classes That Support MVVM</span></span>

 <span data-ttu-id="a2482-113">ポータブル クラス ライブラリ プロジェクトで .NET Framework 4.5、Windows 8.x Store アプリ用 .NET、Silverlight、または Windows Phone 7.5 をターゲットとする場合、MVVM パターンを実装するために次のクラスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="a2482-113">When you target the .NET Framework 4.5, .NET for Windows 8.x Store apps, Silverlight, or Windows Phone 7.5 for your Portable Class Library project, the following classes are available for implementing the MVVM pattern:</span></span>

- <span data-ttu-id="a2482-114"><xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> クラス</span><span class="sxs-lookup"><span data-stu-id="a2482-114"><xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="a2482-115"><xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> クラス</span><span class="sxs-lookup"><span data-stu-id="a2482-115"><xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="a2482-116"><xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType> クラス</span><span class="sxs-lookup"><span data-stu-id="a2482-116"><xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="a2482-117"><xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType> クラス</span><span class="sxs-lookup"><span data-stu-id="a2482-117"><xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="a2482-118"><xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType> クラス</span><span class="sxs-lookup"><span data-stu-id="a2482-118"><xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="a2482-119"><xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType> クラス</span><span class="sxs-lookup"><span data-stu-id="a2482-119"><xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="a2482-120"><xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType> クラス</span><span class="sxs-lookup"><span data-stu-id="a2482-120"><xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="a2482-121"><xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType> クラス</span><span class="sxs-lookup"><span data-stu-id="a2482-121"><xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="a2482-122"><xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType> クラス</span><span class="sxs-lookup"><span data-stu-id="a2482-122"><xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="a2482-123"><xref:System.Windows.Input.ICommand?displayProperty=nameWithType> クラス</span><span class="sxs-lookup"><span data-stu-id="a2482-123"><xref:System.Windows.Input.ICommand?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="a2482-124"><xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType> 名前空間に含まれるすべてのクラス</span><span class="sxs-lookup"><span data-stu-id="a2482-124">All classes in the <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType> namespace</span></span>

## <a name="implementing-mvvm"></a><span data-ttu-id="a2482-125">MVVM の実装</span><span class="sxs-lookup"><span data-stu-id="a2482-125">Implementing MVVM</span></span>

 <span data-ttu-id="a2482-126">MVVM を実装するには、通常、ポータブル クラス ライブラリ プロジェクトでモデルとビュー モデルの両方を作成します。ポータブル クラス ライブラリ プロジェクトではポータブルでないプロジェクトを参照できないためです。</span><span class="sxs-lookup"><span data-stu-id="a2482-126">To implement MVVM, you typically create both the model and the view model in a Portable Class Library project, because a Portable Class Library project cannot reference a non-portable project.</span></span> <span data-ttu-id="a2482-127">モデルとビュー モデルは、同じプロジェクトに含めても、別々のプロジェクトに含めてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="a2482-127">The model and view model can be in the same project or in separate projects.</span></span> <span data-ttu-id="a2482-128">別々のプロジェクトを使用する場合は、ビュー モデル プロジェクトからモデル プロジェクトへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="a2482-128">If you use separate projects, add a reference from the view model project to the model project.</span></span>

 <span data-ttu-id="a2482-129">モデルとビュー モデルのプロジェクトをコンパイルした後、ビューが含まれるアプリでそれらのアセンブリを参照します。</span><span class="sxs-lookup"><span data-stu-id="a2482-129">After you compile the model and view model projects, you reference those assemblies in the app that contains the view.</span></span> <span data-ttu-id="a2482-130">ビューがビュー モデルとのみ対話する場合は、ビュー モデルが含まれるアセンブリを参照するだけで済みます。</span><span class="sxs-lookup"><span data-stu-id="a2482-130">If the view interacts only with the view model, you only have to reference the assembly that contains the view model.</span></span>

### <a name="model"></a><span data-ttu-id="a2482-131">モデル</span><span class="sxs-lookup"><span data-stu-id="a2482-131">Model</span></span>

 <span data-ttu-id="a2482-132">次の例は、ポータブル クラス ライブラリ プロジェクトに配置できる簡略化されたモデル クラスを示しています。</span><span class="sxs-lookup"><span data-stu-id="a2482-132">The following example shows a simplified model class that could reside in a Portable Class Library project.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#1](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customer.cs#1)]
 [!code-vb[PortableClassLibraryMVVM#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customer.vb#1)]

 <span data-ttu-id="a2482-133">次の例は、ポータブル クラス ライブラリ プロジェクトのデータを設定、取得、および更新するための簡単な方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="a2482-133">The following example shows a simple way to populate, retrieve, and update the data in a Portable Class Library project.</span></span> <span data-ttu-id="a2482-134">実際のアプリでは、Windows Communication Foundation (WCF) サービスなどのソースからデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="a2482-134">In a real app, you would retrieve the data from a source such as a Windows Communication Foundation (WCF) service.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#2](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customerrepository.cs#2)]
 [!code-vb[PortableClassLibraryMVVM#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerrepository.vb#2)]

### <a name="view-model"></a><span data-ttu-id="a2482-135">ビュー モデル</span><span class="sxs-lookup"><span data-stu-id="a2482-135">View Model</span></span>

 <span data-ttu-id="a2482-136">多くの場合、ビュー モデルの基底クラスは MVVM パターンを実装する際に追加されます。</span><span class="sxs-lookup"><span data-stu-id="a2482-136">A base class for view models is frequently added when implementing the MVVM pattern.</span></span> <span data-ttu-id="a2482-137">基底クラスの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a2482-137">The following example shows a base class.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#3](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/viewmodelbase.cs#3)]
 [!code-vb[PortableClassLibraryMVVM#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/viewmodelbase.vb#3)]

 <span data-ttu-id="a2482-138"><xref:System.Windows.Input.ICommand> インターフェイスの実装は、MVVM パターンと共によく使用されます。</span><span class="sxs-lookup"><span data-stu-id="a2482-138">An implementation of the <xref:System.Windows.Input.ICommand> interface is frequently used with the MVVM pattern.</span></span> <span data-ttu-id="a2482-139"><xref:System.Windows.Input.ICommand> インターフェイスを実装する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a2482-139">The following example shows an implementation of the <xref:System.Windows.Input.ICommand> interface.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#4](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/relaycommand.cs#4)]
 [!code-vb[PortableClassLibraryMVVM#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/relaycommand.vb#4)]

 <span data-ttu-id="a2482-140">簡略化されたビュー モデルの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a2482-140">The following example shows a simplified view model.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#5](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainpageviewmodel.cs#5)]
 [!code-vb[PortableClassLibraryMVVM#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerviewmodel.vb#5)]  
  
### <a name="view"></a><span data-ttu-id="a2482-141">表示</span><span class="sxs-lookup"><span data-stu-id="a2482-141">View</span></span>  

 <span data-ttu-id="a2482-142">.NET Framework 4.5 アプリ、Windows 8.x Store アプリ、Silverlight ベースのアプリ、または Windows Phone 7.5 アプリから、モデルとビュー モデルのプロジェクトが含まれるアセンブリを参照できます。</span><span class="sxs-lookup"><span data-stu-id="a2482-142">From a .NET Framework 4.5 app, Windows 8.x Store app, Silverlight-based app, or Windows Phone 7.5 app, you can reference the assembly that contains the model and view model projects.</span></span>  <span data-ttu-id="a2482-143">その後、ビュー モデルと対話するビューを作成します。</span><span class="sxs-lookup"><span data-stu-id="a2482-143">You then create a view that interacts with the view model.</span></span> <span data-ttu-id="a2482-144">次の例は、ビュー モデルからデータを取得して更新する簡素化された Windows Presentation Foundation (WPF) アプリを示しています。</span><span class="sxs-lookup"><span data-stu-id="a2482-144">The following example shows a simplified Windows Presentation Foundation (WPF) app that retrieves and updates data from the view model.</span></span> <span data-ttu-id="a2482-145">Silverlight、Windows Phone、または Windows 8.x Store アプリでも同様のビューを作成できます。</span><span class="sxs-lookup"><span data-stu-id="a2482-145">You could create similar views in Silverlight, Windows Phone, or Windows 8.x Store apps.</span></span>  
  
 [!code-xaml[PortableClassLibraryMVVM#6](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainwindow.xaml#6)]  
  
## <a name="see-also"></a><span data-ttu-id="a2482-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="a2482-146">See also</span></span>

- [<span data-ttu-id="a2482-147">ポータブル クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="a2482-147">Portable Class Library</span></span>](portable-class-library.md)
