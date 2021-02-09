---
description: '詳細情報: My.Forms オブジェクト'
title: My.Forms オブジェクト
ms.date: 07/20/2015
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords:
- My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
ms.openlocfilehash: 18ef8ee475163ff7eb177dfee590d959a242a88e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774409"
---
# <a name="myforms-object"></a><span data-ttu-id="3ad5f-103">My.Forms オブジェクト</span><span class="sxs-lookup"><span data-stu-id="3ad5f-103">My.Forms Object</span></span>

<span data-ttu-id="3ad5f-104">現在のプロジェクトで宣言されている各 Windows フォームのインスタンスにアクセスするためのプロパティを提供します。</span><span class="sxs-lookup"><span data-stu-id="3ad5f-104">Provides properties for accessing an instance of each Windows form declared in the current project.</span></span>

## <a name="remarks"></a><span data-ttu-id="3ad5f-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="3ad5f-105">Remarks</span></span>

<span data-ttu-id="3ad5f-106">`My.Forms` オブジェクトは、現在のプロジェクトで各フォームのインスタンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="3ad5f-106">The `My.Forms` object provides an instance of each form in the current project.</span></span> <span data-ttu-id="3ad5f-107">プロパティの名前は、プロパティがアクセスするフォームの名前と同じになります。</span><span class="sxs-lookup"><span data-stu-id="3ad5f-107">The name of the property is the same as the name of the form that the property accesses.</span></span>

<span data-ttu-id="3ad5f-108">`My.Forms` オブジェクトによって提供されるフォームにアクセスするには、修飾子を付けずにフォームの名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="3ad5f-108">You can access the forms provided by the `My.Forms` object by using the name of the form, without qualification.</span></span> <span data-ttu-id="3ad5f-109">プロパティ名はフォームの型名と同じであるため、これによって既定のインスタンスがあるかのようにフォームにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="3ad5f-109">Because the property name is the same as the form's type name, this allows you to access a form as if it had a default instance.</span></span> <span data-ttu-id="3ad5f-110">たとえば、`My.Forms.Form1.Show` は、`Form1.Show` と同じです。</span><span class="sxs-lookup"><span data-stu-id="3ad5f-110">For example, `My.Forms.Form1.Show` is equivalent to `Form1.Show`.</span></span>

<span data-ttu-id="3ad5f-111">`My.Forms` オブジェクトでは、現在のプロジェクトに関連付けられているフォームのみが公開されます。</span><span class="sxs-lookup"><span data-stu-id="3ad5f-111">The `My.Forms` object exposes only the forms associated with the current project.</span></span> <span data-ttu-id="3ad5f-112">参照されている DLL で宣言されているフォームへのアクセスは提供されません。</span><span class="sxs-lookup"><span data-stu-id="3ad5f-112">It does not provide access to forms declared in referenced DLLs.</span></span> <span data-ttu-id="3ad5f-113">DLL によって提供されるフォームにアクセスするには、 *DllName*.*FormName* として記述されたフォームの修飾名を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3ad5f-113">To access a form that a DLL provides, you must use the qualified name of the form, written as *DllName*.*FormName*.</span></span>

<span data-ttu-id="3ad5f-114"><xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> プロパティを使用して、すべてのアプリケーションの開いているフォームのコレクションを取得できます。</span><span class="sxs-lookup"><span data-stu-id="3ad5f-114">You can use the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> property to get a collection of all the application's open forms.</span></span>

<span data-ttu-id="3ad5f-115">オブジェクトとそのプロパティは、Windows アプリケーションでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="3ad5f-115">The object and its properties are available only for Windows applications.</span></span>

## <a name="properties"></a><span data-ttu-id="3ad5f-116">プロパティ</span><span class="sxs-lookup"><span data-stu-id="3ad5f-116">Properties</span></span>

<span data-ttu-id="3ad5f-117">`My.Forms` オブジェクトの各プロパティにより、現在のプロジェクトのフォームのインスタンスにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="3ad5f-117">Each property of the `My.Forms` object provides access to an instance of a form in the current project.</span></span> <span data-ttu-id="3ad5f-118">プロパティの名前は、プロパティがアクセスするフォームの名前と同じになり、プロパティの型はフォームの型と同じになります。</span><span class="sxs-lookup"><span data-stu-id="3ad5f-118">The name of the property is the same as the name of the form that the property accesses, and the property type is the same as the form's type.</span></span>

> [!NOTE]
> <span data-ttu-id="3ad5f-119">名前の競合がある場合、フォームにアクセスするためのプロパティ名は、*RootNamespace* _ *Namespace*\_*FormName* になります。</span><span class="sxs-lookup"><span data-stu-id="3ad5f-119">If there is a name collision, the property name to access a form is *RootNamespace* _ *Namespace*\_*FormName*.</span></span> <span data-ttu-id="3ad5f-120">たとえば、`Form1.` という名前の 2 つのフォームを考えてみます。これらのフォームのいずれかがルート名前空間 `WindowsApplication1` と名前空間 `Namespace1` にある場合、`My.Forms.WindowsApplication1_Namespace1_Form1` によってそのフォームにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="3ad5f-120">For example, consider two forms named `Form1.`If one of these forms is in the root namespace `WindowsApplication1` and in the namespace `Namespace1`, you would access that form through `My.Forms.WindowsApplication1_Namespace1_Form1`.</span></span>

<span data-ttu-id="3ad5f-121">`My.Forms` オブジェクトでは、起動時に作成されたアプリケーションのメイン フォームのインスタンスにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="3ad5f-121">The `My.Forms` object provides access to the instance of the application's main form that was created on startup.</span></span> <span data-ttu-id="3ad5f-122">その他のすべてのフォームの場合、`My.Forms` オブジェクトによって、アクセス時にフォームの新しいインスタンスが作成され、格納されます。</span><span class="sxs-lookup"><span data-stu-id="3ad5f-122">For all other forms, the `My.Forms` object creates a new instance of the form when it is accessed and stores it.</span></span> <span data-ttu-id="3ad5f-123">その後、そのプロパティにアクセスしようとすると、フォームのインスタンスが返されます。</span><span class="sxs-lookup"><span data-stu-id="3ad5f-123">Subsequent attempts to access that property return that instance of the form.</span></span>

<span data-ttu-id="3ad5f-124">フォームを破棄するには、そのフォームのプロパティに `Nothing` を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="3ad5f-124">You can dispose of a form by assigning `Nothing` to the property for that form.</span></span> <span data-ttu-id="3ad5f-125">プロパティ セッターによって、フォームの <xref:System.Windows.Forms.Form.Close%2A> メソッドが呼び出され、格納されている値に `Nothing` が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="3ad5f-125">The property setter calls the <xref:System.Windows.Forms.Form.Close%2A> method of the form, and then assigns `Nothing` to the stored value.</span></span> <span data-ttu-id="3ad5f-126">プロパティに `Nothing` 以外の値を割り当てた場合、セッターが <xref:System.ArgumentException> 例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="3ad5f-126">If you assign any value other than `Nothing` to the property, the setter throws an <xref:System.ArgumentException> exception.</span></span>

<span data-ttu-id="3ad5f-127">`My.Forms` オブジェクトのプロパティにフォームのインスタンスが格納されているかどうかをテストするには、`Is` または `IsNot` 演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="3ad5f-127">You can test whether a property of the `My.Forms` object stores an instance of the form by using the `Is` or `IsNot` operator.</span></span> <span data-ttu-id="3ad5f-128">これらの演算子を使用すると、プロパティの値が `Nothing` かどうかをチェックできます。</span><span class="sxs-lookup"><span data-stu-id="3ad5f-128">You can use those operators to check if the value of the property is `Nothing`.</span></span>

> [!NOTE]
> <span data-ttu-id="3ad5f-129">通常、`Is` または `IsNot` 演算子では、比較を実行するためにプロパティの値を読み取る必要があります。</span><span class="sxs-lookup"><span data-stu-id="3ad5f-129">Typically, the `Is` or `IsNot` operator has to read the value of the property to perform the comparison.</span></span> <span data-ttu-id="3ad5f-130">ただし、プロパティに現在 `Nothing` が格納されている場合は、プロパティによってフォームの新しいインスタンスが作成され、そのインスタンスが返されます。</span><span class="sxs-lookup"><span data-stu-id="3ad5f-130">However, if the property currently stores `Nothing`, the property creates a new instance of the form and then returns that instance.</span></span> <span data-ttu-id="3ad5f-131">ただし、Visual Basic コンパイラでは、`My.Forms` オブジェクトのプロパティが異なって処理されるため、`Is` または `IsNot` 演算子によって、値を変更せずにプロパティの状態をチェックできます。</span><span class="sxs-lookup"><span data-stu-id="3ad5f-131">However, the Visual Basic compiler treats the properties of the `My.Forms` object differently and allows the `Is` or `IsNot` operator to check the status of the property without altering its value.</span></span>

## <a name="example"></a><span data-ttu-id="3ad5f-132">例</span><span class="sxs-lookup"><span data-stu-id="3ad5f-132">Example</span></span>

<span data-ttu-id="3ad5f-133">この例では、既定の `SidebarMenu` フォームのタイトルを変更しています。</span><span class="sxs-lookup"><span data-stu-id="3ad5f-133">This example changes the title of the default `SidebarMenu` form.</span></span>

[!code-vb[VbVbalrMyForms#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyForms/VB/Class1.vb#2)]

<span data-ttu-id="3ad5f-134">この例を機能させるには、プロジェクトに `SidebarMenu` という名前のフォームが必要です。</span><span class="sxs-lookup"><span data-stu-id="3ad5f-134">For this example to work, your project must have a form named `SidebarMenu`.</span></span>

<span data-ttu-id="3ad5f-135">このコードは、Windows アプリケーション プロジェクトでのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="3ad5f-135">This code will work only in a Windows Application project.</span></span>

## <a name="requirements"></a><span data-ttu-id="3ad5f-136">必要条件</span><span class="sxs-lookup"><span data-stu-id="3ad5f-136">Requirements</span></span>

### <a name="availability-by-project-type"></a><span data-ttu-id="3ad5f-137">プロジェクトの種類別の可用性</span><span class="sxs-lookup"><span data-stu-id="3ad5f-137">Availability by Project Type</span></span>

|<span data-ttu-id="3ad5f-138">プロジェクトの種類</span><span class="sxs-lookup"><span data-stu-id="3ad5f-138">Project type</span></span>|<span data-ttu-id="3ad5f-139">使用可能</span><span class="sxs-lookup"><span data-stu-id="3ad5f-139">Available</span></span>|
|---|---|
|<span data-ttu-id="3ad5f-140">Windows アプリケーション</span><span class="sxs-lookup"><span data-stu-id="3ad5f-140">Windows Application</span></span>|<span data-ttu-id="3ad5f-141">**はい**</span><span class="sxs-lookup"><span data-stu-id="3ad5f-141">**Yes**</span></span>|
|<span data-ttu-id="3ad5f-142">クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="3ad5f-142">Class Library</span></span>|<span data-ttu-id="3ad5f-143">いいえ</span><span class="sxs-lookup"><span data-stu-id="3ad5f-143">No</span></span>|
|<span data-ttu-id="3ad5f-144">コンソール アプリケーション</span><span class="sxs-lookup"><span data-stu-id="3ad5f-144">Console Application</span></span>|<span data-ttu-id="3ad5f-145">いいえ</span><span class="sxs-lookup"><span data-stu-id="3ad5f-145">No</span></span>|
|<span data-ttu-id="3ad5f-146">Windows コントロール ライブラリ</span><span class="sxs-lookup"><span data-stu-id="3ad5f-146">Windows Control Library</span></span>|<span data-ttu-id="3ad5f-147">いいえ</span><span class="sxs-lookup"><span data-stu-id="3ad5f-147">No</span></span>|
|<span data-ttu-id="3ad5f-148">Web コントロール ライブラリ</span><span class="sxs-lookup"><span data-stu-id="3ad5f-148">Web Control Library</span></span>|<span data-ttu-id="3ad5f-149">いいえ</span><span class="sxs-lookup"><span data-stu-id="3ad5f-149">No</span></span>|
|<span data-ttu-id="3ad5f-150">Windows サービス</span><span class="sxs-lookup"><span data-stu-id="3ad5f-150">Windows Service</span></span>|<span data-ttu-id="3ad5f-151">いいえ</span><span class="sxs-lookup"><span data-stu-id="3ad5f-151">No</span></span>|
|<span data-ttu-id="3ad5f-152">Web サイト</span><span class="sxs-lookup"><span data-stu-id="3ad5f-152">Web Site</span></span>|<span data-ttu-id="3ad5f-153">いいえ</span><span class="sxs-lookup"><span data-stu-id="3ad5f-153">No</span></span>|

## <a name="see-also"></a><span data-ttu-id="3ad5f-154">関連項目</span><span class="sxs-lookup"><span data-stu-id="3ad5f-154">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>
- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Form.Close%2A>
- [<span data-ttu-id="3ad5f-155">オブジェクト</span><span class="sxs-lookup"><span data-stu-id="3ad5f-155">Objects</span></span>](index.md)
- [<span data-ttu-id="3ad5f-156">Is 演算子</span><span class="sxs-lookup"><span data-stu-id="3ad5f-156">Is Operator</span></span>](../operators/is-operator.md)
- [<span data-ttu-id="3ad5f-157">IsNot 演算子</span><span class="sxs-lookup"><span data-stu-id="3ad5f-157">IsNot Operator</span></span>](../operators/isnot-operator.md)
- [<span data-ttu-id="3ad5f-158">アプリケーション フォームへのアクセス</span><span class="sxs-lookup"><span data-stu-id="3ad5f-158">Accessing Application Forms</span></span>](../../developing-apps/programming/accessing-application-forms.md)
