---
description: '詳細情報: BC42017:遅延バインドの解決です。ランタイム エラーが発生する可能性があります。'
title: 遅延バインドの解決です。ランタイム エラーが発生する可能性があります。
ms.date: 07/20/2015
f1_keywords:
- vbc42017
- BC42017
helpviewer_keywords:
- BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
ms.openlocfilehash: 2c783a7aff46df8ab033463f49c45f4c797220ea
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795925"
---
# <a name="bc42017-late-bound-resolution-runtime-errors-could-occur"></a><span data-ttu-id="823db-103">BC42017:遅延バインドの解決です。ランタイム エラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="823db-103">BC42017: Late bound resolution; runtime errors could occur</span></span>

<span data-ttu-id="823db-104">オブジェクトは、[Object データ型](../data-types/object-data-type.md)として宣言された変数に代入されます。</span><span class="sxs-lookup"><span data-stu-id="823db-104">An object is assigned to a variable declared to be of the [Object Data Type](../data-types/object-data-type.md).</span></span>

 <span data-ttu-id="823db-105">変数を `Object` として宣言した場合、コンパイラでは *遅延バインディング* を実行する必要があり、これによって実行時に余分な処理が発生します。</span><span class="sxs-lookup"><span data-stu-id="823db-105">When you declare a variable as `Object`, the compiler must perform *late binding*, which causes extra operations at run time.</span></span> <span data-ttu-id="823db-106">また、アプリケーションで実行時エラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="823db-106">It also exposes your application to potential run-time errors.</span></span> <span data-ttu-id="823db-107">たとえば、`Object` 変数に <xref:System.Windows.Forms.Form> を代入し、<xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> プロパティにアクセスしようとすると、<xref:System.Windows.Forms.Form> クラスが `NameTable` プロパティを公開しないため、ランタイムで <xref:System.MemberAccessException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="823db-107">For example, if you assign a <xref:System.Windows.Forms.Form> to the `Object` variable and then try to access the <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> property, the runtime throws a <xref:System.MemberAccessException> because the <xref:System.Windows.Forms.Form> class does not expose a `NameTable` property.</span></span>

 <span data-ttu-id="823db-108">変数を特定の型として宣言する場合、コンパイラではコンパイル時に *事前バインディング* を実行できます。</span><span class="sxs-lookup"><span data-stu-id="823db-108">If you declare the variable to be of a specific type, the compiler can perform *early binding* at compile time.</span></span> <span data-ttu-id="823db-109">これにより、パフォーマンスが向上し、特定の型のメンバーへのアクセスが制御され、コードが読みやすくなります。</span><span class="sxs-lookup"><span data-stu-id="823db-109">This results in improved performance, controlled access to the members of the specific type, and better readability of your code.</span></span>

 <span data-ttu-id="823db-110">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="823db-110">By default, this message is a warning.</span></span> <span data-ttu-id="823db-111">警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="823db-111">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="823db-112">**エラー ID:** BC42017</span><span class="sxs-lookup"><span data-stu-id="823db-112">**Error ID:** BC42017</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="823db-113">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="823db-113">To correct this error</span></span>

- <span data-ttu-id="823db-114">可能であれば、変数を特定の型として宣言します。</span><span class="sxs-lookup"><span data-stu-id="823db-114">If possible, declare the variable to be of a specific type.</span></span>

## <a name="see-also"></a><span data-ttu-id="823db-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="823db-115">See also</span></span>

- [<span data-ttu-id="823db-116">事前バインディングと遅延バインディング</span><span class="sxs-lookup"><span data-stu-id="823db-116">Early and Late Binding</span></span>](../../programming-guide/language-features/early-late-binding/index.md)
- [<span data-ttu-id="823db-117">オブジェクト変数の宣言</span><span class="sxs-lookup"><span data-stu-id="823db-117">Object Variable Declaration</span></span>](../../programming-guide/language-features/variables/object-variable-declaration.md)
