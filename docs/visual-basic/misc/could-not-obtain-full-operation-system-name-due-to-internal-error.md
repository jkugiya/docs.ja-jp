---
description: '詳細情報: 内部エラーのために完全な運用システム名を取得できませんでした'
title: 内部エラーのために完全な運用システム名を取得できませんでした
ms.date: 07/20/2015
f1_keywords:
- vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
ms.openlocfilehash: d274a08728b084b21309862de69e2fded5c164da
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100463495"
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a>内部エラーのために完全な運用システム名を取得できませんでした

内部エラーのために完全な運用システム名を取得できませんでした。 これは、現在のコンピューターに WMI が存在しないことが原因である場合があります。  
  
 `My.Computer.Info.OSFullName` プロパティの呼び出しに失敗しました。 このエラーの考えられる原因は、Windows Management Instrumentation (WMI) が、現在のコンピューターにインストールされていないことです。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. `Try...Catch` プロパティの呼び出しの周囲に `My.Computer.Info.OSFullName` ブロックを追加します。  
  
2. WMI およびそのインストール方法の詳細については、 にアクセスし、「Windows Management Instrumentation Core」を検索します。  
  
## <a name="see-also"></a>関連項目

- [My.Computer.Info.OSFullName](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)
- [.NET での例外の処理とスロー](../../standard/exceptions/index.md)
- [Try...Catch...Finally ステートメント](../language-reference/statements/try-catch-finally-statement.md)
