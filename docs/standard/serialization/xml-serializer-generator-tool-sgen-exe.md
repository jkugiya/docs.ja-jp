---
title: XML シリアライザー ジェネレーター ツール (Sgen.exe)
description: XML シリアライザー ジェネレーター ツールは、アセンブリ内の型の XML シリアル化アセンブリを生成します。これにより、XmlSerializer の起動パフォーマンスが向上します。
ms.date: 03/30/2017
ms.assetid: cc1d1f1c-fb26-4be9-885a-3fe84c81cec6
ms.openlocfilehash: b703f6755a4aab809c28f8009a0b358c2e6962bb
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102259851"
---
# <a name="xml-serializer-generator-tool-sgenexe"></a><span data-ttu-id="14bd3-103">XML シリアライザー ジェネレーター ツール (Sgen.exe)</span><span class="sxs-lookup"><span data-stu-id="14bd3-103">XML Serializer Generator Tool (Sgen.exe)</span></span>

<span data-ttu-id="14bd3-104">XML シリアライザー ジェネレーターは、指定されたアセンブリの種類に対応する XML シリアル化アセンブリを作成します。</span><span class="sxs-lookup"><span data-stu-id="14bd3-104">The XML Serializer Generator creates an XML serialization assembly for types in a specified assembly.</span></span> <span data-ttu-id="14bd3-105">シリアル化アセンブリは、指定された型のオブジェクトのシリアル化または逆シリアル化の際に、<xref:System.Xml.Serialization.XmlSerializer> の起動パフォーマンスを向上させます。</span><span class="sxs-lookup"><span data-stu-id="14bd3-105">The serialization assembly improves the startup performance of a <xref:System.Xml.Serialization.XmlSerializer> when it serializes or deserializes objects of the specified types.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="14bd3-106">構文</span><span class="sxs-lookup"><span data-stu-id="14bd3-106">Syntax</span></span>

<span data-ttu-id="14bd3-107">コマンド ラインでツールを実行します。</span><span class="sxs-lookup"><span data-stu-id="14bd3-107">Run the tool from the command line.</span></span>
  
```console  
sgen [options]  
```
  
> [!TIP]
> <span data-ttu-id="14bd3-108">.NET Framework ツールが適切に機能するには、 `Path`、`Include`、および `Lib` の各環境変数を正しく設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="14bd3-108">For .NET Framework tools to function properly, you must set your `Path`, `Include`, and `Lib` environment variables correctly.</span></span> <span data-ttu-id="14bd3-109">これらの環境変数を設定するには、\<SDK>\\\<version>\Bin ディレクトリにある SDKVars.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="14bd3-109">Set these environment variables by running SDKVars.bat, which is located in the \<SDK>\\\<version>\Bin directory.</span></span> <span data-ttu-id="14bd3-110">SDKVars.bat は、コマンド シェルごとに実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="14bd3-110">SDKVars.bat must be executed in every command shell.</span></span>
  
## <a name="parameters"></a><span data-ttu-id="14bd3-111">パラメーター</span><span class="sxs-lookup"><span data-stu-id="14bd3-111">Parameters</span></span>  
  
|<span data-ttu-id="14bd3-112">オプション</span><span class="sxs-lookup"><span data-stu-id="14bd3-112">Option</span></span>|<span data-ttu-id="14bd3-113">説明</span><span class="sxs-lookup"><span data-stu-id="14bd3-113">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="14bd3-114">**/a\[ssembly\]:** _filename_</span><span class="sxs-lookup"><span data-stu-id="14bd3-114">**/a\[ssembly\]:**_filename_</span></span>|<span data-ttu-id="14bd3-115">アセンブリ、または *filename* によって指定される実行可能ファイルに含まれるすべての型に対して、シリアル化コードを生成します。</span><span class="sxs-lookup"><span data-stu-id="14bd3-115">Generates serialization code for all the types contained in the assembly or executable specified by *filename*.</span></span> <span data-ttu-id="14bd3-116">指定できるファイル名は 1 つのみです。</span><span class="sxs-lookup"><span data-stu-id="14bd3-116">Only one file name can be provided.</span></span> <span data-ttu-id="14bd3-117">この引数を複数指定した場合は、最後のファイル名が使用されます。</span><span class="sxs-lookup"><span data-stu-id="14bd3-117">If this argument is repeated, the last file name is used.</span></span>|  
|<span data-ttu-id="14bd3-118">**/c\[ompiler\]:** _options_</span><span class="sxs-lookup"><span data-stu-id="14bd3-118">**/c\[ompiler\]:**_options_</span></span>|<span data-ttu-id="14bd3-119">オプションを C# コンパイラに渡すように指定します。</span><span class="sxs-lookup"><span data-stu-id="14bd3-119">Specifies the options to pass to the C# compiler.</span></span> <span data-ttu-id="14bd3-120">csc.exe のすべてのオプションがサポートされ、コンパイラに渡されます。</span><span class="sxs-lookup"><span data-stu-id="14bd3-120">All csc.exe options are supported as they are passed to the compiler.</span></span> <span data-ttu-id="14bd3-121">このオプションを使用して、アセンブリに署名してキー ファイルを指定するように指定できます。</span><span class="sxs-lookup"><span data-stu-id="14bd3-121">This can be used to specify that the assembly should be signed and to specify the key file.</span></span>|  
|<span data-ttu-id="14bd3-122">**/d\[ebug\]**</span><span class="sxs-lookup"><span data-stu-id="14bd3-122">**/d\[ebug\]**</span></span>|<span data-ttu-id="14bd3-123">デバッガーで使用できるイメージを生成します。</span><span class="sxs-lookup"><span data-stu-id="14bd3-123">Generates an image that can be used with a debugger.</span></span>|  
|<span data-ttu-id="14bd3-124">**/f\[orce\]**</span><span class="sxs-lookup"><span data-stu-id="14bd3-124">**/f\[orce\]**</span></span>|<span data-ttu-id="14bd3-125">同じ名前の既存のアセンブリに上書きします。</span><span class="sxs-lookup"><span data-stu-id="14bd3-125">Forces the overwriting of an existing assembly of the same name.</span></span> <span data-ttu-id="14bd3-126">既定値は **false** です。</span><span class="sxs-lookup"><span data-stu-id="14bd3-126">The default is **false**.</span></span>|  
|<span data-ttu-id="14bd3-127">**/help または /?**</span><span class="sxs-lookup"><span data-stu-id="14bd3-127">**/help or /?**</span></span>|<span data-ttu-id="14bd3-128">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="14bd3-128">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="14bd3-129">**/k\[eep\]**</span><span class="sxs-lookup"><span data-stu-id="14bd3-129">**/k\[eep\]**</span></span>|<span data-ttu-id="14bd3-130">生成されたソース ファイルとその他の一時ファイルをシリアル化アセンブリにコンパイルした後、元のファイルを削除しません。</span><span class="sxs-lookup"><span data-stu-id="14bd3-130">Suppresses the deletion of the generated source files and other temporary files after they have been compiled into the serialization assembly.</span></span> <span data-ttu-id="14bd3-131">このオプションを使用して、ツールが特定の型に対してシリアル化コードを生成するかどうかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="14bd3-131">This can be used to determine whether the tool is generating serialization code for a particular type.</span></span>|  
|<span data-ttu-id="14bd3-132">**/n\[ologo\]**</span><span class="sxs-lookup"><span data-stu-id="14bd3-132">**/n\[ologo\]**</span></span>|<span data-ttu-id="14bd3-133">Microsoft の著作権情報を表示しません。</span><span class="sxs-lookup"><span data-stu-id="14bd3-133">Suppresses the display of the Microsoft startup banner.</span></span>|  
|<span data-ttu-id="14bd3-134">**/o\[ut\]:** _path_</span><span class="sxs-lookup"><span data-stu-id="14bd3-134">**/o\[ut\]:**_path_</span></span>|<span data-ttu-id="14bd3-135">生成されたアセンブリの保存先のディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="14bd3-135">Specifies the directory in which to save the generated assembly.</span></span> <span data-ttu-id="14bd3-136">**注:** 生成されたアセンブリの名前は、入力アセンブリの名前と "xmlSerializers.dll" で構成されます。</span><span class="sxs-lookup"><span data-stu-id="14bd3-136">**Note:**  The name of the generated assembly is composed of the name of the input assembly plus "xmlSerializers.dll".</span></span>|  
|<span data-ttu-id="14bd3-137">**/p\[roxytypes\]**</span><span class="sxs-lookup"><span data-stu-id="14bd3-137">**/p\[roxytypes\]**</span></span>|<span data-ttu-id="14bd3-138">XML Web サービス プロキシ型に対してのみシリアル化コードを生成します。</span><span class="sxs-lookup"><span data-stu-id="14bd3-138">Generates serialization code only for the XML Web service proxy types.</span></span>|  
|<span data-ttu-id="14bd3-139">**/r\[eference\]:** _assemblyfiles_</span><span class="sxs-lookup"><span data-stu-id="14bd3-139">**/r\[eference\]:**_assemblyfiles_</span></span>|<span data-ttu-id="14bd3-140">XML シリアル化が必要な型によって参照されるアセンブリを指定します。</span><span class="sxs-lookup"><span data-stu-id="14bd3-140">Specifies the assemblies that are referenced by the types requiring XML serialization.</span></span> <span data-ttu-id="14bd3-141">コンマで区切られた複数のアセンブリ ファイルを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="14bd3-141">Accepts multiple assembly files separated by commas.</span></span>|  
|<span data-ttu-id="14bd3-142">**/s\[ilent\]**</span><span class="sxs-lookup"><span data-stu-id="14bd3-142">**/s\[ilent\]**</span></span>|<span data-ttu-id="14bd3-143">成功メッセージを表示しません。</span><span class="sxs-lookup"><span data-stu-id="14bd3-143">Suppresses the display of success messages.</span></span>|  
|<span data-ttu-id="14bd3-144">**/t\[ype\]:** _type_</span><span class="sxs-lookup"><span data-stu-id="14bd3-144">**/t\[ype\]:**_type_</span></span>|<span data-ttu-id="14bd3-145">指定された型に対してのみ、シリアル化コードを生成します。</span><span class="sxs-lookup"><span data-stu-id="14bd3-145">Generates serialization code only for the specified type.</span></span>|  
|<span data-ttu-id="14bd3-146">**/v\[erbose\]**</span><span class="sxs-lookup"><span data-stu-id="14bd3-146">**/v\[erbose\]**</span></span>|<span data-ttu-id="14bd3-147">デバッグに関する詳細出力を表示します。</span><span class="sxs-lookup"><span data-stu-id="14bd3-147">Displays verbose output for debugging.</span></span> <span data-ttu-id="14bd3-148"><xref:System.Xml.Serialization.XmlSerializer> でシリアル化できない対象アセンブリの型を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="14bd3-148">Lists types from the target assembly that cannot be serialized with the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>|  
|<span data-ttu-id="14bd3-149">**/?**</span><span class="sxs-lookup"><span data-stu-id="14bd3-149">**/?**</span></span>|<span data-ttu-id="14bd3-150">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="14bd3-150">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14bd3-151">Remarks</span><span class="sxs-lookup"><span data-stu-id="14bd3-151">Remarks</span></span>  

 <span data-ttu-id="14bd3-152">XML シリアライザー ジェネレーターを使用しない場合、<xref:System.Xml.Serialization.XmlSerializer> はアプリケーションを実行するたびに、各型に対してシリアル化コードとシリアル化アセンブリを生成します。</span><span class="sxs-lookup"><span data-stu-id="14bd3-152">When the XML Serializer Generator is not used, a <xref:System.Xml.Serialization.XmlSerializer> generates serialization code and a serialization assembly for each type every time an application is run.</span></span> <span data-ttu-id="14bd3-153">XML シリアル化起動のパフォーマンスを向上させるには、Sgen.exe ツールを使用して、あらかじめこれらのアセンブリを生成します。</span><span class="sxs-lookup"><span data-stu-id="14bd3-153">To improve the performance of XML serialization startup, use the Sgen.exe tool to generate those assemblies in advance.</span></span> <span data-ttu-id="14bd3-154">生成したアセンブリは、アプリケーションで配置できます。</span><span class="sxs-lookup"><span data-stu-id="14bd3-154">These assemblies can then be deployed with the application.</span></span>  
  
 <span data-ttu-id="14bd3-155">XML シリアライザー ジェネレーターは、サーバーとの通信に XML Web サービス プロキシを使用するクライアントのパフォーマンスも向上させますが、これは型が初めて読み込まれるとき、シリアル化プロセスによってパフォーマンスが低下しないためです。</span><span class="sxs-lookup"><span data-stu-id="14bd3-155">The XML Serializer Generator can also improve the performance of clients that use XML Web service proxies to communicate with servers because the serialization process will not incur a performance hit when the type is loaded the first time.</span></span>  
  
 <span data-ttu-id="14bd3-156">これらの生成されたアセンブリは、Web サービスのサーバー側では使用できません。</span><span class="sxs-lookup"><span data-stu-id="14bd3-156">These generated assemblies cannot be used on the server side of a Web service.</span></span> <span data-ttu-id="14bd3-157">このツールは、Web サービス クライアントと手動シリアル化シナリオに対してのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="14bd3-157">This tool is only for Web service clients and manual serialization scenarios.</span></span>  
  
 <span data-ttu-id="14bd3-158">シリアル化する型を含むアセンブリの名前が MyType.dll の場合、関連するシリアル化アセンブリの名前は MyType.XmlSerializers.dll となります。</span><span class="sxs-lookup"><span data-stu-id="14bd3-158">If the assembly containing the type to serialize is named MyType.dll, then the associated serialization assembly will be named MyType.XmlSerializers.dll.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="14bd3-159">使用例</span><span class="sxs-lookup"><span data-stu-id="14bd3-159">Examples</span></span>  

 <span data-ttu-id="14bd3-160">次のコマンドは、Data.dll という名前のアセンブリに含まれるすべての型をシリアル化するために、Data.XmlSerializers.dll という名前のアセンブリを作成します。</span><span class="sxs-lookup"><span data-stu-id="14bd3-160">The following command creates an assembly named Data.XmlSerializers.dll for serializing all the types contained in the assembly named Data.dll.</span></span>  
  
```console  
sgen Data.dll
```  
  
 <span data-ttu-id="14bd3-161">Data.XmlSerializers.dll アセンブリは、Data.dll の型をシリアル化および逆シリアル化する必要のあるコードから参照できます。</span><span class="sxs-lookup"><span data-stu-id="14bd3-161">The Data.XmlSerializers.dll assembly can be referenced from code that needs to serialize and deserialize the types in Data.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14bd3-162">関連項目</span><span class="sxs-lookup"><span data-stu-id="14bd3-162">See also</span></span>

- [<span data-ttu-id="14bd3-163">ツール</span><span class="sxs-lookup"><span data-stu-id="14bd3-163">Tools</span></span>](../../framework/tools/index.md)
- [<span data-ttu-id="14bd3-164">開発者コマンドライン シェル</span><span class="sxs-lookup"><span data-stu-id="14bd3-164">Developer command-line shells</span></span>](/visualstudio/ide/reference/command-prompt-powershell)
