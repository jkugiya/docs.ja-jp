---
ms.openlocfilehash: 3275865cf7f4669ba7deaacea320136d02f64dda
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99804236"
---

<span data-ttu-id="8aa4b-101">"**パッケージ {dotnet-package} が見つかりません**" や "**一部のパッケージをインストールできませんでした**" のようなエラー メッセージが表示される場合は、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="8aa4b-101">If you receive an error message similar to **Unable to locate package {dotnet-package}** or **Some packages could not be installed**, run the following commands.</span></span>

<span data-ttu-id="8aa4b-102">次の一連のコマンドには、2 つのプレースホルダーがあります。</span><span class="sxs-lookup"><span data-stu-id="8aa4b-102">There are two placeholders in the following set of commands.</span></span>

- `{dotnet-package}`\
<span data-ttu-id="8aa4b-103">これは、`aspnetcore-runtime-3.1` など、インストールする .NET パッケージを表します。</span><span class="sxs-lookup"><span data-stu-id="8aa4b-103">This represents the .NET package you're installing, such as `aspnetcore-runtime-3.1`.</span></span> <span data-ttu-id="8aa4b-104">これは、次の `sudo apt-get install` コマンドで使用されます。</span><span class="sxs-lookup"><span data-stu-id="8aa4b-104">This is used in the following `sudo apt-get install` command.</span></span>

- `{os-version}`\
<span data-ttu-id="8aa4b-105">これは、使用しているディストリビューションのバージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="8aa4b-105">This represents the distribution version you're on.</span></span> <span data-ttu-id="8aa4b-106">これは、次の `wget` コマンドで使用されます。</span><span class="sxs-lookup"><span data-stu-id="8aa4b-106">This is used in the `wget` command below.</span></span> <span data-ttu-id="8aa4b-107">ディストリビューションのバージョンは、Ubuntu での `20.04` や Debian での `10` などの数値です。</span><span class="sxs-lookup"><span data-stu-id="8aa4b-107">The distribution version is the numerical value, such as `20.04` on Ubuntu or `10` on Debian.</span></span>

<span data-ttu-id="8aa4b-108">まず、パッケージ リストを消去してみてください。</span><span class="sxs-lookup"><span data-stu-id="8aa4b-108">First, try purging the package list:</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
```

<span data-ttu-id="8aa4b-109">次に、.NET を再度インストールしてください。</span><span class="sxs-lookup"><span data-stu-id="8aa4b-109">Then, try to install .NET again.</span></span> <span data-ttu-id="8aa4b-110">それでも解決しない場合は、次のコマンドを使用して手動インストールを実行できます。</span><span class="sxs-lookup"><span data-stu-id="8aa4b-110">If that doesn't work, you can run a manual install with the following commands:</span></span>
