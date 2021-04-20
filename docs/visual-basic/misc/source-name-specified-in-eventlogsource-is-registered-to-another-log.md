---
description: '詳細情報: EventLogSource で指定したソース名は、EventLogName で指定したログ以外のログに登録されています'
title: EventLogSource で指定したソース名は、EventLogName で指定したログ以外のログに登録されています
ms.date: 07/20/2015
ms.assetid: 7317e100-098b-408d-86e5-7c74cf8558c7
ms.openlocfilehash: d6b9c1265276f94369d37e6ac55604b761fb9bcc
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100455458"
---
# <a name="source-name-specified-in-eventlogsource-is-registered-to-a-log-other-than-that-specified-in-eventlogname"></a>EventLogSource で指定したソース名は、EventLogName で指定したログ以外のログに登録されています

`EventLog` が、別のログに登録されているソースを参照しようとしています。 イベント ログにエントリを書き込んでいる場合は、 <xref:System.Diagnostics.EventLog.Source%2A> プロパティを指定する必要があります。 <xref:System.Diagnostics.EventLog.Source%2A> プロパティはコンポーネントを有効なエントリのソースとしてイベント ログに登録します。 1 つのソースは一度に 1 つのイベント ログにのみ関連付ける (つまり、エントリを書き込む) ことができます。  
  
 既定では、先にコンポーネントを有効なソースとして登録しないでエントリを書き込もうとした場合、 <xref:System.Diagnostics.EventLog.Source%2A> プロパティの値をソース文字列として使用して、自動的にソースがイベント ログに登録されます。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- ソースが、正しいログに登録されていることを確認します。 これを行うには、 <xref:System.Diagnostics.EventLog.CreateEventSource%2A> メソッドまたをそのオーバーロードのいずれかを使用して、コンポーネントを一意に識別する文字列をイベント ログに指定します。  
  
## <a name="see-also"></a>関連項目

- [イベント ログの管理](/previous-versions/visualstudio/visual-studio-2008/4f69axw4(v=vs.90))
- [イベント ログの参照](/previous-versions/visualstudio/visual-studio-2008/k43k9z2a(v=vs.90))
- [方法: イベント ログ エントリのソースとしてアプリケーションを追加する](/previous-versions/visualstudio/visual-studio-2008/xz73e171(v=vs.90))
- [方法: イベント ソースを削除する](/previous-versions/visualstudio/visual-studio-2008/k57466fc(v=vs.90))
