---
description: '詳細情報: 方法:DBML ファイルおよび外部マッピング ファイルを検証する'
title: '方法: DBML ファイルおよび外部マッピング ファイルを検証する'
ms.date: 03/30/2017
ms.assetid: d9ea37f5-0a9e-4401-8fc3-1e6fd44c49f9
ms.openlocfilehash: 46e5c787bef8e152020fc97631ef8c1c4928fe74
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785784"
---
# <a name="how-to-validate-dbml-and-external-mapping-files"></a><span data-ttu-id="08e55-103">方法: DBML ファイルおよび外部マッピング ファイルを検証する</span><span class="sxs-lookup"><span data-stu-id="08e55-103">How to: Validate DBML and External Mapping Files</span></span>

<span data-ttu-id="08e55-104">変更した外部マッピング ファイルや .dbml ファイルは、それぞれのスキーマ定義に対して検証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="08e55-104">External mapping files and .dbml files that you modify must be validated against their respective schema definitions.</span></span> <span data-ttu-id="08e55-105">このトピックでは、Visual Studio ユーザーを対象に、検証プロセスを実装する手順を示します。</span><span class="sxs-lookup"><span data-stu-id="08e55-105">This topic provides Visual Studio users with the steps to implement the validation process.</span></span>

[!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]

### <a name="to-validate-a-dbml-or-xml-file"></a><span data-ttu-id="08e55-106">.dbml ファイルまたは XML ファイルを検証するには</span><span class="sxs-lookup"><span data-stu-id="08e55-106">To validate a .dbml or XML file</span></span>

1. <span data-ttu-id="08e55-107">Visual Studio で、 **[ファイル]** メニューの **[開く]** をポイントし、 **[ファイル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08e55-107">On the Visual Studio **File** menu, point to **Open**, and then click **File**.</span></span>

2. <span data-ttu-id="08e55-108">**[ファイルを開く]** ダイアログ ボックスで、検証する .dbml ファイルまたは XML マッピング ファイルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="08e55-108">In the **Open File** dialog box, click the .dbml or XML mapping file that you want to validate.</span></span>

    <span data-ttu-id="08e55-109">**XML エディター** でファイルが開きます。</span><span class="sxs-lookup"><span data-stu-id="08e55-109">The file opens in the **XML Editor**.</span></span>

3. <span data-ttu-id="08e55-110">ウィンドウを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08e55-110">Right-click the window, and then click **Properties**.</span></span>

4. <span data-ttu-id="08e55-111">**[プロパティ]** ウィンドウで、 **[Schemas]** プロパティの横にある省略記号をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08e55-111">In the **Properties** window, click the ellipsis for the **Schemas** property.</span></span>

    <span data-ttu-id="08e55-112">**[XML スキーマ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="08e55-112">The **XML Schemas** dialog box opens.</span></span>

5. <span data-ttu-id="08e55-113">目的に適したスキーマ定義を見つけます。</span><span class="sxs-lookup"><span data-stu-id="08e55-113">Note the appropriate schema definition for your purpose.</span></span>

    - <span data-ttu-id="08e55-114">DbmlSchema.xsd は、.dbml ファイルを検証するためのスキーマ定義です。</span><span class="sxs-lookup"><span data-stu-id="08e55-114">DbmlSchema.xsd is the schema definition for validating a .dbml file.</span></span> <span data-ttu-id="08e55-115">詳しくは、「[LINQ to SQL でのコード生成](code-generation-in-linq-to-sql.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="08e55-115">For more information, see [Code Generation in LINQ to SQL](code-generation-in-linq-to-sql.md).</span></span>

    - <span data-ttu-id="08e55-116">LinqToSqlMapping.xsd は、外部 XML マッピング ファイルを検証するためのスキーマ定義です。</span><span class="sxs-lookup"><span data-stu-id="08e55-116">LinqToSqlMapping.xsd is the schema definition for validating an external XML mapping file.</span></span> <span data-ttu-id="08e55-117">詳細については、「[外部マップ](external-mapping.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08e55-117">For more information, see [External Mapping](external-mapping.md).</span></span>

6. <span data-ttu-id="08e55-118">目的のスキーマ定義の行の **[使用]** 列をクリックしてドロップダウン ボックスを表示し、 **[このスキーマを使用する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08e55-118">In the **Use** column of the desired schema definition row, click to open the drop-down box, and then click **Use this schema**.</span></span>

    <span data-ttu-id="08e55-119">これで、スキーマ定義ファイルが DBML ファイルまたは XML マッピング ファイルに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="08e55-119">The schema definition file is now associated with your DBML or XML mapping file.</span></span>

    <span data-ttu-id="08e55-120">他のスキーマ定義は選択しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="08e55-120">Make sure no other schema definitions are selected.</span></span>

7. <span data-ttu-id="08e55-121">**[表示]** メニューの **[エラー一覧]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08e55-121">On the **View** menu, click **Error List**.</span></span>

    <span data-ttu-id="08e55-122">エラー、警告、またはメッセージが生成されていないか確認します。</span><span class="sxs-lookup"><span data-stu-id="08e55-122">Determine whether errors, warnings, or messages have been generated.</span></span> <span data-ttu-id="08e55-123">生成されていなければ、XML ファイルはスキーマ定義に対して有効です。</span><span class="sxs-lookup"><span data-stu-id="08e55-123">If not, the XML file is valid against the schema definition.</span></span>

## <a name="alternate-method-for-supplying-schema-definition"></a><span data-ttu-id="08e55-124">スキーマ定義を指定する別の方法</span><span class="sxs-lookup"><span data-stu-id="08e55-124">Alternate Method for Supplying Schema Definition</span></span>

<span data-ttu-id="08e55-125">なんらかの理由で **[XML スキーマ]** ダイアログ ボックスに適切な .xsd ファイルが表示されない場合は、ヘルプ トピックから .xsd ファイルをダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="08e55-125">If for some reason the appropriate .xsd file does not appear in the **XML Schemas** dialog box, you can download the .xsd file from a Help topic.</span></span> <span data-ttu-id="08e55-126">次の手順を使用すると、ダウンロードしたファイルを、Visual Studio の XML エディターに対応する Unicode 形式で保存できます。</span><span class="sxs-lookup"><span data-stu-id="08e55-126">The following steps help you save the downloaded file in the Unicode format required by the Visual Studio XML Editor.</span></span>

#### <a name="to-copy-a-schema-definition-file-from-a-help-topic"></a><span data-ttu-id="08e55-127">スキーマ定義ファイルをヘルプ トピックからコピーするには</span><span class="sxs-lookup"><span data-stu-id="08e55-127">To copy a schema definition file from a Help topic</span></span>

1. <span data-ttu-id="08e55-128">このトピックで既に説明したように、スキーマ定義が含まれているヘルプ トピックを表示します。</span><span class="sxs-lookup"><span data-stu-id="08e55-128">Locate the Help topic that contains the schema definition as described earlier in this topic.</span></span>

    - <span data-ttu-id="08e55-129">.dbml ファイルについては、「[LINQ to SQL でのコード生成](code-generation-in-linq-to-sql.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="08e55-129">For .dbml files, see [Code Generation in LINQ to SQL](code-generation-in-linq-to-sql.md).</span></span>

    - <span data-ttu-id="08e55-130">外部マッピング ファイルについては、「[外部マップ](external-mapping.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="08e55-130">For external mapping files, see [External Mapping](external-mapping.md).</span></span>

2. <span data-ttu-id="08e55-131">**[コードのコピー]** をクリックして、コード ファイルをクリップボードにコピーします。</span><span class="sxs-lookup"><span data-stu-id="08e55-131">Click **Copy Code** to copy the code file to the Clipboard.</span></span>

3. <span data-ttu-id="08e55-132">メモ帳を起動して、新しいファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="08e55-132">Start Notepad to create a new file.</span></span>

4. <span data-ttu-id="08e55-133">クリップボードからメモ帳のファイルにコードを貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="08e55-133">Paste the code from the clipboard into Notepad file.</span></span>

5. <span data-ttu-id="08e55-134">メモ帳で、 **[ファイル]** メニューの **[名前を付けて保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08e55-134">On the Notepad **File** menu, click **Save As**.</span></span>

6. <span data-ttu-id="08e55-135">**[文字コード]** ボックスの一覧の **[Unicode]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="08e55-135">In the **Encoding** box, select **Unicode**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="08e55-136">これを選択することで、テキスト ファイルの先頭に Unicode-16 のバイト順マーカー (`FFFE`) が追加されます。</span><span class="sxs-lookup"><span data-stu-id="08e55-136">This selection guarantees that the Unicode-16 byte-order marker (`FFFE`) is prepended to the text file.</span></span>

7. <span data-ttu-id="08e55-137">**[ファイル名]** ボックスに、ファイル名と拡張子 .xsd を入力します。</span><span class="sxs-lookup"><span data-stu-id="08e55-137">In the **File name** box, create a file name with an .xsd extension.</span></span>

## <a name="see-also"></a><span data-ttu-id="08e55-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="08e55-138">See also</span></span>

- [<span data-ttu-id="08e55-139">参照</span><span class="sxs-lookup"><span data-stu-id="08e55-139">Reference</span></span>](reference.md)
