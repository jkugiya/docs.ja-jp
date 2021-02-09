---
description: '詳細情報: Visual Basic でのコンポーネントの作成および使用'
title: コンポーネントの作成および使用
ms.date: 07/20/2015
helpviewer_keywords:
- components [Visual Basic]
ms.assetid: ee6a4156-73f7-4e9b-8e01-c74c4798b65c
ms.openlocfilehash: f59b4774556d95dcbc1befb16409d68a51c50535
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666590"
---
# <a name="creating-and-using-components-in-visual-basic"></a><span data-ttu-id="1491d-103">Visual Basic でのコンポーネントの作成および使用</span><span class="sxs-lookup"><span data-stu-id="1491d-103">Creating and Using Components in Visual Basic</span></span>

<span data-ttu-id="1491d-104">*コンポーネント* は、<xref:System.ComponentModel.IComponent?displayProperty=nameWithType> インターフェイスを実装するか、<xref:System.ComponentModel.IComponent> を実装するクラスから直接的または間接的に派生するクラスです。</span><span class="sxs-lookup"><span data-stu-id="1491d-104">A *component* is a class that implements the <xref:System.ComponentModel.IComponent?displayProperty=nameWithType> interface or that derives directly or indirectly from a class that implements <xref:System.ComponentModel.IComponent>.</span></span> <span data-ttu-id="1491d-105">.NET コンポーネントは、再利用可能なオブジェクトであり、他のオブジェクトとやり取りでき、外部リソースの制御やデザイン時のサポートが用意されています。</span><span class="sxs-lookup"><span data-stu-id="1491d-105">A .NET component is an object that is reusable, can interact with other objects, and provides control over external resources and design-time support.</span></span>  
  
 <span data-ttu-id="1491d-106">コンポーネントの重要な特徴の 1 つは、コンポーネントがデザイン可能であるということです。つまり、コンポーネントであるクラスは Visual Studio 統合開発環境で使用できます。</span><span class="sxs-lookup"><span data-stu-id="1491d-106">An important feature of components is that they are designable, which means that a class that is a component can be used in the Visual Studio Integrated Development Environment.</span></span> <span data-ttu-id="1491d-107">コンポーネントは、ツールボックスへの追加、フォームへのドラッグ アンド ドロップ、デザイン サーフェイスでの操作が可能です。</span><span class="sxs-lookup"><span data-stu-id="1491d-107">A component can be added to the Toolbox, dragged and dropped onto a form, and manipulated on a design surface.</span></span> <span data-ttu-id="1491d-108">.NET には、コンポーネントのベースのデザイン時サポートが組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="1491d-108">Base design-time support for components is built into .NET.</span></span> <span data-ttu-id="1491d-109">コンポーネントの開発者は、ベースのデザイン時機能を利用するために、追加の作業を行う必要はありません。</span><span class="sxs-lookup"><span data-stu-id="1491d-109">A component developer does not have to do any additional work to take advantage of the base design-time functionality.</span></span>  
  
 <span data-ttu-id="1491d-110">デザイン可能という点では、"*コントロール*" もコンポーネントに似ています。</span><span class="sxs-lookup"><span data-stu-id="1491d-110">A *control* is similar to a component, as both are designable.</span></span> <span data-ttu-id="1491d-111">ただし、コントロールにはユーザー インターフェイスが用意されているのに対し、コンポーネントには用意されていません。</span><span class="sxs-lookup"><span data-stu-id="1491d-111">However, a control provides a user interface, while a component does not.</span></span> <span data-ttu-id="1491d-112">コントロールは基本コントロール クラスである <xref:System.Windows.Forms.Control> または <xref:System.Web.UI.Control> から派生する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1491d-112">A control must derive from one of the base control classes: <xref:System.Windows.Forms.Control> or <xref:System.Web.UI.Control>.</span></span>  
  
## <a name="when-to-create-a-component"></a><span data-ttu-id="1491d-113">コンポーネントを作成する状況</span><span class="sxs-lookup"><span data-stu-id="1491d-113">When to Create a Component</span></span>  

 <span data-ttu-id="1491d-114">デザイン サーフェイス (Windows フォーム デザイナーや Web フォーム デザイナーなど) で使用するクラスにユーザー インターフェイスがない場合、そのクラスは、コンポーネントにして、<xref:System.ComponentModel.IComponent> を実装するか、<xref:System.ComponentModel.IComponent> を直接または間接的に実装するクラスから派生させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="1491d-114">If your class will be used on a design surface (such as the Windows Forms or Web Forms Designer) but has no user interface, it should be a component and implement <xref:System.ComponentModel.IComponent>, or derive from a class that directly or indirectly implements <xref:System.ComponentModel.IComponent>.</span></span>  
  
 <span data-ttu-id="1491d-115"><xref:System.ComponentModel.Component> クラスと <xref:System.ComponentModel.MarshalByValueComponent> クラスは、<xref:System.ComponentModel.IComponent> インターフェイスの基本実装です。</span><span class="sxs-lookup"><span data-stu-id="1491d-115">The <xref:System.ComponentModel.Component> and <xref:System.ComponentModel.MarshalByValueComponent> classes are base implementations of the <xref:System.ComponentModel.IComponent> interface.</span></span> <span data-ttu-id="1491d-116">これらのクラスの主な違いは、<xref:System.ComponentModel.Component> クラスは参照渡しでマーシャリングされ、<xref:System.ComponentModel.IComponent> は値渡しでマーシャリングされることにあります。</span><span class="sxs-lookup"><span data-stu-id="1491d-116">The main difference between these classes is that the <xref:System.ComponentModel.Component> class is marshaled by reference, while <xref:System.ComponentModel.IComponent> is marshaled by value.</span></span> <span data-ttu-id="1491d-117">実装のためのガイドラインを次に示します。</span><span class="sxs-lookup"><span data-stu-id="1491d-117">The following list provides broad guidelines for implementers.</span></span>  
  
- <span data-ttu-id="1491d-118">コンポーネントを参照渡しでマーシャリングする必要がある場合は、<xref:System.ComponentModel.Component> から派生させます。</span><span class="sxs-lookup"><span data-stu-id="1491d-118">If your component needs to be marshaled by reference, derive from <xref:System.ComponentModel.Component>.</span></span>  
  
- <span data-ttu-id="1491d-119">コンポーネントを値渡しでマーシャリングする必要がある場合は、<xref:System.ComponentModel.MarshalByValueComponent> から派生させます。</span><span class="sxs-lookup"><span data-stu-id="1491d-119">If your component needs to be marshaled by value, derive from <xref:System.ComponentModel.MarshalByValueComponent>.</span></span>  
  
- <span data-ttu-id="1491d-120">単一継承が原因でいずれかの基本実装からコンポーネントを派生できない場合は、<xref:System.ComponentModel.IComponent> を実装します。</span><span class="sxs-lookup"><span data-stu-id="1491d-120">If your component cannot derive from one of the base implementations due to single inheritance, implement <xref:System.ComponentModel.IComponent>.</span></span>  
  
## <a name="component-classes"></a><span data-ttu-id="1491d-121">コンポーネントのクラス</span><span class="sxs-lookup"><span data-stu-id="1491d-121">Component Classes</span></span>  

 <span data-ttu-id="1491d-122"><xref:System.ComponentModel> 名前空間は、コンポーネントとコントロールの実行時およびデザイン時の動作を実装するために使用できるクラスを提供します。</span><span class="sxs-lookup"><span data-stu-id="1491d-122">The <xref:System.ComponentModel> namespace provides classes that are used to implement the run-time and design-time behavior of components and controls.</span></span> <span data-ttu-id="1491d-123">この名前空間には、属性と型コンバーターの実装、データ ソースへのバインド、コンポーネントのライセンス処理のための基底クラスと基底インターフェイスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="1491d-123">This namespace includes the base classes and interfaces for implementing attributes and type converters, binding to data sources, and licensing components.</span></span>  
  
 <span data-ttu-id="1491d-124">核となるコンポーネント クラスは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1491d-124">The core component classes are:</span></span>  
  
- <span data-ttu-id="1491d-125"><xref:System.ComponentModel.Component>.</span><span class="sxs-lookup"><span data-stu-id="1491d-125"><xref:System.ComponentModel.Component>.</span></span> <span data-ttu-id="1491d-126"><xref:System.ComponentModel.IComponent> インターフェイスの基本実装。</span><span class="sxs-lookup"><span data-stu-id="1491d-126">A base implementation for the <xref:System.ComponentModel.IComponent> interface.</span></span> <span data-ttu-id="1491d-127">このクラスにより、アプリケーション間でオブジェクトの共有が可能になります。</span><span class="sxs-lookup"><span data-stu-id="1491d-127">This class enables object sharing between applications.</span></span>  
  
- <span data-ttu-id="1491d-128"><xref:System.ComponentModel.MarshalByValueComponent>。</span><span class="sxs-lookup"><span data-stu-id="1491d-128"><xref:System.ComponentModel.MarshalByValueComponent>.</span></span> <span data-ttu-id="1491d-129"><xref:System.ComponentModel.IComponent> インターフェイスの基本実装。</span><span class="sxs-lookup"><span data-stu-id="1491d-129">A base implementation for the <xref:System.ComponentModel.IComponent> interface.</span></span>  
  
- <span data-ttu-id="1491d-130"><xref:System.ComponentModel.Container>.</span><span class="sxs-lookup"><span data-stu-id="1491d-130"><xref:System.ComponentModel.Container>.</span></span> <span data-ttu-id="1491d-131"><xref:System.ComponentModel.IContainer> インターフェイスの基本実装。</span><span class="sxs-lookup"><span data-stu-id="1491d-131">The base implementation for the <xref:System.ComponentModel.IContainer> interface.</span></span> <span data-ttu-id="1491d-132">このクラスは、0 個以上のコンポーネントをカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="1491d-132">This class encapsulates zero or more components.</span></span>  
  
 <span data-ttu-id="1491d-133">コンポーネントのライセンス処理に使用するクラスのいくつかを次に示します。</span><span class="sxs-lookup"><span data-stu-id="1491d-133">Some of the classes used for component licensing are:</span></span>  
  
- <span data-ttu-id="1491d-134"><xref:System.ComponentModel.License>.</span><span class="sxs-lookup"><span data-stu-id="1491d-134"><xref:System.ComponentModel.License>.</span></span> <span data-ttu-id="1491d-135">すべてのライセンスの抽象基底クラスです。</span><span class="sxs-lookup"><span data-stu-id="1491d-135">The abstract base class for all licenses.</span></span> <span data-ttu-id="1491d-136">ライセンスは、コンポーネントの特定のインスタンスに付与されます。</span><span class="sxs-lookup"><span data-stu-id="1491d-136">A license is granted to a specific instance of a component.</span></span>  
  
- <span data-ttu-id="1491d-137"><xref:System.ComponentModel.LicenseManager>。</span><span class="sxs-lookup"><span data-stu-id="1491d-137"><xref:System.ComponentModel.LicenseManager>.</span></span> <span data-ttu-id="1491d-138">コンポーネントにライセンスを追加し、<xref:System.ComponentModel.LicenseProvider> を管理するためのプロパティとメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="1491d-138">Provides properties and methods to add a license to a component and to manage a <xref:System.ComponentModel.LicenseProvider>.</span></span>  
  
- <span data-ttu-id="1491d-139"><xref:System.ComponentModel.LicenseProvider>。</span><span class="sxs-lookup"><span data-stu-id="1491d-139"><xref:System.ComponentModel.LicenseProvider>.</span></span> <span data-ttu-id="1491d-140">ライセンス プロバイダーを実装するための抽象基底クラスです。</span><span class="sxs-lookup"><span data-stu-id="1491d-140">The abstract base class for implementing a license provider.</span></span>  
  
- <span data-ttu-id="1491d-141"><xref:System.ComponentModel.LicenseProviderAttribute>.</span><span class="sxs-lookup"><span data-stu-id="1491d-141"><xref:System.ComponentModel.LicenseProviderAttribute>.</span></span> <span data-ttu-id="1491d-142">クラスで使用する <xref:System.ComponentModel.LicenseProvider> クラスを指定します。</span><span class="sxs-lookup"><span data-stu-id="1491d-142">Specifies the <xref:System.ComponentModel.LicenseProvider> class to use with a class.</span></span>  
  
 <span data-ttu-id="1491d-143">コンポーネントの説明や永続化に一般的に使用するクラスを次に示します。</span><span class="sxs-lookup"><span data-stu-id="1491d-143">Classes commonly used for describing and persisting components.</span></span>  
  
- <span data-ttu-id="1491d-144"><xref:System.ComponentModel.TypeDescriptor>。</span><span class="sxs-lookup"><span data-stu-id="1491d-144"><xref:System.ComponentModel.TypeDescriptor>.</span></span> <span data-ttu-id="1491d-145">属性、プロパティ、イベントなど、コンポーネントの特性に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="1491d-145">Provides information about the characteristics for a component, such as its attributes, properties, and events.</span></span>  
  
- <span data-ttu-id="1491d-146"><xref:System.ComponentModel.EventDescriptor>。</span><span class="sxs-lookup"><span data-stu-id="1491d-146"><xref:System.ComponentModel.EventDescriptor>.</span></span> <span data-ttu-id="1491d-147">イベントに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="1491d-147">Provides information about an event.</span></span>  
  
- <span data-ttu-id="1491d-148"><xref:System.ComponentModel.PropertyDescriptor>.</span><span class="sxs-lookup"><span data-stu-id="1491d-148"><xref:System.ComponentModel.PropertyDescriptor>.</span></span> <span data-ttu-id="1491d-149">プロパティに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="1491d-149">Provides information about a property.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1491d-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="1491d-150">Related Sections</span></span>  

 [<span data-ttu-id="1491d-151">コントロールとコンポーネントの作成時のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="1491d-151">Troubleshooting Control and Component Authoring</span></span>](/dotnet/desktop/winforms/controls/troubleshooting-control-and-component-authoring)  
 <span data-ttu-id="1491d-152">一般的な問題に対処する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1491d-152">Explains how to fix common problems.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1491d-153">関連項目</span><span class="sxs-lookup"><span data-stu-id="1491d-153">See also</span></span>

- [<span data-ttu-id="1491d-154">方法: Windows フォームでデザイン時サポートにアクセスする</span><span class="sxs-lookup"><span data-stu-id="1491d-154">How to: Access Design-Time Support in Windows Forms</span></span>](/dotnet/desktop/winforms/controls/developing-windows-forms-controls-at-design-time)
