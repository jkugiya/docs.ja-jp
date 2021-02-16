---
description: '詳細情報: 方法:列挙値に関連付けられている文字列を確認する (Visual Basic)'
title: '方法: 列挙値に関連付けられている文字列を確認する'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- strings [Visual Basic], enumeration values
- values [Visual Basic], enumeration members
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
ms.openlocfilehash: 391cb097fa8163f7131cc30f85f8a4f85ba826a4
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100471605"
---
# <a name="how-to-determine-the-string-associated-with-an-enumeration-value-visual-basic"></a><span data-ttu-id="6a1c4-103">方法: 列挙値に関連付けられている文字列を確認する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6a1c4-103">How to: Determine the String Associated with an Enumeration Value (Visual Basic)</span></span>

<span data-ttu-id="6a1c4-104"><xref:System.Enum.GetValues%2A> メソッドと <xref:System.Enum.GetNames%2A> メソッドを使用することで、列挙型メンバーに関連付けられている文字列と値を確認できます。</span><span class="sxs-lookup"><span data-stu-id="6a1c4-104">The <xref:System.Enum.GetValues%2A> and <xref:System.Enum.GetNames%2A> methods allow you to determine the strings and values associated with enumeration members.</span></span>  
  
### <a name="to-determine-the-string-associated-with-an-enumeration"></a><span data-ttu-id="6a1c4-105">列挙型に関連付けられている文字列を確認するには</span><span class="sxs-lookup"><span data-stu-id="6a1c4-105">To determine the string associated with an enumeration</span></span>  
  
- <span data-ttu-id="6a1c4-106">列挙型メンバーに関連付けられている文字列を取得するには、<xref:System.Enum.GetNames%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="6a1c4-106">Use the <xref:System.Enum.GetNames%2A> method to retrieve the strings associated with the enumeration members.</span></span> <span data-ttu-id="6a1c4-107">次の例では、列挙型 `flavorEnum` を宣言してから、各メンバーに関連付けられている文字列を <xref:System.Enum.GetNames%2A> メソッドにより表示します。</span><span class="sxs-lookup"><span data-stu-id="6a1c4-107">This example declares an enumeration, `flavorEnum`, then uses the <xref:System.Enum.GetNames%2A> method to display the strings associated with each member.</span></span>  
  
     [!code-vb[VbEnumsTask#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="6a1c4-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="6a1c4-108">See also</span></span>

- <xref:System.Enum.GetValues%2A>
- <xref:System.Enum.GetNames%2A>
- <xref:System.Enum>
- [<span data-ttu-id="6a1c4-109">方法: 列挙型を宣言する</span><span class="sxs-lookup"><span data-stu-id="6a1c4-109">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="6a1c4-110">方法: 列挙型のメンバーを参照する</span><span class="sxs-lookup"><span data-stu-id="6a1c4-110">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="6a1c4-111">列挙型と名前の修飾</span><span class="sxs-lookup"><span data-stu-id="6a1c4-111">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="6a1c4-112">方法: Visual Basic で列挙型を反復処理する</span><span class="sxs-lookup"><span data-stu-id="6a1c4-112">How to: Iterate Through An Enumeration in Visual Basic</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="6a1c4-113">列挙型を使用する状況</span><span class="sxs-lookup"><span data-stu-id="6a1c4-113">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
- [<span data-ttu-id="6a1c4-114">Enum ステートメント</span><span class="sxs-lookup"><span data-stu-id="6a1c4-114">Enum Statement</span></span>](../../../language-reference/statements/enum-statement.md)
