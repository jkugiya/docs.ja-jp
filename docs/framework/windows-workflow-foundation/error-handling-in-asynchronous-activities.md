---
description: 詳細については、「非同期アクティビティでのエラー処理」を参照してください。
title: 非同期アクティビティ内のエラー処理
ms.date: 03/30/2017
ms.assetid: e8f8ce2b-50c9-4e44-b187-030e0cf30a5d
ms.openlocfilehash: df223998737259aca01a4dc18ed9f2a911d80366
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742408"
---
# <a name="error-handling-in-asynchronous-activities"></a><span data-ttu-id="5a1a0-103">非同期アクティビティ内のエラー処理</span><span class="sxs-lookup"><span data-stu-id="5a1a0-103">Error handling in asynchronous activities</span></span>

<span data-ttu-id="5a1a0-104"><xref:System.Activities.AsyncCodeActivity> でのエラー処理には、アクティビティのコールバック システムを使用したエラーの送信が含まれています。</span><span class="sxs-lookup"><span data-stu-id="5a1a0-104">Providing error handling in an <xref:System.Activities.AsyncCodeActivity> involves routing the error through the activity’s callback system.</span></span> <span data-ttu-id="5a1a0-105">このトピックでは、SendMail アクティビティのサンプルを使用してホストへ非同期操作でスローされるエラーを取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5a1a0-105">This topic describes how to get an error that is thrown in an asynchronous operation back to the host, using the SendMail activity sample.</span></span>  
  
## <a name="returning-an-error-thrown-in-an-asynchronous-activity-back-to-the-host"></a><span data-ttu-id="5a1a0-106">非同期アクティビティでスローされたエラーをホストへ返す</span><span class="sxs-lookup"><span data-stu-id="5a1a0-106">Returning an error thrown in an asynchronous activity back to the host</span></span>  

 <span data-ttu-id="5a1a0-107">SendMail アクティビティ サンプルでの、ホストに返される非同期操作でのエラーのルーティングの手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5a1a0-107">Routing an error in an asynchronous operation back to the host in the SendMail activity sample involves the following steps:</span></span>  
  
- <span data-ttu-id="5a1a0-108">Exception プロパティを `SendMailAsyncResult` クラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="5a1a0-108">Add an Exception property to the `SendMailAsyncResult` class.</span></span>  
  
- <span data-ttu-id="5a1a0-109">スローされたエラーを `SendCompleted` イベント ハンドラー内でそのプロパティにコピーします。</span><span class="sxs-lookup"><span data-stu-id="5a1a0-109">Copy the thrown error to that property in the `SendCompleted` event handler.</span></span>  
  
- <span data-ttu-id="5a1a0-110">`EndExecute` イベント ハンドラー内で例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="5a1a0-110">Throw the exception in the `EndExecute` event handler.</span></span>  
  
 <span data-ttu-id="5a1a0-111">結果として得られるコードは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="5a1a0-111">The resulting code is as follows.</span></span>  
  
```csharp  
class SendMailAsyncResult : IAsyncResult  
        {  
            …  
            public Exception Error { get; set; }
            …  
            void SendCompleted(object sender, AsyncCompletedEventArgs e)  
            {  
                Error = e.Error;  
                this.asyncWaitHandle.Set();  
                callback(this);  
            }  
         }  
  
    public sealed class SendMail: AsyncCodeActivity  
    {  
         …  
        protected override void EndExecute(AsyncCodeActivityContext context, IAsyncResult result)  
        {  
            SendMailAsyncResult sendMailResult = result as SendMailAsyncResult;  
            if (sendMailResult != null && sendMailResult.Error != null)  
                throw sendMailResult.Error;
        }  
    }  
```
