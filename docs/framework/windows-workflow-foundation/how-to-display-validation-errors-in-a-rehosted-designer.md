---
description: '詳細については、「方法: 再ホストされたデザイナーで検証エラーを表示する」を参照してください。'
title: '方法: 再ホストされたデザイナーの検証エラーを表示する'
ms.date: 03/30/2017
ms.assetid: 5aa8fb53-8f75-433b-bc06-7c7d33583d5d
ms.openlocfilehash: 75ff45e6e9a81df96a9940ce21d1b160cab1000e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99777737"
---
# <a name="how-to-display-validation-errors-in-a-rehosted-designer"></a><span data-ttu-id="667e7-103">方法: 再ホストされたデザイナーの検証エラーを表示する</span><span class="sxs-lookup"><span data-stu-id="667e7-103">How to: Display Validation Errors in a Rehosted Designer</span></span>

<span data-ttu-id="667e7-104">このトピックでは、再ホストされた Windows ワークフローデザイナーで検証エラーを取得して発行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="667e7-104">This topic describes how to retrieve and publish validation errors in a rehosted Windows Workflow Designer.</span></span> <span data-ttu-id="667e7-105">再ホストされたデザイナー内のワークフローが有効であることを確認するために手順を示します。</span><span class="sxs-lookup"><span data-stu-id="667e7-105">This provides us with a procedure to confirm that a workflow in a rehosted designer is valid.</span></span>  
  
 <span data-ttu-id="667e7-106">このタスクは 2 つの部分で構成されています。</span><span class="sxs-lookup"><span data-stu-id="667e7-106">This task has two parts.</span></span> <span data-ttu-id="667e7-107">最初に、<xref:System.Activities.Presentation.Validation.IValidationErrorService> を実装します。</span><span class="sxs-lookup"><span data-stu-id="667e7-107">The first is to provide an implementation <xref:System.Activities.Presentation.Validation.IValidationErrorService>.</span></span>  <span data-ttu-id="667e7-108">このインターフェイスには、1 つの重要なメソッド <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> を実装します。このメソッドは、エラーに関する情報を含む <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> オブジェクトの一覧をデバッグ ログに渡します。</span><span class="sxs-lookup"><span data-stu-id="667e7-108">There is one critical method to implement on this interface, <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> which will pass you a list of <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> objects containing information about the errors to the debug log.</span></span>  <span data-ttu-id="667e7-109">このインターフェイスを実装した後に、その実装のインスタンスを編集コンテキストに発行して、エラー情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="667e7-109">After implementing the interface, you retrieve the error information by publishing an instance of that implementation to the editing context.</span></span>  
  
### <a name="implement-the-ivalidationerrorservice-interface"></a><span data-ttu-id="667e7-110">IValidationErrorService インターフェイスの実装</span><span class="sxs-lookup"><span data-stu-id="667e7-110">Implement the IValidationErrorService Interface</span></span>  
  
1. <span data-ttu-id="667e7-111">以下に、検証エラーをデバッグ ログに書き込む単純な実装を表すコード例を示します。</span><span class="sxs-lookup"><span data-stu-id="667e7-111">Here is a code sample for a simple implementation that will write out the validation errors to the debug log.</span></span>  
  
    ```csharp  
    using System.Activities.Presentation.Validation;  
    using System.Collections.Generic;  
    using System.Diagnostics;  
    using System.Linq;  
  
    namespace VariableFinderShell  
    {  
        class DebugValidationErrorService : IValidationErrorService  
        {  
            public void ShowValidationErrors(IList<ValidationErrorInfo> errors)  
            {  
                errors.ToList().ForEach(vei => Debug.WriteLine($"Error: {vei.Message}"));  
            }  
        }  
    }  
    ```  
  
### <a name="publishing-to-the-editing-context"></a><span data-ttu-id="667e7-112">編集コンテキストへの発行</span><span class="sxs-lookup"><span data-stu-id="667e7-112">Publishing to the Editing Context</span></span>  
  
1. <span data-ttu-id="667e7-113">以下に、編集コンテキストに発行するコードを示します。</span><span class="sxs-lookup"><span data-stu-id="667e7-113">Here is the code that will publish this to the editing context.</span></span>  
  
    ```csharp  
    wd.Context.Services.Publish<IValidationErrorService>(new DebugValidationErrorService());  
    ```
