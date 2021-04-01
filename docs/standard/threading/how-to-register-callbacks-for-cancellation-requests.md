---
description: '詳細情報: キャンセル要求のコールバックの登録'
title: キャンセル要求のコールバックを登録する
ms.date: 08/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, how to register callbacks
ms.assetid: 8838dd75-18ed-4b8b-b322-cd4531faac64
ms.openlocfilehash: a791338fc7c39e3d259f90bc4c4723079eac4236
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666772"
---
# <a name="register-callbacks-for-cancellation-requests"></a>キャンセル要求のコールバックを登録する

<xref:System.Threading.CancellationToken.IsCancellationRequested%2A> プロパティが true になったときに呼び出されるデリゲートを登録する方法について説明します。 この値は、トークンを作成したオブジェクトが <xref:System.Threading.CancellationTokenSource.Cancel%2A> を呼び出したときに、false から true に変更されます。 この方法は、統合キャンセル フレームワークをネイティブにはサポートしていない非同期操作を取り消す場合や、非同期操作の終了を待機している可能性のあるメソッドのブロックを解除する場合に使用できます。

> [!NOTE]
> [マイ コードのみ] が有効になっている場合、Visual Studio では、例外をスローする行で処理が中断され、"ユーザー コードで処理されない例外" に関するエラー メッセージが表示されることがあります。 このエラーは問題にはなりません。 <kbd>F5</kbd> キーを押して、処理が中断された箇所から続行し、以下の例に示す例外処理動作を確認できます。 Visual Studio による処理が最初のエラーで中断しないようにするには、 **[ツール] メニューの [オプション]、[デバッグ] 、[全般]** の順にクリックし、[マイ コードのみ] チェック ボックスをオフにします。

## <a name="example"></a>例

次の例では、<xref:System.Net.WebClient.CancelAsync%2A> メソッドを、キャンセル トークンを通じてキャンセルが要求されたときに呼び出されるメソッドとして登録します。

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb":::

コールバックを登録するときにキャンセルが既に要求されていても、コールバックは必ず呼び出されます。 このような場合、進行中の非同期操作がないと <xref:System.Net.WebClient.CancelAsync%2A> メソッドは何も実行しないので、このメソッドの呼び出しは常に安全です。

## <a name="see-also"></a>関連項目

- [マネージド スレッドのキャンセル](cancellation-in-managed-threads.md)
- <xref:System.Net.WebClient.DownloadStringTaskAsync(System.String)?displayProperty=nameWithType>
