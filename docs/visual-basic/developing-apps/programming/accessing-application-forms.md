---
description: '詳細情報: アプリケーション フォームへのアクセス (Visual Basic)'
title: アプリケーション フォームへのアクセス
ms.date: 07/20/2015
helpviewer_keywords:
- forms [Visual Basic], communicating between
- application forms [Visual Basic], accessing
- forms [Visual Basic], accessing one from another
- My.Forms object
- forms [Visual Basic], accessing all open
ms.assetid: 9aaf5aaf-2012-4f97-89c7-6e62b9d17863
ms.openlocfilehash: dae73700434f9cdbb145ebea605c87c33f7c0c73
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797901"
---
# <a name="accessing-application-forms-visual-basic"></a><span data-ttu-id="19267-103">アプリケーション フォームへのアクセス (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="19267-103">Accessing Application Forms (Visual Basic)</span></span>

<span data-ttu-id="19267-104">`My.Forms` オブジェクトは、アプリケーションのプロジェクトで宣言された各 Windows フォームのインスタンスに簡単にアクセスする方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="19267-104">The `My.Forms` object provides an easy way to access an instance of each Windows Form declared in the application's project.</span></span> <span data-ttu-id="19267-105">`My.Application` オブジェクトのプロパティを利用し、アプリケーションのスプラッシュ スクリーンとメイン フォームにアクセスし、アプリケーションのオープン フォームの一覧を取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="19267-105">You can also use properties of the `My.Application` object to access the application's splash screen and main form, and get a list of the application's open forms.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="19267-106">タスク</span><span class="sxs-lookup"><span data-stu-id="19267-106">Tasks</span></span>  

 <span data-ttu-id="19267-107">次の表に示すのは、アプリケーションのフォームにアクセスする方法を示す例です。</span><span class="sxs-lookup"><span data-stu-id="19267-107">The following table lists examples showing how to access an application's forms.</span></span>  
  
|<span data-ttu-id="19267-108">終了</span><span class="sxs-lookup"><span data-stu-id="19267-108">To</span></span>|<span data-ttu-id="19267-109">解決方法については、</span><span class="sxs-lookup"><span data-stu-id="19267-109">See</span></span>|  
|---|---|  
|<span data-ttu-id="19267-110">アプリケーションのあるフォームから別のフォームにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="19267-110">Access one form from another form in an application.</span></span>|[<span data-ttu-id="19267-111">My.Forms オブジェクト</span><span class="sxs-lookup"><span data-stu-id="19267-111">My.Forms Object</span></span>](../../language-reference/objects/my-forms-object.md)|  
|<span data-ttu-id="19267-112">アプリケーションのすべてのオープン フォームのタイトルを表示します。</span><span class="sxs-lookup"><span data-stu-id="19267-112">Display the titles of all the application's open forms.</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>|  
|<span data-ttu-id="19267-113">アプリケーションの起動時に状態情報でスプラッシュ スクリーンを更新します。</span><span class="sxs-lookup"><span data-stu-id="19267-113">Update the splash screen with status information as the application starts.</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="19267-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="19267-114">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>
- [<span data-ttu-id="19267-115">My.Forms オブジェクト</span><span class="sxs-lookup"><span data-stu-id="19267-115">My.Forms Object</span></span>](../../language-reference/objects/my-forms-object.md)
