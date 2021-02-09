---
description: '詳細情報: 方法:Visual Basic でユーザー設定を永続化する'
title: '方法: ユーザー設定を永続化する'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], persisting user settings
- persistence [Visual Basic], persisting user settings [Visual Basic]
- user settings [Visual Basic], persisting
ms.assetid: 0e5e6415-b6e2-4602-9be0-a65fa167d007
ms.openlocfilehash: 43ca82442678356afacb8e05149a35d485603059
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797836"
---
# <a name="how-to-persist-user-settings-in-visual-basic"></a><span data-ttu-id="345ad-103">方法 : Visual Basic でユーザー設定を永続化する</span><span class="sxs-lookup"><span data-stu-id="345ad-103">How to: Persist User Settings in Visual Basic</span></span>

<span data-ttu-id="345ad-104">`My.Settings.Save` メソッドを使用して、ユーザー設定の変更を永続化できます。</span><span class="sxs-lookup"><span data-stu-id="345ad-104">You can use the `My.Settings.Save` method to persist changes to the user settings.</span></span>  
  
 <span data-ttu-id="345ad-105">通常、アプリケーションでは、ユーザー設定の変更を、アプリケーションのシャットダウン時に永続化するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="345ad-105">Typically, applications are designed to persist the changes to the user settings when the application shuts down.</span></span> <span data-ttu-id="345ad-106">これは、複数の要因から、設定の保存に数秒かかることがあるためです。</span><span class="sxs-lookup"><span data-stu-id="345ad-106">This is because saving the settings can take, depending on several factors, several seconds.</span></span>  
  
 <span data-ttu-id="345ad-107">詳細については、「[My.Settings オブジェクト](../../../language-reference/objects/my-settings-object.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="345ad-107">For more information, see [My.Settings Object](../../../language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="345ad-108">ユーザー スコープ設定の値は実行時に変更および保存できますが、アプリケーション スコープ設定は読み取り専用であり、プログラムで変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="345ad-108">Although you can change and save the values of user-scope settings at run time, application-scope settings are read-only and cannot be changed programmatically.</span></span> <span data-ttu-id="345ad-109">アプリケーション スコープの設定を変更するには、アプリケーションを作成するときに、**プロジェクト デザイナー** を使用するか、アプリケーションの構成ファイルを編集します。</span><span class="sxs-lookup"><span data-stu-id="345ad-109">You can change application-scope settings when creating the application, through the **Project Designer**, or by editing the application's configuration file.</span></span> <span data-ttu-id="345ad-110">詳細については、「[アプリケーションの設定の管理 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="345ad-110">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="345ad-111">例</span><span class="sxs-lookup"><span data-stu-id="345ad-111">Example</span></span>  

 <span data-ttu-id="345ad-112">この例では、`LastChanged` ユーザー設定の値を変更し、`My.Settings.Save` メソッドを呼び出して、その変更を保存します。</span><span class="sxs-lookup"><span data-stu-id="345ad-112">This example changes the value of the `LastChanged` user setting and saves that change by calling the `My.Settings.Save` method.</span></span>  
  
 [!code-vb[VbVbalrMyResources#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#5)]  
  
 <span data-ttu-id="345ad-113">この例を動作させるには、アプリケーションに `Date` 型の `LastChanged` ユーザー設定が必要です。</span><span class="sxs-lookup"><span data-stu-id="345ad-113">For this example to work, your application must have a `LastChanged` user setting, of type `Date`.</span></span> <span data-ttu-id="345ad-114">詳細については、「[アプリケーションの設定の管理 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="345ad-114">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="345ad-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="345ad-115">See also</span></span>

- [<span data-ttu-id="345ad-116">My.Settings オブジェクト</span><span class="sxs-lookup"><span data-stu-id="345ad-116">My.Settings Object</span></span>](../../../language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="345ad-117">方法: Visual Basic でアプリケーション設定を読み取る</span><span class="sxs-lookup"><span data-stu-id="345ad-117">How to: Read Application Settings in Visual Basic</span></span>](how-to-read-application-settings.md)
- [<span data-ttu-id="345ad-118">方法: Visual Basic でユーザー設定を変更する</span><span class="sxs-lookup"><span data-stu-id="345ad-118">How to: Change User Settings in Visual Basic</span></span>](how-to-change-user-settings.md)
- [<span data-ttu-id="345ad-119">方法: Visual Basic でユーザー設定のためのプロパティ グリッドを作成する</span><span class="sxs-lookup"><span data-stu-id="345ad-119">How to: Create Property Grids for User Settings in Visual Basic</span></span>](how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="345ad-120">アプリケーションの設定の管理 (.NET)</span><span class="sxs-lookup"><span data-stu-id="345ad-120">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
