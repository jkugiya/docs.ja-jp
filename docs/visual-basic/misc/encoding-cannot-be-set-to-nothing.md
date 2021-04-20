---
description: '詳細情報: エンコードは Nothing に設定できません'
title: エンコードは Nothing に設定できません
ms.date: 07/20/2015
ms.assetid: 59f7c731-8291-4a85-bf51-c225e48cdc84
ms.openlocfilehash: 4fa9cbd9488501b5295da8d8ace41ef06a706c12
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100462996"
---
# <a name="encoding-cannot-be-set-to-nothing"></a>エンコードは Nothing に設定できません

パラメーター `encoding` が `Nothing` に設定されていますが、正しい値が必要なため、ファイルへの読み取りまたは書き込みに失敗しました。  
  
 <xref:System.Text.Encoding> は、ファイルへの書き込み時に使用するエンコードを判別するのに使用されます。 既定は UTF-8 です。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- 正しい値を `encoding` パラメーターに指定します。  
  
## <a name="see-also"></a>関連項目

- [ファイル エンコーディング](../developing-apps/programming/drives-directories-files/file-encodings.md)
- [ファイルの読み取り](../developing-apps/programming/drives-directories-files/reading-from-files.md)
- [ファイルへの書き込み](../developing-apps/programming/drives-directories-files/writing-to-files.md)
- [My.Computer.FileSystem.ReadAllText](xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A)
- [My.Computer.FileSystem.WriteAllText](xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A)
