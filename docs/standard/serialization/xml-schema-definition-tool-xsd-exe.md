---
title: XML Schema Definition Tool (Xsd.exe)
description: XML シリアライザー ジェネレーター ツールは、指定されたアセンブリ内の型の XML シリアル化アセンブリを生成します。これにより、XmlSerializer の起動パフォーマンスが向上します。
ms.date: 03/30/2017
ms.assetid: a6e6e65c-347f-4494-9457-653bf29baac2
ms.openlocfilehash: 2d849bec988c093cfe22cb9ce65ce23cbb1ce78d
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102259877"
---
# <a name="xml-schema-definition-tool-xsdexe"></a><span data-ttu-id="7017e-103">XML Schema Definition Tool (Xsd.exe)</span><span class="sxs-lookup"><span data-stu-id="7017e-103">XML Schema Definition Tool (Xsd.exe)</span></span>

<span data-ttu-id="7017e-104">XML スキーマ定義ツール (Xsd.exe) は、XDR、XML、および XSD ファイル、またはランタイム アセンブリ内のクラスから XML スキーマ クラスまたは共通言語ランタイム クラスを生成します。</span><span class="sxs-lookup"><span data-stu-id="7017e-104">The XML Schema Definition (Xsd.exe) tool generates XML schema or common language runtime classes from XDR, XML, and XSD files, or from classes in a runtime assembly.</span></span>

<span data-ttu-id="7017e-105">通常、XML スキーマ定義ツール (Xsd.exe) は、次のパスにあります。</span><span class="sxs-lookup"><span data-stu-id="7017e-105">The XML Schema Definition tool (Xsd.exe) usually can be found in the following path:\</span></span>
<span data-ttu-id="7017e-106">_C:\\Program Files (x86)\\Microsoft SDKs\\Windows\\{version}\\bin\\NETFX {version} Tools\\_</span><span class="sxs-lookup"><span data-stu-id="7017e-106">_C:\\Program Files (x86)\\Microsoft SDKs\\Windows\\{version}\\bin\\NETFX {version} Tools\\_</span></span>

## <a name="syntax"></a><span data-ttu-id="7017e-107">構文</span><span class="sxs-lookup"><span data-stu-id="7017e-107">Syntax</span></span>

<span data-ttu-id="7017e-108">コマンド ラインでツールを実行します。</span><span class="sxs-lookup"><span data-stu-id="7017e-108">Run the tool from the command line.</span></span>

```console
xsd file.xdr [-outputdir:directory][/parameters:file.xml]
xsd file.xml [-outputdir:directory] [/parameters:file.xml]
xsd file.xsd {/classes | /dataset} [/element:element]
             [/enableLinqDataSet] [/language:language]
                          [/namespace:namespace] [-outputdir:directory] [URI:uri]
                          [/parameters:file.xml]
xsd {file.dll | file.exe} [-outputdir:directory] [/type:typename [...]][/parameters:file.xml]
```
  
> [!TIP]
> <span data-ttu-id="7017e-109">.NET Framework ツールが適切に機能するには、 `Path`、`Include`、および `Lib` の各環境変数を正しく設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7017e-109">For .NET Framework tools to function properly, you must set your `Path`, `Include`, and `Lib` environment variables correctly.</span></span> <span data-ttu-id="7017e-110">これらの環境変数を設定するには、\<SDK>\\\<version>\Bin ディレクトリにある SDKVars.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="7017e-110">Set these environment variables by running SDKVars.bat, which is located in the \<SDK>\\\<version>\Bin directory.</span></span> <span data-ttu-id="7017e-111">SDKVars.bat は、コマンド シェルごとに実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7017e-111">SDKVars.bat must be executed in every command shell.</span></span>

## <a name="argument"></a><span data-ttu-id="7017e-112">引数</span><span class="sxs-lookup"><span data-stu-id="7017e-112">Argument</span></span>

|<span data-ttu-id="7017e-113">引数</span><span class="sxs-lookup"><span data-stu-id="7017e-113">Argument</span></span>|<span data-ttu-id="7017e-114">説明</span><span class="sxs-lookup"><span data-stu-id="7017e-114">Description</span></span>|
|--------------|-----------------|
|<span data-ttu-id="7017e-115">*file.extension*</span><span class="sxs-lookup"><span data-stu-id="7017e-115">*file.extension*</span></span>|<span data-ttu-id="7017e-116">変換元の入力ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="7017e-116">Specifies the input file to convert.</span></span> <span data-ttu-id="7017e-117">拡張子として、.xdr、.xml、.xsd、.dll、または .exe のいずれかを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7017e-117">You must specify the extension as one of the following: .xdr, .xml, .xsd, .dll, or .exe.</span></span><br /><br /> <span data-ttu-id="7017e-118">XDR スキーマ ファイル (拡張子 .xdr) を指定すると、Xsd.exe は XDR スキーマを XSD スキーマに変換します。</span><span class="sxs-lookup"><span data-stu-id="7017e-118">If you specify an XDR schema file (.xdr extension), Xsd.exe converts the XDR schema to an XSD schema.</span></span> <span data-ttu-id="7017e-119">出力ファイルの名前は XDR スキーマと同じですが、拡張子は .xsd となります。</span><span class="sxs-lookup"><span data-stu-id="7017e-119">The output file has the same name as the XDR schema, but with the .xsd extension.</span></span><br /><br /> <span data-ttu-id="7017e-120">XML ファイル (拡張子 .xml) を指定すると、Xsd.exe はそのファイル内のデータからスキーマを推測して XSD スキーマを生成します。</span><span class="sxs-lookup"><span data-stu-id="7017e-120">If you specify an XML file (.xml extension), Xsd.exe infers a schema from the data in the file and produces an XSD schema.</span></span> <span data-ttu-id="7017e-121">出力ファイルの名前は XML ファイルと同じですが、拡張子は .xsd となります。</span><span class="sxs-lookup"><span data-stu-id="7017e-121">The output file has the same name as the XML file, but with the .xsd extension.</span></span><br /><br /> <span data-ttu-id="7017e-122">XML スキーマ ファイル (拡張子 .xsd) を指定すると、XML スキーマと対応するランタイム オブジェクト用のソース コードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="7017e-122">If you specify an XML schema file (.xsd extension), Xsd.exe generates source code for runtime objects that correspond to the XML schema.</span></span><br /><br /> <span data-ttu-id="7017e-123">ランタイム アセンブリ ファイル (拡張子 .exe または .dll) を指定すると、そのアセンブリに含まれる 1 つ以上の型用のスキーマが生成されます。</span><span class="sxs-lookup"><span data-stu-id="7017e-123">If you specify a runtime assembly file (.exe or .dll extension), Xsd.exe generates schemas for one or more types in that assembly.</span></span> <span data-ttu-id="7017e-124">`/type` オプションを使用して、スキーマを生成する対象の型を指定できます。</span><span class="sxs-lookup"><span data-stu-id="7017e-124">You can use the `/type` option to specify the types for which to generate schemas.</span></span> <span data-ttu-id="7017e-125">出力スキーマには、schema0.xsd、schema1.xsd などの名前が付けられます。</span><span class="sxs-lookup"><span data-stu-id="7017e-125">The output schemas are named schema0.xsd, schema1.xsd, and so on.</span></span> <span data-ttu-id="7017e-126">Xsd.exe が複数のスキーマを生成するのは、指定した型によって、カスタム属性 `XMLRoot` を使用する名前空間が特定される場合のみです。</span><span class="sxs-lookup"><span data-stu-id="7017e-126">Xsd.exe produces multiple schemas only if the given types specify a namespace using the `XMLRoot` custom attribute.</span></span>|

## <a name="general-options"></a><span data-ttu-id="7017e-127">一般オプション</span><span class="sxs-lookup"><span data-stu-id="7017e-127">General Options</span></span>

|<span data-ttu-id="7017e-128">オプション</span><span class="sxs-lookup"><span data-stu-id="7017e-128">Option</span></span>|<span data-ttu-id="7017e-129">説明</span><span class="sxs-lookup"><span data-stu-id="7017e-129">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="7017e-130">**/h\[elp\]**</span><span class="sxs-lookup"><span data-stu-id="7017e-130">**/h\[elp\]**</span></span>|<span data-ttu-id="7017e-131">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="7017e-131">Displays command syntax and options for the tool.</span></span>|
|<span data-ttu-id="7017e-132">**/o\[utputdir\]:** _directory_</span><span class="sxs-lookup"><span data-stu-id="7017e-132">**/o\[utputdir\]:**_directory_</span></span>|<span data-ttu-id="7017e-133">出力ファイル用のディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="7017e-133">Specifies the directory for output files.</span></span> <span data-ttu-id="7017e-134">この引数は 1 回だけ指定できます。</span><span class="sxs-lookup"><span data-stu-id="7017e-134">This argument can appear only once.</span></span> <span data-ttu-id="7017e-135">既定値は、現在のディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="7017e-135">The default is the current directory.</span></span>|
|<span data-ttu-id="7017e-136">**/?**</span><span class="sxs-lookup"><span data-stu-id="7017e-136">**/?**</span></span>|<span data-ttu-id="7017e-137">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="7017e-137">Displays command syntax and options for the tool.</span></span>|
|<span data-ttu-id="7017e-138">**/p\[arameters\]:** _file.xml_</span><span class="sxs-lookup"><span data-stu-id="7017e-138">**/p\[arameters\]:**_file.xml_</span></span>|<span data-ttu-id="7017e-139">指定された .xml ファイルから各種のオペレーション モードのためのオプションを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="7017e-139">Read options for various operation modes from the specified .xml file.</span></span> <span data-ttu-id="7017e-140">短縮形は `/p:` です。</span><span class="sxs-lookup"><span data-stu-id="7017e-140">The short form is `/p:`.</span></span> <span data-ttu-id="7017e-141">詳細については、「[解説](#remarks)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7017e-141">For more information, see the [Remarks](#remarks) section.</span></span>|

## <a name="xsd-file-options"></a><span data-ttu-id="7017e-142">XSD ファイルのオプション</span><span class="sxs-lookup"><span data-stu-id="7017e-142">XSD File Options</span></span>

 <span data-ttu-id="7017e-143">.xsd ファイルについては、次のオプションのうち 1 つだけを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7017e-143">You must specify only one of the following options for .xsd files.</span></span>

|<span data-ttu-id="7017e-144">オプション</span><span class="sxs-lookup"><span data-stu-id="7017e-144">Option</span></span>|<span data-ttu-id="7017e-145">説明</span><span class="sxs-lookup"><span data-stu-id="7017e-145">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="7017e-146">**/c\[lasses\]**</span><span class="sxs-lookup"><span data-stu-id="7017e-146">**/c\[lasses\]**</span></span>|<span data-ttu-id="7017e-147">指定したスキーマと対応するクラスを生成します。</span><span class="sxs-lookup"><span data-stu-id="7017e-147">Generates classes that correspond to the specified schema.</span></span> <span data-ttu-id="7017e-148">オブジェクトに XML データを読み込むには、<xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A?displayProperty=nameWithType> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="7017e-148">To read XML data into the object, use the <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A?displayProperty=nameWithType> method.</span></span>|
|<span data-ttu-id="7017e-149">**/d\[ataset\]**</span><span class="sxs-lookup"><span data-stu-id="7017e-149">**/d\[ataset\]**</span></span>|<span data-ttu-id="7017e-150">指定したスキーマに対応する <xref:System.Data.DataSet> から派生したクラスを生成します。</span><span class="sxs-lookup"><span data-stu-id="7017e-150">Generates a class derived from <xref:System.Data.DataSet> that corresponds to the specified schema.</span></span> <span data-ttu-id="7017e-151">派生したクラスに XML データを読み込むには、<xref:System.Data.DataSet.ReadXml%2A?displayProperty=nameWithType> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="7017e-151">To read XML data into the derived class, use the <xref:System.Data.DataSet.ReadXml%2A?displayProperty=nameWithType> method.</span></span>|

 <span data-ttu-id="7017e-152">.xsd ファイルについては、次のオプションのうち任意のオプションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="7017e-152">You can also specify any of the following options for .xsd files.</span></span>

|<span data-ttu-id="7017e-153">オプション</span><span class="sxs-lookup"><span data-stu-id="7017e-153">Option</span></span>|<span data-ttu-id="7017e-154">説明</span><span class="sxs-lookup"><span data-stu-id="7017e-154">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="7017e-155">**/e\[lement\]:** _element_</span><span class="sxs-lookup"><span data-stu-id="7017e-155">**/e\[lement\]:**_element_</span></span>|<span data-ttu-id="7017e-156">コードを生成する対象とする、スキーマ内の要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="7017e-156">Specifies the element in the schema to generate code for.</span></span> <span data-ttu-id="7017e-157">既定では、すべての要素が指定されます。</span><span class="sxs-lookup"><span data-stu-id="7017e-157">By default all elements are typed.</span></span> <span data-ttu-id="7017e-158">この引数は、複数回指定できます。</span><span class="sxs-lookup"><span data-stu-id="7017e-158">You can specify this argument more than once.</span></span>|
|<span data-ttu-id="7017e-159">**/enableDataBinding**</span><span class="sxs-lookup"><span data-stu-id="7017e-159">**/enableDataBinding**</span></span>|<span data-ttu-id="7017e-160">データ バインディングを有効にするために、生成されたすべての型に <xref:System.ComponentModel.INotifyPropertyChanged> インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="7017e-160">Implements the <xref:System.ComponentModel.INotifyPropertyChanged> interface on all generated types to enable data binding.</span></span> <span data-ttu-id="7017e-161">短縮形は `/edb` です。</span><span class="sxs-lookup"><span data-stu-id="7017e-161">The short form is `/edb`.</span></span>|
|<span data-ttu-id="7017e-162">**/enableLinqDataSet**</span><span class="sxs-lookup"><span data-stu-id="7017e-162">**/enableLinqDataSet**</span></span>|<span data-ttu-id="7017e-163">(短縮形: `/eld`)LINQ to DataSet を使用して、生成された DataSet を照会できるように指定します。</span><span class="sxs-lookup"><span data-stu-id="7017e-163">(Short form: `/eld`.) Specifies that the generated DataSet can be queried against using LINQ to DataSet.</span></span> <span data-ttu-id="7017e-164">このオプションは /dataset オプションも指定した場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="7017e-164">This option is used when the /dataset option is also specified.</span></span> <span data-ttu-id="7017e-165">詳細については、「[LINQ to DataSet Overview](../../framework/data/adonet/linq-to-dataset-overview.md)」(LINQ to DataSet Overview) と「[Querying Typed DataSets](../../framework/data/adonet/querying-typed-datasets.md)」(型指定された DataSet のクエリ) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7017e-165">For more information, see [LINQ to DataSet Overview](../../framework/data/adonet/linq-to-dataset-overview.md) and [Querying Typed DataSets](../../framework/data/adonet/querying-typed-datasets.md).</span></span> <span data-ttu-id="7017e-166">LINQ の使用に関する一般的な情報については、「[統合言語クエリ (LINQ) - C#](../../csharp/programming-guide/concepts/linq/index.md)」または「[統合言語クエリ (LINQ) - Visual Basic](../../visual-basic/programming-guide/concepts/linq/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7017e-166">For general information about using LINQ, see [Language-Integrated Query (LINQ) - C#](../../csharp/programming-guide/concepts/linq/index.md) or [Language-Integrated Query (LINQ) - Visual Basic](../../visual-basic/programming-guide/concepts/linq/index.md).</span></span>|
|<span data-ttu-id="7017e-167">**/f\[ields\]**</span><span class="sxs-lookup"><span data-stu-id="7017e-167">**/f\[ields\]**</span></span>|<span data-ttu-id="7017e-168">プロパティの代わりにフィールドを生成します。</span><span class="sxs-lookup"><span data-stu-id="7017e-168">Generates fields instead of properties.</span></span> <span data-ttu-id="7017e-169">既定では、プロパティが生成されます。</span><span class="sxs-lookup"><span data-stu-id="7017e-169">By default, properties are generated.</span></span>|
|<span data-ttu-id="7017e-170">**/l\[anguage\]:** _language_</span><span class="sxs-lookup"><span data-stu-id="7017e-170">**/l\[anguage\]:**_language_</span></span>|<span data-ttu-id="7017e-171">使用するプログラミング言語を指定します。</span><span class="sxs-lookup"><span data-stu-id="7017e-171">Specifies the programming language to use.</span></span> <span data-ttu-id="7017e-172">`CS` (C#、既定値)、`VB` (Visual Basic)、`JS` (JScript)、または `VJS` (Visual J#) から選択します。</span><span class="sxs-lookup"><span data-stu-id="7017e-172">Choose from `CS` (C#, which is the default), `VB` (Visual Basic), `JS` (JScript), or `VJS` (Visual J#).</span></span> <span data-ttu-id="7017e-173"><xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> を実装するクラスの完全修飾名を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="7017e-173">You can also specify a fully qualified name for a class implementing <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType></span></span>|
|<span data-ttu-id="7017e-174">**/n\[amespace\]:** _namespace_</span><span class="sxs-lookup"><span data-stu-id="7017e-174">**/n\[amespace\]:**_namespace_</span></span>|<span data-ttu-id="7017e-175">生成する型のランタイム名前空間を指定します。</span><span class="sxs-lookup"><span data-stu-id="7017e-175">Specifies the runtime namespace for the generated types.</span></span> <span data-ttu-id="7017e-176">既定の名前空間は `Schemas` です。</span><span class="sxs-lookup"><span data-stu-id="7017e-176">The default namespace is `Schemas`.</span></span>|
|<span data-ttu-id="7017e-177">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="7017e-177">**/nologo**</span></span>|<span data-ttu-id="7017e-178">バナーを表示しません。</span><span class="sxs-lookup"><span data-stu-id="7017e-178">Suppresses the banner.</span></span>|
|<span data-ttu-id="7017e-179">**/order**</span><span class="sxs-lookup"><span data-stu-id="7017e-179">**/order**</span></span>|<span data-ttu-id="7017e-180">すべてのパーティクル メンバーに明示的な順序 ID を生成します。</span><span class="sxs-lookup"><span data-stu-id="7017e-180">Generates explicit order identifiers on all particle members.</span></span>|
|<span data-ttu-id="7017e-181">**/o\[ut\]:** _directoryName_</span><span class="sxs-lookup"><span data-stu-id="7017e-181">**/o\[ut\]:**_directoryName_</span></span>|<span data-ttu-id="7017e-182">ファイルを格納する出力ディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="7017e-182">Specifies the output directory to place the files in.</span></span> <span data-ttu-id="7017e-183">既定値は、現在のディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="7017e-183">The default is the current directory.</span></span>|
|<span data-ttu-id="7017e-184">**/u\[ri\]:** _uri_</span><span class="sxs-lookup"><span data-stu-id="7017e-184">**/u\[ri\]:**_uri_</span></span>|<span data-ttu-id="7017e-185">コードを生成する対象とする、スキーマ内の要素の URI を指定します。</span><span class="sxs-lookup"><span data-stu-id="7017e-185">Specifies the URI for the elements in the schema to generate code for.</span></span> <span data-ttu-id="7017e-186">指定した場合、この URI は `/element` オプションで指定したすべての要素に適用されます。</span><span class="sxs-lookup"><span data-stu-id="7017e-186">This URI, if present, applies to all elements specified with the `/element` option.</span></span>|

## <a name="dll-and-exe-file-options"></a><span data-ttu-id="7017e-187">DLL ファイルと EXE ファイルのオプション</span><span class="sxs-lookup"><span data-stu-id="7017e-187">DLL and EXE File Options</span></span>

|<span data-ttu-id="7017e-188">オプション</span><span class="sxs-lookup"><span data-stu-id="7017e-188">Option</span></span>|<span data-ttu-id="7017e-189">説明</span><span class="sxs-lookup"><span data-stu-id="7017e-189">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="7017e-190">**/t\[ype\]:** _typename_</span><span class="sxs-lookup"><span data-stu-id="7017e-190">**/t\[ype\]:**_typename_</span></span>|<span data-ttu-id="7017e-191">スキーマの作成対象とする型の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="7017e-191">Specifies the name of the type to create a schema for.</span></span> <span data-ttu-id="7017e-192">複数の型の引数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="7017e-192">You can specify multiple type arguments.</span></span> <span data-ttu-id="7017e-193">*typename* によって名前空間が特定されない場合、指定された型を持つアセンブリに含まれるすべての型が対象となります。</span><span class="sxs-lookup"><span data-stu-id="7017e-193">If *typename* does not specify a namespace, Xsd.exe matches all types in the assembly with the specified type.</span></span> <span data-ttu-id="7017e-194">*typename* によって名前空間が特定される場合は、その型だけが対象になります。</span><span class="sxs-lookup"><span data-stu-id="7017e-194">If *typename* specifies a namespace, only that type is matched.</span></span> <span data-ttu-id="7017e-195">*typename* の末尾がアスタリスク (\*) の場合は、\* の前にある文字列で始まる型のすべてが対象となります。</span><span class="sxs-lookup"><span data-stu-id="7017e-195">If *typename* ends with an asterisk character (\*), the tool matches all types that start with the string preceding the \*.</span></span> <span data-ttu-id="7017e-196">`/type` オプションを省略すると、アセンブリに含まれるすべての型についてスキーマが生成されます。</span><span class="sxs-lookup"><span data-stu-id="7017e-196">If you omit the `/type` option, Xsd.exe generates schemas for all types in the assembly.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7017e-197">Remarks</span><span class="sxs-lookup"><span data-stu-id="7017e-197">Remarks</span></span>

<span data-ttu-id="7017e-198">Xsd.exe が実行する操作を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="7017e-198">The following table shows the operations that Xsd.exe performs.</span></span>

| | |
|------------|-----------------|
|<span data-ttu-id="7017e-199">XDR から XSD へ</span><span class="sxs-lookup"><span data-stu-id="7017e-199">XDR to XSD</span></span>|<span data-ttu-id="7017e-200">XML-Data-Reduced スキーマ ファイルから XML スキーマを生成します。</span><span class="sxs-lookup"><span data-stu-id="7017e-200">Generates an XML schema from an XML-Data-Reduced schema file.</span></span> <span data-ttu-id="7017e-201">XDR は初期の XML ベースのスキーマ形式です。</span><span class="sxs-lookup"><span data-stu-id="7017e-201">XDR is an early XML-based schema format.</span></span>|
|<span data-ttu-id="7017e-202">XML から XSD へ</span><span class="sxs-lookup"><span data-stu-id="7017e-202">XML to XSD</span></span>|<span data-ttu-id="7017e-203">XML ファイルから XML スキーマを生成します。</span><span class="sxs-lookup"><span data-stu-id="7017e-203">Generates an XML schema from an XML file.</span></span>|
|<span data-ttu-id="7017e-204">XSD から DataSet へ</span><span class="sxs-lookup"><span data-stu-id="7017e-204">XSD to DataSet</span></span>|<span data-ttu-id="7017e-205">XSD スキーマ ファイルから共通言語ランタイムの <xref:System.Data.DataSet> クラスを生成します。</span><span class="sxs-lookup"><span data-stu-id="7017e-205">Generates common language runtime <xref:System.Data.DataSet> classes from an XSD schema file.</span></span> <span data-ttu-id="7017e-206">生成されるクラスには、標準の XML データ用のリッチ オブジェクト モデルが用意されています。</span><span class="sxs-lookup"><span data-stu-id="7017e-206">The generated classes provide a rich object model for regular XML data.</span></span>|
|<span data-ttu-id="7017e-207">XSD からクラスへ</span><span class="sxs-lookup"><span data-stu-id="7017e-207">XSD to Classes</span></span>|<span data-ttu-id="7017e-208">XSD スキーマ ファイルからランタイム クラスを生成します。</span><span class="sxs-lookup"><span data-stu-id="7017e-208">Generates runtime classes from an XSD schema file.</span></span> <span data-ttu-id="7017e-209">生成されたクラスを <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> と組み合わせて使用すると、このスキーマに従う XML コードの読み書きを実行できます。</span><span class="sxs-lookup"><span data-stu-id="7017e-209">The generated classes can be used in conjunction with <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> to read and write XML code that follows the schema.</span></span>|
|<span data-ttu-id="7017e-210">クラスから XSD へ</span><span class="sxs-lookup"><span data-stu-id="7017e-210">Classes to XSD</span></span>| <span data-ttu-id="7017e-211">ランタイム アセンブリ ファイルに含まれる 1 つ以上の型から XML スキーマを生成します。</span><span class="sxs-lookup"><span data-stu-id="7017e-211">Generates an XML schema from a type or types in a runtime assembly file.</span></span> <span data-ttu-id="7017e-212">生成されたスキーマは、<xref:System.Xml.Serialization.XmlSerializer> で使用される XML 形式を定義します。</span><span class="sxs-lookup"><span data-stu-id="7017e-212">The generated schema defines the XML format used by the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>|

 <span data-ttu-id="7017e-213">Xsd.exe によって操作できるのは、W3C (World Wide Web Consortium) が提唱する XSD (XML スキーマ定義) に準拠した XML スキーマだけです。</span><span class="sxs-lookup"><span data-stu-id="7017e-213">Xsd.exe only allows you to manipulate XML schemas that follow the XML Schema Definition (XSD) language proposed by the World Wide Web Consortium (W3C).</span></span> <span data-ttu-id="7017e-214">XML スキーマ定義の提唱や XML 標準の詳細については、<https://w3.org> を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7017e-214">For more information on the XML Schema Definition proposal or the XML standard, see <https://w3.org>.</span></span>

## <a name="setting-options-with-an-xml-file"></a><span data-ttu-id="7017e-215">XML ファイルによるオプションの設定</span><span class="sxs-lookup"><span data-stu-id="7017e-215">Setting Options with an XML File</span></span>

<span data-ttu-id="7017e-216">`/parameters` スイッチを使用すると、各種のオプションを設定する単一の XML ファイルを指定できます。</span><span class="sxs-lookup"><span data-stu-id="7017e-216">By using the `/parameters` switch, you can specify a single XML file that sets various options.</span></span> <span data-ttu-id="7017e-217">設定できるオプションは、XSD.exe ツールの使用方法によって異なります。</span><span class="sxs-lookup"><span data-stu-id="7017e-217">The options you can set depend on how you are using the XSD.exe tool.</span></span> <span data-ttu-id="7017e-218">選択肢には、スキーマの生成、コード ファイルの生成、または `DataSet` 機能を含むコード ファイルの生成があります。</span><span class="sxs-lookup"><span data-stu-id="7017e-218">Choices include generating schemas, generating code files, or generating code files that include `DataSet` features.</span></span> <span data-ttu-id="7017e-219">たとえば、コード ファイルではなくスキーマを生成する場合、実行可能ファイル (.exe) またはタイプ ライブラリ (.dll) ファイルの名前に `<assembly>` 要素を設定できます。</span><span class="sxs-lookup"><span data-stu-id="7017e-219">For example, you can set the `<assembly>` element to the name of an executable (.exe) or type library (.dll) file when generating a schema, but not when generating a code file.</span></span> <span data-ttu-id="7017e-220">次の XML に、指定された実行可能ファイルで `<generateSchemas>` 要素を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="7017e-220">The following XML shows how to use the `<generateSchemas>` element with a specified executable:</span></span>

```xml
<!-- This is in a file named GenerateSchemas.xml. -->
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
<generateSchemas>
   <assembly>ConsoleApplication1.exe</assembly>
</generateSchemas>
</xsd>
```

<span data-ttu-id="7017e-221">この XML が GenerateSchemas.xml というファイルに含まれる場合、コマンド プロンプトで、`/parameters` スイッチを使用して次のように入力し、**Enter** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="7017e-221">If the preceding XML is contained in a file named GenerateSchemas.xml, then use the `/parameters` switch by typing the following at a command prompt and pressing **Enter**:</span></span>

```console
 xsd /p:GenerateSchemas.xml
```

<span data-ttu-id="7017e-222">アセンブリにある単一の型のスキーマを生成する場合は、次のような XML を使用します。</span><span class="sxs-lookup"><span data-stu-id="7017e-222">On the other hand, if you are generating a schema for a single type found in the assembly, you can use the following XML:</span></span>

```xml
<!-- This is in a file named GenerateSchemaFromType.xml. -->
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
<generateSchemas>
   <type>IDItems</type>
</generateSchemas>
</xsd>
```

<span data-ttu-id="7017e-223">しかし、上のコードを使用するには、コマンド プロンプトでアセンブリの名前も指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7017e-223">But to use preceding code, you must also supply the name of the assembly at the command prompt.</span></span> <span data-ttu-id="7017e-224">コマンド プロンプトで次のように入力します (XML ファイルの名前を GenerateSchemaFromType.xml と仮定します)。</span><span class="sxs-lookup"><span data-stu-id="7017e-224">Enter the following at a command prompt (presuming the XML file is named GenerateSchemaFromType.xml):</span></span>

```console
xsd /p:GenerateSchemaFromType.xml ConsoleApplication1.exe
```

<span data-ttu-id="7017e-225">`<generateSchemas>` 要素に対しては、次のオプションのうち 1 つだけを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7017e-225">You must specify only one of the following options for the `<generateSchemas>` element.</span></span>

|<span data-ttu-id="7017e-226">要素</span><span class="sxs-lookup"><span data-stu-id="7017e-226">Element</span></span>|<span data-ttu-id="7017e-227">説明</span><span class="sxs-lookup"><span data-stu-id="7017e-227">Description</span></span>|
|-------------|-----------------|
|\<assembly>|<span data-ttu-id="7017e-228">スキーマを生成するアセンブリを指定します。</span><span class="sxs-lookup"><span data-stu-id="7017e-228">Specifies an assembly to generate the schema from.</span></span>|
|\<type>|<span data-ttu-id="7017e-229">スキーマを生成するアセンブリに含まれる型を指定します。</span><span class="sxs-lookup"><span data-stu-id="7017e-229">Specifies a type found in an assembly to generate a schema for.</span></span>|
|\<xml>|<span data-ttu-id="7017e-230">スキーマを生成する XML ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="7017e-230">Specifies an XML file to generate a schema for.</span></span>|
|\<xdr>|<span data-ttu-id="7017e-231">スキーマを生成する XDR ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="7017e-231">Specifies an XDR file to generate a schema for.</span></span>|

<span data-ttu-id="7017e-232">コード ファイルを生成するには、`<generateClasses>` 要素を使用します。</span><span class="sxs-lookup"><span data-stu-id="7017e-232">To generate a code file, use the `<generateClasses>` element.</span></span> <span data-ttu-id="7017e-233">コード ファイルを生成する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="7017e-233">The following example generates a code file.</span></span> <span data-ttu-id="7017e-234">この例では、生成されるファイルのプログラミング言語と名前空間を設定するための 2 つの属性も示されています。</span><span class="sxs-lookup"><span data-stu-id="7017e-234">Note that two attributes are also shown that allow you to set the programming language and namespace of the generated file.</span></span>

```xml
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
<generateClasses language='VB' namespace='Microsoft.Serialization.Examples'/>
</xsd>
<!-- You must supply an .xsd file when typing in the command line.-->
<!-- For example: xsd /p:genClasses mySchema.xsd -->
```

 <span data-ttu-id="7017e-235">`<generateClasses>` 要素に設定できるオプションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7017e-235">Options you can set for the `<generateClasses>` element include the following.</span></span>

|<span data-ttu-id="7017e-236">要素</span><span class="sxs-lookup"><span data-stu-id="7017e-236">Element</span></span>|<span data-ttu-id="7017e-237">説明</span><span class="sxs-lookup"><span data-stu-id="7017e-237">Description</span></span>|
|-------------|-----------------|
|\<element>|<span data-ttu-id="7017e-238">コードを生成する対象となる .xsd ファイルの要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="7017e-238">Specifies an element in the .xsd file to generate code for.</span></span>|
|\<schemaImporterExtensions>|<span data-ttu-id="7017e-239"><xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> クラスから派生する型を指定します。</span><span class="sxs-lookup"><span data-stu-id="7017e-239">Specifies a type derived from the <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> class.</span></span>|
|\<schema>|<span data-ttu-id="7017e-240">コードを生成する XML スキーマ ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="7017e-240">Specifies a XML Schema file to generate code for.</span></span> <span data-ttu-id="7017e-241">複数の \<schema> 要素を使用して、複数の XML スキーマ ファイルを指定できます。</span><span class="sxs-lookup"><span data-stu-id="7017e-241">Multiple XML Schema files can be specified using multiple \<schema> elements.</span></span>|

<span data-ttu-id="7017e-242">次の表に、`<generateClasses>` 要素と共に使用するその他の属性を示します。</span><span class="sxs-lookup"><span data-stu-id="7017e-242">The following table shows the attributes that can also be used with the `<generateClasses>` element.</span></span>

|<span data-ttu-id="7017e-243">属性</span><span class="sxs-lookup"><span data-stu-id="7017e-243">Attribute</span></span>|<span data-ttu-id="7017e-244">説明</span><span class="sxs-lookup"><span data-stu-id="7017e-244">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="7017e-245">language</span><span class="sxs-lookup"><span data-stu-id="7017e-245">language</span></span>|<span data-ttu-id="7017e-246">使用するプログラミング言語を指定します。</span><span class="sxs-lookup"><span data-stu-id="7017e-246">Specifies the programming language to use.</span></span> <span data-ttu-id="7017e-247">`CS` (C#、既定値)、`VB` (Visual Basic)、`JS` (JScript)、または `VJS` (Visual J#) から選択します。</span><span class="sxs-lookup"><span data-stu-id="7017e-247">Choose from `CS` (C#, the default), `VB` (Visual Basic), `JS` (JScript), or `VJS` (Visual J#).</span></span> <span data-ttu-id="7017e-248"><xref:System.CodeDom.Compiler.CodeDomProvider> を実装するクラスの完全修飾名を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="7017e-248">You can also specify a fully qualified name for a class that implements <xref:System.CodeDom.Compiler.CodeDomProvider>.</span></span>|
|<span data-ttu-id="7017e-249">namespace</span><span class="sxs-lookup"><span data-stu-id="7017e-249">namespace</span></span>|<span data-ttu-id="7017e-250">生成するコードの名前空間を指定します。</span><span class="sxs-lookup"><span data-stu-id="7017e-250">Specifies the namespace for the generated code.</span></span> <span data-ttu-id="7017e-251">名前空間は、スペースやバックスラッシュ文字を使用しないなどの CLR 標準に準拠する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7017e-251">The namespace must conform to CLR standards (for example, no spaces or backslash characters).</span></span>|
|<span data-ttu-id="7017e-252">options</span><span class="sxs-lookup"><span data-stu-id="7017e-252">options</span></span>|<span data-ttu-id="7017e-253">`none`、`properties` (パブリック フィールドの代わりにプロパティを生成)、`order`、または `enableDataBinding` (前の「XSD ファイルのオプション」セクションの `/order` と `/enableDataBinding` スイッチを参照) のいずれかの値です。</span><span class="sxs-lookup"><span data-stu-id="7017e-253">One of the following values: `none`, `properties` (generates properties instead of public fields), `order`, or `enableDataBinding` (see the `/order` and `/enableDataBinding` switches in the preceding XSD File Options section.</span></span>|

 <span data-ttu-id="7017e-254">`DataSet` 要素を使用すると、`<generateDataSet>` コードを生成する方法を制御できます。</span><span class="sxs-lookup"><span data-stu-id="7017e-254">You can also control how `DataSet` code is generated by using the `<generateDataSet>` element.</span></span> <span data-ttu-id="7017e-255">次の XML は、生成されたコードが `DataSet` 構造体 (<xref:System.Data.DataTable> クラスなど) を使用して指定された要素のための Visual Basic コードを作成するように指定します。</span><span class="sxs-lookup"><span data-stu-id="7017e-255">The following XML specifies that the generated code uses `DataSet` structures (such as the <xref:System.Data.DataTable> class) to create Visual Basic code for a specified element.</span></span> <span data-ttu-id="7017e-256">生成された DataSet 構造体では LINQ クエリがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="7017e-256">The generated DataSet structures will support LINQ queries.</span></span>

 ```xml
 <xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
     <generateDataSet language='VB' namespace='Microsoft.Serialization.Examples' enableLinqDataSet='true'>
     </generateDataSet>
 </xsd>
```

<span data-ttu-id="7017e-257">`<generateDataSet>` 要素に設定できるオプションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7017e-257">Options you can set for the `<generateDataSet>` element include the following.</span></span>

|<span data-ttu-id="7017e-258">要素</span><span class="sxs-lookup"><span data-stu-id="7017e-258">Element</span></span>|<span data-ttu-id="7017e-259">説明</span><span class="sxs-lookup"><span data-stu-id="7017e-259">Description</span></span>|
|-------------|-----------------|
|\<schema>|<span data-ttu-id="7017e-260">コードを生成する XML スキーマ ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="7017e-260">Specifies an XML Schema file to generate code for.</span></span> <span data-ttu-id="7017e-261">複数の \<schema> 要素を使用して、複数の XML スキーマ ファイルを指定できます。</span><span class="sxs-lookup"><span data-stu-id="7017e-261">Multiple XML Schema files can be specified using multiple \<schema> elements.</span></span>|

 <span data-ttu-id="7017e-262">`<generateDataSet>` 要素と共に使用できる属性を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="7017e-262">The following table shows the attributes that can be used with the `<generateDataSet>` element.</span></span>

|<span data-ttu-id="7017e-263">属性</span><span class="sxs-lookup"><span data-stu-id="7017e-263">Attribute</span></span>|<span data-ttu-id="7017e-264">説明</span><span class="sxs-lookup"><span data-stu-id="7017e-264">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="7017e-265">enableLinqDataSet</span><span class="sxs-lookup"><span data-stu-id="7017e-265">enableLinqDataSet</span></span>|<span data-ttu-id="7017e-266">LINQ to DataSet を使用して、生成された DataSet を照会できるように指定します。</span><span class="sxs-lookup"><span data-stu-id="7017e-266">Specifies that the generated DataSet can be queried against using LINQ to DataSet.</span></span> <span data-ttu-id="7017e-267">既定値は false です。</span><span class="sxs-lookup"><span data-stu-id="7017e-267">The default value is false.</span></span>|
|<span data-ttu-id="7017e-268">language</span><span class="sxs-lookup"><span data-stu-id="7017e-268">language</span></span>|<span data-ttu-id="7017e-269">使用するプログラミング言語を指定します。</span><span class="sxs-lookup"><span data-stu-id="7017e-269">Specifies the programming language to use.</span></span> <span data-ttu-id="7017e-270">`CS` (C#、既定値)、`VB` (Visual Basic)、`JS` (JScript)、または `VJS` (Visual J#) から選択します。</span><span class="sxs-lookup"><span data-stu-id="7017e-270">Choose from `CS` (C#, the default), `VB` (Visual Basic), `JS` (JScript), or `VJS` (Visual J#).</span></span> <span data-ttu-id="7017e-271"><xref:System.CodeDom.Compiler.CodeDomProvider> を実装するクラスの完全修飾名を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="7017e-271">You can also specify a fully qualified name for a class that implements <xref:System.CodeDom.Compiler.CodeDomProvider>.</span></span>|
|<span data-ttu-id="7017e-272">namespace</span><span class="sxs-lookup"><span data-stu-id="7017e-272">namespace</span></span>|<span data-ttu-id="7017e-273">生成するコードの名前空間を指定します。</span><span class="sxs-lookup"><span data-stu-id="7017e-273">Specifies the namespace for the generated code.</span></span> <span data-ttu-id="7017e-274">名前空間は、スペースやバックスラッシュ文字を使用しないなどの CLR 標準に準拠する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7017e-274">The namespace must conform to CLR standards (for example, no spaces or backslash characters).</span></span>|

 <span data-ttu-id="7017e-275">トップ レベルの `<xsd>` 要素に設定できる属性があります。</span><span class="sxs-lookup"><span data-stu-id="7017e-275">There are attributes that you can set on the top level `<xsd>` element.</span></span> <span data-ttu-id="7017e-276">これらのオプションは、`<generateSchemas>`、`<generateClasses>`、または `<generateDataSet>` の各子要素と共に使用できます。</span><span class="sxs-lookup"><span data-stu-id="7017e-276">These options can be used with any of the child elements (`<generateSchemas>`, `<generateClasses>` or `<generateDataSet>`).</span></span> <span data-ttu-id="7017e-277">次の XML コードは、"MyOutputDirectory" という出力ディレクトリの "IDItems" という要素のコードを生成します。</span><span class="sxs-lookup"><span data-stu-id="7017e-277">The following XML code generates code for an element named "IDItems" in the output directory named "MyOutputDirectory".</span></span>

```xml
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/' output='MyOutputDirectory'>
<generateClasses>
    <element>IDItems</element>
</generateClasses>
</xsd>
```

<span data-ttu-id="7017e-278">次の表に、`<xsd>` 要素と共に使用するその他の属性を示します。</span><span class="sxs-lookup"><span data-stu-id="7017e-278">The following table shows the attributes that can also be used with the `<xsd>` element.</span></span>

|<span data-ttu-id="7017e-279">属性</span><span class="sxs-lookup"><span data-stu-id="7017e-279">Attribute</span></span>|<span data-ttu-id="7017e-280">説明</span><span class="sxs-lookup"><span data-stu-id="7017e-280">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="7017e-281">出力</span><span class="sxs-lookup"><span data-stu-id="7017e-281">output</span></span>|<span data-ttu-id="7017e-282">生成されたスキーマまたはコード ファイルが格納されるディレクトリの名前です。</span><span class="sxs-lookup"><span data-stu-id="7017e-282">The name of a directory where the generated schema or code file will be placed.</span></span>|
|<span data-ttu-id="7017e-283">nologo</span><span class="sxs-lookup"><span data-stu-id="7017e-283">nologo</span></span>|<span data-ttu-id="7017e-284">バナーを表示しません。</span><span class="sxs-lookup"><span data-stu-id="7017e-284">Suppresses the banner.</span></span> <span data-ttu-id="7017e-285">`true` または `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="7017e-285">Set to `true` or `false`.</span></span>|
|<span data-ttu-id="7017e-286">help</span><span class="sxs-lookup"><span data-stu-id="7017e-286">help</span></span>|<span data-ttu-id="7017e-287">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="7017e-287">Displays command syntax and options for the tool.</span></span> <span data-ttu-id="7017e-288">`true` または `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="7017e-288">Set to `true` or `false`.</span></span>|

## <a name="examples"></a><span data-ttu-id="7017e-289">使用例</span><span class="sxs-lookup"><span data-stu-id="7017e-289">Examples</span></span>

 <span data-ttu-id="7017e-290">`myFile.xdr` から XML スキーマを生成し、現在のディレクトリに保存するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="7017e-290">The following command generates an XML schema from `myFile.xdr` and saves it to the current directory.</span></span>

```console
xsd myFile.xdr
```

<span data-ttu-id="7017e-291">`myFile.xml` から XML スキーマを生成し、指定したディレクトリに保存するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="7017e-291">The following command generates an XML schema from `myFile.xml` and saves it to the specified directory.</span></span>

```console
xsd myFile.xml /outputdir:myOutputDir
```

<span data-ttu-id="7017e-292">指定したスキーマと対応するデータセットを C# 言語で生成し、現在のディレクトリ内に `XSDSchemaFile.cs` として保存するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="7017e-292">The following command generates a data set that corresponds to the specified schema in the C# language and saves it as `XSDSchemaFile.cs` in the current directory.</span></span>

```console
xsd /dataset /language:CS XSDSchemaFile.xsd
```

<span data-ttu-id="7017e-293">`myAssembly.dll` アセンブリ内のすべての型について XML スキーマを生成し、それらを `schema0.xsd` として現在のディレクトリ内に保存するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="7017e-293">The following command generates XML schemas for all types in the assembly `myAssembly.dll` and saves them as `schema0.xsd` in the current directory.</span></span>

```console
xsd myAssembly.dll
```

## <a name="see-also"></a><span data-ttu-id="7017e-294">関連項目</span><span class="sxs-lookup"><span data-stu-id="7017e-294">See also</span></span>

- <xref:System.Data.DataSet>
- <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
- [<span data-ttu-id="7017e-295">ツール</span><span class="sxs-lookup"><span data-stu-id="7017e-295">Tools</span></span>](../../framework/tools/index.md)
- [<span data-ttu-id="7017e-296">開発者コマンドライン シェル</span><span class="sxs-lookup"><span data-stu-id="7017e-296">Developer command-line shells</span></span>](/visualstudio/ide/reference/command-prompt-powershell)
- [<span data-ttu-id="7017e-297">LINQ to DataSet の概要</span><span class="sxs-lookup"><span data-stu-id="7017e-297">LINQ to DataSet Overview</span></span>](../../framework/data/adonet/linq-to-dataset-overview.md)
- [<span data-ttu-id="7017e-298">型指定された DataSet のクエリ</span><span class="sxs-lookup"><span data-stu-id="7017e-298">Querying Typed DataSets</span></span>](../../framework/data/adonet/querying-typed-datasets.md)
- [<span data-ttu-id="7017e-299">統合言語クエリ (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="7017e-299">LINQ (Language-Integrated Query) (C#)</span></span>](../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="7017e-300">統合言語クエリ (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7017e-300">LINQ (Language-Integrated Query) (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/index.md)
