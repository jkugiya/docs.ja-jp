---
description: '詳細情報: -sdkpath'
title: -sdkpath
ms.date: 07/20/2015
f1_keywords:
- sdkpath
- -sdkpath
helpviewer_keywords:
- -sdkpath compiler option [Visual Basic]
- /sdkpath compiler option [Visual Basic]
- sdkpath compiler option [Visual Basic]
ms.assetid: fec8a3f1-b791-4a37-8af7-344859f8212d
ms.openlocfilehash: 3c593d56924f4b903540b2392cb86b31cae09cc8
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100473993"
---
# <a name="-sdkpath"></a><span data-ttu-id="121c8-103">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="121c8-103">-sdkpath</span></span>

<span data-ttu-id="121c8-104">mscorlib.dll および Microsoft.VisualBasic.dll の場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="121c8-104">Specifies the location of mscorlib.dll and Microsoft.VisualBasic.dll.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="121c8-105">構文</span><span class="sxs-lookup"><span data-stu-id="121c8-105">Syntax</span></span>  
  
```console  
-sdkpath:path  
```  
  
## <a name="arguments"></a><span data-ttu-id="121c8-106">引数</span><span class="sxs-lookup"><span data-stu-id="121c8-106">Arguments</span></span>  

 `path`  
 <span data-ttu-id="121c8-107">コンパイルに使用する mscorlib.dll と Microsoft.VisualBasic.dll のバージョンを格納しているディレクトリ。</span><span class="sxs-lookup"><span data-stu-id="121c8-107">The directory containing the versions of mscorlib.dll and Microsoft.VisualBasic.dll to use for compilation.</span></span> <span data-ttu-id="121c8-108">このパスは、読み込まれるまで検証されません。</span><span class="sxs-lookup"><span data-stu-id="121c8-108">This path is not verified until it is loaded.</span></span> <span data-ttu-id="121c8-109">ディレクトリ名に空白が含まれている場合は、名前を二重引用符 (" ") で囲みます。</span><span class="sxs-lookup"><span data-stu-id="121c8-109">Enclose the directory name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="121c8-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="121c8-110">Remarks</span></span>  

 <span data-ttu-id="121c8-111">このオプションにより、Visual Basic コンパイラに対して、既定以外の場所から mscorlib.dll ファイルと Microsoft.VisualBasic.dll ファイルを読み込むように指示します。</span><span class="sxs-lookup"><span data-stu-id="121c8-111">This option tells the Visual Basic compiler to load the mscorlib.dll and Microsoft.VisualBasic.dll files from a non-default location.</span></span> <span data-ttu-id="121c8-112">`-sdkpath` オプションは、[-netcf](netcf.md) と共に使用するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="121c8-112">The `-sdkpath` option was designed to be used with [-netcf](netcf.md).</span></span> <span data-ttu-id="121c8-113">.NET Compact Framework では、これらのサポート ライブラリのさまざまなバージョンを使用して、デバイスに見つからない型と言語機能の使用を回避します。</span><span class="sxs-lookup"><span data-stu-id="121c8-113">The .NET Compact Framework uses different versions of these support libraries to avoid the use of types and language features not found on the devices.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="121c8-114">`-sdkpath` オプションは、Visual Studio 開発環境からは利用できません。これはコマンド ラインからコンパイルするときにのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="121c8-114">The `-sdkpath` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="121c8-115">`-sdkpath` オプションは、Visual Basic デバイス プロジェクトが読み込まれるときに設定されます。</span><span class="sxs-lookup"><span data-stu-id="121c8-115">The `-sdkpath` option is set when a Visual Basic device project is loaded.</span></span>  
  
 <span data-ttu-id="121c8-116">`-vbruntime` コンパイラ オプションを使うと、コンパイラで Visual Basic ランタイム ライブラリを参照せずにコンパイルすることを指定できます。</span><span class="sxs-lookup"><span data-stu-id="121c8-116">You can specify that the compiler should compile without a reference to the Visual Basic Runtime Library by using the `-vbruntime` compiler option.</span></span> <span data-ttu-id="121c8-117">詳細については、「[-vbruntime](vbruntime.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="121c8-117">For more information, see [-vbruntime](vbruntime.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="121c8-118">例</span><span class="sxs-lookup"><span data-stu-id="121c8-118">Example</span></span>  

 <span data-ttu-id="121c8-119">次のコードでは、C ドライブ上の .NET Compact Framework の既定のインストール ディレクトリにある Mscorlib.dll と Microsoft.VisualBasic.dll のバージョンを使用して、.NET Compact Framework で `Myfile.vb` がコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="121c8-119">The following code compiles `Myfile.vb` with the .NET Compact Framework, using the versions of Mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the .NET Compact Framework on the C drive.</span></span> <span data-ttu-id="121c8-120">通常は、最新バージョンの .NET Compact Framework を使用します。</span><span class="sxs-lookup"><span data-stu-id="121c8-120">Typically, you would use the most recent version of the .NET Compact Framework.</span></span>  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="121c8-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="121c8-121">See also</span></span>

- [<span data-ttu-id="121c8-122">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="121c8-122">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="121c8-123">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="121c8-123">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="121c8-124">-netcf</span><span class="sxs-lookup"><span data-stu-id="121c8-124">-netcf</span></span>](netcf.md)
- [<span data-ttu-id="121c8-125">-vbruntime</span><span class="sxs-lookup"><span data-stu-id="121c8-125">-vbruntime</span></span>](vbruntime.md)
