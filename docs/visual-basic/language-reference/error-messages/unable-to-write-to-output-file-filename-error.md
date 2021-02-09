---
description: "詳細情報: BC31019:出力ファイル '<filename>' に書き込めません : <error>"
title: "出力ファイル '<filename>' に書き込めません : <error>"
ms.date: 07/20/2015
f1_keywords:
- vbc31019
- bc31019
helpviewer_keywords:
- BC31019
ms.assetid: 0845b245-11bb-46fd-95ca-f6cef3c318ef
ms.openlocfilehash: 4a1feff6429a5b82968d3a87e4c9c9ef80e6612a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640902"
---
# <a name="bc31019-unable-to-write-to-output-file-filename-error"></a><span data-ttu-id="9aff3-103">BC31019:出力ファイル '\<filename>' に書き込めません : \<error></span><span class="sxs-lookup"><span data-stu-id="9aff3-103">BC31019: Unable to write to output file '\<filename>': \<error></span></span>

<span data-ttu-id="9aff3-104">ファイルの作成で問題が発生しました。</span><span class="sxs-lookup"><span data-stu-id="9aff3-104">There was a problem creating the file.</span></span>

 <span data-ttu-id="9aff3-105">出力ファイルを書き込み用に開くことができません。</span><span class="sxs-lookup"><span data-stu-id="9aff3-105">An output file cannot be opened for writing.</span></span> <span data-ttu-id="9aff3-106">ファイル (または、そのファイルが格納されているフォルダー) は、別のプロセスによって排他的に開かれているか、読み取り専用属性が設定されている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9aff3-106">The file (or the folder containing the file) may be opened for exclusive use by another process, or it may have its read-only attribute set.</span></span>

 <span data-ttu-id="9aff3-107">ファイルが排他的に開かれている一般的な原因として、次の状況が考えられます。</span><span class="sxs-lookup"><span data-stu-id="9aff3-107">Common situations where a file is opened exclusively are:</span></span>

- <span data-ttu-id="9aff3-108">このアプリケーションが既に実行されていて、ファイルを使用している。</span><span class="sxs-lookup"><span data-stu-id="9aff3-108">The application is already running and using its files.</span></span> <span data-ttu-id="9aff3-109">この問題を解決するためには、アプリケーションを終了します。</span><span class="sxs-lookup"><span data-stu-id="9aff3-109">To solve this problem, make sure that the application is not running.</span></span>

- <span data-ttu-id="9aff3-110">別のアプリケーションがファイルを開いている。</span><span class="sxs-lookup"><span data-stu-id="9aff3-110">Another application has opened the file.</span></span> <span data-ttu-id="9aff3-111">この問題を解決するためには、ファイルにアクセスしている他のアプリケーションがないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="9aff3-111">To solve this problem, make sure that no other application is accessing the files.</span></span> <span data-ttu-id="9aff3-112">ファイルにアクセスしているアプリケーションがわからない場合があります。この場合、アプリケーションを終了する最も簡単な方法として、コンピューターの再起動が考えられます。</span><span class="sxs-lookup"><span data-stu-id="9aff3-112">It is not always obvious which application is accessing your files; in that case, restarting the computer might be the easiest way to terminate the application.</span></span>

 <span data-ttu-id="9aff3-113">プロジェクトの出力ファイルのいずれか 1 つだけが読み取り専用になっている場合でも、この例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="9aff3-113">If even one of the project output files is marked as read-only, this exception will be thrown.</span></span>

 <span data-ttu-id="9aff3-114">**エラー ID:** BC31019</span><span class="sxs-lookup"><span data-stu-id="9aff3-114">**Error ID:** BC31019</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="9aff3-115">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="9aff3-115">To correct this error</span></span>

1. <span data-ttu-id="9aff3-116">プログラムをもう一度コンパイルし、エラーがまだ発生するかどうか確認します。</span><span class="sxs-lookup"><span data-stu-id="9aff3-116">Compile the program again to see if the error recurs.</span></span>

2. <span data-ttu-id="9aff3-117">エラーが引き続き発生する場合は、作業内容を保存し、Visual Studio を再起動します。</span><span class="sxs-lookup"><span data-stu-id="9aff3-117">If the error continues, save your work and restart Visual Studio.</span></span>

3. <span data-ttu-id="9aff3-118">エラーが引き続き発生する場合は、コンピューターを再起動します。</span><span class="sxs-lookup"><span data-stu-id="9aff3-118">If the error continues, restart the computer.</span></span>

4. <span data-ttu-id="9aff3-119">エラーがまだ発生する場合は、Visual Basic を再インストールします。</span><span class="sxs-lookup"><span data-stu-id="9aff3-119">If the error recurs, reinstall Visual Basic.</span></span>

5. <span data-ttu-id="9aff3-120">再インストールした後にエラーが続く場合は、マイクロソフト プロダクト サポート サービスに通知してください。</span><span class="sxs-lookup"><span data-stu-id="9aff3-120">If the error persists after reinstallation, notify Microsoft Product Support Services.</span></span>

### <a name="to-check-file-attributes-in-file-explorer"></a><span data-ttu-id="9aff3-121">エクスプローラーでファイル属性を確認するには</span><span class="sxs-lookup"><span data-stu-id="9aff3-121">To check file attributes in File Explorer</span></span>

1. <span data-ttu-id="9aff3-122">対象のフォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="9aff3-122">Open the folder you are interested in.</span></span>

2. <span data-ttu-id="9aff3-123">**[表示]** アイコンをクリックし、 **[詳細]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9aff3-123">Click the **Views** icon and choose **Details**.</span></span>

3. <span data-ttu-id="9aff3-124">列ヘッダーを右クリックして、ドロップダウン リストから **[属性]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9aff3-124">Right-click the column header, and choose **Attributes** from the drop-down list.</span></span>

### <a name="to-change-the-attributes-of-a-file-or-folder"></a><span data-ttu-id="9aff3-125">ファイルやフォルダーの属性を変更するには</span><span class="sxs-lookup"><span data-stu-id="9aff3-125">To change the attributes of a file or folder</span></span>

1. <span data-ttu-id="9aff3-126">**[エクスプローラー]** でファイルまたはフォルダーを右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9aff3-126">In **File Explorer**, right-click the file or folder and choose **Properties**.</span></span>

2. <span data-ttu-id="9aff3-127">**[全般]** タブの **[属性]** セクションにある **[読み取り専用]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="9aff3-127">In the **Attributes** section of the **General** tab, clear the **Read-only** box.</span></span>

3. <span data-ttu-id="9aff3-128">**[OK]** を押します。</span><span class="sxs-lookup"><span data-stu-id="9aff3-128">Press **OK**.</span></span>

## <a name="see-also"></a><span data-ttu-id="9aff3-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="9aff3-129">See also</span></span>

- [<span data-ttu-id="9aff3-130">ご意見</span><span class="sxs-lookup"><span data-stu-id="9aff3-130">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
