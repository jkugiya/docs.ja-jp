---
description: '詳細情報: 方法:Visual Basic で XML ドキュメントを作成する'
title: '方法: XML ドキュメントを作成する'
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
ms.openlocfilehash: d54c79d820a170b246e5c85d7562487fbe66f39c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475956"
---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a><span data-ttu-id="e96b8-103">方法: Visual Basic で XML ドキュメントを作成する</span><span class="sxs-lookup"><span data-stu-id="e96b8-103">How to: Create XML Documentation in Visual Basic</span></span>

<span data-ttu-id="e96b8-104">この例では、XML ドキュメント コメントをコードに追加する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e96b8-104">This example shows how to add XML documentation comments to your code.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-xml-documentation-for-a-type-or-member"></a><span data-ttu-id="e96b8-105">型またはメンバーの XML ドキュメントを作成するには</span><span class="sxs-lookup"><span data-stu-id="e96b8-105">To create XML documentation for a type or member</span></span>

1. <span data-ttu-id="e96b8-106">**コード エディター** で、ドキュメントを作成する型またはメンバーの上の行にカーソルを置きます。</span><span class="sxs-lookup"><span data-stu-id="e96b8-106">In the **Code Editor**, position your cursor on the line above the type or member for which you want to create documentation.</span></span>

2. <span data-ttu-id="e96b8-107">`'''` (3 つの単一引用符) を入力します。</span><span class="sxs-lookup"><span data-stu-id="e96b8-107">Type `'''` (three single-quotation marks).</span></span>

    <span data-ttu-id="e96b8-108">型またはメンバーの XML スケルトンが **コード エディター** に追加されます。</span><span class="sxs-lookup"><span data-stu-id="e96b8-108">An XML skeleton for the type or member is added in the **Code Editor**.</span></span>

3. <span data-ttu-id="e96b8-109">適切なタグの間に説明情報を追加します。</span><span class="sxs-lookup"><span data-stu-id="e96b8-109">Add descriptive information between the appropriate tags.</span></span>

    > [!NOTE]
    > <span data-ttu-id="e96b8-110">XML ドキュメント ブロック内に行を追加する場合は、各行が `'''` で始まる必要があります。</span><span class="sxs-lookup"><span data-stu-id="e96b8-110">If you add additional lines within the XML documentation block, each line must begin with `'''`.</span></span>

4. <span data-ttu-id="e96b8-111">新しい XML ドキュメント コメントと共に型またはメンバーを使用するコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="e96b8-111">Add additional code that uses the type or member with the new XML documentation comments.</span></span>

    <span data-ttu-id="e96b8-112">IntelliSense により、型またはメンバーの \<summary> タグのテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e96b8-112">IntelliSense displays the text from the \<summary> tag for the type or member.</span></span>

5. <span data-ttu-id="e96b8-113">コードをコンパイルして、ドキュメント コメントを含む XML ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="e96b8-113">Compile the code to generate an XML file containing the documentation comments.</span></span> <span data-ttu-id="e96b8-114">詳細については、「[-doc](../../reference/command-line-compiler/doc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e96b8-114">For more information, see [-doc](../../reference/command-line-compiler/doc.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e96b8-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="e96b8-115">See also</span></span>

- [<span data-ttu-id="e96b8-116">XML の使用によるコードのドキュメントの作成</span><span class="sxs-lookup"><span data-stu-id="e96b8-116">Documenting Your Code with XML</span></span>](documenting-your-code-with-xml.md)
- [<span data-ttu-id="e96b8-117">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="e96b8-117">XML Comment Tags</span></span>](../../language-reference/xmldoc/index.md)
- [<span data-ttu-id="e96b8-118">-doc</span><span class="sxs-lookup"><span data-stu-id="e96b8-118">-doc</span></span>](../../reference/command-line-compiler/doc.md)
