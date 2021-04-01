---
description: '詳細情報: ドキュメントに埋め込まれたスタイル シート ディレクティブ'
title: ドキュメントに埋め込まれたスタイル シート ディレクティブ
ms.date: 03/30/2017
ms.assetid: d79fb295-ebc7-438d-ba1b-05be7d534834
ms.openlocfilehash: 3585cc2f9e7d931a89c1f81283282712195720f0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782937"
---
# <a name="style-sheet-directives-embedded-in-a-document"></a><span data-ttu-id="d9acd-103">ドキュメントに埋め込まれたスタイル シート ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="d9acd-103">Style Sheet Directives Embedded in a Document</span></span>

<span data-ttu-id="d9acd-104">既存の XML に `<?xml:stylesheet?>` というスタイル シート ディレクティブが含まれていることがあります。</span><span class="sxs-lookup"><span data-stu-id="d9acd-104">Occasionally, existing XML contains the style sheet directive of `<?xml:stylesheet?>`.</span></span> <span data-ttu-id="d9acd-105">Microsoft Internet Explorer は、これを `<?xml-stylesheet?>` 構文に代わるものとして受け入れます。</span><span class="sxs-lookup"><span data-stu-id="d9acd-105">Microsoft Internet Explorer accepts this as an alternative to the `<?xml-stylesheet?>` syntax.</span></span> <span data-ttu-id="d9acd-106">次のように `<?xml:stylesheet?>` ディレクティブが含まれている XML データを XML ドキュメント オブジェクト モデル (DOM) に読み込もうとすると、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="d9acd-106">When the XML data contains an `<?xml:stylesheet?>` directive, as shown in the following data, attempting to load this data into the XML Document Object Model (DOM) throws an exception.</span></span>

```xml
<?xml version="1.0" ?>
<?xml:stylesheet type="text/xsl" href="test2.xsl"?>
<root>
    <test>Node 1</test>
    <test>Node 2</test>
</root>
```

<span data-ttu-id="d9acd-107">例外が発生するのは、`<?xml:stylesheet?>` が DOM に対する無効な **ProcessingInstruction** と見なされるからです。</span><span class="sxs-lookup"><span data-stu-id="d9acd-107">This occurs because the `<?xml:stylesheet?>` is considered an invalid **ProcessingInstruction** to the DOM.</span></span> <span data-ttu-id="d9acd-108">『Namespaces in XML』仕様によれば、**ProcessingInstruction** は、QNames (修飾名) ではなく、NCNames (コロンが含まれない名前) にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d9acd-108">Any **ProcessingInstruction**, according to the Namespaces in XML specification, can only be no-colon names (NCNames), as opposed to qualified names (QNames).</span></span>

<span data-ttu-id="d9acd-109">『Namespaces in XML』仕様書のセクション 6 によると、**Load** メソッドと **LoadXml** メソッドをこの仕様に準拠させた場合の影響として、ドキュメントには次の規則が適用されることになります。</span><span class="sxs-lookup"><span data-stu-id="d9acd-109">From Section 6 of the Namespaces in XML specification, the effect of having the **Load** and **LoadXml** methods conform to the specification is that in a document:</span></span>

- <span data-ttu-id="d9acd-110">すべての要素型と属性名は、0 個または 1 個のコロンを含みます。</span><span class="sxs-lookup"><span data-stu-id="d9acd-110">All element types and attribute names contain either zero or one colon.</span></span>

- <span data-ttu-id="d9acd-111">エンティティ名、処理命令ターゲット、記法名は、いずれもコロンを含みません。</span><span class="sxs-lookup"><span data-stu-id="d9acd-111">No entity names, ProcessingInstruction targets, or notation names contain any colons.</span></span>

<span data-ttu-id="d9acd-112">コロンが含まれた `<?xml:stylesheet?>` は、2 番目の規則に違反します。</span><span class="sxs-lookup"><span data-stu-id="d9acd-112">With the `<?xml:stylesheet?>` containing a colon, you now violate the rule in the second bullet.</span></span>

<span data-ttu-id="d9acd-113">W3C (World Wide Web Consortium) 勧告『[Associating Style Sheets with XML documents Version 1.0](https://www.w3.org/TR/xml-stylesheet/)』によれば、XSLT スタイル シートを XML ドキュメントに関連付ける処理命令は、コロンをダッシュに置き換えた `<?xml-stylesheet?>` です。</span><span class="sxs-lookup"><span data-stu-id="d9acd-113">According to the World Wide Web Consortium (W3C) [Associating Style Sheets with XML documents Version 1.0 Recommendation](https://www.w3.org/TR/xml-stylesheet/),  the processing instruction to associate an XSLT style sheet with an XML document is `<?xml-stylesheet?>`, with a dash replacing the colon.</span></span>

## <a name="see-also"></a><span data-ttu-id="d9acd-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="d9acd-114">See also</span></span>

- [<span data-ttu-id="d9acd-115">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="d9acd-115">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
