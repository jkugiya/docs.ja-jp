---
title: '方法: アセンブリをグローバル アセンブリ キャッシュにインストールする'
description: アセンブリを .NET のグローバル アセンブリ キャッシュ (GAC) にインストールして、多くのアプリケーションで共有できるようにします。 Windows インストーラーまたは GAC ユーティリティを使用します。
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
- windows installer, global assembly cache
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
ms.openlocfilehash: 0034c6d7a7184e8fc3a6384c829f6bf13aad6cdd
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2021
ms.locfileid: "104653466"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a><span data-ttu-id="47338-104">方法: アセンブリをグローバル アセンブリ キャッシュにインストールする</span><span class="sxs-lookup"><span data-stu-id="47338-104">How to: Install an assembly into the global assembly cache</span></span>

<span data-ttu-id="47338-105">グローバル アセンブリ キャッシュ (GAC) には、複数のアプリケーションで共有されるアセンブリが格納されています。</span><span class="sxs-lookup"><span data-stu-id="47338-105">The global assembly cache (GAC) stores assemblies that several applications share.</span></span> <span data-ttu-id="47338-106">次のコンポーネントのいずれかを使用して、アセンブリを[グローバル アセンブリ キャッシュ](gac.md)にインストールします。</span><span class="sxs-lookup"><span data-stu-id="47338-106">Install an assembly into the [global assembly cache](gac.md) with one of the following components:</span></span>

- [<span data-ttu-id="47338-107">Windows インストーラー</span><span class="sxs-lookup"><span data-stu-id="47338-107">Windows Installer</span></span>](#windows-installer)
- [<span data-ttu-id="47338-108">グローバル アセンブリ キャッシュ ツール</span><span class="sxs-lookup"><span data-stu-id="47338-108">Global Assembly Cache tool</span></span>](#global-assembly-cache-tool)

> [!IMPORTANT]
> <span data-ttu-id="47338-109">グローバル アセンブリ キャッシュにインストールできるのは、厳密な名前のアセンブリだけです。</span><span class="sxs-lookup"><span data-stu-id="47338-109">You can install only strong-named assemblies into the global assembly cache.</span></span> <span data-ttu-id="47338-110">厳密な名前付きのアセンブリを作成する方法については、「[方法:厳密な名前でアセンブリに署名する](../../standard/assembly/sign-strong-name.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47338-110">For information about how to create a strong-named assembly, see [How to: Sign an assembly with a strong name](../../standard/assembly/sign-strong-name.md).</span></span>

## <a name="windows-installer"></a><span data-ttu-id="47338-111">Windows インストーラー</span><span class="sxs-lookup"><span data-stu-id="47338-111">Windows Installer</span></span>

<span data-ttu-id="47338-112">アセンブリをグローバル アセンブリ キャッシュに追加するための推奨する方法は、[Windows インストーラー](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache)(Windows インストール エンジン) です。</span><span class="sxs-lookup"><span data-stu-id="47338-112">[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), the Windows installation engine, is the recommended way to add assemblies to the global assembly cache.</span></span> <span data-ttu-id="47338-113">Windows インストーラーを使用すると、グローバル アセンブリ キャッシュ内のアセンブリの参照カウントが示されるなどの利点があります。</span><span class="sxs-lookup"><span data-stu-id="47338-113">Windows Installer provides reference counting of assemblies in the global assembly cache and other benefits.</span></span> <span data-ttu-id="47338-114">Windows インストーラー用のインストーラー パッケージを作成するには、[Visual Studio 2017 用 WiX Toolset 拡張機能](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension)を使用します。</span><span class="sxs-lookup"><span data-stu-id="47338-114">To create an installer package for Windows Installer, use the [WiX toolset extension for Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).</span></span>

## <a name="global-assembly-cache-tool"></a><span data-ttu-id="47338-115">グローバル アセンブリ キャッシュ ツール</span><span class="sxs-lookup"><span data-stu-id="47338-115">Global Assembly Cache tool</span></span>

<span data-ttu-id="47338-116">[.NET グローバル アセンブリ キャッシュ ユーティリティ (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) を使用して、アセンブリをグローバル アセンブリ キャッシュに追加したり、グローバル アセンブリ キャッシュの内容を表示したりできます。</span><span class="sxs-lookup"><span data-stu-id="47338-116">You can use the [.NET Global Assembly Cache utility (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add assemblies to the global assembly cache and to view the contents of the global assembly cache.</span></span>

   > [!NOTE]
   > <span data-ttu-id="47338-117">*Gacutil.exe* は、開発のみを目的としています。</span><span class="sxs-lookup"><span data-stu-id="47338-117">*Gacutil.exe* is for development purposes only.</span></span> <span data-ttu-id="47338-118">これは運用環境のアセンブリをグローバル アセンブリ キャッシュにインストールするのには使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="47338-118">Don't use it to install production assemblies into the global assembly cache.</span></span>

<span data-ttu-id="47338-119">*gacutil.exe* を使用して GAC にアセンブリをインストールするための構文は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="47338-119">The syntax for using *gacutil.exe* to install an assembly in the GAC is as follows:</span></span>

```cmd
gacutil -i <assembly name>
```

<span data-ttu-id="47338-120">このコマンドで *\<assembly name>* は、グローバル アセンブリ キャッシュにインストールされるアセンブリの名前です。</span><span class="sxs-lookup"><span data-stu-id="47338-120">In this command, *\<assembly name>* is the name of the assembly to install in the global assembly cache.</span></span>

<span data-ttu-id="47338-121">システム パスに *gacutil.exe* がない場合は、[Visual Studio 開発者コマンド プロンプトまたは Visual Studio Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell) を使用します。</span><span class="sxs-lookup"><span data-stu-id="47338-121">If *gacutil.exe* isn't in your system path, use [Visual Studio Developer Command Prompt or Visual Studio Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell).</span></span>

<span data-ttu-id="47338-122">ファイル名 *hello.dll* のアセンブリをグローバル アセンブリ キャッシュにインストールする例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="47338-122">The following example installs an assembly with the file name *hello.dll* into the global assembly cache.</span></span>

```cmd
gacutil -i hello.dll
```

> [!NOTE]
> <span data-ttu-id="47338-123">以前のバージョンの .NET Framework では、Windows のシェル拡張機能である *Shfusion.dll* により、ファイル エクスプローラーにアセンブリをドラッグしてインストールすることができました。</span><span class="sxs-lookup"><span data-stu-id="47338-123">In earlier versions of .NET Framework, the *Shfusion.dll* Windows shell extension let you install assemblies by dragging them to File Explorer.</span></span> <span data-ttu-id="47338-124">.NET Framework 4 以降では、*Shfusion.dll* は廃止されました。</span><span class="sxs-lookup"><span data-stu-id="47338-124">Beginning with .NET Framework 4, *Shfusion.dll* is obsolete.</span></span>

## <a name="see-also"></a><span data-ttu-id="47338-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="47338-125">See also</span></span>

- [<span data-ttu-id="47338-126">アセンブリとグローバル アセンブリ キャッシュの使用</span><span class="sxs-lookup"><span data-stu-id="47338-126">Work with assemblies and the global assembly cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="47338-127">方法: グローバル アセンブリ キャッシュからアセンブリを削除する</span><span class="sxs-lookup"><span data-stu-id="47338-127">How to: Remove an assembly from the global assembly cache</span></span>](how-to-remove-an-assembly-from-the-gac.md)
- [<span data-ttu-id="47338-128">Gacutil.exe (グローバル アセンブリ キャッシュ ツール)</span><span class="sxs-lookup"><span data-stu-id="47338-128">Gacutil.exe (Global Assembly Cache tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
- [<span data-ttu-id="47338-129">方法: 厳密な名前でアセンブリに署名する</span><span class="sxs-lookup"><span data-stu-id="47338-129">How to: Sign an assembly with a strong name</span></span>](../../standard/assembly/sign-strong-name.md)
