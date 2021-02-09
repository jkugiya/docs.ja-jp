---
description: '詳細情報: スタートアップ フォームが指定されていません。'
title: スタートアップ フォームが指定されていません。
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_NoStartupForm
ms.assetid: 8e04af49-4bef-49de-a7ec-e407e9873da7
ms.openlocfilehash: 4b00890f07121ef55ce49978842010cc54aba29b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797186"
---
# <a name="a-startup-form-has-not-been-specified"></a><span data-ttu-id="57c43-103">スタートアップ フォームが指定されていません。</span><span class="sxs-lookup"><span data-stu-id="57c43-103">A startup form has not been specified</span></span>

<span data-ttu-id="57c43-104">アプリケーションで <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> クラスが使用されていますが、スタートアップ フォームが指定されていません。</span><span class="sxs-lookup"><span data-stu-id="57c43-104">The application uses the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> class but does not specify the startup form.</span></span>  
  
 <span data-ttu-id="57c43-105">これは、プロジェクト デザイナーで **[アプリケーション フレームワークを有効にする]** チェック ボックスがオンになっていても、 **[スタートアップ フォーム]** が指定されていない場合に発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="57c43-105">This can occur if the **Enable application framework** check box is selected in the project designer but the **Startup form** is not specified.</span></span> <span data-ttu-id="57c43-106">詳細については、「[[アプリケーション] ページ (プロジェクト デザイナー) (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57c43-106">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="57c43-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="57c43-107">To correct this error</span></span>  
  
1. <span data-ttu-id="57c43-108">アプリケーションのスタートアップ オブジェクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="57c43-108">Specify a startup object for the application.</span></span>  
  
     <span data-ttu-id="57c43-109">詳細については、「[[アプリケーション] ページ (プロジェクト デザイナー) (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57c43-109">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
2. <span data-ttu-id="57c43-110"><xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> メソッドをオーバーライドして、スタートアップ フォームに <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="57c43-110">Override the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> method to set the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> property to the startup form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57c43-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="57c43-111">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A>
- [<span data-ttu-id="57c43-112">Visual Basic アプリケーション モデルの概要</span><span class="sxs-lookup"><span data-stu-id="57c43-112">Overview of the Visual Basic Application Model</span></span>](../../developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)
