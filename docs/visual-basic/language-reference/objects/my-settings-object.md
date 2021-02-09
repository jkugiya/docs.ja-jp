---
description: '詳細情報: My.Settings オブジェクト'
title: My.Settings オブジェクト
ms.date: 07/20/2015
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
helpviewer_keywords:
- My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
ms.openlocfilehash: 92323c5379d0c5a4dbf96cfdbe0becccc2bad7cd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640603"
---
# <a name="mysettings-object"></a><span data-ttu-id="d2234-103">My.Settings オブジェクト</span><span class="sxs-lookup"><span data-stu-id="d2234-103">My.Settings Object</span></span>

<span data-ttu-id="d2234-104">アプリケーションの設定にアクセスするためのプロパティとメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="d2234-104">Provides properties and methods for accessing the application's settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2234-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="d2234-105">Remarks</span></span>  

 <span data-ttu-id="d2234-106">`My.Settings` オブジェクトは、アプリケーションの設定へのアクセスを提供し、アプリケーションのプロパティ設定やその他の情報を動的に格納し、取得できるようにします。</span><span class="sxs-lookup"><span data-stu-id="d2234-106">The `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="d2234-107">詳細については、「[アプリケーションの設定の管理 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2234-107">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d2234-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="d2234-108">Properties</span></span>  

 <span data-ttu-id="d2234-109">`My.Settings` オブジェクトのプロパティを使用すると、アプリケーションの設定にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="d2234-109">The properties of the `My.Settings` object provide access to your application's settings.</span></span> <span data-ttu-id="d2234-110">設定を追加または削除するには、**設定デザイナー** を使用します。</span><span class="sxs-lookup"><span data-stu-id="d2234-110">To add or remove settings, use the **Settings Designer**.</span></span>  
  
 <span data-ttu-id="d2234-111">各設定には **[名前]** 、 **[型]** 、 **[スコープ]** 、および **[値]** が含まれ、これらの設定によって、各設定にアクセスするためのプロパティが `My.Settings` オブジェクトにどのように表示されるかが決まります。</span><span class="sxs-lookup"><span data-stu-id="d2234-111">Each setting has a **Name**, **Type**, **Scope**, and **Value**, and these settings determine how the property to access each setting appears in the `My.Settings` object:</span></span>  
  
- <span data-ttu-id="d2234-112">**[名前]** は、プロパティの名前を決定します。</span><span class="sxs-lookup"><span data-stu-id="d2234-112">**Name** determines the name of the property.</span></span>  
  
- <span data-ttu-id="d2234-113">**[型]** は、プロパティの型を決定します。</span><span class="sxs-lookup"><span data-stu-id="d2234-113">**Type** determines the type of the property.</span></span>  
  
- <span data-ttu-id="d2234-114">**[スコープ]** は、プロパティが読み取り専用かどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="d2234-114">**Scope** indicates if the property is read-only.</span></span> <span data-ttu-id="d2234-115">値が **[アプリケーション]** の場合、プロパティは読み取り専用です。値が **[ユーザー]** の場合、プロパティは読み取り/書き込みです。</span><span class="sxs-lookup"><span data-stu-id="d2234-115">If the value is **Application**, the property is read-only; if the value is **User**, the property is read-write.</span></span>  
  
- <span data-ttu-id="d2234-116">**[値]** はプロパティの既定値です。</span><span class="sxs-lookup"><span data-stu-id="d2234-116">**Value** is the default value of the property.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d2234-117">メソッド</span><span class="sxs-lookup"><span data-stu-id="d2234-117">Methods</span></span>  
  
|<span data-ttu-id="d2234-118">メソッド</span><span class="sxs-lookup"><span data-stu-id="d2234-118">Method</span></span>|<span data-ttu-id="d2234-119">説明</span><span class="sxs-lookup"><span data-stu-id="d2234-119">Description</span></span>|  
|---|---|  
|`Reload`|<span data-ttu-id="d2234-120">最後に保存した値からユーザー設定を再度読み込みます。</span><span class="sxs-lookup"><span data-stu-id="d2234-120">Reloads the user settings from the last saved values.</span></span>|  
|`Save`|<span data-ttu-id="d2234-121">現在のユーザー設定を保存します。</span><span class="sxs-lookup"><span data-stu-id="d2234-121">Saves the current user settings.</span></span>|  
  
 <span data-ttu-id="d2234-122">`My.Settings` オブジェクトは、<xref:System.Configuration.ApplicationSettingsBase> クラスから継承された高度なプロパティやメソッドも提供します。</span><span class="sxs-lookup"><span data-stu-id="d2234-122">The `My.Settings` object also provides advanced properties and methods, inherited from the <xref:System.Configuration.ApplicationSettingsBase> class.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="d2234-123">タスク</span><span class="sxs-lookup"><span data-stu-id="d2234-123">Tasks</span></span>  

 <span data-ttu-id="d2234-124">次の表に、`My.Settings` オブジェクトに関連するタスクの例を示します。</span><span class="sxs-lookup"><span data-stu-id="d2234-124">The following table lists examples of tasks involving the `My.Settings` object.</span></span>  
  
|<span data-ttu-id="d2234-125">終了</span><span class="sxs-lookup"><span data-stu-id="d2234-125">To</span></span>|<span data-ttu-id="d2234-126">解決方法については、</span><span class="sxs-lookup"><span data-stu-id="d2234-126">See</span></span>|  
|---|---|  
|<span data-ttu-id="d2234-127">アプリケーション設定を読み取る</span><span class="sxs-lookup"><span data-stu-id="d2234-127">Read an application setting</span></span>|[<span data-ttu-id="d2234-128">方法: Visual Basic でアプリケーション設定を読み取る</span><span class="sxs-lookup"><span data-stu-id="d2234-128">How to: Read Application Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|<span data-ttu-id="d2234-129">ユーザー設定を変更する</span><span class="sxs-lookup"><span data-stu-id="d2234-129">Change a user setting</span></span>|[<span data-ttu-id="d2234-130">方法: Visual Basic でユーザー設定を変更する</span><span class="sxs-lookup"><span data-stu-id="d2234-130">How to: Change User Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|<span data-ttu-id="d2234-131">ユーザー設定を永続化する</span><span class="sxs-lookup"><span data-stu-id="d2234-131">Persist user settings</span></span>|[<span data-ttu-id="d2234-132">方法: Visual Basic でユーザー設定を永続化する</span><span class="sxs-lookup"><span data-stu-id="d2234-132">How to: Persist User Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|<span data-ttu-id="d2234-133">ユーザー設定のためのプロパティ グリッドを作成する</span><span class="sxs-lookup"><span data-stu-id="d2234-133">Create a property grid for user settings</span></span>|[<span data-ttu-id="d2234-134">方法: Visual Basic でユーザー設定のためのプロパティ グリッドを作成する</span><span class="sxs-lookup"><span data-stu-id="d2234-134">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a><span data-ttu-id="d2234-135">例</span><span class="sxs-lookup"><span data-stu-id="d2234-135">Example</span></span>  

 <span data-ttu-id="d2234-136">次の例は、`Nickname` の設定値を表示します。</span><span class="sxs-lookup"><span data-stu-id="d2234-136">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 <span data-ttu-id="d2234-137">この例を実行するには、アプリケーションで `String` 型の `Nickname` を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2234-137">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2234-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="d2234-138">See also</span></span>

- <xref:System.Configuration.ApplicationSettingsBase>
- [<span data-ttu-id="d2234-139">方法: Visual Basic でアプリケーション設定を読み取る</span><span class="sxs-lookup"><span data-stu-id="d2234-139">How to: Read Application Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="d2234-140">方法: Visual Basic でユーザー設定を変更する</span><span class="sxs-lookup"><span data-stu-id="d2234-140">How to: Change User Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="d2234-141">方法: Visual Basic でユーザー設定を永続化する</span><span class="sxs-lookup"><span data-stu-id="d2234-141">How to: Persist User Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="d2234-142">方法: Visual Basic でユーザー設定のためのプロパティ グリッドを作成する</span><span class="sxs-lookup"><span data-stu-id="d2234-142">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="d2234-143">アプリケーションの設定の管理 (.NET)</span><span class="sxs-lookup"><span data-stu-id="d2234-143">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
