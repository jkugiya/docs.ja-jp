---
description: '詳細情報: Visual Basic の名前付け規則'
title: 命名規則
ms.date: 07/20/2015
helpviewer_keywords:
- names [Visual Basic], Visual Basic rules
- naming conventions
- naming conventions [Visual Basic], Visual Basic
- Visual Basic code, naming conventions
- conventions [Visual Basic], Visual Basic coding
- names [Visual Basic], naming conventions
- naming conventions [Visual Basic], classes
ms.assetid: 164949a4-2a7c-4736-9d82-9c3078e2e56c
ms.openlocfilehash: 058d3b06ca1da71c4d8993c6bd451531ec758dbd
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100461009"
---
# <a name="visual-basic-naming-conventions"></a><span data-ttu-id="bea46-103">Visual Basic の名前付け規則</span><span class="sxs-lookup"><span data-stu-id="bea46-103">Visual Basic Naming Conventions</span></span>

<span data-ttu-id="bea46-104">Visual Basic アプリケーションで要素に名前を付けるときは、その名前の最初の文字を英文字またはアンダースコアにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="bea46-104">When you name an element in your Visual Basic application, the first character of that name must be an alphabetic character or an underscore.</span></span> <span data-ttu-id="bea46-105">ただし、アンダースコアで始まる名前は、[言語への非依存性、および言語非依存コンポーネント](../../../standard/language-independence-and-language-independent-components.md) (CLS) に準拠していないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="bea46-105">Note, however, that names beginning with an underscore are not compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span>  
  
 <span data-ttu-id="bea46-106">名前付けには、次の推奨事項が適用されます。</span><span class="sxs-lookup"><span data-stu-id="bea46-106">The following suggestions apply to naming.</span></span>  
  
- <span data-ttu-id="bea46-107">名前の個々の単語は大文字で始めます (例: `FindLastRecord`、`RedrawMyForm`)。</span><span class="sxs-lookup"><span data-stu-id="bea46-107">Begin each separate word in a name with a capital letter, as in `FindLastRecord` and `RedrawMyForm`.</span></span>  
  
- <span data-ttu-id="bea46-108">関数名とメソッド名は動詞で始めます (例: `InitNameArray`、`CloseDialog`)。</span><span class="sxs-lookup"><span data-stu-id="bea46-108">Begin function and method names with a verb, as in `InitNameArray` or `CloseDialog`.</span></span>  
  
- <span data-ttu-id="bea46-109">クラス、構造体、モジュール、プロパティの名前は名詞で始めます (例: `EmployeeName`、`CarAccessory`)。</span><span class="sxs-lookup"><span data-stu-id="bea46-109">Begin class, structure, module, and property names with a noun, as in `EmployeeName` or `CarAccessory`.</span></span>  
  
- <span data-ttu-id="bea46-110">インターフェイス名はプレフィックス "I" で始め、その後に名詞または名詞句を続けるか (例: `IComponent`)、インターフェイスの動作を示す形容詞を続けます (例: `IPersistable`)。</span><span class="sxs-lookup"><span data-stu-id="bea46-110">Begin interface names with the prefix "I", followed by a noun or a noun phrase, like `IComponent`, or with an adjective describing the interface's behavior, like `IPersistable`.</span></span> <span data-ttu-id="bea46-111">アンダースコアは使用しないでください。また、省略形は混乱を招く可能性があるため、慎重に使用してください。</span><span class="sxs-lookup"><span data-stu-id="bea46-111">Do not use the underscore, and use abbreviations sparingly, because abbreviations can cause confusion.</span></span>  
  
- <span data-ttu-id="bea46-112">イベント ハンドラー名は、イベントの種類を示す名詞で始め、その後に "`EventHandler`" サフィックスを付けます (例: `MouseEventHandler`)。</span><span class="sxs-lookup"><span data-stu-id="bea46-112">Begin event handler names with a noun describing the type of event followed by the "`EventHandler`" suffix, as in "`MouseEventHandler`".</span></span>  
  
- <span data-ttu-id="bea46-113">イベント引数クラスの名前には、"`EventArgs`" サフィックスを含めます。</span><span class="sxs-lookup"><span data-stu-id="bea46-113">In names of event argument classes, include the "`EventArgs`" suffix.</span></span>  
  
- <span data-ttu-id="bea46-114">イベントに "前" または "後" の概念がある場合は、現在形または過去形のサフィックスを使用します (例: `ControlAdd`、`ControlAdded`)。</span><span class="sxs-lookup"><span data-stu-id="bea46-114">If an event has a concept of "before" or "after," use a suffix in present or past tense, as in "`ControlAdd`" or "`ControlAdded`".</span></span>  
  
- <span data-ttu-id="bea46-115">長い用語や頻繁に使用される用語については、省略形を使用して名前を妥当な長さにとどめます。たとえば、"Hypertext Markup Language" ではなく、"HTML" を使用します。</span><span class="sxs-lookup"><span data-stu-id="bea46-115">For long or frequently used terms, use abbreviations to keep name lengths reasonable, for example, "HTML", instead of "Hypertext Markup Language".</span></span> <span data-ttu-id="bea46-116">一般に、低解像度に設定されたモニターでは、32 文字を超える変数名は読みにくくなります。</span><span class="sxs-lookup"><span data-stu-id="bea46-116">In general, variable names greater than 32 characters are difficult to read on a monitor set to a low resolution.</span></span> <span data-ttu-id="bea46-117">また、アプリケーション全体で省略形が一貫している必要があります。</span><span class="sxs-lookup"><span data-stu-id="bea46-117">Also, make sure your abbreviations are consistent throughout the entire application.</span></span> <span data-ttu-id="bea46-118">プロジェクト内で "HTML" と "Hypertext Markup Language" をランダムに切り替えると、混乱が生じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bea46-118">Randomly switching in a project between "HTML" and "Hypertext Markup Language" can lead to confusion.</span></span>  
  
- <span data-ttu-id="bea46-119">外側のスコープ内の名前と同じ名前を内側のスコープで使用しないようにします。</span><span class="sxs-lookup"><span data-stu-id="bea46-119">Avoid using names in an inner scope that are the same as names in an outer scope.</span></span> <span data-ttu-id="bea46-120">間違った変数にアクセスすると、エラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bea46-120">Errors can result if the wrong variable is accessed.</span></span> <span data-ttu-id="bea46-121">同じ名前の変数とキーワード間で競合が発生した場合は、キーワードの前に適切なタイプ ライブラリを指定して、キーワードを識別する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bea46-121">If a conflict occurs between a variable and the keyword of the same name, you must identify the keyword by preceding it with the appropriate type library.</span></span> <span data-ttu-id="bea46-122">たとえば、`Date` という変数がある場合、組み込み関数の `Date` は、<xref:System.DateTime.Date%2A?displayProperty=nameWithType> を呼び出すことによってのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="bea46-122">For example, if you have a variable called `Date`, you can use the intrinsic `Date` function only by calling <xref:System.DateTime.Date%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bea46-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="bea46-123">See also</span></span>

- [<span data-ttu-id="bea46-124">コード内の要素名としてのキーワード</span><span class="sxs-lookup"><span data-stu-id="bea46-124">Keywords as Element Names in Code</span></span>](keywords-as-element-names-in-code.md)
- [<span data-ttu-id="bea46-125">Me、My、MyBase、および MyClass</span><span class="sxs-lookup"><span data-stu-id="bea46-125">Me, My, MyBase, and MyClass</span></span>](me-my-mybase-and-myclass.md)
- [<span data-ttu-id="bea46-126">宣言された要素の名前</span><span class="sxs-lookup"><span data-stu-id="bea46-126">Declared Element Names</span></span>](../language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="bea46-127">プログラム構造とコード規則</span><span class="sxs-lookup"><span data-stu-id="bea46-127">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)
- [<span data-ttu-id="bea46-128">Visual Basic の言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="bea46-128">Visual Basic Language Reference</span></span>](../../language-reference/index.md)
