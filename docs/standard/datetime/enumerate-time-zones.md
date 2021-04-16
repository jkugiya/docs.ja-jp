---
description: '詳細情報: コンピューター上に存在するタイム ゾーンを列挙する'
title: '方法: コンピューター上に存在するタイム ゾーンを列挙する'
ms.date: 04/10/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET], enumerating
- enumerating time zones [.NET]
ms.assetid: bb7a42ab-6bd9-4c5c-b734-5546d51f8669
ms.openlocfilehash: 98227d61ed81828f9c0614f622fed9a9667c6f4e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702679"
---
# <a name="how-to-enumerate-time-zones-present-on-a-computer"></a><span data-ttu-id="e22f8-103">方法: コンピューター上に存在するタイム ゾーンを列挙する</span><span class="sxs-lookup"><span data-stu-id="e22f8-103">How to: Enumerate time zones present on a computer</span></span>

<span data-ttu-id="e22f8-104">指定されたタイム ゾーンを正しく処理するには、そのタイム ゾーンに関する情報がシステムで使用できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="e22f8-104">Successfully working with a designated time zone requires that information about that time zone be available to the system.</span></span> <span data-ttu-id="e22f8-105">Windows XP および Windows Vista オペレーティング システムでは、この情報はレジストリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="e22f8-105">The Windows XP and Windows Vista operating systems store this information in the registry.</span></span> <span data-ttu-id="e22f8-106">しかし、世界中に存在するタイム ゾーンの合計数は大きいものの、レジストリにはそれらの一部に関する情報しか含まれません。</span><span class="sxs-lookup"><span data-stu-id="e22f8-106">However, although the total number of time zones that exist throughout the world is large, the registry contains information about only a subset of them.</span></span> <span data-ttu-id="e22f8-107">さらに、レジストリ自体は、内容が意図的に、および誤って変更される可能性がある動的な構造です。</span><span class="sxs-lookup"><span data-stu-id="e22f8-107">In addition, the registry itself is a dynamic structure whose contents are subject to both deliberate and accidental change.</span></span> <span data-ttu-id="e22f8-108">その結果、アプリケーションは、特定のタイム ゾーンがシステムで定義され、使用できると常に想定することができません。</span><span class="sxs-lookup"><span data-stu-id="e22f8-108">As a result, an application cannot always assume that a particular time zone is defined and available on a system.</span></span> <span data-ttu-id="e22f8-109">タイム ゾーン情報のアプリケーションを使用する多くのアプリケーションの最初の手順は、必要なタイム ゾーンがローカル システムで使用できるかどうかを判断する、またはタイム ゾーンの一覧をユーザーに提供して選択させることです。</span><span class="sxs-lookup"><span data-stu-id="e22f8-109">The first step for many applications that use time zone information applications is to determine whether required time zones are available on the local system, or to give the user a list of time zones from which to select.</span></span> <span data-ttu-id="e22f8-110">これには、アプリケーションがローカル システムで定義されているタイム ゾーンを列挙する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e22f8-110">This requires that an application enumerate the time zones defined on a local system.</span></span>

> [!NOTE]
> <span data-ttu-id="e22f8-111">アプリケーションが、ローカル システムで定義されていない特定のタイム ゾーンの存在に依存している場合は、タイム ゾーンに関する情報をシリアル化および逆シリアル化することによってアプリケーションからその存在を確認できます。</span><span class="sxs-lookup"><span data-stu-id="e22f8-111">If an application relies on the presence of a particular time zone that may not be defined on a local system, the application can ensure its presence by serializing and deserializing information about the time zone.</span></span> <span data-ttu-id="e22f8-112">その後、タイム ゾーンをリスト コントロールに追加して、アプリケーション ユーザーが選択できるようにできます。</span><span class="sxs-lookup"><span data-stu-id="e22f8-112">The time zone can then be added to a list control so that the application user can select it.</span></span> <span data-ttu-id="e22f8-113">詳細については、「[方法: 埋め込みリソースにタイム ゾーンを保存する](save-time-zones-to-an-embedded-resource.md)」および「[方法: 埋め込みリソースからタイム ゾーンを復元する](restore-time-zones-from-an-embedded-resource.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e22f8-113">For details, see [How to: Save Time Zones to an Embedded Resource](save-time-zones-to-an-embedded-resource.md) and [How to: Restore time zones from an embedded resource](restore-time-zones-from-an-embedded-resource.md).</span></span>

### <a name="to-enumerate-the-time-zones-present-on-the-local-system"></a><span data-ttu-id="e22f8-114">ローカル システムに存在するタイム ゾーンを列挙するには</span><span class="sxs-lookup"><span data-stu-id="e22f8-114">To enumerate the time zones present on the local system</span></span>

1. <span data-ttu-id="e22f8-115"><xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e22f8-115">Call the <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e22f8-116">このメソッドから、<xref:System.TimeZoneInfo> オブジェクトのジェネリックの <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> コレクションが返されます。</span><span class="sxs-lookup"><span data-stu-id="e22f8-116">The method returns a generic <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> collection of <xref:System.TimeZoneInfo> objects.</span></span> <span data-ttu-id="e22f8-117">コレクション内のエントリは、その <xref:System.TimeZoneInfo.DisplayName%2A> プロパティによって並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="e22f8-117">The entries in the collection are sorted by their <xref:System.TimeZoneInfo.DisplayName%2A> property.</span></span> <span data-ttu-id="e22f8-118">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="e22f8-118">For example:</span></span>

   [!code-csharp[System.TimeZone2.Concepts#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#1)]
   [!code-vb[System.TimeZone2.Concepts#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#1)]

2. <span data-ttu-id="e22f8-119">コレクション内の個々の <xref:System.TimeZoneInfo> オブジェクトを列挙するには `foreach` ループ (C# の場合) または `For Each`…`Next`</span><span class="sxs-lookup"><span data-stu-id="e22f8-119">Enumerate the individual <xref:System.TimeZoneInfo> objects in the collection by using a `foreach` loop (in C#) or a `For Each`…`Next`</span></span> <span data-ttu-id="e22f8-120">ループ (Visual Basic の場合) を使用し、各オブジェクトに対して必要な処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="e22f8-120">loop (in Visual Basic), and perform any necessary processing on each object.</span></span> <span data-ttu-id="e22f8-121">たとえば、次のコードでは、手順 1 で返された <xref:System.TimeZoneInfo> オブジェクトの <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> コレクションを列挙し、各タイム ゾーンの表示名をコンソールに一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="e22f8-121">For example, the following code enumerates the <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> collection of <xref:System.TimeZoneInfo> objects returned in step 1 and lists the display name of each time zone on the console.</span></span>

   [!code-csharp[System.TimeZone2.Concepts#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#12)]
   [!code-vb[System.TimeZone2.Concepts#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#12)]

### <a name="to-present-the-user-with-a-list-of-time-zones-present-on-the-local-system"></a><span data-ttu-id="e22f8-122">ローカル システム上に存在するタイム ゾーンの一覧をユーザーに表示するには</span><span class="sxs-lookup"><span data-stu-id="e22f8-122">To present the user with a list of time zones present on the local system</span></span>

1. <span data-ttu-id="e22f8-123"><xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e22f8-123">Call the <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e22f8-124">このメソッドから、<xref:System.TimeZoneInfo> オブジェクトのジェネリックの <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> コレクションが返されます。</span><span class="sxs-lookup"><span data-stu-id="e22f8-124">The method returns a generic <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> collection of <xref:System.TimeZoneInfo> objects.</span></span>

2. <span data-ttu-id="e22f8-125">手順 1 で返されたコレクションを、Windows フォームまたは ASP.NET のリスト コントロールの `DataSource` プロパティに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="e22f8-125">Assign the collection returned in step 1 to the `DataSource` property of a Windows forms or ASP.NET list control.</span></span>

3. <span data-ttu-id="e22f8-126">ユーザーが選択した <xref:System.TimeZoneInfo> オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="e22f8-126">Retrieve the <xref:System.TimeZoneInfo> object that the user has selected.</span></span>

<span data-ttu-id="e22f8-127">Windows アプリケーションの場合の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e22f8-127">The example provides an illustration for a Windows application.</span></span>

## <a name="example"></a><span data-ttu-id="e22f8-128">例</span><span class="sxs-lookup"><span data-stu-id="e22f8-128">Example</span></span>

<span data-ttu-id="e22f8-129">この例では、システムで定義されているタイム ゾーンをリスト ボックスに表示する Windows アプリケーションを開始します。</span><span class="sxs-lookup"><span data-stu-id="e22f8-129">The example starts a Windows application that displays the time zones defined on a system in a list box.</span></span> <span data-ttu-id="e22f8-130">次いでこの例では、ユーザーによって選択されたタイム ゾーン オブジェクトの <xref:System.TimeZoneInfo.DisplayName%2A> プロパティの値を含むダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e22f8-130">The example then displays a dialog box that contains the value of the <xref:System.TimeZoneInfo.DisplayName%2A> property of the time zone object selected by the user.</span></span>

[!code-csharp[System.TimeZone2.Concepts#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#2)]
[!code-vb[System.TimeZone2.Concepts#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#2)]

<span data-ttu-id="e22f8-131">ほとんどのリスト コントロール (<xref:System.Windows.Forms.ListBox?displayProperty=nameWithType> または <xref:System.Web.UI.WebControls.BulletedList?displayProperty=nameWithType> コントロールなど) では、オブジェクト変数のコレクションをコントロールの `DataSource` プロパティに割り当てることができます。ただし、そのコレクションが <xref:System.Collections.IEnumerable> インターフェイスを実装している必要があります。</span><span class="sxs-lookup"><span data-stu-id="e22f8-131">Most list controls (such as the <xref:System.Windows.Forms.ListBox?displayProperty=nameWithType> or <xref:System.Web.UI.WebControls.BulletedList?displayProperty=nameWithType> control) allow you to assign a collection of object variables to their `DataSource` property as long as that collection implements the <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="e22f8-132">(<xref:System.Collections.ObjectModel.ReadOnlyCollection%601> ジェネリック クラスはその一例です)。コレクションの各オブジェクトを表示するため、コントロールでは、そのオブジェクトの `ToString` メソッドを呼び出して、オブジェクトを表現するために使用する文字列を抽出します。</span><span class="sxs-lookup"><span data-stu-id="e22f8-132">(The generic <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> class does this.) To display an individual object in the collection, the control calls that object's `ToString` method to extract the string that is used to represent the object.</span></span> <span data-ttu-id="e22f8-133"><xref:System.TimeZoneInfo> オブジェクトの場合、`ToString` メソッドからは <xref:System.TimeZoneInfo> オブジェクトの表示名 (その <xref:System.TimeZoneInfo.DisplayName%2A> プロパティの値) が返されます。</span><span class="sxs-lookup"><span data-stu-id="e22f8-133">In the case of <xref:System.TimeZoneInfo> objects, the `ToString` method returns the <xref:System.TimeZoneInfo> object's display name (the value of its <xref:System.TimeZoneInfo.DisplayName%2A> property).</span></span>

> [!NOTE]
> <span data-ttu-id="e22f8-134">リスト コントロールではオブジェクトの `ToString` メソッドが呼び出されるため、オブジェクト <xref:System.TimeZoneInfo> のコレクションをコントロールに割り当てて、各オブジェクトのわかりやすい名前をコントロールに表示させ、ユーザーが選択した <xref:System.TimeZoneInfo> オブジェクトを取得することができます。</span><span class="sxs-lookup"><span data-stu-id="e22f8-134">Because list controls call an object's `ToString` method, you can assign a collection of <xref:System.TimeZoneInfo> objects to the control, have the control display a meaningful name for each object, and retrieve the <xref:System.TimeZoneInfo> object that the user has selected.</span></span> <span data-ttu-id="e22f8-135">これにより、コレクション内の各オブジェクトについて文字列を抽出し、その文字列を別のコレクションに割り当てた後、そのコレクションをコントロールの `DataSource` プロパティに割り当てて、ユーザーが選択した文字列を取得し、その文字列を使用してそれが表しているオブジェクトを抽出する、という必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="e22f8-135">This eliminates the need to extract a string for each object in the collection, assign the string to a collection that is in turn assigned to the control's `DataSource` property, retrieve the string the user has selected, and then use this string to extract the object that it describes.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="e22f8-136">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="e22f8-136">Compiling the code</span></span>

<span data-ttu-id="e22f8-137">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e22f8-137">This example requires:</span></span>

- <span data-ttu-id="e22f8-138">次の名前空間がインポートされていること。</span><span class="sxs-lookup"><span data-stu-id="e22f8-138">That the following namespaces be imported:</span></span>

  <span data-ttu-id="e22f8-139"><xref:System> (C# コードの場合)</span><span class="sxs-lookup"><span data-stu-id="e22f8-139"><xref:System> (in C# code)</span></span>

  <xref:System.Collections.ObjectModel>

## <a name="see-also"></a><span data-ttu-id="e22f8-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="e22f8-140">See also</span></span>

- [<span data-ttu-id="e22f8-141">日付、時刻、およびタイム ゾーン</span><span class="sxs-lookup"><span data-stu-id="e22f8-141">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="e22f8-142">方法: 埋め込みリソースにタイム ゾーンを保存する</span><span class="sxs-lookup"><span data-stu-id="e22f8-142">How to: Save time zones to an embedded resource</span></span>](save-time-zones-to-an-embedded-resource.md)
- [<span data-ttu-id="e22f8-143">方法: 埋め込みリソースからタイム ゾーンを復元する</span><span class="sxs-lookup"><span data-stu-id="e22f8-143">How to: Restore time zones from an embedded resource</span></span>](restore-time-zones-from-an-embedded-resource.md)
