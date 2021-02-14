---
title: タブ補完を有効にする
description: この記事では、PowerShell、Bash、zsh、fish 向けの .NET CLI のタブ補完を有効にする方法を説明します。
author: adegeo
ms.author: adegeo
ms.topic: how-to
ms.date: 11/03/2019
ms.openlocfilehash: b5b63166faa1762d9fa82a93aa70aebb33167630
ms.sourcegitcommit: 65af0f0ad316858882845391d60ef7e303b756e8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2021
ms.locfileid: "99585560"
---
# <a name="how-to-enable-tab-completion-for-the-net-cli"></a><span data-ttu-id="8c768-103">.NET CLI のタブ補完を有効にする方法</span><span class="sxs-lookup"><span data-stu-id="8c768-103">How to enable TAB completion for the .NET CLI</span></span>

<span data-ttu-id="8c768-104">**この記事の対象:** ✔️ .NET Core 2.1 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="8c768-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="8c768-105">この記事では、4 つのシェル、PowerShell、Bash、zsh、fish のタブ補完を構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8c768-105">This article describes how to configure tab completion for four shells, PowerShell, Bash, zsh, and fish.</span></span> <span data-ttu-id="8c768-106">他のシェルについては、タブ補完を構成する方法に関するシェルのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c768-106">For other shells, refer to their documentation on how to configure tab completion.</span></span>

<span data-ttu-id="8c768-107">セットアップが完了したら、シェルに `dotnet` コマンドを入力した後、TAB キーを押すと、.NET CLI のタブ補完がトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="8c768-107">Once set up, tab completion for the .NET CLI is triggered by typing a `dotnet` command in the shell, and then pressing the TAB key.</span></span> <span data-ttu-id="8c768-108">現在のコマンド ラインが `dotnet complete` コマンドに送信され、結果がシェルによって処理されます。</span><span class="sxs-lookup"><span data-stu-id="8c768-108">The current command line is sent to the `dotnet complete` command, and the results are processed by your shell.</span></span> <span data-ttu-id="8c768-109">何かを `dotnet complete` コマンドに直接送信することで、タブ補完を有効にせずに結果をテストすることができます。</span><span class="sxs-lookup"><span data-stu-id="8c768-109">You can test the results without enabling tab completion by sending something directly to the `dotnet complete` command.</span></span> <span data-ttu-id="8c768-110">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="8c768-110">For example:</span></span>

```console
> dotnet complete "dotnet a"
add
clean
--diagnostics
migrate
pack
```

<span data-ttu-id="8c768-111">そのコマンドが機能しない場合は、.NET Core 2.0 SDK 以降がインストールされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8c768-111">If that command doesn't work, make sure that .NET Core 2.0 SDK or above is installed.</span></span> <span data-ttu-id="8c768-112">インストールされているにもかかわらず、そのコマンドが機能しない場合は、`dotnet` コマンドが .NET Core 2.0 SDK 以降のバージョンに解決されることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8c768-112">If it's installed, but that command still doesn't work, make sure that the `dotnet` command resolves to a version of .NET Core 2.0 SDK and above.</span></span> <span data-ttu-id="8c768-113">`dotnet --version` コマンドを使用して、現在のパスの解決先となっている `dotnet` のバージョンを確認します。</span><span class="sxs-lookup"><span data-stu-id="8c768-113">Use the `dotnet --version` command to see what version of `dotnet` your current path is resolving to.</span></span> <span data-ttu-id="8c768-114">詳細については、「[使用する .NET のバージョンを選択する](../versions/selection.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c768-114">For more information, see [Select the .NET version to use](../versions/selection.md).</span></span>

### <a name="examples"></a><span data-ttu-id="8c768-115">使用例</span><span class="sxs-lookup"><span data-stu-id="8c768-115">Examples</span></span>

<span data-ttu-id="8c768-116">タブ補完で提供されることの例をいくつか次に示します。</span><span class="sxs-lookup"><span data-stu-id="8c768-116">Here are some examples of what tab completion provides:</span></span>

<span data-ttu-id="8c768-117">入力</span><span class="sxs-lookup"><span data-stu-id="8c768-117">Input</span></span>                                | <span data-ttu-id="8c768-118">結果</span><span class="sxs-lookup"><span data-stu-id="8c768-118">becomes</span></span>                                                                     | <span data-ttu-id="8c768-119">理由</span><span class="sxs-lookup"><span data-stu-id="8c768-119">because</span></span>
:------------------------------------|:----------------------------------------------------------------------------|:--------------------------------
`dotnet a⇥`                          | `dotnet add`                                                                 | <span data-ttu-id="8c768-120">アルファベット順では、`add` が最初のサブコマンドのため。</span><span class="sxs-lookup"><span data-stu-id="8c768-120">`add` is the first subcommand, alphabetically.</span></span>
`dotnet add p⇥`                      | `dotnet add --help`                                                          | <span data-ttu-id="8c768-121">タブ補完が部分文字列と一致しており、アルファベット順では `--help` が先になるため。</span><span class="sxs-lookup"><span data-stu-id="8c768-121">Tab completion matches substrings and `--help` comes first alphabetically.</span></span>
`dotnet add p⇥⇥`                    | `dotnet add package`                                                          | <span data-ttu-id="8c768-122">Tab キーを 2 回押すと、次の修正候補が表示されるため。</span><span class="sxs-lookup"><span data-stu-id="8c768-122">Pressing tab a second time brings up the next suggestion.</span></span>
`dotnet add package Microsoft⇥`      | `dotnet add package Microsoft.ApplicationInsights.Web`                      | <span data-ttu-id="8c768-123">結果はアルファベット順に返されるため。</span><span class="sxs-lookup"><span data-stu-id="8c768-123">Results are returned alphabetically.</span></span>
`dotnet remove reference ⇥`          | `dotnet remove reference ..\..\src\OmniSharp.DotNet\OmniSharp.DotNet.csproj` | <span data-ttu-id="8c768-124">タブ補完がプロジェクト ファイルに対応しているため。</span><span class="sxs-lookup"><span data-stu-id="8c768-124">Tab completion is project file aware.</span></span>

## <a name="powershell"></a><span data-ttu-id="8c768-125">PowerShell</span><span class="sxs-lookup"><span data-stu-id="8c768-125">PowerShell</span></span>

<span data-ttu-id="8c768-126">.NET CLI の **PowerShell** にタブ補完を追加するには、変数 `$PROFILE` に格納されているプロファイルを作成または編集します。</span><span class="sxs-lookup"><span data-stu-id="8c768-126">To add tab completion to **PowerShell** for the .NET CLI, create or edit the profile stored in the variable `$PROFILE`.</span></span> <span data-ttu-id="8c768-127">詳細については、[プロファイルの作成方法](/powershell/module/microsoft.powershell.core/about/about_profiles#how-to-create-a-profile)と[プロファイルと実行ポリシー](/powershell/module/microsoft.powershell.core/about/about_profiles#profiles-and-execution-policy)のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c768-127">For more information, see [How to create your profile](/powershell/module/microsoft.powershell.core/about/about_profiles#how-to-create-a-profile) and [Profiles and execution policy](/powershell/module/microsoft.powershell.core/about/about_profiles#profiles-and-execution-policy).</span></span>

<span data-ttu-id="8c768-128">自分のプロファイルに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="8c768-128">Add the following code to your profile:</span></span>

```powershell
# PowerShell parameter completion shim for the dotnet CLI
Register-ArgumentCompleter -Native -CommandName dotnet -ScriptBlock {
     param($commandName, $wordToComplete, $cursorPosition)
         dotnet complete --position $cursorPosition "$wordToComplete" | ForEach-Object {
            [System.Management.Automation.CompletionResult]::new($_, $_, 'ParameterValue', $_)
         }
 }
```

## <a name="bash"></a><span data-ttu-id="8c768-129">Bash</span><span class="sxs-lookup"><span data-stu-id="8c768-129">bash</span></span>

<span data-ttu-id="8c768-130">.NET CLI の **bash** シェルにタブ補完を追加するには、次のコードを `.bashrc` ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="8c768-130">To add tab completion to your **bash** shell for the .NET CLI, add the following code to your `.bashrc` file:</span></span>

```bash
# bash parameter completion for the dotnet CLI

_dotnet_bash_complete()
{
  local word=${COMP_WORDS[COMP_CWORD]}

  local completions
  completions="$(dotnet complete --position "${COMP_POINT}" "${COMP_LINE}" 2>/dev/null)"
  if [ $? -ne 0 ]; then
    completions=""
  fi

  COMPREPLY=( $(compgen -W "$completions" -- "$word") )
}

complete -f -F _dotnet_bash_complete dotnet
```

## <a name="zsh"></a><span data-ttu-id="8c768-131">zsh</span><span class="sxs-lookup"><span data-stu-id="8c768-131">zsh</span></span>

<span data-ttu-id="8c768-132">.NET CLI の **zsh** シェルにタブ補完を追加するには、次のコードを `.zshrc` ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="8c768-132">To add tab completion to your **zsh** shell for the .NET CLI, add the following code to your `.zshrc` file:</span></span>

```zsh
# zsh parameter completion for the dotnet CLI

_dotnet_zsh_complete()
{
  local completions=("$(dotnet complete "$words")")

  reply=( "${(ps:\n:)completions}" )
}

compctl -K _dotnet_zsh_complete dotnet
```

## <a name="fish"></a><span data-ttu-id="8c768-133">fish</span><span class="sxs-lookup"><span data-stu-id="8c768-133">fish</span></span>

<span data-ttu-id="8c768-134">.NET CLI の **fish** シェルにタブ補完を追加するには、次のコードを `config.fish` ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="8c768-134">To add tab completion to your **fish** shell for the .NET CLI, add the following code to your `config.fish` file:</span></span>

```fish
complete -f -c dotnet -a "(dotnet complete)"
```
