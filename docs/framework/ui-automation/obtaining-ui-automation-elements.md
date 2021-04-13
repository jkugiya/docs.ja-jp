---
title: UI オートメーション要素の取得
description: ユーザー インターフェイス (UI) 要素の UI オートメーション要素 (AutomationElement) オブジェクトを取得するためのさまざまな方法を確認します。
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, obtaining elements
- elements, UI Automation, obtaining
ms.assetid: c2caaf45-e59c-42a1-bc9b-77a6de520171
ms.openlocfilehash: 66a8d9e944a8f8a777ec744a33f2cdb2d33e200c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96237353"
---
# <a name="obtaining-ui-automation-elements"></a><span data-ttu-id="e2cf5-103">UI オートメーション要素の取得</span><span class="sxs-lookup"><span data-stu-id="e2cf5-103">Obtaining UI Automation Elements</span></span>

> [!NOTE]
> <span data-ttu-id="e2cf5-104">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="e2cf5-105">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="e2cf5-106">このトピックでは、 <xref:System.Windows.Automation.AutomationElement> 要素の [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] オブジェクトを取得するさまざまな方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-106">This topic describes the various ways of obtaining <xref:System.Windows.Automation.AutomationElement> objects for [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elements.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="e2cf5-107">クライアント アプリケーションが独自のユーザー インターフェイスで要素の検索を試行する可能性がある場合は、すべての [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] の呼び出しを個別のスレッドで実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-107">If your client application might attempt to find elements in its own user interface, you must make all [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] calls on a separate thread.</span></span> <span data-ttu-id="e2cf5-108">詳細については、「 [UI オートメーション スレッド処理の問題点](ui-automation-threading-issues.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-108">For more information, see [UI Automation Threading Issues](ui-automation-threading-issues.md).</span></span>  
  
<a name="The_Root_Element"></a>

## <a name="root-element"></a><span data-ttu-id="e2cf5-109">Root 要素</span><span class="sxs-lookup"><span data-stu-id="e2cf5-109">Root Element</span></span>  

 <span data-ttu-id="e2cf5-110"><xref:System.Windows.Automation.AutomationElement> オブジェクトの検索には必ず、開始場所が必要です。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-110">All searches for <xref:System.Windows.Automation.AutomationElement> objects must have a starting-place.</span></span> <span data-ttu-id="e2cf5-111">この開始場所には、デスクトップ、アプリケーション ウィンドウ、コントロールなど任意の要素を指定できます。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-111">This can be any element, including the desktop, an application window, or a control.</span></span>  
  
 <span data-ttu-id="e2cf5-112">デスクトップのルート要素 (すべての要素が派生する) が静的 <xref:System.Windows.Automation.AutomationElement.RootElement%2A?displayProperty=nameWithType> プロパティから取得されます。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-112">The root element for the desktop, from which all elements are descended, is obtained from the static <xref:System.Windows.Automation.AutomationElement.RootElement%2A?displayProperty=nameWithType> property.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="e2cf5-113">通常、 <xref:System.Windows.Automation.AutomationElement.RootElement%2A>の直接の子のみの取得を試行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-113">In general, you should try to obtain only direct children of the <xref:System.Windows.Automation.AutomationElement.RootElement%2A>.</span></span> <span data-ttu-id="e2cf5-114">子孫の検索は、数百または数千もの要素を反復処理する場合があり、スタック オーバーフローを引き起こす可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-114">A search for descendants may iterate through hundreds or even thousands of elements, possibly resulting in a stack overflow.</span></span> <span data-ttu-id="e2cf5-115">下位レベルの特定の要素を取得しようとする場合、アプリケーション ウィンドウから、または下位レベルのコンテナーから検索を開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-115">If you are attempting to obtain a specific element at a lower level, you should start your search from the application window or from a container at a lower level.</span></span>  
  
<a name="Using_Conditions"></a>

## <a name="conditions"></a><span data-ttu-id="e2cf5-116">条件</span><span class="sxs-lookup"><span data-stu-id="e2cf5-116">Conditions</span></span>  

 <span data-ttu-id="e2cf5-117">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 要素を取得するために使用できるほとんどの手法では、 <xref:System.Windows.Automation.Condition>を指定する必要があります。これは、取得する要素を定義する一連の条件になります。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-117">For most techniques you can use to retrieve [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elements, you must specify a <xref:System.Windows.Automation.Condition>, which is a set of criteria defining what elements you want to retrieve.</span></span>  
  
 <span data-ttu-id="e2cf5-118">最も簡単な条件は <xref:System.Windows.Automation.Condition.TrueCondition>で、検索範囲内のすべての要素を指定する定義済みオブジェクトが返されます。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-118">The simplest condition is <xref:System.Windows.Automation.Condition.TrueCondition>, a predefined object specifying that all elements within the search scope are to be returned.</span></span> <span data-ttu-id="e2cf5-119">要素が検出されなくなるため、<xref:System.Windows.Automation.Condition.FalseCondition>( <xref:System.Windows.Automation.Condition.TrueCondition>の逆) はあまり有用ではありません。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-119"><xref:System.Windows.Automation.Condition.FalseCondition>, the converse of <xref:System.Windows.Automation.Condition.TrueCondition>, is less useful, as it would prevent any elements from being found.</span></span>  
  
 <span data-ttu-id="e2cf5-120">その他の 3 つの定義済み条件 ( <xref:System.Windows.Automation.Automation.ContentViewCondition>、 <xref:System.Windows.Automation.Automation.ControlViewCondition>、および <xref:System.Windows.Automation.Automation.RawViewCondition>) は、単独で使用することも、その他の条件と組み合わせて使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-120">Three other predefined conditions can be used alone or in combination with other conditions: <xref:System.Windows.Automation.Automation.ContentViewCondition>, <xref:System.Windows.Automation.Automation.ControlViewCondition>, and <xref:System.Windows.Automation.Automation.RawViewCondition>.</span></span> <span data-ttu-id="e2cf5-121"><xref:System.Windows.Automation.Automation.RawViewCondition>を単独で使用した場合、 <xref:System.Windows.Automation.Condition.TrueCondition>または <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> プロパティで要素をフィルター処理しないため <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> と同等になります。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-121"><xref:System.Windows.Automation.Automation.RawViewCondition>, used by itself, is equivalent to <xref:System.Windows.Automation.Condition.TrueCondition>, because it does not filter elements by their <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> or <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> properties.</span></span>  
  
 <span data-ttu-id="e2cf5-122">その他の条件は 1 つ以上の <xref:System.Windows.Automation.PropertyCondition> オブジェクトで構築され、それぞれはプロパティ値を指定します。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-122">Other conditions are built up from one or more <xref:System.Windows.Automation.PropertyCondition> objects, each of which specifies a property value.</span></span> <span data-ttu-id="e2cf5-123">たとえば、 <xref:System.Windows.Automation.PropertyCondition> は要素が有効であることを指定したり、特定のコントロール パターンをサポートすることを指定したりします。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-123">For example, a <xref:System.Windows.Automation.PropertyCondition> might specify that the element is enabled, or that it supports a certain control pattern.</span></span>  
  
 <span data-ttu-id="e2cf5-124"><xref:System.Windows.Automation.AndCondition>、 <xref:System.Windows.Automation.OrCondition>、および <xref:System.Windows.Automation.NotCondition>の型のオブジェクトを構築することによって、ブール ロジックを使用して条件を組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-124">Conditions can be combined using Boolean logic by constructing objects of types <xref:System.Windows.Automation.AndCondition>, <xref:System.Windows.Automation.OrCondition>, and <xref:System.Windows.Automation.NotCondition>.</span></span>  
  
<a name="Search_Scope"></a>

## <a name="search-scope"></a><span data-ttu-id="e2cf5-125">検索範囲</span><span class="sxs-lookup"><span data-stu-id="e2cf5-125">Search Scope</span></span>  

 <span data-ttu-id="e2cf5-126"><xref:System.Windows.Automation.AutomationElement.FindFirst%2A> または <xref:System.Windows.Automation.AutomationElement.FindAll%2A> 使用した検索には、範囲と開始場所が必要です。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-126">Searches done by using <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> or <xref:System.Windows.Automation.AutomationElement.FindAll%2A> must have a scope as well as a starting-place.</span></span>  
  
 <span data-ttu-id="e2cf5-127">範囲は、検索対象の開始場所の周囲の領域を定義します。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-127">The scope defines the space around the starting-place that is to be searched.</span></span> <span data-ttu-id="e2cf5-128">これには、要素自体、その兄弟、その親、その先祖、その直接の子、およびその子孫を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-128">This might include the element itself, its siblings, its parent, its ancestors, its immediate children, and its descendants.</span></span>  
  
 <span data-ttu-id="e2cf5-129"><xref:System.Windows.Automation.TreeScope> 列挙の値のビットごとの組み合わせによって、検索の範囲が定義されます。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-129">The scope of a search is defined by a bitwise combination of values from the <xref:System.Windows.Automation.TreeScope> enumeration.</span></span>  
  
<a name="Finding_a_Known_Element"></a>

## <a name="finding-a-known-element"></a><span data-ttu-id="e2cf5-130">既知の要素の検索</span><span class="sxs-lookup"><span data-stu-id="e2cf5-130">Finding a Known Element</span></span>  

 <span data-ttu-id="e2cf5-131">既知の要素 (その <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>、 <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AutomationId%2A>、または他のプロパティまたはプロパティの組み合わせによって識別される) を検索する方法として、 <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> メソッドを使用する方法が最も簡単です。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-131">To find a known element, identified by its <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AutomationId%2A>, or some other property or combination of properties, it is easiest to use the <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> method.</span></span> <span data-ttu-id="e2cf5-132">検索する要素がアプリケーション ウィンドウである場合は、検索の開始点を <xref:System.Windows.Automation.AutomationElement.RootElement%2A>にすることができます。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-132">If the element sought is an application window, the starting-point of the search can be the <xref:System.Windows.Automation.AutomationElement.RootElement%2A>.</span></span>  
  
 <span data-ttu-id="e2cf5-133">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 要素を検索するこの方法は、自動化されたシナリオ テストの最も有用な方法になります。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-133">This way of finding [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elements is most useful in automated testing scenarios.</span></span>  
  
<a name="Finding_Elements_in_a_Subtree"></a>

## <a name="finding-elements-in-a-subtree"></a><span data-ttu-id="e2cf5-134">サブツリー内の要素の検索</span><span class="sxs-lookup"><span data-stu-id="e2cf5-134">Finding Elements in a Subtree</span></span>  

 <span data-ttu-id="e2cf5-135">既知の要素に関連する特定の条件を満たすすべての要素を検索するには、 <xref:System.Windows.Automation.AutomationElement.FindAll%2A>を使用します。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-135">To find all elements meeting specific criteria that are related to a known element, you can use <xref:System.Windows.Automation.AutomationElement.FindAll%2A>.</span></span> <span data-ttu-id="e2cf5-136">たとえば、このメソッドを使用して、リストまたはメニューからリスト項目またはメニュー項目を取得したり、ダイアログ ボックスのすべてのコントロールを識別したりできます。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-136">For example, you could use this method to retrieve list items or menu items from a list or menu, or to identify all controls in a dialog box.</span></span>  
  
<a name="Walking_a_Subtree"></a>

## <a name="walking-a-subtree"></a><span data-ttu-id="e2cf5-137">サブツリーのウォーク</span><span class="sxs-lookup"><span data-stu-id="e2cf5-137">Walking a Subtree</span></span>  

 <span data-ttu-id="e2cf5-138">クライアントで使用されるアプリケーションについて予備知識がない場合、 <xref:System.Windows.Automation.TreeWalker> クラスを使用して、対象となるすべての要素のサブツリーを構築することができます。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-138">If you have no prior knowledge of the applications that your client may be used with, you can construct a subtree of all elements of interest by using the <xref:System.Windows.Automation.TreeWalker> class.</span></span> <span data-ttu-id="e2cf5-139">アプリケーションは、フォーカス変更イベントへの応答でこれを実行することができます。つまり、アプリケーションやコントロールが入力フォーカスを受け取るときに、UI オートメーション クライアントはフォーカスされている要素の子およびすべての子孫を調べます。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-139">Your application might do this in response to a focus-changed event; that is, when an application or control receives input focus, the UI Automation client examines children and perhaps all descendants of the focused element.</span></span>  
  
 <span data-ttu-id="e2cf5-140"><xref:System.Windows.Automation.TreeWalker> で使用できる別の方法は、要素の先祖を特定する方法です。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-140">Another way in which <xref:System.Windows.Automation.TreeWalker> can be used is to identify the ancestors of an element.</span></span> <span data-ttu-id="e2cf5-141">たとえば、ツリーをウォークすることによって、コントロールの親ウィンドウを特定できます。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-141">For example, by walking up the tree you can identify the parent window of a control.</span></span>  
  
 <span data-ttu-id="e2cf5-142">クラスのオブジェクトを作成する ( <xref:System.Windows.Automation.TreeWalker> を渡すことによって対象の要素を定義する) か、 <xref:System.Windows.Automation.Condition>のフィールドとして定義されている次の定義済みオブジェクトのいずれかを使用することによって、 <xref:System.Windows.Automation.TreeWalker>を使用できます。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-142">You can use <xref:System.Windows.Automation.TreeWalker> either by creating an object of the class (defining the elements of interest by passing a <xref:System.Windows.Automation.Condition>), or by using one of the following predefined objects that are defined as fields of <xref:System.Windows.Automation.TreeWalker>.</span></span>  
  
|||  
|-|-|  
|<xref:System.Windows.Automation.TreeWalker.ContentViewWalker>|<span data-ttu-id="e2cf5-143"><xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> プロパティが `true`である要素のみを検索します。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-143">Finds only elements whose <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> property is `true`.</span></span>|  
|<xref:System.Windows.Automation.TreeWalker.ControlViewWalker>|<span data-ttu-id="e2cf5-144"><xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> プロパティが `true`である要素のみを検索します。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-144">Finds only elements whose <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> property is `true`.</span></span>|  
|<xref:System.Windows.Automation.TreeWalker.RawViewWalker>|<span data-ttu-id="e2cf5-145">すべての要素を検索します。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-145">Finds all elements.</span></span>|  
  
 <span data-ttu-id="e2cf5-146"><xref:System.Windows.Automation.TreeWalker>を取得した後、それを使用することは簡単です。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-146">After you have obtained a <xref:System.Windows.Automation.TreeWalker>, using it is straightforward.</span></span> <span data-ttu-id="e2cf5-147">`Get` メソッドを呼び出し、サブツリーの要素間を移動するだけです。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-147">Simply call the `Get` methods to navigate among elements of the subtree.</span></span>  
  
 <span data-ttu-id="e2cf5-148"><xref:System.Windows.Automation.TreeWalker.Normalize%2A> メソッドを使用すると、ビューの一部ではない要素からサブツリー内の他の要素に移動できます。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-148">The <xref:System.Windows.Automation.TreeWalker.Normalize%2A> method can be used for navigating to an element in the subtree from another element that is not part of the view.</span></span> <span data-ttu-id="e2cf5-149">たとえば、 <xref:System.Windows.Automation.TreeWalker.ContentViewWalker>を使用してサブツリーのビューを作成したとします。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-149">For example, suppose you have created a view of a subtree by using <xref:System.Windows.Automation.TreeWalker.ContentViewWalker>.</span></span> <span data-ttu-id="e2cf5-150">スクロール バーが入力フォーカスを受信したことを示す通知を、アプリケーションが受け取ります。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-150">Your application then receives notification that a scroll bar has received the input focus.</span></span> <span data-ttu-id="e2cf5-151">スクロール バーはコンテンツ要素ではないため、サブツリーのビューには存在しません。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-151">Because a scroll bar is not a content element, it is not present in your view of the subtree.</span></span> <span data-ttu-id="e2cf5-152">しかし、スクロール バーを表す <xref:System.Windows.Automation.AutomationElement> を <xref:System.Windows.Automation.TreeWalker.Normalize%2A> に渡し、コンテンツ ビュー内にある最も近い先祖を取得することができます。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-152">However, you can pass the <xref:System.Windows.Automation.AutomationElement> representing the scroll bar to <xref:System.Windows.Automation.TreeWalker.Normalize%2A> and retrieve the nearest ancestor that is in the content view.</span></span>  
  
<a name="Other_Ways_to_Retrieve_an_Element"></a>

## <a name="other-ways-to-retrieve-an-element"></a><span data-ttu-id="e2cf5-153">要素を取得する別の方法</span><span class="sxs-lookup"><span data-stu-id="e2cf5-153">Other Ways to Retrieve an Element</span></span>  

 <span data-ttu-id="e2cf5-154">検索とナビゲーションに加えて、次の方法で <xref:System.Windows.Automation.AutomationElement> を取得できます。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-154">In addition to searches and navigation, you can retrieve an <xref:System.Windows.Automation.AutomationElement> in the following ways.</span></span>  
  
### <a name="from-an-event"></a><span data-ttu-id="e2cf5-155">イベントから</span><span class="sxs-lookup"><span data-stu-id="e2cf5-155">From an Event</span></span>  

 <span data-ttu-id="e2cf5-156">アプリケーションが [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] イベントを受信するときに、イベント ハンドラーに渡されるソース オブジェクトは <xref:System.Windows.Automation.AutomationElement>です。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-156">When your application receives a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] event, the source object passed to your event handler is an <xref:System.Windows.Automation.AutomationElement>.</span></span> <span data-ttu-id="e2cf5-157">たとえば、フォーカス変更イベントをサブスクライブしている場合、 <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> に渡されるソースはフォーカスを受け取った要素になります。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-157">For example, if you have subscribed to focus-changed events, the source passed to your <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> is the element that received the focus.</span></span>  
  
 <span data-ttu-id="e2cf5-158">詳細については、「 [UI オートメーション イベントのサブスクライブ](subscribe-to-ui-automation-events.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-158">For more information, see [Subscribe to UI Automation Events](subscribe-to-ui-automation-events.md).</span></span>  
  
### <a name="from-a-point"></a><span data-ttu-id="e2cf5-159">ポイントから</span><span class="sxs-lookup"><span data-stu-id="e2cf5-159">From a Point</span></span>  

 <span data-ttu-id="e2cf5-160">画面座標 (たとえば、カーソル位置) がある場合、静的 <xref:System.Windows.Automation.AutomationElement> メソッドを使用して <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> を取得できます。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-160">If you have screen coordinates (for example, a cursor position), you can retrieve an <xref:System.Windows.Automation.AutomationElement> by using the static <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> method.</span></span>  
  
### <a name="from-a-window-handle"></a><span data-ttu-id="e2cf5-161">ウィンドウ ハンドルから</span><span class="sxs-lookup"><span data-stu-id="e2cf5-161">From a Window Handle</span></span>  

 <span data-ttu-id="e2cf5-162">HWND から <xref:System.Windows.Automation.AutomationElement> を取得するには、静的 <xref:System.Windows.Automation.AutomationElement.FromHandle%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-162">To retrieve an <xref:System.Windows.Automation.AutomationElement> from an HWND, use the static <xref:System.Windows.Automation.AutomationElement.FromHandle%2A> method.</span></span>  
  
### <a name="from-the-focused-control"></a><span data-ttu-id="e2cf5-163">フォーカスされたコントロールから</span><span class="sxs-lookup"><span data-stu-id="e2cf5-163">From the Focused Control</span></span>  

 <span data-ttu-id="e2cf5-164">静的 <xref:System.Windows.Automation.AutomationElement> プロパティから、フォーカスされたコントロールを表す <xref:System.Windows.Automation.AutomationElement.FocusedElement%2A> を取得できます。</span><span class="sxs-lookup"><span data-stu-id="e2cf5-164">You can retrieve an <xref:System.Windows.Automation.AutomationElement> that represents the focused control from the static <xref:System.Windows.Automation.AutomationElement.FocusedElement%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2cf5-165">関連項目</span><span class="sxs-lookup"><span data-stu-id="e2cf5-165">See also</span></span>

- [<span data-ttu-id="e2cf5-166">プロパティ条件に基づく UI オートメーション要素の検索</span><span class="sxs-lookup"><span data-stu-id="e2cf5-166">Find a UI Automation Element Based on a Property Condition</span></span>](find-a-ui-automation-element-based-on-a-property-condition.md)
- [<span data-ttu-id="e2cf5-167">TreeWalker を使用した UI オートメーション要素間の移動</span><span class="sxs-lookup"><span data-stu-id="e2cf5-167">Navigate Among UI Automation Elements with TreeWalker</span></span>](navigate-among-ui-automation-elements-with-treewalker.md)
- [<span data-ttu-id="e2cf5-168">UI オートメーション ツリーの概要</span><span class="sxs-lookup"><span data-stu-id="e2cf5-168">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
