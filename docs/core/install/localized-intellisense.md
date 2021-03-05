---
title: ローカライズされた IntelliSense ファイルをインストールする
description: Visual Studio で .NET 5+ プロジェクト (.NET Core を含む) のローカライズされた IntelliSense ファイルを使用するように開発用マシンを設定する方法について説明します。
ms.date: 11/06/2020
ms.openlocfilehash: febd748429dd3a2e13460354eb7402d25515f934
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105207"
---
# <a name="how-to-install-localized-intellisense-files-for-net"></a>.NET のローカライズされた IntelliSense ファイルをインストールする方法

[IntelliSense](/visualstudio/ide/using-intellisense) は、Visual Studio などのさまざまな統合開発環境 (IDE) で使用できるコード補完機能です。 既定では、.NET プロジェクトを開発している場合、SDK には、英語版の IntelliSense ファイルのみが含まれます。 この記事では、以下の内容について説明しています。

- ローカライズ版のファイルをインストールする方法。
- 別の言語を使用するように Visual Studio のインストールを変更する方法。

## <a name="prerequisites"></a>前提条件

- [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet) 以降のバージョン ([.NET 5 SDK](https://dotnet.microsoft.com/download/dotnet/5.0) など)。
- [Visual Studio 2019 バージョン 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) 以降のバージョン。

## <a name="download-and-install-the-localized-intellisense-files"></a>ローカライズされた IntelliSense ファイルをダウンロードしてインストールする

> [!IMPORTANT]
> この手順では、IntelliSense ファイルを .NET のインストール フォルダーにコピーするための管理者権限が必要です。

1. [IntelliSense ファイルのダウンロード](https://dotnet.microsoft.com/download/intellisense)のページに移動します。

1. 使用したい言語とバージョンの IntelliSense ファイルをダウンロードします。

1. .zip ファイルの内容を抽出します。

1. .NET の IntelliSense フォルダーに移動します。

   1. .NET のインストール フォルダーに移動します。 既定では *%ProgramFiles%\dotnet\packs* の下にあります。
   1. IntelliSense をインストールする SDK を選択し、関連付けられているパスに移動します。 次のオプションがあります。

      | SDK の種類              | Path                               |
      |-----------------------|------------------------------------|
      | .NET 5+ および .NET Core | *Microsoft.NETCore.App.Ref*        |
      | Windows デスクトップ       | *Microsoft.WindowsDesktop.App.Ref* |
      | .NET Standard         | *NETStandard.Library.Ref*          |

   1. ローカライズされた IntelliSense をインストールするバージョンに移動します。 たとえば、*5.0.0* です。
   1. *ref* フォルダーを開きます。
   1. モニカー フォルダーを開きます。 たとえば、*net5.0* です。

   したがって、移動先の完全なパスは *C:\Program Files\dotnet\packs\Microsoft.NETCore.App.Ref\5.0.0\ref\net5.0* のようになります。

1. 開いたばかりのモニカー フォルダー内にサブフォルダーを作成します。 フォルダーの名前は、使用する言語を示します。 次の表に、さまざまなオプションを示します。

   | 言語              | [フォルダー名] |
   | --------------------- | ----------- |
   | ポルトガル語 (ブラジル)  | *pt-br*     |
   | 簡体中国語  | *zh-hans*   |
   | 繁体中国語 | *zh-hant*   |
   | フランス語                | *fr*        |
   | German                | *de*        |
   | イタリア語               | *it*        |
   | 日本語              | *ja*        |
   | 韓国語                | *ko*        |
   | ロシア語               | *ru*        |
   | スペイン語               | *es*        |

1. ステップ 3 で抽出した *.xml* ファイルをこの新しいフォルダーにコピーします。 *.xml* ファイルは SDK フォルダーごとに分割されているため、ステップ 4 で選択したものと一致する SDK にコピーします。

## <a name="modify-visual-studio-language"></a>Visual Studio の言語を変更する

Visual Studio で IntelliSense に別の言語を使用するには、適切な言語パックをインストールします。 これは[インストール時](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional)に行うことも、後から Visual Studio のインストールを変更して行うこともできます。 Visual Studio が既に選択した言語に構成されている場合は、IntelliSense のインストールの準備ができています。

### <a name="install-the-language-pack"></a>言語パックをインストールする

設定時に目的の言語パックをインストールしなかった場合は、次のようにして Visual Studio を更新して言語パックをインストールします。

> [!IMPORTANT]
> Visual Studio をインストール、更新、または変更するには、管理者のアクセス許可を持つアカウントでログオンする必要があります。 詳細については、「[ユーザー アクセス許可と Visual Studio](/visualstudio/ide/user-permissions-and-visual-studio)」を参照してください。

1. コンピューター上で Visual Studio インストーラーを見つけます。

   たとえば、Windows 10 を実行しているコンピューター上で、 **[スタート]** を選択し、**Visual Studio インストーラー** としてリスト表示される **V** の文字までスクロールします。

   ![Windows から Visual Studio インストーラーを開く](./media/localized-intellisense/vs-installer-windows-start.png)

   > [!NOTE]
   > また、Visual Studio インストーラーは次の場所にもあります。
   >
   > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

   続行する前に、インストーラーの更新が必要な場合があります。 その場合は、画面の指示に従います。

1. インストーラーで、言語パックを追加する Visual Studio のエディションを探し、 **[変更]** を選択します。

   ![Visual Studio の更新または変更](./media/localized-intellisense/vs-installer-modify.png)

   > [!IMPORTANT]
   > **[変更]** ボタンが表示されず、代わりに **[更新]** ボタンが表示されている場合は、インストールを変更する前に Visual Studio を更新する必要があります。
   > 更新が完了すると、 **[変更]** ボタンが表示されます。

1. **[言語パック]** タブで、インストールまたはアンインストールする言語を選択または選択解除します。

   ![Visual Studio の [言語パック] タブ](./media/localized-intellisense/vs-modify-language-packs.png)

1. **[変更]** を選択します。 更新が開始されます。

### <a name="modify-language-settings-in-visual-studio"></a>Visual Studio の言語設定を変更する

目的の言語パックをインストールしたら、別の言語を使用するように Visual Studio の設定を変更します。

1. Visual Studio を開きます。

1. スタート ウィンドウで、 **[コードなしで続行]** を選択します。

1. メニュー バーで、 **[ツール]**  >  **[オプション]** の順に選択します。 [オプション] ダイアログが表示されます。

1. **[環境]** ノードで、 **[国際対応の設定]** を選択します。

1. **[言語]** ドロップダウンで目的の言語を選択します。 **[OK]** をクリックします。

1. 変更を有効にするために Visual Studio を再起動する必要があることを示すダイアログが表示されます。 **[OK]** をクリックします。

1. Visual Studio を再起動します。

その後、インストールした IntelliSense ファイルのバージョンを対象とする .NET プロジェクトを開くと、IntelliSense が期待どおりに動作するようになります。

## <a name="see-also"></a>参照

- [Visual Studio での IntelliSense](/visualstudio/ide/using-intellisense)
