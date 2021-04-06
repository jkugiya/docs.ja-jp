---
title: XML シリアライザー ジェネレーター ツール (Sgen.exe)
description: XML シリアライザー ジェネレーター ツールは、アセンブリ内の型の XML シリアル化アセンブリを生成します。これにより、XmlSerializer の起動パフォーマンスが向上します。
ms.date: 03/30/2017
ms.assetid: cc1d1f1c-fb26-4be9-885a-3fe84c81cec6
ms.openlocfilehash: 259f4cbafbe76d3645940ad425f41afb0b8cd304
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2021
ms.locfileid: "104653817"
---
# <a name="xml-serializer-generator-tool-sgenexe"></a><span data-ttu-id="bdb68-103">XML シリアライザー ジェネレーター ツール (Sgen.exe)</span><span class="sxs-lookup"><span data-stu-id="bdb68-103">XML Serializer Generator Tool (Sgen.exe)</span></span>

<span data-ttu-id="bdb68-104">XML シリアライザー ジェネレーターは、指定されたアセンブリの種類に対応する XML シリアル化アセンブリを作成します。</span><span class="sxs-lookup"><span data-stu-id="bdb68-104">The XML Serializer Generator creates an XML serialization assembly for types in a specified assembly.</span></span> <span data-ttu-id="bdb68-105">シリアル化アセンブリは、指定された型のオブジェクトのシリアル化または逆シリアル化の際に、<xref:System.Xml.Serialization.XmlSerializer> の起動パフォーマンスを向上させます。</span><span class="sxs-lookup"><span data-stu-id="bdb68-105">The serialization assembly improves the startup performance of a <xref:System.Xml.Serialization.XmlSerializer> when it serializes or deserializes objects of the specified types.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="bdb68-106">構文</span><span class="sxs-lookup"><span data-stu-id="bdb68-106">Syntax</span></span>

<span data-ttu-id="bdb68-107">コマンド ラインでツールを実行します。</span><span class="sxs-lookup"><span data-stu-id="bdb68-107">Run the tool from the command line.</span></span>
  
```console  
sgen [options]  
```
  
> [!TIP]
> <span data-ttu-id="bdb68-108">.NET Framework ツールを正常に機能させるには、[Visual Studio 開発者コマンド プロンプトまたは Visual Studio Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell) を使用するか、`Path`、`Include`、`Lib` の各環境変数を正しく設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bdb68-108">For .NET Framework tools to function properly, you must either use [Visual Studio Developer Command Prompt or Visual Studio Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell) or set the `Path`, `Include`, and `Lib` environment variables correctly.</span></span> <span data-ttu-id="bdb68-109">これらの環境変数を設定するには、 *\<SDK>\\\<version>\Bin* ディレクトリにある *SDKVars.bat* を実行します。</span><span class="sxs-lookup"><span data-stu-id="bdb68-109">To set these environment variables, run *SDKVars.bat*, which is located in the *\<SDK>\\\<version>\Bin* directory.</span></span>
  
## <a name="parameters"></a><span data-ttu-id="bdb68-110">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bdb68-110">Parameters</span></span>  
  
|<span data-ttu-id="bdb68-111">オプション</span><span class="sxs-lookup"><span data-stu-id="bdb68-111">Option</span></span>|<span data-ttu-id="bdb68-112">説明</span><span class="sxs-lookup"><span data-stu-id="bdb68-112">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="bdb68-113">**/a\[ssembly\]:** _filename_</span><span class="sxs-lookup"><span data-stu-id="bdb68-113">**/a\[ssembly\]:**_filename_</span></span>|<span data-ttu-id="bdb68-114">アセンブリ、または *filename* によって指定される実行可能ファイルに含まれるすべての型に対して、シリアル化コードを生成します。</span><span class="sxs-lookup"><span data-stu-id="bdb68-114">Generates serialization code for all the types contained in the assembly or executable specified by *filename*.</span></span> <span data-ttu-id="bdb68-115">指定できるファイル名は 1 つのみです。</span><span class="sxs-lookup"><span data-stu-id="bdb68-115">Only one file name can be provided.</span></span> <span data-ttu-id="bdb68-116">この引数を複数指定した場合は、最後のファイル名が使用されます。</span><span class="sxs-lookup"><span data-stu-id="bdb68-116">If this argument is repeated, the last file name is used.</span></span>|  
|<span data-ttu-id="bdb68-117">**/c\[ompiler\]:** _options_</span><span class="sxs-lookup"><span data-stu-id="bdb68-117">**/c\[ompiler\]:**_options_</span></span>|<span data-ttu-id="bdb68-118">オプションを C# コンパイラに渡すように指定します。</span><span class="sxs-lookup"><span data-stu-id="bdb68-118">Specifies the options to pass to the C# compiler.</span></span> <span data-ttu-id="bdb68-119">csc.exe のすべてのオプションがサポートされ、コンパイラに渡されます。</span><span class="sxs-lookup"><span data-stu-id="bdb68-119">All csc.exe options are supported as they are passed to the compiler.</span></span> <span data-ttu-id="bdb68-120">このオプションを使用して、アセンブリに署名してキー ファイルを指定するように指定できます。</span><span class="sxs-lookup"><span data-stu-id="bdb68-120">This can be used to specify that the assembly should be signed and to specify the key file.</span></span>|  
|<span data-ttu-id="bdb68-121">**/d\[ebug\]**</span><span class="sxs-lookup"><span data-stu-id="bdb68-121">**/d\[ebug\]**</span></span>|<span data-ttu-id="bdb68-122">デバッガーで使用できるイメージを生成します。</span><span class="sxs-lookup"><span data-stu-id="bdb68-122">Generates an image that can be used with a debugger.</span></span>|  
|<span data-ttu-id="bdb68-123">**/f\[orce\]**</span><span class="sxs-lookup"><span data-stu-id="bdb68-123">**/f\[orce\]**</span></span>|<span data-ttu-id="bdb68-124">同じ名前の既存のアセンブリに上書きします。</span><span class="sxs-lookup"><span data-stu-id="bdb68-124">Forces the overwriting of an existing assembly of the same name.</span></span> <span data-ttu-id="bdb68-125">既定値は **false** です。</span><span class="sxs-lookup"><span data-stu-id="bdb68-125">The default is **false**.</span></span>|  
|<span data-ttu-id="bdb68-126">**/help または /?**</span><span class="sxs-lookup"><span data-stu-id="bdb68-126">**/help or /?**</span></span>|<span data-ttu-id="bdb68-127">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="bdb68-127">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="bdb68-128">**/k\[eep\]**</span><span class="sxs-lookup"><span data-stu-id="bdb68-128">**/k\[eep\]**</span></span>|<span data-ttu-id="bdb68-129">生成されたソース ファイルとその他の一時ファイルをシリアル化アセンブリにコンパイルした後、元のファイルを削除しません。</span><span class="sxs-lookup"><span data-stu-id="bdb68-129">Suppresses the deletion of the generated source files and other temporary files after they have been compiled into the serialization assembly.</span></span> <span data-ttu-id="bdb68-130">このオプションを使用して、ツールが特定の型に対してシリアル化コードを生成するかどうかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="bdb68-130">This can be used to determine whether the tool is generating serialization code for a particular type.</span></span>|  
|<span data-ttu-id="bdb68-131">**/n\[ologo\]**</span><span class="sxs-lookup"><span data-stu-id="bdb68-131">**/n\[ologo\]**</span></span>|<span data-ttu-id="bdb68-132">Microsoft の著作権情報を表示しません。</span><span class="sxs-lookup"><span data-stu-id="bdb68-132">Suppresses the display of the Microsoft startup banner.</span></span>|  
|<span data-ttu-id="bdb68-133">**/o\[ut\]:** _path_</span><span class="sxs-lookup"><span data-stu-id="bdb68-133">**/o\[ut\]:**_path_</span></span>|<span data-ttu-id="bdb68-134">生成されたアセンブリの保存先のディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="bdb68-134">Specifies the directory in which to save the generated assembly.</span></span> <span data-ttu-id="bdb68-135">**注:** 生成されたアセンブリの名前は、入力アセンブリの名前と "xmlSerializers.dll" で構成されます。</span><span class="sxs-lookup"><span data-stu-id="bdb68-135">**Note:**  The name of the generated assembly is composed of the name of the input assembly plus "xmlSerializers.dll".</span></span>|  
|<span data-ttu-id="bdb68-136">**/p\[roxytypes\]**</span><span class="sxs-lookup"><span data-stu-id="bdb68-136">**/p\[roxytypes\]**</span></span>|<span data-ttu-id="bdb68-137">XML Web サービス プロキシ型に対してのみシリアル化コードを生成します。</span><span class="sxs-lookup"><span data-stu-id="bdb68-137">Generates serialization code only for the XML Web service proxy types.</span></span>|  
|<span data-ttu-id="bdb68-138">**/r\[eference\]:** _assemblyfiles_</span><span class="sxs-lookup"><span data-stu-id="bdb68-138">**/r\[eference\]:**_assemblyfiles_</span></span>|<span data-ttu-id="bdb68-139">XML シリアル化が必要な型によって参照されるアセンブリを指定します。</span><span class="sxs-lookup"><span data-stu-id="bdb68-139">Specifies the assemblies that are referenced by the types requiring XML serialization.</span></span> <span data-ttu-id="bdb68-140">コンマで区切られた複数のアセンブリ ファイルを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="bdb68-140">Accepts multiple assembly files separated by commas.</span></span>|  
|<span data-ttu-id="bdb68-141">**/s\[ilent\]**</span><span class="sxs-lookup"><span data-stu-id="bdb68-141">**/s\[ilent\]**</span></span>|<span data-ttu-id="bdb68-142">成功メッセージを表示しません。</span><span class="sxs-lookup"><span data-stu-id="bdb68-142">Suppresses the display of success messages.</span></span>|  
|<span data-ttu-id="bdb68-143">**/t\[ype\]:** _type_</span><span class="sxs-lookup"><span data-stu-id="bdb68-143">**/t\[ype\]:**_type_</span></span>|<span data-ttu-id="bdb68-144">指定された型に対してのみ、シリアル化コードを生成します。</span><span class="sxs-lookup"><span data-stu-id="bdb68-144">Generates serialization code only for the specified type.</span></span>|  
|<span data-ttu-id="bdb68-145">**/v\[erbose\]**</span><span class="sxs-lookup"><span data-stu-id="bdb68-145">**/v\[erbose\]**</span></span>|<span data-ttu-id="bdb68-146">デバッグに関する詳細出力を表示します。</span><span class="sxs-lookup"><span data-stu-id="bdb68-146">Displays verbose output for debugging.</span></span> <span data-ttu-id="bdb68-147"><xref:System.Xml.Serialization.XmlSerializer> でシリアル化できない対象アセンブリの型を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="bdb68-147">Lists types from the target assembly that cannot be serialized with the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>|  
|<span data-ttu-id="bdb68-148">**/?**</span><span class="sxs-lookup"><span data-stu-id="bdb68-148">**/?**</span></span>|<span data-ttu-id="bdb68-149">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="bdb68-149">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bdb68-150">Remarks</span><span class="sxs-lookup"><span data-stu-id="bdb68-150">Remarks</span></span>  

 <span data-ttu-id="bdb68-151">XML シリアライザー ジェネレーターを使用しない場合、<xref:System.Xml.Serialization.XmlSerializer> はアプリケーションを実行するたびに、各型に対してシリアル化コードとシリアル化アセンブリを生成します。</span><span class="sxs-lookup"><span data-stu-id="bdb68-151">When the XML Serializer Generator is not used, a <xref:System.Xml.Serialization.XmlSerializer> generates serialization code and a serialization assembly for each type every time an application is run.</span></span> <span data-ttu-id="bdb68-152">XML シリアル化起動のパフォーマンスを向上させるには、Sgen.exe ツールを使用して、あらかじめこれらのアセンブリを生成します。</span><span class="sxs-lookup"><span data-stu-id="bdb68-152">To improve the performance of XML serialization startup, use the Sgen.exe tool to generate those assemblies in advance.</span></span> <span data-ttu-id="bdb68-153">生成したアセンブリは、アプリケーションで配置できます。</span><span class="sxs-lookup"><span data-stu-id="bdb68-153">These assemblies can then be deployed with the application.</span></span>  
  
 <span data-ttu-id="bdb68-154">XML シリアライザー ジェネレーターは、サーバーとの通信に XML Web サービス プロキシを使用するクライアントのパフォーマンスも向上させますが、これは型が初めて読み込まれるとき、シリアル化プロセスによってパフォーマンスが低下しないためです。</span><span class="sxs-lookup"><span data-stu-id="bdb68-154">The XML Serializer Generator can also improve the performance of clients that use XML Web service proxies to communicate with servers because the serialization process will not incur a performance hit when the type is loaded the first time.</span></span>  
  
 <span data-ttu-id="bdb68-155">これらの生成されたアセンブリは、Web サービスのサーバー側では使用できません。</span><span class="sxs-lookup"><span data-stu-id="bdb68-155">These generated assemblies cannot be used on the server side of a Web service.</span></span> <span data-ttu-id="bdb68-156">このツールは、Web サービス クライアントと手動シリアル化シナリオに対してのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="bdb68-156">This tool is only for Web service clients and manual serialization scenarios.</span></span>  
  
 <span data-ttu-id="bdb68-157">シリアル化する型を含むアセンブリの名前が MyType.dll の場合、関連するシリアル化アセンブリの名前は MyType.XmlSerializers.dll となります。</span><span class="sxs-lookup"><span data-stu-id="bdb68-157">If the assembly containing the type to serialize is named MyType.dll, then the associated serialization assembly will be named MyType.XmlSerializers.dll.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="bdb68-158">使用例</span><span class="sxs-lookup"><span data-stu-id="bdb68-158">Examples</span></span>  

 <span data-ttu-id="bdb68-159">次のコマンドは、Data.dll という名前のアセンブリに含まれるすべての型をシリアル化するために、Data.XmlSerializers.dll という名前のアセンブリを作成します。</span><span class="sxs-lookup"><span data-stu-id="bdb68-159">The following command creates an assembly named Data.XmlSerializers.dll for serializing all the types contained in the assembly named Data.dll.</span></span>  
  
```console  
sgen Data.dll
```  
  
 <span data-ttu-id="bdb68-160">Data.XmlSerializers.dll アセンブリは、Data.dll の型をシリアル化および逆シリアル化する必要のあるコードから参照できます。</span><span class="sxs-lookup"><span data-stu-id="bdb68-160">The Data.XmlSerializers.dll assembly can be referenced from code that needs to serialize and deserialize the types in Data.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdb68-161">関連項目</span><span class="sxs-lookup"><span data-stu-id="bdb68-161">See also</span></span>

- [<span data-ttu-id="bdb68-162">ツール</span><span class="sxs-lookup"><span data-stu-id="bdb68-162">Tools</span></span>](../../framework/tools/index.md)
- [<span data-ttu-id="bdb68-163">開発者コマンドライン シェル</span><span class="sxs-lookup"><span data-stu-id="bdb68-163">Developer command-line shells</span></span>](/visualstudio/ide/reference/command-prompt-powershell)
