---
description: '詳細情報: -win32manifest (Visual Basic)'
title: -win32manifest
ms.date: 03/13/2018
helpviewer_keywords:
- /win32manifest compiler option [Visual Basic]
- win32manifest compiler option [Visual Basic]
- -win32manifest compiler option [Visual Basic]
ms.assetid: 9e3191b4-90db-41c8-966a-28036fd20005
ms.openlocfilehash: d8b674d3eb101fdaa05cca7fa67ba0a43999ca37
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100433511"
---
# <a name="-win32manifest-visual-basic"></a><span data-ttu-id="eba7a-103">-win32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eba7a-103">-win32manifest (Visual Basic)</span></span>

<span data-ttu-id="eba7a-104">プロジェクトのポータブル実行可能 (PE) ファイルに埋め込まれる、ユーザー定義の Win32 アプリケーション マニフェスト ファイルを識別します。</span><span class="sxs-lookup"><span data-stu-id="eba7a-104">Identifies a user-defined Win32 application manifest file to be embedded into a project's portable executable (PE) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eba7a-105">構文</span><span class="sxs-lookup"><span data-stu-id="eba7a-105">Syntax</span></span>  
  
```console  
-win32manifest: fileName  
```  
  
## <a name="arguments"></a><span data-ttu-id="eba7a-106">引数</span><span class="sxs-lookup"><span data-stu-id="eba7a-106">Arguments</span></span>  
  
|<span data-ttu-id="eba7a-107">用語</span><span class="sxs-lookup"><span data-stu-id="eba7a-107">Term</span></span>|<span data-ttu-id="eba7a-108">定義</span><span class="sxs-lookup"><span data-stu-id="eba7a-108">Definition</span></span>|  
|---|---|  
|`fileName`|<span data-ttu-id="eba7a-109">カスタム マニフェスト ファイルのパス。</span><span class="sxs-lookup"><span data-stu-id="eba7a-109">The path of the custom manifest file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eba7a-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="eba7a-110">Remarks</span></span>  

 <span data-ttu-id="eba7a-111">既定では、asInvoker の要求実行レベルを指定するアプリケーション マニフェストが、Visual Basic コンパイラによって埋め込まれます。</span><span class="sxs-lookup"><span data-stu-id="eba7a-111">By default, the Visual Basic compiler embeds an application manifest that specifies a requested execution level of asInvoker.</span></span> <span data-ttu-id="eba7a-112">マニフェストは、実行可能ファイルがビルドされたのと同じフォルダー (Visual Studio を使用している場合、通常は bin\Debug または bin\Release フォルダー) に作成されます。</span><span class="sxs-lookup"><span data-stu-id="eba7a-112">It creates the manifest in the same folder in which the executable file is built, typically the bin\Debug or bin\Release folder when you use Visual Studio.</span></span> <span data-ttu-id="eba7a-113">カスタム マニフェストを指定する (たとえば、highestAvailable または requireAdministrator の要求実行レベルを指定する) 場合は、このオプションを使用してファイルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="eba7a-113">If you want to supply a custom manifest, for example to specify a requested execution level of highestAvailable or requireAdministrator, use this option to specify the name of the file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eba7a-114">このオプションと [-win32resource](win32resource.md) オプションは、相互に排他的です。</span><span class="sxs-lookup"><span data-stu-id="eba7a-114">This option and the [-win32resource](win32resource.md) option are mutually exclusive.</span></span> <span data-ttu-id="eba7a-115">同じコマンド ラインで両方のオプションを使おうすると、ビルド エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="eba7a-115">If you try to use both options in the same command line, you will get a build error.</span></span>  
  
 <span data-ttu-id="eba7a-116">アプリケーション マニフェストを持たないアプリケーションは、要求実行レベルを指定した場合、Windows Vista のユーザー アカウント制御機能によって、ファイルまたはレジストリの仮想化の対象となります。</span><span class="sxs-lookup"><span data-stu-id="eba7a-116">An application that has no application manifest that specifies a requested execution level will be subject to file/registry virtualization under the User Account Control feature in Windows Vista.</span></span> <span data-ttu-id="eba7a-117">仮想化について詳しくは、「[Windows Vista の ClickOnce 配置](/visualstudio/deployment/clickonce-deployment-on-windows-vista)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eba7a-117">For more information about virtualization, see [ClickOnce Deployment on Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span></span>  
  
 <span data-ttu-id="eba7a-118">次の条件のいずれかに該当する場合、アプリケーションは仮想化の対象となります。</span><span class="sxs-lookup"><span data-stu-id="eba7a-118">Your application will be subject to virtualization if either of the following conditions is true:</span></span>  
  
1. <span data-ttu-id="eba7a-119">`-nowin32manifest` オプションを使用していて、後のビルド手順でマニフェストを提供していないか、`-win32resource` オプションを使用して Windows リソース (.res) ファイルの一部としていない。</span><span class="sxs-lookup"><span data-stu-id="eba7a-119">You use the `-nowin32manifest` option and you do not provide a manifest in a later build step or as part of a Windows Resource (.res) file by using the `-win32resource` option.</span></span>  
  
2. <span data-ttu-id="eba7a-120">要求実行レベルが指定されていないカスタム マニフェストを提供している。</span><span class="sxs-lookup"><span data-stu-id="eba7a-120">You provide a custom manifest that does not specify a requested execution level.</span></span>  
  
 <span data-ttu-id="eba7a-121">Visual Studio は、既定の .manifest ファイルを作成し、それを実行可能ファイルと一緒にデバッグ ディレクトリとリリース ディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="eba7a-121">Visual Studio creates a default .manifest file and stores it in the debug and release directories alongside the executable file.</span></span> <span data-ttu-id="eba7a-122">既定の app.manifest ファイルは、プロジェクト デザイナーの **[アプリケーション]** タブにある **[UAC 設定の表示]** をクリックして表示または編集することができます。</span><span class="sxs-lookup"><span data-stu-id="eba7a-122">You can view or edit the default app.manifest file by clicking **View UAC Settings** on the **Application** tab in the Project Designer.</span></span> <span data-ttu-id="eba7a-123">詳細については、「[[アプリケーション] ページ (プロジェクト デザイナー) (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eba7a-123">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="eba7a-124">アプリケーション マニフェストは、カスタムのビルド後手順として提供するか、`-nowin32manifest` オプションを使用して、Win32 リソース ファイルの一部として提供できます。</span><span class="sxs-lookup"><span data-stu-id="eba7a-124">You can provide the application manifest as a custom post-build step or as part of a Win32 resource file by using the `-nowin32manifest` option.</span></span> <span data-ttu-id="eba7a-125">アプリケーションを Windows Vista でファイルまたはレジストリの仮想化の対象にする場合は、これと同じオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="eba7a-125">Use that same option if you want your application to be subject to file or registry virtualization on Windows Vista.</span></span> <span data-ttu-id="eba7a-126">これにより、コンパイラで PE ファイル内に既定のマニフェストが作成されて埋め込まれなくなります。</span><span class="sxs-lookup"><span data-stu-id="eba7a-126">This will prevent the compiler from creating and embedding a default manifest in the PE file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eba7a-127">例</span><span class="sxs-lookup"><span data-stu-id="eba7a-127">Example</span></span>  

 <span data-ttu-id="eba7a-128">次の例は、Visual Basic コンパイラによって PE に挿入される既定のマニフェストを示しています。</span><span class="sxs-lookup"><span data-stu-id="eba7a-128">The following example shows the default manifest that the Visual Basic compiler inserts into a PE.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eba7a-129">コンパイラによって、標準のアプリケーション名 MyApplication.app がマニフェスト XML に挿入されます。</span><span class="sxs-lookup"><span data-stu-id="eba7a-129">The compiler inserts a standard application name MyApplication.app into the manifest XML.</span></span> <span data-ttu-id="eba7a-130">これは、アプリケーションを Windows Server 2003 Service Pack 3 で実行できるようにするための回避策です。</span><span class="sxs-lookup"><span data-stu-id="eba7a-130">This is a workaround to enable applications to run on Windows Server 2003 Service Pack 3.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
  <assemblyIdentity version="1.0.0.0" name="MyApplication.app"/>  
  <trustInfo xmlns="urn:schemas-microsoft-com:asm.v2">  
    <security>  
      <requestedPrivileges xmlns="urn:schemas-microsoft-com:asm.v3">  
        <requestedExecutionLevel level="asInvoker"/>  
      </requestedPrivileges>  
    </security>  
  </trustInfo>  
</assembly>  
```  
  
## <a name="see-also"></a><span data-ttu-id="eba7a-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="eba7a-131">See also</span></span>

- [<span data-ttu-id="eba7a-132">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="eba7a-132">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="eba7a-133">-nowin32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eba7a-133">-nowin32manifest (Visual Basic)</span></span>](nowin32manifest.md)
