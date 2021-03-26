---
description: '詳細情報: BC30145:アセンブリを作成できません : <error message>'
title: 'アセンブリを作成できません : <error message>'
ms.date: 08/14/2018
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
ms.openlocfilehash: 2ba476b39b6aa441d8778ee0618dcc3dcf3f7ac8
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2021
ms.locfileid: "104653283"
---
# <a name="bc30145-unable-to-emit-assembly-error-message"></a>BC30145:アセンブリを作成できません : \<error message>

Visual Basic コンパイラは、マニフェストを伴うアセンブリを生成するためにアセンブリ リンカー (*Al.exe*、Alink とも呼ばれます) を呼び出し、アセンブリを作成する出力段階でリンカーからエラーが報告されます。

**エラー ID:** BC30145

## <a name="to-correct-this-error"></a>このエラーを解決するには

1. 引用符で囲まれたエラー メッセージを調べ、トピック「[Al.exe](../../../framework/tools/al-exe-assembly-linker.md)」でより詳細な説明とアドバイスを参照します。

2. [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) または [Sn.exe (厳密名ツール)](../../../framework/tools/sn-exe-strong-name-tool.md) を使用して、手動でアセンブリに署名してみてください。

3. エラーが続く場合は、状況に関する情報を収集し、マイクロソフト プロダクト サポート サービスに通知してください。

### <a name="to-sign-the-assembly-manually"></a>アセンブリを手動で署名するには

1. [Sn.exe (厳密名ツール)](../../../framework/tools/sn-exe-strong-name-tool.md) を使用して、公開キーと秘密キーのペア ファイルを作成します。

   このファイルは *.snk* の拡張子を持ちます。

2. エラーが発生している COM 参照をプロジェクトから削除します。

3. [Visual Studio 開発者コマンド プロンプトまたは Visual Studio Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell) を開きます。

4. アセンブリ ラッパーを格納するディレクトリに、ディレクトリを変更します。

5. 次のコマンドを入力します。

    ```cmd
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>
    ```

   入力できる実際のコマンドの例を次に示します。

    ```cmd
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"
    ```

   > [!TIP]
   > パスやファイルに空白が含まれている場合には、二重引用符を使用します。

6. Visual Studio で、作成したファイルに .NET アセンブリへの参照を追加します。

## <a name="see-also"></a>関連項目

- [Al.exe](../../../framework/tools/al-exe-assembly-linker.md)
- [Sn.exe (厳密名ツール)](../../../framework/tools/sn-exe-strong-name-tool.md)
- [方法: 公開キーと秘密キーのキー ペアを作成する](../../../standard/assembly/create-public-private-key-pair.md)
- [Visual Studio フィードバック オプション](/visualstudio/ide/feedback-options)
