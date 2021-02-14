---
description: "詳細情報: BC30955:型 '<typename1>' の値を '<typename2>' に変換できません"
title: 型 '<typename1>' の値を '<typename2>' に変換できません。
ms.date: 07/20/2015
f1_keywords:
- vbc30955
- bc30955
helpviewer_keywords:
- BC30955
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
ms.openlocfilehash: e03201d5dbb84faf06b7acbe42fe6b3bb4272ab9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666252"
---
# <a name="bc30955-value-of-type-typename1-cannot-be-converted-to-typename2"></a><span data-ttu-id="eda03-103">BC30955:型 '\<typename1>' の値を '\<typename2>' に変換できません。</span><span class="sxs-lookup"><span data-stu-id="eda03-103">BC30955: Value of type '\<typename1>' cannot be converted to '\<typename2>'</span></span>

<span data-ttu-id="eda03-104">型 '\<typename1>' の値を '\<typename2>' に変換できません。</span><span class="sxs-lookup"><span data-stu-id="eda03-104">Value of type '\<typename1>' cannot be converted to '\<typename2>'.</span></span> <span data-ttu-id="eda03-105">ファイル参照とアセンブリ '\<assemblyname>' へのプロジェクト参照との混在により、型の不一致が生じた可能性があります。</span><span class="sxs-lookup"><span data-stu-id="eda03-105">Type mismatch could be due to the mixing of a file reference with a project reference to assembly '\<assemblyname>'.</span></span> <span data-ttu-id="eda03-106">プロジェクト '\<projectname1>' の '\<filepath>' へのファイル参照を '\<projectname2>' へのプロジェクト参照で置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="eda03-106">Try replacing the file reference to '\<filepath>' in project '\<projectname1>' with a project reference to '\<projectname2>'.</span></span>

 <span data-ttu-id="eda03-107">プロジェクトがプロジェクト参照とファイル参照の両方を行う場合、コンパイラは、1 つの型を別の型に変換できることを保証できません。</span><span class="sxs-lookup"><span data-stu-id="eda03-107">In a situation where a project makes both a project reference and a file reference, the compiler cannot guarantee that one type can be converted to another.</span></span>

 <span data-ttu-id="eda03-108">次の擬似コードは、このエラーを生成する可能性がある状況を示しています。</span><span class="sxs-lookup"><span data-stu-id="eda03-108">The following pseudo-code illustrates a situation that can generate this error.</span></span>

 `' ================ Visual Basic project P1 ================`

 `'        P1 makes a PROJECT REFERENCE to project P2`

 `'        and a FILE REFERENCE to project P3.`

 `Public commonObject As P3.commonClass`

 `commonObject = P2.getCommonClass()`

 `' ================ Visual Basic project P2 ================`

 `'        P2 makes a PROJECT REFERENCE to project P3`

 `Public Function getCommonClass() As P3.commonClass`

 `Return New P3.commonClass`

 `End Function`

 `' ================ Visual Basic project P3 ================`

 `Public Class commonClass`

 `End Class`

 <span data-ttu-id="eda03-109">プロジェクト `P1` は、プロジェクト `P2` からプロジェクト `P3` への間接プロジェクト参照と、`P3` への直接ファイル参照を行います。</span><span class="sxs-lookup"><span data-stu-id="eda03-109">Project `P1` makes an indirect project reference through project `P2` to project `P3`, and also a direct file reference to `P3`.</span></span> <span data-ttu-id="eda03-110">`commonObject` の宣言は `P3` へのファイル参照を使用しますが、`P2.getCommonClass` の呼び出しは `P3` へのプロジェクト参照を使用します。</span><span class="sxs-lookup"><span data-stu-id="eda03-110">The declaration of `commonObject` uses the file reference to `P3`, while the call to `P2.getCommonClass` uses the project reference to `P3`.</span></span>

 <span data-ttu-id="eda03-111">この場合の問題は、ファイル参照が `P3` (通常は p3.dll) の出力ファイルのファイル パスと名前を指定する一方、プロジェクト参照はプロジェクト名でソース プロジェクト (`P3`) を識別することです。</span><span class="sxs-lookup"><span data-stu-id="eda03-111">The problem in this situation is that the file reference specifies a file path and name for the output file of `P3` (typically p3.dll), while the project references identify the source project (`P3`) by project name.</span></span> <span data-ttu-id="eda03-112">このため、コンパイラは、型 `P3.commonClass` が 2 つの異なる参照を使用した同じソース コードからのものであることを保証できません。</span><span class="sxs-lookup"><span data-stu-id="eda03-112">Because of this, the compiler cannot guarantee that the type `P3.commonClass` comes from the same source code through the two different references.</span></span>

 <span data-ttu-id="eda03-113">この状況は通常、プロジェクト参照とファイル参照が混在している場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="eda03-113">This situation typically occurs when project references and file references are mixed.</span></span> <span data-ttu-id="eda03-114">前の図の、`P1` でファイル参照ではなく `P3` への直接プロジェクト参照が行われた場合、この問題は発生しません。</span><span class="sxs-lookup"><span data-stu-id="eda03-114">In the preceding illustration, the problem would not occur if `P1` made a direct project reference to `P3` instead of a file reference.</span></span>

 <span data-ttu-id="eda03-115">**エラー ID:** BC30955</span><span class="sxs-lookup"><span data-stu-id="eda03-115">**Error ID:** BC30955</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="eda03-116">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="eda03-116">To correct this error</span></span>

- <span data-ttu-id="eda03-117">ファイル参照をプロジェクト参照に変更します。</span><span class="sxs-lookup"><span data-stu-id="eda03-117">Change the file reference to a project reference.</span></span>

## <a name="see-also"></a><span data-ttu-id="eda03-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="eda03-118">See also</span></span>

- [<span data-ttu-id="eda03-119">Visual Basic における型変換</span><span class="sxs-lookup"><span data-stu-id="eda03-119">Type Conversions in Visual Basic</span></span>](../../programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="eda03-120">プロジェクト内の参照の管理</span><span class="sxs-lookup"><span data-stu-id="eda03-120">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
