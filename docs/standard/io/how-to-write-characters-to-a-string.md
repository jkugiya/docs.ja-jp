---
description: '詳細情報: 文字列に文字を書き込む方法'
title: '方法: 文字列に文字を書き込む'
ms.date: 01/21/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data streams, writing characters to string
- writing characters to strings
- streams, writing characters to strings
- I/O [.NET], writing characters to strings
ms.assetid: 1222cbeb-0760-44bf-9888-914a2a37174b
ms.openlocfilehash: 86b19222d05e720904192d16f2082e8ae53a993f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675625"
---
# <a name="how-to-write-characters-to-a-string"></a>方法: 文字列に文字を書き込む

次のコード例では、文字列の配列から同期または非同期的に文字が書き込まれます。  
  
## <a name="example-write-characters-synchronously-in-a-console-app"></a>例: コンソール アプリで文字を同期的に書き込む  

 次の例では、<xref:System.IO.StringWriter> を使用し、5 つの文字が <xref:System.Text.StringBuilder> オブジェクトに同時に書き込まれます。
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example-write-characters-asynchronously-in-a-wpf-app"></a>例: WPF アプリで文字を非同期的に書き込む

 次の例は WPF アプリの裏側にあるコードです。 ウィンドウを読み込むと、<xref:System.Windows.Controls.TextBox> コントロールから非同期的にすべての文字を読み取り、配列に格納します。 次に、<xref:System.Windows.Controls.TextBlock> コントロールの個別の行に各文字または空白文字が非同期で書き込まれます。  
  
 [!code-csharp[StreamReaderWriter](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[StreamReaderWriter](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.IO.StringWriter>  
- <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>  
- <xref:System.Text.StringBuilder>  
- [ファイルおよびストリーム入出力](index.md)  
- [非同期ファイル I/O](asynchronous-file-i-o.md)  
- [方法: ディレクトリとファイルを列挙する](how-to-enumerate-directories-and-files.md)  
- [方法: 新しく作成されたデータ ファイルに対して読み書きする](how-to-read-and-write-to-a-newly-created-data-file.md)  
- [方法: ログ ファイルを開いて情報を追加する](how-to-open-and-append-to-a-log-file.md)  
- [方法: ファイルからテキストを読み取る](how-to-read-text-from-a-file.md)  
- [方法: テキストのファイルへの書き込み](how-to-write-text-to-a-file.md)  
- [方法: 文字列からの文字の読み取り](how-to-read-characters-from-a-string.md)
