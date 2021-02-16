---
description: '詳細情報: 方法:Visual Basic で列挙型を反復処理する'
title: '方法: 列挙型を反復処理する'
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
ms.openlocfilehash: a14d65a33e8a2f7872203a6a332dec1e753704f8
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100471566"
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a><span data-ttu-id="c5660-103">方法: Visual Basic で列挙型を反復処理する</span><span class="sxs-lookup"><span data-stu-id="c5660-103">How to: Iterate Through An Enumeration in Visual Basic</span></span>

<span data-ttu-id="c5660-104">一連の関連する定数を操作する場合や、定数値に名前を関連付ける場合は、列挙型を使うと便利です。</span><span class="sxs-lookup"><span data-stu-id="c5660-104">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="c5660-105"><xref:System.Enum.GetValues%2A> メソッドを使用して列挙型を配列に入れると、列挙型の反復処理を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="c5660-105">To iterate through an enumeration, you can move it into an array using the <xref:System.Enum.GetValues%2A> method.</span></span> <span data-ttu-id="c5660-106">また、`For...Each` ステートメント、<xref:System.Enum.GetNames%2A> メソッド、または <xref:System.Enum.GetValues%2A> メソッドを使用して列挙型の反復処理を行うと、文字列値または数値を抽出できます。</span><span class="sxs-lookup"><span data-stu-id="c5660-106">You could also iterate through an enumeration using a `For...Each` statement, using the <xref:System.Enum.GetNames%2A> or <xref:System.Enum.GetValues%2A> method to extract the string or numeric value.</span></span>  
  
### <a name="to-iterate-through-an-enumeration"></a><span data-ttu-id="c5660-107">列挙型を反復処理するには</span><span class="sxs-lookup"><span data-stu-id="c5660-107">To iterate through an enumeration</span></span>  
  
- <span data-ttu-id="c5660-108">他の変数の場合と同様に、配列を宣言して <xref:System.Enum.GetValues%2A> メソッドにより列挙型をその配列に変換してから、配列を渡します。</span><span class="sxs-lookup"><span data-stu-id="c5660-108">Declare an array and convert the enumeration to it with the <xref:System.Enum.GetValues%2A> method before passing the array as you would any other variable.</span></span> <span data-ttu-id="c5660-109">次の例では、列挙型 <xref:Microsoft.VisualBasic.FirstDayOfWeek> の反復処理の進捗に応じて、この列挙型の各メンバーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c5660-109">The following example displays each member of the enumeration <xref:Microsoft.VisualBasic.FirstDayOfWeek> as it iterates through the enumeration.</span></span>  
  
     [!code-vb[VbEnumsTask#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="c5660-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="c5660-110">See also</span></span>

- [<span data-ttu-id="c5660-111">列挙型の概要</span><span class="sxs-lookup"><span data-stu-id="c5660-111">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="c5660-112">方法: 列挙型を宣言する</span><span class="sxs-lookup"><span data-stu-id="c5660-112">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="c5660-113">列挙型を使用する状況</span><span class="sxs-lookup"><span data-stu-id="c5660-113">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
- [<span data-ttu-id="c5660-114">方法: 列挙値に関連付けられている文字列を確認する</span><span class="sxs-lookup"><span data-stu-id="c5660-114">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="c5660-115">方法: 列挙型のメンバーを参照する</span><span class="sxs-lookup"><span data-stu-id="c5660-115">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="c5660-116">列挙型と名前の修飾</span><span class="sxs-lookup"><span data-stu-id="c5660-116">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="c5660-117">配列</span><span class="sxs-lookup"><span data-stu-id="c5660-117">Arrays</span></span>](../arrays/index.md)
