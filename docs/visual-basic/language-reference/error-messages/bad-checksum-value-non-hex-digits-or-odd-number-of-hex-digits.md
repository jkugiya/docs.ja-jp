---
description: '詳細情報: BC42033:不適切なチェックサム値です。16 進数ではないか、または奇数の 16 進数です。'
title: 不適切なチェックサム値です。16 進数ではないか、または奇数の 16 進数です。
ms.date: 07/20/2015
f1_keywords:
- bc42033
- vbc42033
helpviewer_keywords:
- BC42033
ms.assetid: 4575554d-3615-46e4-9c6a-18e9c338e4ed
ms.openlocfilehash: 051ee0e8ec8b87be4d5feeac8298c0e7a71baea7
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102103882"
---
# <a name="bc42033-bad-checksum-value-non-hex-digits-or-odd-number-of-hex-digits"></a>BC42033:不適切なチェックサム値です。16 進数ではないか、または奇数の 16 進数です。

チェックサムの値に無効な 16 進数が含まれるか、桁数が奇数です。

 ASP.NET は Visual Basic のソース ファイル (拡張子 .vb) を生成するとき、チェックサムを計算して `#externalchecksum` で指定された隠しソース ファイルに格納します。 ユーザーが同じ目的で .vb ファイルを生成することもできますが、このプロセスは内部使用のままにしておくことをお勧めします。

 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」をご覧ください。

 **エラー ID:** BC42033

## <a name="to-correct-this-error"></a>このエラーを解決するには

1. ASP.NET が Visual Basic ソース ファイルを生成している場合は、プロジェクト ビルドを再起動してください。

2. 再起動してもこの警告が続く場合は、ASP.NET をインストールし直してもう一度ビルドしてください。

3. それでも警告が続くか、ASP.NET を使用していない場合は、状況に関する情報を収集し、マイクロソフト プロダクト サポート サービスに通知してください。

## <a name="see-also"></a>関連項目

- [ASP.NET の概要](/aspnet/overview)
- [Visual Studio フィードバック オプション](/visualstudio/ide/feedback-options)
