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
# <a name="calling-asynchronous-methods-using-iasyncresult"></a>IAsyncResult を使用した非同期メソッドの呼び出し

.NET ライブラリとサードパーティのクラス ライブラリの型では、アプリケーションのメイン スレッド以外のスレッドで非同期操作を実行しながら、アプリケーションを実行し続けることを許可するメソッドを提供できます。 次のセクションでは、コード例を取り上げ、<xref:System.IAsyncResult> 設計パターンを使用する非同期メソッドをさまざまな方法で呼び出します。  
  
- [非同期操作の終了によるアプリケーション実行のブロック](blocking-application-execution-by-ending-an-async-operation.md)。  
  
- [AsyncWaitHandle の使用によるアプリケーション実行のブロック](blocking-application-execution-using-an-asyncwaithandle.md)。  
  
- [非同期操作のステータスのポーリング](polling-for-the-status-of-an-asynchronous-operation.md)。  
  
- [AsyncCallback デリゲートの使用による非同期操作の終了](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)。  
  
## <a name="see-also"></a>参照

- [イベント ベースの非同期パターン (EAP)](event-based-asynchronous-pattern-eap.md)
- [イベントベースの非同期パターンの概要](event-based-asynchronous-pattern-overview.md)
