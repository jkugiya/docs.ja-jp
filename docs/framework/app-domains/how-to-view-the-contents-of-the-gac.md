---
title: '方法: グローバル アセンブリ キャッシュの内容を表示する'
description: グローバル アセンブリ キャッシュ (GAC) ツール (gacutil.exe) を使用して .NET でグローバル アセンブリ キャッシュの内容を表示する方法について説明します。
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, viewing contents
- viewing assemblies in global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- GAC (global assembly cache), viewing contents
- list of assemblies in global assembly cache
- Global Assembly Cache tool
ms.assetid: c5f786a0-969b-4f14-9f02-e77c3384d9af
ms.openlocfilehash: a40c371e6f95f6c90ecbfbf28183226632a58e5b
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102258313"
---
# <a name="how-to-view-the-contents-of-the-global-assembly-cache"></a><span data-ttu-id="1d561-103">方法: グローバル アセンブリ キャッシュの内容を表示する</span><span class="sxs-lookup"><span data-stu-id="1d561-103">How to: View the contents of the global assembly cache</span></span>

<span data-ttu-id="1d561-104">[グローバル アセンブリ キャッシュ ツール (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) を使用して、グローバル アセンブリ キャッシュ (GAC) の内容を表示できます。</span><span class="sxs-lookup"><span data-stu-id="1d561-104">Use the [global assembly cache tool (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to view the contents of the global assembly cache (GAC).</span></span>

## <a name="view-the-assemblies-in-the-gac"></a><span data-ttu-id="1d561-105">GAC 内のアセンブリを表示する</span><span class="sxs-lookup"><span data-stu-id="1d561-105">View the assemblies in the GAC</span></span>

<span data-ttu-id="1d561-106">グローバル アセンブリ キャッシュ内のアセンブリの一覧を表示するには、[開発者向けのコマンドライン シェル](/visualstudio/ide/reference/command-prompt-powershell)を開き、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="1d561-106">To view a list of the assemblies in the global assembly cache, open a [command-line shell for developers](/visualstudio/ide/reference/command-prompt-powershell), and then enter the following command:</span></span>

```shell
gacutil -l
```

<span data-ttu-id="1d561-107">- または -</span><span class="sxs-lookup"><span data-stu-id="1d561-107">-or-</span></span>

```shell
gacutil /l
```

> [!NOTE]
> <span data-ttu-id="1d561-108">以前のバージョンの .NET Framework では、Windows のシェル拡張機能である [Shfusion.dll](/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) により、エクスプローラーでグローバル アセンブリ キャッシュを表示することができました。</span><span class="sxs-lookup"><span data-stu-id="1d561-108">In earlier versions of .NET Framework, the [Shfusion.dll](/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) Windows shell extension enabled you to view the global assembly cache in File Explorer.</span></span> <span data-ttu-id="1d561-109">.NET Framework 4 以降では、Shfusion.dll は廃止されました。</span><span class="sxs-lookup"><span data-stu-id="1d561-109">Beginning with .NET Framework 4, Shfusion.dll is obsolete.</span></span>

## <a name="see-also"></a><span data-ttu-id="1d561-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="1d561-110">See also</span></span>

- [<span data-ttu-id="1d561-111">アセンブリとグローバル アセンブリ キャッシュの使用</span><span class="sxs-lookup"><span data-stu-id="1d561-111">Working with Assemblies and the Global Assembly Cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="1d561-112">Gacutil.exe (グローバル アセンブリ キャッシュ ツール)</span><span class="sxs-lookup"><span data-stu-id="1d561-112">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
