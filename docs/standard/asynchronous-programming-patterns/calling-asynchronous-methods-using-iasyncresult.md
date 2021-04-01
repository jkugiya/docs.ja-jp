---
description: '詳細情報: IAsyncResult を使用した非同期メソッドの呼び出し'
title: IAsyncResult を使用した非同期メソッドの呼び出し
ms.date: 03/30/2017
helpviewer_keywords:
- ending asynchronous operations
- waiting for asynchronous operations
- asynchronous method calling
- calling asynchronous methods
- asynchronous programming, calling asynchronous methods
- IAsyncResult interface, calling asynchronous methods
- stopping asynchronous operations
ms.assetid: 07fba116-045b-473c-a0b7-acdbeb49861f
ms.openlocfilehash: 0fcf71c95fc0170a41ea2ad2085b9308c75264f8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754577"
---
# <a name="calling-asynchronous-methods-using-iasyncresult"></a><span data-ttu-id="44a0a-103">IAsyncResult を使用した非同期メソッドの呼び出し</span><span class="sxs-lookup"><span data-stu-id="44a0a-103">Calling Asynchronous Methods Using IAsyncResult</span></span>

<span data-ttu-id="44a0a-104">.NET ライブラリとサードパーティのクラス ライブラリの型では、アプリケーションのメイン スレッド以外のスレッドで非同期操作を実行しながら、アプリケーションを実行し続けることを許可するメソッドを提供できます。</span><span class="sxs-lookup"><span data-stu-id="44a0a-104">Types in the .NET libraries and third-party class libraries can provide methods that allow an application to continue executing while performing asynchronous operations in threads other than the main application thread.</span></span> <span data-ttu-id="44a0a-105">次のセクションでは、コード例を取り上げ、<xref:System.IAsyncResult> 設計パターンを使用する非同期メソッドをさまざまな方法で呼び出します。</span><span class="sxs-lookup"><span data-stu-id="44a0a-105">The following sections describe and provide code examples that demonstrate the different ways you can call asynchronous methods that use the <xref:System.IAsyncResult> design pattern.</span></span>  
  
- <span data-ttu-id="44a0a-106">[非同期操作の終了によるアプリケーション実行のブロック](blocking-application-execution-by-ending-an-async-operation.md)。</span><span class="sxs-lookup"><span data-stu-id="44a0a-106">[Blocking Application Execution by Ending an Async Operation](blocking-application-execution-by-ending-an-async-operation.md).</span></span>  
  
- <span data-ttu-id="44a0a-107">[AsyncWaitHandle の使用によるアプリケーション実行のブロック](blocking-application-execution-using-an-asyncwaithandle.md)。</span><span class="sxs-lookup"><span data-stu-id="44a0a-107">[Blocking Application Execution Using an AsyncWaitHandle](blocking-application-execution-using-an-asyncwaithandle.md).</span></span>  
  
- <span data-ttu-id="44a0a-108">[非同期操作のステータスのポーリング](polling-for-the-status-of-an-asynchronous-operation.md)。</span><span class="sxs-lookup"><span data-stu-id="44a0a-108">[Polling for the Status of an Asynchronous Operation](polling-for-the-status-of-an-asynchronous-operation.md).</span></span>  
  
- <span data-ttu-id="44a0a-109">[AsyncCallback デリゲートの使用による非同期操作の終了](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)。</span><span class="sxs-lookup"><span data-stu-id="44a0a-109">[Using an AsyncCallback Delegate to End an Asynchronous Operation](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44a0a-110">参照</span><span class="sxs-lookup"><span data-stu-id="44a0a-110">See also</span></span>

- [<span data-ttu-id="44a0a-111">イベント ベースの非同期パターン (EAP)</span><span class="sxs-lookup"><span data-stu-id="44a0a-111">Event-based Asynchronous Pattern (EAP)</span></span>](event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="44a0a-112">イベントベースの非同期パターンの概要</span><span class="sxs-lookup"><span data-stu-id="44a0a-112">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)
