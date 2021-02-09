---
description: '詳細情報: メタデータと自己言及的なコンポーネント'
title: メタデータと自己言及的なコンポーネント
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- runtime, metadata
- languages, interoperability
- portable executable files, metadata
- self-describing files
- metadata, about metadata
- common language runtime, metadata
- PE files, metadata
- components [.NET], metadata
ms.assetid: 3dd13c5d-a508-455b-8dce-0a852882a5a7
ms.openlocfilehash: 5f043a1e204c019f83fb15705ca44562a82ad6a2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702211"
---
# <a name="metadata-and-self-describing-components"></a><span data-ttu-id="40351-103">メタデータと自己言及的なコンポーネント</span><span class="sxs-lookup"><span data-stu-id="40351-103">Metadata and Self-Describing Components</span></span>

<span data-ttu-id="40351-104">以前は、ある 1 つの言語で記述されたソフトウェア コンポーネント (.exe または .dll) で、別の言語で記述されたコンポーネントを使用するのは簡単ではありませんでした。</span><span class="sxs-lookup"><span data-stu-id="40351-104">In the past, a software component (.exe or .dll) that was written in one language could not easily use a software component that was written in another language.</span></span> <span data-ttu-id="40351-105">COM により、この問題が解決するための手段が提供されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="40351-105">COM provided a step towards solving this problem.</span></span> <span data-ttu-id="40351-106">.NET により、コンパイラからすべてのモジュールやアセンブリに追加の宣言情報を挿入できるようすることで、コンポーネントの相互運用性がより簡易化されています。</span><span class="sxs-lookup"><span data-stu-id="40351-106">.NET makes component interoperation even easier by allowing compilers to emit additional declarative information into all modules and assemblies.</span></span> <span data-ttu-id="40351-107">メタデータと呼ばれるこの情報により、コンポーネント間のシームレスな相互作用がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="40351-107">This information, called metadata, helps components to interact seamlessly.</span></span>

 <span data-ttu-id="40351-108">メタデータはプログラムを説明するバイナリ情報であり、共通言語ランタイムのポータブル実行可能 (PE) ファイルまたはメモリのいずれかに格納されます。</span><span class="sxs-lookup"><span data-stu-id="40351-108">Metadata is binary information describing your program that is stored either in a common language runtime portable executable (PE) file or in memory.</span></span> <span data-ttu-id="40351-109">コードを PE ファイルとしてコンパイルすると、PE ファイルの特定の部分にメタデータが挿入され、コードは Microsoft Intermediate Language (MSIL) に変換されて PE ファイル内の別の部分に挿入されます。</span><span class="sxs-lookup"><span data-stu-id="40351-109">When you compile your code into a PE file, metadata is inserted into one portion of the file, and your code is converted to Microsoft intermediate language (MSIL) and inserted into another portion of the file.</span></span> <span data-ttu-id="40351-110">モジュール内またはアセンブリ内で定義され、参照されているすべての型およびメンバーは、メタデータ内部に記述されます。</span><span class="sxs-lookup"><span data-stu-id="40351-110">Every type and member that is defined and referenced in a module or assembly is described within metadata.</span></span> <span data-ttu-id="40351-111">コードを実行すると、ランタイムはメタデータをメモリに読み込み、コードのクラス、メンバー、継承などの情報を検索するためにメタデータを参照します。</span><span class="sxs-lookup"><span data-stu-id="40351-111">When code is executed, the runtime loads metadata into memory and references it to discover information about your code's classes, members, inheritance, and so on.</span></span>

 <span data-ttu-id="40351-112">メタデータには、コードに定義されているすべての型およびメンバーが言語に中立的な形で記述されています。</span><span class="sxs-lookup"><span data-stu-id="40351-112">Metadata describes every type and member defined in your code in a language-neutral manner.</span></span> <span data-ttu-id="40351-113">メタデータには、次の情報が格納されいてます。</span><span class="sxs-lookup"><span data-stu-id="40351-113">Metadata stores the following information:</span></span>

- <span data-ttu-id="40351-114">アセンブリに関する記述</span><span class="sxs-lookup"><span data-stu-id="40351-114">Description of the assembly.</span></span>

  - <span data-ttu-id="40351-115">ID (名前、バージョン、カルチャ、公開キー)</span><span class="sxs-lookup"><span data-stu-id="40351-115">Identity (name, version, culture, public key).</span></span>

  - <span data-ttu-id="40351-116">エクスポートされる型</span><span class="sxs-lookup"><span data-stu-id="40351-116">The types that are exported.</span></span>

  - <span data-ttu-id="40351-117">そのアセンブリが依存している他のアセンブリ</span><span class="sxs-lookup"><span data-stu-id="40351-117">Other assemblies that this assembly depends on.</span></span>

  - <span data-ttu-id="40351-118">実行のために必要なセキュリティ アクセス許可</span><span class="sxs-lookup"><span data-stu-id="40351-118">Security permissions needed to run.</span></span>

- <span data-ttu-id="40351-119">型に関する説明</span><span class="sxs-lookup"><span data-stu-id="40351-119">Description of types.</span></span>

  - <span data-ttu-id="40351-120">名前、参照可能範囲、基底クラス、および実装されているインターフェイス</span><span class="sxs-lookup"><span data-stu-id="40351-120">Name, visibility, base class, and interfaces implemented.</span></span>

  - <span data-ttu-id="40351-121">メンバー (メソッド、フィールド、プロパティ、イベント、入れ子になった型)</span><span class="sxs-lookup"><span data-stu-id="40351-121">Members (methods, fields, properties, events, nested types).</span></span>

- <span data-ttu-id="40351-122">属性。</span><span class="sxs-lookup"><span data-stu-id="40351-122">Attributes.</span></span>

  - <span data-ttu-id="40351-123">型やメンバーを修飾する追加の記述要素</span><span class="sxs-lookup"><span data-stu-id="40351-123">Additional descriptive elements that modify types and members.</span></span>

## <a name="benefits-of-metadata"></a><span data-ttu-id="40351-124">メタデータの利点</span><span class="sxs-lookup"><span data-stu-id="40351-124">Benefits of Metadata</span></span>

<span data-ttu-id="40351-125">メタデータは、プログラミング モデルを簡素化するうえで重要な役割を果たします。これにより、インターフェイス定義言語 (IDL: Interface Definition Language) ファイル、ヘッダー ファイル、およびその他のコンポーネント参照の外部メソッドは一切不要になります。</span><span class="sxs-lookup"><span data-stu-id="40351-125">Metadata is the key to a simpler programming model, and eliminates the need for Interface Definition Language (IDL) files, header files, or any external method of component reference.</span></span> <span data-ttu-id="40351-126">メタデータを使用すると、.NET の各言語は、開発者やユーザーからは見えない、言語に依存しない形式で自動的に記述されるようになります。</span><span class="sxs-lookup"><span data-stu-id="40351-126">Metadata enables .NET languages to describe themselves automatically in a language-neutral manner, unseen by both the developer and the user.</span></span> <span data-ttu-id="40351-127">また、属性を使用することにより、メタデータを拡張することもできます。</span><span class="sxs-lookup"><span data-stu-id="40351-127">Additionally, metadata is extensible through the use of attributes.</span></span> <span data-ttu-id="40351-128">メタデータの主な利点は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="40351-128">Metadata provides the following major benefits:</span></span>

- <span data-ttu-id="40351-129">自己言及的なファイル</span><span class="sxs-lookup"><span data-stu-id="40351-129">Self-describing files.</span></span>

  <span data-ttu-id="40351-130">共通言語ランタイム モジュールおよびアセンブリは、自己言及的なファイルです。</span><span class="sxs-lookup"><span data-stu-id="40351-130">Common language runtime modules and assemblies are self-describing.</span></span> <span data-ttu-id="40351-131">モジュールのメタデータには、他のモジュールと相互作用するのに必要なすべての情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="40351-131">A module's metadata contains everything needed to interact with another module.</span></span> <span data-ttu-id="40351-132">メタデータは自動的に COM の IDL の機能を提供するため、ユーザーは 1 つのファイルを定義と実装の両方に使用できます。</span><span class="sxs-lookup"><span data-stu-id="40351-132">Metadata automatically provides the functionality of IDL in COM, so you can use one file for both definition and implementation.</span></span> <span data-ttu-id="40351-133">また、ランタイム モジュールやアセンブリをオペレーティング システムに登録する必要もありません。</span><span class="sxs-lookup"><span data-stu-id="40351-133">Runtime modules and assemblies do not even require registration with the operating system.</span></span> <span data-ttu-id="40351-134">これにより、ランタイムが使用する記述は常にコンパイル済みファイル内の実際のコードに反映されるため、アプリケーションの信頼性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="40351-134">As a result, the descriptions used by the runtime always reflect the actual code in your compiled file, which increases application reliability.</span></span>

- <span data-ttu-id="40351-135">言語の相互運用性と簡単なコンポーネント ベースのデザイン</span><span class="sxs-lookup"><span data-stu-id="40351-135">Language interoperability and easier component-based design.</span></span>

  <span data-ttu-id="40351-136">メタデータは、他の言語で記述されている PE ファイルからクラスを継承するのに必要な、コンパイル済みコードについてのすべての情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="40351-136">Metadata provides all the information required about compiled code for you to inherit a class from a PE file written in a different language.</span></span> <span data-ttu-id="40351-137">明示的なマーシャリングや相互運用可能なカスタム コードの使用を考慮せずに、マネージド言語 (共通言語ランタイムに変換される言語) で記述された任意のクラスのインスタンスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="40351-137">You can create an instance of any class written in any managed language (any language that targets the common language runtime) without worrying about explicit marshaling or using custom interoperability code.</span></span>

- <span data-ttu-id="40351-138">属性。</span><span class="sxs-lookup"><span data-stu-id="40351-138">Attributes.</span></span>

  <span data-ttu-id="40351-139">.NET を使用すると、コンパイル済みファイル内で "属性" と呼ばれる特定の種類のメタデータを宣言できます。</span><span class="sxs-lookup"><span data-stu-id="40351-139">.NET lets you declare specific kinds of metadata, called attributes, in your compiled file.</span></span> <span data-ttu-id="40351-140">属性は、.NET 全体で使用され、実行時のプログラムの動作を詳細に制御します。</span><span class="sxs-lookup"><span data-stu-id="40351-140">Attributes can be found throughout .NET and are used to control in more detail how your program behaves at run time.</span></span> <span data-ttu-id="40351-141">また、ユーザー定義のカスタム属性によって、独自に作成したメタデータを .NET のファイルに挿入できます。</span><span class="sxs-lookup"><span data-stu-id="40351-141">Additionally, you can emit your own custom metadata into .NET files through user-defined custom attributes.</span></span> <span data-ttu-id="40351-142">詳細については、「[属性](attributes/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="40351-142">For more information, see [Attributes](attributes/index.md).</span></span>

## <a name="metadata-and-the-pe-file-structure"></a><span data-ttu-id="40351-143">メタデータと PE ファイルの構造</span><span class="sxs-lookup"><span data-stu-id="40351-143">Metadata and the PE File Structure</span></span>

<span data-ttu-id="40351-144">メタデータと Microsoft Intermediate Language (MSIL) は、それぞれ、.NET のポータブル実行可能 (PE) ファイルの別のセクションに格納されます。</span><span class="sxs-lookup"><span data-stu-id="40351-144">Metadata is stored in one section of a .NET portable executable (PE) file, while Microsoft intermediate language (MSIL) is stored in another section of the PE file.</span></span> <span data-ttu-id="40351-145">ファイルのメタデータ部分には、一連のテーブルとヒープ データの構造が格納されています。</span><span class="sxs-lookup"><span data-stu-id="40351-145">The metadata portion of the file contains a series of table and heap data structures.</span></span> <span data-ttu-id="40351-146">MSIL 部分には、PE ファイルのメタデータ部分を参照する MSIL とメタデータ トークンが格納されています。</span><span class="sxs-lookup"><span data-stu-id="40351-146">The MSIL portion contains MSIL and metadata tokens that reference the metadata portion of the PE file.</span></span> <span data-ttu-id="40351-147">コードの MSIL を表示する [MSIL 逆アセンブラー (Ildasm.exe)](../framework/tools/ildasm-exe-il-disassembler.md) のようなツールを使用すると、メタデータ トークンが表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="40351-147">You might encounter metadata tokens when you use tools such as the [MSIL Disassembler (Ildasm.exe)](../framework/tools/ildasm-exe-il-disassembler.md) to view your code's MSIL, for example.</span></span>

### <a name="metadata-tables-and-heaps"></a><span data-ttu-id="40351-148">メタデータのテーブルおよびヒープ</span><span class="sxs-lookup"><span data-stu-id="40351-148">Metadata Tables and Heaps</span></span>

<span data-ttu-id="40351-149">各メタデータ テーブルには、プログラムの要素に関する情報が保持されています。</span><span class="sxs-lookup"><span data-stu-id="40351-149">Each metadata table holds information about the elements of your program.</span></span> <span data-ttu-id="40351-150">たとえば、1 つのメタデータ テーブルにはコード内のクラスが記述されており、別のテーブルにはフィールドが記述されています。</span><span class="sxs-lookup"><span data-stu-id="40351-150">For example, one metadata table describes the classes in your code, another table describes the fields, and so on.</span></span> <span data-ttu-id="40351-151">コードに 10 個のクラスが存在する場合、クラス テーブルには、各クラスごとに 1 行、つまり 10 行が存在します。</span><span class="sxs-lookup"><span data-stu-id="40351-151">If you have ten classes in your code, the class table will have tens rows, one for each class.</span></span> <span data-ttu-id="40351-152">メタデータ テーブルは、他のテーブルおよびヒープを参照します。</span><span class="sxs-lookup"><span data-stu-id="40351-152">Metadata tables reference other tables and heaps.</span></span> <span data-ttu-id="40351-153">たとえば、クラスのメタデータ テーブルは、メソッドのテーブルを参照します。</span><span class="sxs-lookup"><span data-stu-id="40351-153">For example, the metadata table for classes references the table for methods.</span></span>

<span data-ttu-id="40351-154">また、メタデータは、4 つのヒープ構造 (文字列、BLOB、ユーザー文字列、および GUID) に情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="40351-154">Metadata also stores information in four heap structures: string, blob, user string, and GUID.</span></span> <span data-ttu-id="40351-155">型やメンバーに名前を付けるために使用する文字列はすべて、文字列ヒープに格納されています。</span><span class="sxs-lookup"><span data-stu-id="40351-155">All the strings used to name types and members are stored in the string heap.</span></span> <span data-ttu-id="40351-156">たとえば、特定のメソッドの名前はメソッド テーブルに直接は格納されず、メソッド テーブルから文字列ヒープ内に格納されているメソッドの名前を参照します。</span><span class="sxs-lookup"><span data-stu-id="40351-156">For example, a method table does not directly store the name of a particular method, but points to the method's name stored in the string heap.</span></span>

### <a name="metadata-tokens"></a><span data-ttu-id="40351-157">メタデータ トークン</span><span class="sxs-lookup"><span data-stu-id="40351-157">Metadata Tokens</span></span>

<span data-ttu-id="40351-158">各メタデータ テーブルのそれぞれの行は、メタデータ トークンによって、PE ファイルの MSIL 部分内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="40351-158">Each row of each metadata table is uniquely identified in the MSIL portion of the PE file by a metadata token.</span></span> <span data-ttu-id="40351-159">メタデータ トークンは、概念上、ポインターに類似しており、特定のメタデータ テーブルを参照します。</span><span class="sxs-lookup"><span data-stu-id="40351-159">Metadata tokens are conceptually similar to pointers, persisted in MSIL, that reference a particular metadata table.</span></span>

<span data-ttu-id="40351-160">メタデータ トークンは、4 バイトで構成される数値です。</span><span class="sxs-lookup"><span data-stu-id="40351-160">A metadata token is a four-byte number.</span></span> <span data-ttu-id="40351-161">最上位バイトは、特定のトークンの参照先であるメタデータ テーブル (メソッド、型など) を表します。</span><span class="sxs-lookup"><span data-stu-id="40351-161">The top byte denotes the metadata table to which a particular token refers (method, type, and so on).</span></span> <span data-ttu-id="40351-162">残り 3 バイトは、記述されているプログラミング要素と対応する、メタデータ テーブル内の行を指定します。</span><span class="sxs-lookup"><span data-stu-id="40351-162">The remaining three bytes specify the row in the metadata table that corresponds to the programming element being described.</span></span> <span data-ttu-id="40351-163">たとえば、C# 言語でメソッドを定義し、そのメソッドを PE ファイルとしてコンパイルすると、PE ファイルの MSIL 部分に次のようなメタデータ トークンが格納されます。</span><span class="sxs-lookup"><span data-stu-id="40351-163">If you define a method in C# and compile it into a PE file, the following metadata token might exist in the MSIL portion of the PE file:</span></span>

`0x06000004`

<span data-ttu-id="40351-164">最上位バイト (`0x06`) は、**MethodDef** トークンであることを示します。</span><span class="sxs-lookup"><span data-stu-id="40351-164">The top byte (`0x06`) indicates that this is a **MethodDef** token.</span></span> <span data-ttu-id="40351-165">下位 3 バイト (`000004`) は、**MethodDef** テーブル内の、このメソッドの定義を記述する情報に対応する 4 行目を参照するように、共通言語ランタイムに指示します。</span><span class="sxs-lookup"><span data-stu-id="40351-165">The lower three bytes (`000004`) tells the common language runtime to look in the fourth row of the **MethodDef** table for the information that describes this method definition.</span></span>

### <a name="metadata-within-a-pe-file"></a><span data-ttu-id="40351-166">PE ファイル内のメタデータ</span><span class="sxs-lookup"><span data-stu-id="40351-166">Metadata within a PE File</span></span>

<span data-ttu-id="40351-167">プログラムを共通言語ランタイムとしてコンパイルすると、プログラムは 3 つの部分で構成される PE ファイルに変換されます。</span><span class="sxs-lookup"><span data-stu-id="40351-167">When a program is compiled for the common language runtime, it is converted to a PE file that consists of three parts.</span></span> <span data-ttu-id="40351-168">各部分の内容を説明する表を次に示します。</span><span class="sxs-lookup"><span data-stu-id="40351-168">The following table describes the contents of each part.</span></span>

|<span data-ttu-id="40351-169">PE セクション</span><span class="sxs-lookup"><span data-stu-id="40351-169">PE section</span></span>|<span data-ttu-id="40351-170">PE セクションの内容</span><span class="sxs-lookup"><span data-stu-id="40351-170">Contents of PE section</span></span>|
|----------------|----------------------------|
|<span data-ttu-id="40351-171">PE ヘッダー</span><span class="sxs-lookup"><span data-stu-id="40351-171">PE header</span></span>|<span data-ttu-id="40351-172">PE ファイルの主要なセクションのインデックスとエントリ ポイントのアドレス。</span><span class="sxs-lookup"><span data-stu-id="40351-172">The index of the PE file's main sections and the address of the entry point.</span></span><br /><br /> <span data-ttu-id="40351-173">ランタイムはこの情報に基づいてファイルを PE ファイルとして識別し、実行開始位置と、メモリにプログラムをいつ読み込むかを判断します。</span><span class="sxs-lookup"><span data-stu-id="40351-173">The runtime uses this information to identify the file as a PE file and to determine where execution starts when loading the program into memory.</span></span>|
|<span data-ttu-id="40351-174">MSIL の命令</span><span class="sxs-lookup"><span data-stu-id="40351-174">MSIL instructions</span></span>|<span data-ttu-id="40351-175">コードを構成する Microsoft Intermediate Language (MSIL) の命令。</span><span class="sxs-lookup"><span data-stu-id="40351-175">The Microsoft intermediate language instructions (MSIL) that make up your code.</span></span> <span data-ttu-id="40351-176">ほとんどの MSIL 命令には、メタデータ トークンが付いています。</span><span class="sxs-lookup"><span data-stu-id="40351-176">Many MSIL instructions are accompanied by metadata tokens.</span></span>|
|<span data-ttu-id="40351-177">メタデータ</span><span class="sxs-lookup"><span data-stu-id="40351-177">Metadata</span></span>|<span data-ttu-id="40351-178">メタデータ テーブルおよびヒープ。</span><span class="sxs-lookup"><span data-stu-id="40351-178">Metadata tables and heaps.</span></span> <span data-ttu-id="40351-179">ランタイムはこのセクションを使用してコード内のすべての型およびメンバーに関する情報を記録します。</span><span class="sxs-lookup"><span data-stu-id="40351-179">The runtime uses this section to record information about every type and member in your code.</span></span> <span data-ttu-id="40351-180">また、このセクションには、カスタム属性やセキュリティ情報も格納されています。</span><span class="sxs-lookup"><span data-stu-id="40351-180">This section also includes custom attributes and security information.</span></span>|

## <a name="run-time-use-of-metadata"></a><span data-ttu-id="40351-181">実行時のメタデータの使用</span><span class="sxs-lookup"><span data-stu-id="40351-181">Run-Time Use of Metadata</span></span>

<span data-ttu-id="40351-182">メタデータと、共通言語ランタイムでのメタデータの役割をより深く理解するために、簡単なプログラムを作成し、メタデータがその有効期間中にどのように機能するかを示します。</span><span class="sxs-lookup"><span data-stu-id="40351-182">To better understand metadata and its role in the common language runtime, it might be helpful to construct a simple program and illustrate how metadata affects its run-time life.</span></span> <span data-ttu-id="40351-183">`MyApp` と呼ばれるクラス内の 2 つのメソッドを表すコードの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="40351-183">The following code example shows two methods inside a class called `MyApp`.</span></span> <span data-ttu-id="40351-184">`Main` メソッドは、プログラムのエントリ ポイントです。`Add` メソッドは、2 つの整数引数の合計値を返します。</span><span class="sxs-lookup"><span data-stu-id="40351-184">The `Main` method is the program entry point, while the `Add` method simply returns the sum of two integer arguments.</span></span>

```vb
Public Class MyApp
   Public Shared Sub Main()
      Dim ValueOne As Integer = 10
      Dim ValueTwo As Integer = 20
      Console.WriteLine("The Value is: {0}", Add(ValueOne, ValueTwo))
   End Sub

   Public Shared Function Add(One As Integer, Two As Integer) As Integer
      Return (One + Two)
   End Function
End Class
```

```csharp
using System;
public class MyApp
{
   public static int Main()
   {
      int ValueOne = 10;
      int ValueTwo = 20;
      Console.WriteLine("The Value is: {0}", Add(ValueOne, ValueTwo));
      return 0;
   }
   public static int Add(int One, int Two)
   {
      return (One + Two);
   }
}
```

<span data-ttu-id="40351-185">このコードを実行すると、ランタイムがモジュールをメモリに読み込み、このクラスのメタデータを調べます。</span><span class="sxs-lookup"><span data-stu-id="40351-185">When the code runs, the runtime loads the module into memory and consults the metadata for this class.</span></span> <span data-ttu-id="40351-186">モジュールを読み込んだ後、ランタイムはメソッドの Microsoft Intermediate Language (MSIL) ストリームを詳細に分析して、そのストリームを高速のネイティブ機械語命令に変換します。</span><span class="sxs-lookup"><span data-stu-id="40351-186">Once loaded, the runtime performs extensive analysis of the method's Microsoft intermediate language (MSIL) stream to convert it to fast native machine instructions.</span></span> <span data-ttu-id="40351-187">ランタイムはジャスト イン タイム (JIT) コンパイラを使用して、それぞれのメソッドを必要なときに 1 つずつ、MSIL 命令からネイティブ マシン語コードに変換します。</span><span class="sxs-lookup"><span data-stu-id="40351-187">The runtime uses a just-in-time (JIT) compiler to convert the MSIL instructions to native machine code one method at a time as needed.</span></span>

<span data-ttu-id="40351-188">上記のコードの `Main` 関数によって生成された MSIL の一部の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="40351-188">The following example shows part of the MSIL produced from the previous code's `Main` function.</span></span> <span data-ttu-id="40351-189">MSIL とメタデータは、[MSIL 逆アセンブラー (Ildasm.exe)](../framework/tools/ildasm-exe-il-disassembler.md) を使用することにより、任意の .NET アプリケーションから表示できます。</span><span class="sxs-lookup"><span data-stu-id="40351-189">You can view the MSIL and metadata from any .NET application using the [MSIL Disassembler (Ildasm.exe)](../framework/tools/ildasm-exe-il-disassembler.md).</span></span>

```console
.entrypoint
.maxstack  3
.locals ([0] int32 ValueOne,
         [1] int32 ValueTwo,
         [2] int32 V_2,
         [3] int32 V_3)
IL_0000:  ldc.i4.s   10
IL_0002:  stloc.0
IL_0003:  ldc.i4.s   20
IL_0005:  stloc.1
IL_0006:  ldstr      "The Value is: {0}"
IL_000b:  ldloc.0
IL_000c:  ldloc.1
IL_000d:  call int32 ConsoleApplication.MyApp::Add(int32,int32) /* 06000003 */
```

<span data-ttu-id="40351-190">JIT コンパイラはこのメソッド全体の MSIL を読み取って詳細に分析し、このメソッドの効率的なネイティブ命令を生成します。</span><span class="sxs-lookup"><span data-stu-id="40351-190">The JIT compiler reads the MSIL for the whole method, analyzes it thoroughly, and generates efficient native instructions for the method.</span></span> <span data-ttu-id="40351-191">`IL_000d` で、`Add` メソッドのメタデータ トークン (`/*` `06000003 */`) が検出されます。ランタイムは、このトークンを使用して **MethodDef** テーブルの 3 行目を調べます。</span><span class="sxs-lookup"><span data-stu-id="40351-191">At `IL_000d`, a metadata token for the `Add` method (`/*` `06000003 */`) is encountered and the runtime uses the token to consult the third row of the **MethodDef** table.</span></span>

<span data-ttu-id="40351-192">**メソッドが記述されているメタデータ トークンによって参照される、** MethodDef`Add` テーブルの一部の例を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="40351-192">The following table shows part of the **MethodDef** table referenced by the metadata token that describes the `Add` method.</span></span> <span data-ttu-id="40351-193">このアセンブリにはほかにもメタデータ テーブルが存在し、それぞれ独自の値を持っていますが、ここでは、このテーブルだけを参照します。</span><span class="sxs-lookup"><span data-stu-id="40351-193">While other metadata tables exist in this assembly and have their own unique values, only this table is discussed.</span></span>

|<span data-ttu-id="40351-194">行</span><span class="sxs-lookup"><span data-stu-id="40351-194">Row</span></span>|<span data-ttu-id="40351-195">Relative Virtual Address (RVA)</span><span class="sxs-lookup"><span data-stu-id="40351-195">Relative Virtual Address (RVA)</span></span>|<span data-ttu-id="40351-196">ImplFlags</span><span class="sxs-lookup"><span data-stu-id="40351-196">ImplFlags</span></span>|<span data-ttu-id="40351-197">フラグ</span><span class="sxs-lookup"><span data-stu-id="40351-197">Flags</span></span>|<span data-ttu-id="40351-198">名前</span><span class="sxs-lookup"><span data-stu-id="40351-198">Name</span></span><br /><br /> <span data-ttu-id="40351-199">(文字列ヒープを指す)</span><span class="sxs-lookup"><span data-stu-id="40351-199">(Points to string heap.)</span></span>|<span data-ttu-id="40351-200">Signature (BLOB ヒープを指す)</span><span class="sxs-lookup"><span data-stu-id="40351-200">Signature (Points to blob heap.)</span></span>|
|---------|--------------------------------------|---------------|-----------|-----------------------------------------|----------------------------------------|
|<span data-ttu-id="40351-201">1</span><span class="sxs-lookup"><span data-stu-id="40351-201">1</span></span>|<span data-ttu-id="40351-202">0x00002050</span><span class="sxs-lookup"><span data-stu-id="40351-202">0x00002050</span></span>|<span data-ttu-id="40351-203">IL</span><span class="sxs-lookup"><span data-stu-id="40351-203">IL</span></span><br /><br /> <span data-ttu-id="40351-204">マネージド</span><span class="sxs-lookup"><span data-stu-id="40351-204">Managed</span></span>|<span data-ttu-id="40351-205">Public</span><span class="sxs-lookup"><span data-stu-id="40351-205">Public</span></span><br /><br /> <span data-ttu-id="40351-206">ReuseSlot</span><span class="sxs-lookup"><span data-stu-id="40351-206">ReuseSlot</span></span><br /><br /> <span data-ttu-id="40351-207">SpecialName</span><span class="sxs-lookup"><span data-stu-id="40351-207">SpecialName</span></span><br /><br /> <span data-ttu-id="40351-208">RTSpecialName</span><span class="sxs-lookup"><span data-stu-id="40351-208">RTSpecialName</span></span><br /><br /> <span data-ttu-id="40351-209">.ctor</span><span class="sxs-lookup"><span data-stu-id="40351-209">.ctor</span></span>|<span data-ttu-id="40351-210">.ctor (コンストラクター)</span><span class="sxs-lookup"><span data-stu-id="40351-210">.ctor (constructor)</span></span>||
|<span data-ttu-id="40351-211">2</span><span class="sxs-lookup"><span data-stu-id="40351-211">2</span></span>|<span data-ttu-id="40351-212">0x00002058</span><span class="sxs-lookup"><span data-stu-id="40351-212">0x00002058</span></span>|<span data-ttu-id="40351-213">IL</span><span class="sxs-lookup"><span data-stu-id="40351-213">IL</span></span><br /><br /> <span data-ttu-id="40351-214">マネージド</span><span class="sxs-lookup"><span data-stu-id="40351-214">Managed</span></span>|<span data-ttu-id="40351-215">Public</span><span class="sxs-lookup"><span data-stu-id="40351-215">Public</span></span><br /><br /> <span data-ttu-id="40351-216">Static</span><span class="sxs-lookup"><span data-stu-id="40351-216">Static</span></span><br /><br /> <span data-ttu-id="40351-217">ReuseSlot</span><span class="sxs-lookup"><span data-stu-id="40351-217">ReuseSlot</span></span>|<span data-ttu-id="40351-218">メイン</span><span class="sxs-lookup"><span data-stu-id="40351-218">Main</span></span>|<span data-ttu-id="40351-219">String</span><span class="sxs-lookup"><span data-stu-id="40351-219">String</span></span>|
|<span data-ttu-id="40351-220">3</span><span class="sxs-lookup"><span data-stu-id="40351-220">3</span></span>|<span data-ttu-id="40351-221">0x0000208c</span><span class="sxs-lookup"><span data-stu-id="40351-221">0x0000208c</span></span>|<span data-ttu-id="40351-222">IL</span><span class="sxs-lookup"><span data-stu-id="40351-222">IL</span></span><br /><br /> <span data-ttu-id="40351-223">マネージド</span><span class="sxs-lookup"><span data-stu-id="40351-223">Managed</span></span>|<span data-ttu-id="40351-224">Public</span><span class="sxs-lookup"><span data-stu-id="40351-224">Public</span></span><br /><br /> <span data-ttu-id="40351-225">Static</span><span class="sxs-lookup"><span data-stu-id="40351-225">Static</span></span><br /><br /> <span data-ttu-id="40351-226">ReuseSlot</span><span class="sxs-lookup"><span data-stu-id="40351-226">ReuseSlot</span></span>|<span data-ttu-id="40351-227">追加</span><span class="sxs-lookup"><span data-stu-id="40351-227">Add</span></span>|<span data-ttu-id="40351-228">int, int, int</span><span class="sxs-lookup"><span data-stu-id="40351-228">int, int, int</span></span>|

<span data-ttu-id="40351-229">このテーブルの各列には、コードについての重要な情報が格納されています。</span><span class="sxs-lookup"><span data-stu-id="40351-229">Each column of the table contains important information about your code.</span></span> <span data-ttu-id="40351-230">ランタイムは **RVA** 列を使用して、このメソッドを定義する MSIL の開始メモリ アドレスを計算します。</span><span class="sxs-lookup"><span data-stu-id="40351-230">The **RVA** column allows the runtime to calculate the starting memory address of the MSIL that defines this method.</span></span> <span data-ttu-id="40351-231">**ImplFlags** および **Flags** 列には、このメソッドを記述するビットマスク (たとえば、メソッドがパブリックかプライベートかを記述するビットマスク) が格納されています。</span><span class="sxs-lookup"><span data-stu-id="40351-231">The **ImplFlags** and **Flags** columns contain bitmasks that describe the method (for example, whether the method is public or private).</span></span> <span data-ttu-id="40351-232">**Name** 列は、文字列ヒープからメソッドの名前へのインデックスとなります。</span><span class="sxs-lookup"><span data-stu-id="40351-232">The **Name** column indexes the name of the method from the string heap.</span></span> <span data-ttu-id="40351-233">**Signature** 列は、BLOB ヒープ内のメソッドのシグネチャ定義へのインデックスとなります。</span><span class="sxs-lookup"><span data-stu-id="40351-233">The **Signature** column indexes the definition of the method's signature in the blob heap.</span></span>

<span data-ttu-id="40351-234">ランタイムは 3 行目の **RVA** 列から必要なオフセット アドレスを計算し、計算したオフセット アドレスを JIT コンパイラに返します。JIT コンパイラは計算された新しいアドレスに移動します。</span><span class="sxs-lookup"><span data-stu-id="40351-234">The runtime calculates the desired offset address from the **RVA** column in the third row and returns this address to the JIT compiler, which then proceeds to the new address.</span></span> <span data-ttu-id="40351-235">JIT コンパイラは、新しいアドレスから、別のメタデータ トークンを検出するまで MSIL の処理を続行し、処理を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="40351-235">The JIT compiler continues to process MSIL at the new address until it encounters another metadata token and the process is repeated.</span></span>

<span data-ttu-id="40351-236">ランタイムは、メタデータを使用することにより、コードを読み込み、ネイティブ機械語命令に変換するのに必要なすべての情報にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="40351-236">Using metadata, the runtime has access to all the information it needs to load your code and process it into native machine instructions.</span></span> <span data-ttu-id="40351-237">このように、メタデータによって自己言及的なファイルが使用可能になり、メタデータと共通型システムを組み合わせて使用することで、言語間で継承が可能になります。</span><span class="sxs-lookup"><span data-stu-id="40351-237">In this manner, metadata enables self-describing files and, together with the common type system, cross-language inheritance.</span></span>

## <a name="related-topics"></a><span data-ttu-id="40351-238">関連トピック</span><span class="sxs-lookup"><span data-stu-id="40351-238">Related Topics</span></span>

|<span data-ttu-id="40351-239">Title</span><span class="sxs-lookup"><span data-stu-id="40351-239">Title</span></span>|<span data-ttu-id="40351-240">説明</span><span class="sxs-lookup"><span data-stu-id="40351-240">Description</span></span>|
|-----------|-----------------|
|[<span data-ttu-id="40351-241">属性</span><span class="sxs-lookup"><span data-stu-id="40351-241">Attributes</span></span>](attributes/index.md)|<span data-ttu-id="40351-242">属性の適用方法、カスタム属性の記述方法、および属性に格納されている情報の取得方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="40351-242">Describes how to apply attributes, write custom attributes, and retrieve information that is stored in attributes.</span></span>|
