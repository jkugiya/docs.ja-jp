---
description: "詳細情報: BC30920:'<constructorname>' の基本クラス '<baseclassname>' にある '<derivedclassname>' が古い形式に設定されているため、この 'Sub New' の最初のステートメントは、明示的な 'MyBase.New' または 'MyClass.New' への呼び出しでなければなりません: '<errormessage>'"
title: "'<constructorname>' の基本クラス '<baseclassname>' にある '<derivedclassname>' が古い形式に設定されているため、この 'Sub New' の最初のステートメントは、明示的な 'MyBase.New' または 'MyClass.New' への呼び出しでなければなりません: '<errormessage>'"
ms.date: 07/20/2015
f1_keywords:
- vbc30920
- bc30920
helpviewer_keywords:
- BC30920
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
ms.openlocfilehash: 9a61ed67a7d65c49c06d6848acf7d9fc40173af7
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100426596"
---
# <a name="bc30920-first-statement-of-this-sub-new-must-be-an-explicit-call-to-mybasenew-or-myclassnew-because-the-constructorname-in-the-base-class-baseclassname-of-derivedclassname-is-marked-obsolete-errormessage"></a><span data-ttu-id="1cc66-103">BC30920:'\<constructorname>' の基本クラス '\<baseclassname>' にある '\<derivedclassname>' が古い形式に設定されているため、この 'Sub New' の最初のステートメントは、明示的な 'MyBase.New' または 'MyClass.New' への呼び出しでなければなりません: '\<errormessage>'</span><span class="sxs-lookup"><span data-stu-id="1cc66-103">BC30920: First statement of this 'Sub New' must be an explicit call to 'MyBase.New' or 'MyClass.New' because the '\<constructorname>' in the base class '\<baseclassname>' of '\<derivedclassname>' is marked obsolete: '\<errormessage>'</span></span>

<span data-ttu-id="1cc66-104">クラス コンストラクターが基底クラスのコンストラクターを明示的に呼び出さず、暗黙的な基底クラスのコンストラクターが <xref:System.ObsoleteAttribute> 属性およびエラーとして扱うことを示すディレクティブでマークされています。</span><span class="sxs-lookup"><span data-stu-id="1cc66-104">A class constructor does not explicitly call a base class constructor, and the implicit base class constructor is marked with the <xref:System.ObsoleteAttribute> attribute and the directive to treat it as an error.</span></span>

 <span data-ttu-id="1cc66-105">派生クラスのコンストラクターが基底クラスのコンストラクターを呼び出さない場合、Visual Basic では、パラメーターなしの基底クラスのコンストラクターの暗黙的な呼び出しを生成しようとします。</span><span class="sxs-lookup"><span data-stu-id="1cc66-105">When a derived class constructor does not call a base class constructor, Visual Basic attempts to generate an implicit call to a parameterless base class constructor.</span></span> <span data-ttu-id="1cc66-106">引数を指定せずに呼び出すことができるアクセス可能なコンストラクターが基底クラスにない場合、Visual Basic では暗黙的な呼び出しを生成できません。</span><span class="sxs-lookup"><span data-stu-id="1cc66-106">If there is no accessible constructor in the base class that can be called without arguments, Visual Basic cannot generate an implicit call.</span></span> <span data-ttu-id="1cc66-107">この場合、必要なコンストラクターが <xref:System.ObsoleteAttribute> 属性でマークされるため、Visual Basic では呼び出すことができません。</span><span class="sxs-lookup"><span data-stu-id="1cc66-107">In this case, the required constructor is marked with the <xref:System.ObsoleteAttribute> attribute, so Visual Basic cannot call it.</span></span>

 <span data-ttu-id="1cc66-108">どのプログラミング要素でも、 <xref:System.ObsoleteAttribute> を適用すれば、もう使用しなくなったものとしてマークを付けることができます。</span><span class="sxs-lookup"><span data-stu-id="1cc66-108">You can mark any programming element as being no longer in use by applying <xref:System.ObsoleteAttribute> to it.</span></span> <span data-ttu-id="1cc66-109">これを行う場合、この属性の <xref:System.ObsoleteAttribute.IsError%2A> プロパティを `True` または `False`のどちらかに設定できます。</span><span class="sxs-lookup"><span data-stu-id="1cc66-109">If you do this, you can set the attribute's <xref:System.ObsoleteAttribute.IsError%2A> property to either `True` or `False`.</span></span> <span data-ttu-id="1cc66-110">`True`に設定した場合、この要素を使用しようとすると、コンパイラはエラーとして処理します。</span><span class="sxs-lookup"><span data-stu-id="1cc66-110">If you set it to `True`, the compiler treats an attempt to use the element as an error.</span></span> <span data-ttu-id="1cc66-111">`False`に設定した場合、または既定値の `False`を使用した場合、コンパイラはこの要素の使用が試行されると、警告を発行します。</span><span class="sxs-lookup"><span data-stu-id="1cc66-111">If you set it to `False`, or let it default to `False`, the compiler issues a warning if there is an attempt to use the element.</span></span>

 <span data-ttu-id="1cc66-112">**エラー ID:** BC30920</span><span class="sxs-lookup"><span data-stu-id="1cc66-112">**Error ID:** BC30920</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="1cc66-113">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="1cc66-113">To correct this error</span></span>

1. <span data-ttu-id="1cc66-114">引用符で囲まれたエラー メッセージを確認し、適切な処理を行います。</span><span class="sxs-lookup"><span data-stu-id="1cc66-114">Examine the quoted error message and take appropriate action.</span></span>

2. <span data-ttu-id="1cc66-115">`MyBase.New()` または `MyClass.New()` の呼び出しを `Sub New` の最初のステートメントとして派生クラスに含めます。</span><span class="sxs-lookup"><span data-stu-id="1cc66-115">Include a call to `MyBase.New()` or `MyClass.New()` as the first statement of the `Sub New` in the derived class.</span></span>

## <a name="see-also"></a><span data-ttu-id="1cc66-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="1cc66-116">See also</span></span>

- [<span data-ttu-id="1cc66-117">属性の概要</span><span class="sxs-lookup"><span data-stu-id="1cc66-117">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
