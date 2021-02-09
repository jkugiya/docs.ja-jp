---
description: "詳細情報: BC42104:変数 '<variablename>' は、値が割り当てられる前に参照によって使用されています。"
title: 変数 '<variablename>' は、値が割り当てられる前に参照によって使用されています。
ms.date: 07/20/2015
f1_keywords:
- vbc42104
- BC42104
helpviewer_keywords:
- BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
ms.openlocfilehash: 501c3e3971c5ca0ebdba6981134f5029b77d0075
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701496"
---
# <a name="bc42104-variable-variablename-is-used-before-it-has-been-assigned-a-value"></a><span data-ttu-id="8da1c-103">BC42104:変数 '\<variablename>' は、値が割り当てられる前に参照によって使用されています。</span><span class="sxs-lookup"><span data-stu-id="8da1c-103">BC42104: Variable '\<variablename>' is used before it has been assigned a value</span></span>

<span data-ttu-id="8da1c-104">変数 '\<variablename>' は、値が割り当てられる前に使用されています。</span><span class="sxs-lookup"><span data-stu-id="8da1c-104">Variable '\<variablename>' is used before it has been assigned a value.</span></span> <span data-ttu-id="8da1c-105">結果として、実行時に null 参照の例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8da1c-105">A null reference exception could result at run time.</span></span>

 <span data-ttu-id="8da1c-106">アプリケーションには、値が割り当てられる前に変数を読み取るコードを通る可能性があるパスが少なくとも 1 つあります。</span><span class="sxs-lookup"><span data-stu-id="8da1c-106">An application has at least one possible path through its code that reads a variable before any value is assigned to it.</span></span>

 <span data-ttu-id="8da1c-107">変数に値が割り当てられていない場合、変数はそのデータ型の既定値を保持します。</span><span class="sxs-lookup"><span data-stu-id="8da1c-107">If a variable has never been assigned a value, it holds the default value for its data type.</span></span> <span data-ttu-id="8da1c-108">参照データ型の場合、その既定値は [Nothing](../nothing.md)です。</span><span class="sxs-lookup"><span data-stu-id="8da1c-108">For a reference data type, that default value is [Nothing](../nothing.md).</span></span> <span data-ttu-id="8da1c-109">値が `Nothing` である参照変数を読み取ると、状況によって <xref:System.NullReferenceException> が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8da1c-109">Reading a reference variable that has a value of `Nothing` can cause a <xref:System.NullReferenceException> in some circumstances.</span></span>

 <span data-ttu-id="8da1c-110">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="8da1c-110">By default, this message is a warning.</span></span> <span data-ttu-id="8da1c-111">警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8da1c-111">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="8da1c-112">**エラー ID:** BC42104</span><span class="sxs-lookup"><span data-stu-id="8da1c-112">**Error ID:** BC42104</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="8da1c-113">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="8da1c-113">To correct this error</span></span>

- <span data-ttu-id="8da1c-114">制御フロー ロジックをチェックして、変数を読み取るステートメントに制御が渡される前に、変数に有効な値が設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8da1c-114">Check your control flow logic and make sure the variable has a valid value before control passes to any statement that reads it.</span></span>

- <span data-ttu-id="8da1c-115">変数が常に有効な値を持つようにする 1 つの方法は、その宣言の一部として変数を初期化することです。</span><span class="sxs-lookup"><span data-stu-id="8da1c-115">One way to guarantee that the variable always has a valid value is to initialize it as part of its declaration.</span></span> <span data-ttu-id="8da1c-116">[Dim ステートメント](../statements/dim-statement.md)の "初期化" に関する説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8da1c-116">See "Initialization" in [Dim Statement](../statements/dim-statement.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8da1c-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="8da1c-117">See also</span></span>

- [<span data-ttu-id="8da1c-118">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="8da1c-118">Dim Statement</span></span>](../statements/dim-statement.md)
- [<span data-ttu-id="8da1c-119">変数宣言</span><span class="sxs-lookup"><span data-stu-id="8da1c-119">Variable Declaration</span></span>](../../programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="8da1c-120">変数のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="8da1c-120">Troubleshooting Variables</span></span>](../../programming-guide/language-features/variables/troubleshooting-variables.md)
