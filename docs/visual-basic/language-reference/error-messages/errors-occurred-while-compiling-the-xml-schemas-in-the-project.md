---
description: '詳細情報: BC36810:プロジェクトで、XML スキーマのコンパイル中にエラーが発生しました'
title: プロジェクトで、XML スキーマのコンパイル中にエラーが発生しました
ms.date: 07/20/2015
f1_keywords:
- bc36810
- vbc36810
helpviewer_keywords:
- BC36810
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
ms.openlocfilehash: 78e88208c0d3df12e7bad8ab46b1d91bce559923
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796484"
---
# <a name="bc36810-errors-occurred-while-compiling-the-xml-schemas-in-the-project"></a><span data-ttu-id="acd39-103">BC36810:プロジェクトで、XML スキーマのコンパイル中にエラーが発生しました</span><span class="sxs-lookup"><span data-stu-id="acd39-103">BC36810: Errors occurred while compiling the XML schemas in the project</span></span>

<span data-ttu-id="acd39-104">プロジェクトで、XML スキーマのコンパイル中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="acd39-104">Errors occurred while compiling the XML schemas in the project.</span></span> <span data-ttu-id="acd39-105">そのため、XML IntelliSense は使用できません。</span><span class="sxs-lookup"><span data-stu-id="acd39-105">Because of this, XML IntelliSense is not available.</span></span>

 <span data-ttu-id="acd39-106">プロジェクトに含まれている XML スキーマ定義 (XSD) スキーマにエラーがあります。</span><span class="sxs-lookup"><span data-stu-id="acd39-106">There is an error in an XML Schema Definition (XSD) schema included in the project.</span></span> <span data-ttu-id="acd39-107">このエラーは、プロジェクト用の既存の XSD スキーマ セットと競合する XSD スキーマ (.xsd) ファイルを追加したときに発生します。</span><span class="sxs-lookup"><span data-stu-id="acd39-107">This error occurs when you add an XSD schema (.xsd) file that conflicts with the existing XSD schema set for the project.</span></span>

 <span data-ttu-id="acd39-108">**エラー ID:** BC36810</span><span class="sxs-lookup"><span data-stu-id="acd39-108">**Error ID:** BC36810</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="acd39-109">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="acd39-109">To correct this error</span></span>

- <span data-ttu-id="acd39-110">**[エラー一覧]** ウィンドウで警告をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="acd39-110">Double-click the warning in the **Errors List** window.</span></span> <span data-ttu-id="acd39-111">Visual Basic により、警告の原因となった XSD ファイル内の場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="acd39-111">Visual Basic will take you to the location in the XSD file that is the source of the warning.</span></span> <span data-ttu-id="acd39-112">XSD スキーマのエラーを修正します。</span><span class="sxs-lookup"><span data-stu-id="acd39-112">Correct the error in the XSD schema.</span></span>

- <span data-ttu-id="acd39-113">必要な XSD スキーマ (.xsd) ファイルがすべてプロジェクトに含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="acd39-113">Ensure that all required XSD schema (.xsd) files are included in the project.</span></span> <span data-ttu-id="acd39-114">**ソリューション エクスプローラー** で .xsd ファイルを表示するには、 **[プロジェクト]** メニューの **[すべてのファイルを表示]** をクリックする必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="acd39-114">You may need to click **Show All Files** on the **Project** menu to see your .xsd files in **Solution Explorer**.</span></span> <span data-ttu-id="acd39-115">.xsd ファイルを右クリックし、 **[プロジェクトに含める]** をクリックしてプロジェクトにファイルを含めます。</span><span class="sxs-lookup"><span data-stu-id="acd39-115">Right-click an .xsd file and then click **Include In Project** to include the file in your project.</span></span>

- <span data-ttu-id="acd39-116">XML to Schema ウィザードを使用している場合は、同じソースからスキーマを複数回推論すると、このエラーが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="acd39-116">If you are using the XML to Schema Wizard, this error can occur if you infer schemas more than one time from the same source.</span></span> <span data-ttu-id="acd39-117">この場合、プロジェクトから既存の XSD スキーマ ファイルを削除し、新しい XML to Schema 項目テンプレートを追加してから、プロジェクトに適用できるすべての XML ソースを XML to Schema ウィザードに提供できます。</span><span class="sxs-lookup"><span data-stu-id="acd39-117">In this case, you can remove the existing XSD schema files from the project, add a new XML to Schema item template, and then provide the XML to Schema Wizard with all the applicable XML sources for your project.</span></span>

- <span data-ttu-id="acd39-118">XSD スキーマでエラーが識別されない場合は、XML コンパイラに詳細なエラー メッセージを提供するのに十分な情報がない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="acd39-118">If no error is identified in your XSD schema, the XML compiler may not have enough information to provide a detailed error message.</span></span> <span data-ttu-id="acd39-119">プロジェクトに含まれている .xsd ファイルの XML 名前空間が、Visual Studio の XML スキーマ セットで識別された xml 名前空間と一致することを確認すると、より詳細なエラー情報を取得できる場合があります。</span><span class="sxs-lookup"><span data-stu-id="acd39-119">You may be able to get more detailed error information if you ensure that the XML namespaces for the .xsd files included in your project match the XML namespaces identified for the XML Schema set in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="acd39-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="acd39-120">See also</span></span>

- <span data-ttu-id="acd39-121">[[エラー一覧] ウィンドウ](/visualstudio/ide/reference/error-list-window)</span><span class="sxs-lookup"><span data-stu-id="acd39-121">[Error List Window](/visualstudio/ide/reference/error-list-window)</span></span>
- [<span data-ttu-id="acd39-122">XML</span><span class="sxs-lookup"><span data-stu-id="acd39-122">XML</span></span>](../../programming-guide/language-features/xml/index.md)
