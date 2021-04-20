---
description: '詳細情報: ログのストリームを取得できません'
title: ログのストリームを取得できません
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_ExhaustedPossibleStreamNames
ms.assetid: 33994f52-8efb-4790-a459-033e5c1db632
ms.openlocfilehash: 6eda12eb4dc2b3cf303e543a66e1f2f7d739eb6b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100455276"
---
# <a name="unable-to-obtain-a-stream-for-the-log"></a>ログのストリームを取得できません

ログのストリームを取得できません。 \<name> に基づく、可能性のあるファイル名は既に使用されています。  
  
 \<name> に基づく、可能性のあるすべてのログ ファイル名が既に使用されているため、<xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> クラスは新しいログ ファイルを作成できませんでした。  
  
 ログ ファイルが多すぎる場合、アプリケーションにアーキテクチャの問題がある可能性があります。 詳細については、 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> クラスのドキュメントを参照してください。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> プロパティを <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> または <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> に設定して、ログ ファイル名に日付スタンプを含めます。  
  
2. 既存のログをアーカイブし、それらをコンピューターから削除して、 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> オブジェクトが新しいログを作成できるようにします。  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>
- [My.Application.Log](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
- [My.Application.Info.DirectoryPath](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
