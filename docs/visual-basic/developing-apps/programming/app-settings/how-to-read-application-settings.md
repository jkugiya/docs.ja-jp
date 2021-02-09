---
description: '詳細情報: 方法:Visual Basic でアプリケーション設定を読み取る'
title: '方法: アプリケーション設定を読み取る'
ms.date: 07/20/2015
helpviewer_keywords:
- reading application settings
- My.Settings object [Visual Basic], reading application settings
- application settings [Visual Basic], reading
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
ms.openlocfilehash: 30b5a3b0cdf3565fc8c1f0dfa19e7717a714c350
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797823"
---
# <a name="how-to-read-application-settings-in-visual-basic"></a><span data-ttu-id="21ddd-103">方法 : Visual Basic でアプリケーション設定を読み取る</span><span class="sxs-lookup"><span data-stu-id="21ddd-103">How to: Read Application Settings in Visual Basic</span></span>

<span data-ttu-id="21ddd-104">`My.Settings` オブジェクトで設定のプロパティにアクセスすると、ユーザー設定を読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="21ddd-104">You can read a user setting by accessing the setting's property on the `My.Settings` object.</span></span>  
  
 <span data-ttu-id="21ddd-105">`My.Settings` オブジェクトでは、各設定はプロパティとして公開されます。</span><span class="sxs-lookup"><span data-stu-id="21ddd-105">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="21ddd-106">プロパティ名はその設定の名前と同じで、プロパティの型は設定の型と同じです。</span><span class="sxs-lookup"><span data-stu-id="21ddd-106">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="21ddd-107">プロパティが読み取り専用かどうかは、設定の **スコープ** でわかります。つまり、**アプリケーション** スコープの設定のプロパティは読み取り専用であるのに対し、**ユーザー** スコープの設定のプロパティは読み取り/書き込みです。</span><span class="sxs-lookup"><span data-stu-id="21ddd-107">The setting's **Scope** indicates if the property is read-only; the property for an **Application** scope setting is read-only, while the property for a **User** scope setting is read-write.</span></span> <span data-ttu-id="21ddd-108">詳細については、「[My.Settings オブジェクト](../../../language-reference/objects/my-settings-object.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21ddd-108">For more information, see [My.Settings Object](../../../language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="21ddd-109">例</span><span class="sxs-lookup"><span data-stu-id="21ddd-109">Example</span></span>  

 <span data-ttu-id="21ddd-110">次の例は、`Nickname` の設定値を表示します。</span><span class="sxs-lookup"><span data-stu-id="21ddd-110">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 <span data-ttu-id="21ddd-111">この例を実行するには、アプリケーションで `String` 型の `Nickname` を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="21ddd-111">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span> <span data-ttu-id="21ddd-112">詳細については、「[アプリケーションの設定の管理 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21ddd-112">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21ddd-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="21ddd-113">See also</span></span>

- [<span data-ttu-id="21ddd-114">My.Settings オブジェクト</span><span class="sxs-lookup"><span data-stu-id="21ddd-114">My.Settings Object</span></span>](../../../language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="21ddd-115">方法: Visual Basic でユーザー設定を変更する</span><span class="sxs-lookup"><span data-stu-id="21ddd-115">How to: Change User Settings in Visual Basic</span></span>](how-to-change-user-settings.md)
- [<span data-ttu-id="21ddd-116">方法: Visual Basic でユーザー設定を永続化する</span><span class="sxs-lookup"><span data-stu-id="21ddd-116">How to: Persist User Settings in Visual Basic</span></span>](how-to-persist-user-settings.md)
- [<span data-ttu-id="21ddd-117">方法: Visual Basic でユーザー設定のためのプロパティ グリッドを作成する</span><span class="sxs-lookup"><span data-stu-id="21ddd-117">How to: Create Property Grids for User Settings in Visual Basic</span></span>](how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="21ddd-118">アプリケーションの設定の管理 (.NET)</span><span class="sxs-lookup"><span data-stu-id="21ddd-118">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
