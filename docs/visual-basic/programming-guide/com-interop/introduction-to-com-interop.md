---
description: '詳細情報: COM 相互運用の概要 (Visual Basic)'
title: COM 相互運用の概要
ms.date: 07/20/2015
helpviewer_keywords:
- interop assemblies
- COM interop [Visual Basic], about COM interop
ms.assetid: 8bd62e68-383d-407f-998b-29aa0ce0fd67
ms.openlocfilehash: 86741958e63263f0788384a1261063d71d16df16
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100480792"
---
# <a name="introduction-to-com-interop-visual-basic"></a><span data-ttu-id="bfaab-103">COM 相互運用の概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bfaab-103">Introduction to COM Interop (Visual Basic)</span></span>

<span data-ttu-id="bfaab-104">コンポーネント オブジェクト モデル (COM) により、オブジェクトがその機能を他のコンポーネントに公開し、アプリケーションをホストできます。</span><span class="sxs-lookup"><span data-stu-id="bfaab-104">The Component Object Model (COM) lets an object expose its functionality to other components and to host applications.</span></span> <span data-ttu-id="bfaab-105">COM オブジェクトは長年にわたって Windows プログラミングの基本となってきましたが、共通言語ランタイム (CLR) 用に設計されたアプリケーションには多くの利点があります。</span><span class="sxs-lookup"><span data-stu-id="bfaab-105">While COM objects have been fundamental to Windows programming for many years, applications designed for the common language runtime (CLR) offer many advantages.</span></span>  
  
 <span data-ttu-id="bfaab-106">.NET Framework アプリケーションによって、最終的に COM で開発されたものが置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="bfaab-106">.NET Framework applications will eventually replace those developed with COM.</span></span> <span data-ttu-id="bfaab-107">それまでは、Visual Studio を使用して COM オブジェクトを使用するか、作成する必要がある可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bfaab-107">Until then, you may have to use or create COM objects by using Visual Studio.</span></span> <span data-ttu-id="bfaab-108">COM との相互運用性、つまり *COM 相互運用* により、自分のペースで .NET Framework に移行しながら、既存の COM オブジェクトを使用できます。</span><span class="sxs-lookup"><span data-stu-id="bfaab-108">Interoperability with COM, or *COM interop*, enables you to use existing COM objects while transitioning to the .NET Framework at your own pace.</span></span>  
  
 <span data-ttu-id="bfaab-109">.NET Framework を使用して COM コンポーネントを作成することにより、登録を必要としない COM 相互運用を使用できます。</span><span class="sxs-lookup"><span data-stu-id="bfaab-109">By using the .NET Framework to create COM components, you can use registration-free COM interop.</span></span> <span data-ttu-id="bfaab-110">これにより、コンピューターに複数のバージョンがインストールされている場合に有効にする DLL バージョンを制御でき、エンド ユーザーは、XCOPY または FTP を使用して、アプリケーションを、それが実行可能なコンピューター上の適切なディレクトリにコピーできます。</span><span class="sxs-lookup"><span data-stu-id="bfaab-110">This lets you control which DLL version is enabled when more than one version is installed on a computer, and lets end users use XCOPY or FTP to copy your application to an appropriate directory on their computer where it can be run.</span></span> <span data-ttu-id="bfaab-111">詳細については、「[登録を必要としない COM 相互運用機能](../../../framework/interop/registration-free-com-interop.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bfaab-111">For more information, see [Registration-Free COM Interop](../../../framework/interop/registration-free-com-interop.md).</span></span>  
  
## <a name="managed-code-and-data"></a><span data-ttu-id="bfaab-112">マネージド コードとデータ</span><span class="sxs-lookup"><span data-stu-id="bfaab-112">Managed Code and Data</span></span>  

 <span data-ttu-id="bfaab-113">.NET Framework 用に開発されたコードは *マネージド コード* と呼ばれ、CLR によって使用されるメタデータが含まれます。</span><span class="sxs-lookup"><span data-stu-id="bfaab-113">Code developed for the .NET Framework is referred to as *managed code*, and contains metadata that is used by the CLR.</span></span> <span data-ttu-id="bfaab-114">.NET Framework アプリケーションによって使用されるデータは、*マネージド データ* と呼ばれます。ランタイムによって、メモリの割り当てや解放、型チェックの実行などのデータ関連タスクが管理されるためです。</span><span class="sxs-lookup"><span data-stu-id="bfaab-114">Data used by .NET Framework applications is called *managed data* because the runtime manages data-related tasks such as allocating and reclaiming memory and performing type checking.</span></span> <span data-ttu-id="bfaab-115">既定で Visual Basic .NET ではマネージド コードとデータが使用されますが、相互運用アセンブリを使用して、COM オブジェクトのアンマネージド コードとデータにアクセスできます (このページで後述しています)。</span><span class="sxs-lookup"><span data-stu-id="bfaab-115">By default, Visual Basic .NET uses managed code and data, but you can access the unmanaged code and data of COM objects using interop assemblies (described later on this page).</span></span>  
  
## <a name="assemblies"></a><span data-ttu-id="bfaab-116">アセンブリ</span><span class="sxs-lookup"><span data-stu-id="bfaab-116">Assemblies</span></span>  

 <span data-ttu-id="bfaab-117">アセンブリは、.NET Framework アプリケーションの主な構成要素です。</span><span class="sxs-lookup"><span data-stu-id="bfaab-117">An assembly is the primary building block of a .NET Framework application.</span></span> <span data-ttu-id="bfaab-118">これは、1 つ以上のファイルを含む 1 つの実装単位として、ビルド、バージョン管理、およびデプロイされる機能のコレクションです。</span><span class="sxs-lookup"><span data-stu-id="bfaab-118">It is a collection of functionality that is built, versioned, and deployed as a single implementation unit containing one or more files.</span></span> <span data-ttu-id="bfaab-119">各アセンブリには、アセンブリ マニフェストが含まれます。</span><span class="sxs-lookup"><span data-stu-id="bfaab-119">Each assembly contains an assembly manifest.</span></span>  
  
## <a name="type-libraries-and-assembly-manifests"></a><span data-ttu-id="bfaab-120">タイプ ライブラリとアセンブリ マニフェスト</span><span class="sxs-lookup"><span data-stu-id="bfaab-120">Type Libraries and Assembly Manifests</span></span>  

 <span data-ttu-id="bfaab-121">タイプ ライブラリは、メンバー名やデータ型など、COM オブジェクトの特性を記述します。</span><span class="sxs-lookup"><span data-stu-id="bfaab-121">Type libraries describe characteristics of COM objects, such as member names and data types.</span></span> <span data-ttu-id="bfaab-122">アセンブリ マニフェストは、.NET Framework アプリケーションに対して同じ機能を実行します。</span><span class="sxs-lookup"><span data-stu-id="bfaab-122">Assembly manifests perform the same function for .NET Framework applications.</span></span> <span data-ttu-id="bfaab-123">それらには、次に関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="bfaab-123">They include information about the following:</span></span>  
  
- <span data-ttu-id="bfaab-124">アセンブリ ID、バージョン、カルチャ、およびデジタル署名。</span><span class="sxs-lookup"><span data-stu-id="bfaab-124">Assembly identity, version, culture, and digital signature.</span></span>  
  
- <span data-ttu-id="bfaab-125">アセンブリ実装を構成するファイル。</span><span class="sxs-lookup"><span data-stu-id="bfaab-125">Files that make up the assembly implementation.</span></span>  
  
- <span data-ttu-id="bfaab-126">アセンブリを構成する型とリソース。</span><span class="sxs-lookup"><span data-stu-id="bfaab-126">Types and resources that make up the assembly.</span></span> <span data-ttu-id="bfaab-127">これには、そこからエクスポートされたものも含まれます。</span><span class="sxs-lookup"><span data-stu-id="bfaab-127">This includes those that are exported from it.</span></span>  
  
- <span data-ttu-id="bfaab-128">他のアセンブリに対するコンパイル時の依存関係。</span><span class="sxs-lookup"><span data-stu-id="bfaab-128">Compile-time dependencies on other assemblies.</span></span>  
  
- <span data-ttu-id="bfaab-129">アセンブリを正常に実行するために必要なアクセス許可。</span><span class="sxs-lookup"><span data-stu-id="bfaab-129">Permissions required for the assembly to run correctly.</span></span>  
  
 <span data-ttu-id="bfaab-130">アセンブリとアセンブリ マニフェストの詳細については、「[.NET のアセンブリ](../../../standard/assembly/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bfaab-130">For more information about assemblies and assembly manifests, see [Assemblies in .NET](../../../standard/assembly/index.md).</span></span>  
  
### <a name="importing-and-exporting-type-libraries"></a><span data-ttu-id="bfaab-131">タイプ ライブラリのインポートとエクスポート</span><span class="sxs-lookup"><span data-stu-id="bfaab-131">Importing and Exporting Type Libraries</span></span>  

 <span data-ttu-id="bfaab-132">Visual Studio には、Tlbimp というユーティリティが含まれており、これにより、タイプ ライブラリから .NET Framework アプリケーションに情報をインポートできます。</span><span class="sxs-lookup"><span data-stu-id="bfaab-132">Visual Studio contains a utility, Tlbimp, that lets you import information from a type library into a .NET Framework application.</span></span> <span data-ttu-id="bfaab-133">アセンブリからタイプ ライブラリを生成するには、Tlbexp ユーティリティを使用します。</span><span class="sxs-lookup"><span data-stu-id="bfaab-133">You can generate type libraries from assemblies by using the Tlbexp utility.</span></span>  
  
 <span data-ttu-id="bfaab-134">Tlbimp と Tlbexp の詳細については、「[Tlbimp.exe (タイプ ライブラリ インポーター)](../../../framework/tools/tlbimp-exe-type-library-importer.md)」と「[Tlbexp.exe (タイプ ライブラリ エクスポーター)](../../../framework/tools/tlbexp-exe-type-library-exporter.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bfaab-134">For information about Tlbimp and Tlbexp, see [Tlbimp.exe (Type Library Importer)](../../../framework/tools/tlbimp-exe-type-library-importer.md) and [Tlbexp.exe (Type Library Exporter)](../../../framework/tools/tlbexp-exe-type-library-exporter.md).</span></span>  
  
## <a name="interop-assemblies"></a><span data-ttu-id="bfaab-135">相互運用機能アセンブリ</span><span class="sxs-lookup"><span data-stu-id="bfaab-135">Interop Assemblies</span></span>  

 <span data-ttu-id="bfaab-136">相互運用機能アセンブリは、マネージド コードとアンマネージド コードの間を橋渡しし、COM オブジェクト メンバーを同等の .NET Framework マネージド メンバーにマップする .NET Framework アセンブリです。</span><span class="sxs-lookup"><span data-stu-id="bfaab-136">Interop assemblies are .NET Framework assemblies that bridge between managed and unmanaged code, mapping COM object members to equivalent .NET Framework managed members.</span></span> <span data-ttu-id="bfaab-137">Visual Basic .NET によって作成された相互運用機能アセンブリは、相互運用マーシャリングなど、COM オブジェクトの操作に関する多くの詳細を処理します。</span><span class="sxs-lookup"><span data-stu-id="bfaab-137">Interop assemblies created by Visual Basic .NET handle many of the details of working with COM objects, such as interoperability marshaling.</span></span>  
  
## <a name="interoperability-marshaling"></a><span data-ttu-id="bfaab-138">相互運用マーシャリング</span><span class="sxs-lookup"><span data-stu-id="bfaab-138">Interoperability Marshaling</span></span>  

 <span data-ttu-id="bfaab-139">すべての .NET Framework アプリケーションでは、使用するプログラミング言語に関係なく、オブジェクトの相互運用性を実現する一連の共通型を共有します。</span><span class="sxs-lookup"><span data-stu-id="bfaab-139">All .NET Framework applications share a set of common types that enable interoperability of objects, regardless of the programming language that is used.</span></span> <span data-ttu-id="bfaab-140">COM オブジェクトのパラメーターと戻り値に、マネージド コードで使用されているものと異なるデータ型が使われている場合があります。</span><span class="sxs-lookup"><span data-stu-id="bfaab-140">The parameters and return values of COM objects sometimes use data types that differ from those used in managed code.</span></span> <span data-ttu-id="bfaab-141">*相互運用マーシャリング* は、パラメーターと戻り値を、COM オブジェクトとの間で移動するときと同等のデータ型にパッケージ化するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="bfaab-141">*Interoperability marshaling* is the process of packaging parameters and return values into equivalent data types as they move to and from COM objects.</span></span> <span data-ttu-id="bfaab-142">詳細については、「[相互運用マーシャリング](../../../framework/interop/interop-marshaling.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bfaab-142">For more information, see [Interop Marshaling](../../../framework/interop/interop-marshaling.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfaab-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="bfaab-143">See also</span></span>

- [<span data-ttu-id="bfaab-144">COM 相互運用</span><span class="sxs-lookup"><span data-stu-id="bfaab-144">COM Interop</span></span>](index.md)
- [<span data-ttu-id="bfaab-145">チュートリアル: COM オブジェクトによる継承の実装</span><span class="sxs-lookup"><span data-stu-id="bfaab-145">Walkthrough: Implementing Inheritance with COM Objects</span></span>](walkthrough-implementing-inheritance-with-com-objects.md)
- [<span data-ttu-id="bfaab-146">アンマネージ コードとの相互運用</span><span class="sxs-lookup"><span data-stu-id="bfaab-146">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)
- [<span data-ttu-id="bfaab-147">相互運用性のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="bfaab-147">Troubleshooting Interoperability</span></span>](troubleshooting-interoperability.md)
- [<span data-ttu-id="bfaab-148">.NET のアセンブリ</span><span class="sxs-lookup"><span data-stu-id="bfaab-148">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="bfaab-149">Tlbimp.exe (タイプ ライブラリ インポーター)</span><span class="sxs-lookup"><span data-stu-id="bfaab-149">Tlbimp.exe (Type Library Importer)</span></span>](../../../framework/tools/tlbimp-exe-type-library-importer.md)
- [<span data-ttu-id="bfaab-150">Tlbexp.exe (タイプ ライブラリ エクスポーター)</span><span class="sxs-lookup"><span data-stu-id="bfaab-150">Tlbexp.exe (Type Library Exporter)</span></span>](../../../framework/tools/tlbexp-exe-type-library-exporter.md)
- [<span data-ttu-id="bfaab-151">相互運用マーシャリング</span><span class="sxs-lookup"><span data-stu-id="bfaab-151">Interop Marshaling</span></span>](../../../framework/interop/interop-marshaling.md)
- [<span data-ttu-id="bfaab-152">登録を必要としない COM 相互運用機能</span><span class="sxs-lookup"><span data-stu-id="bfaab-152">Registration-Free COM Interop</span></span>](../../../framework/interop/registration-free-com-interop.md)
