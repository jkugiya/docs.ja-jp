---
description: "詳細情報: BC30971:<message> このエラーは、ファイル参照と '<assemblyname>' へのプロジェクト参照との混合によって生じた可能性があります。"
title: <message> このエラーは、ファイル参照と '<assemblyname>' へのプロジェクト参照との混合によって生じた可能性があります。
ms.date: 07/20/2015
f1_keywords:
- bc30971
- vbc30971
helpviewer_keywords:
- BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
ms.openlocfilehash: 73b0e3623bdb5fd7b8ab2110d85436b3f415b4f9
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100470942"
---
# <a name="bc30971-message-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-assemblyname"></a><span data-ttu-id="0e637-103">BC30971:\<message> このエラーは、ファイル参照と '\<assemblyname>' へのプロジェクト参照との混合によって生じた可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0e637-103">BC30971: \<message> This error could also be due to mixing a file reference with a project reference to assembly '\<assemblyname>'</span></span>

<span data-ttu-id="0e637-104">\<message> このエラーは、ファイル参照とアセンブリ '\<assemblyname> へのプロジェクト参照との混合によって生じた可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0e637-104">\<message> This error could also be due to mixing a file reference with a project reference to assembly '\<assemblyname>.</span></span> <span data-ttu-id="0e637-105">この場合、プロジェクト '\<projectname1>' の '\<assemblyfilename>' へのファイル参照を '\<projectname2>' へのプロジェクト参照で置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="0e637-105">In this case, try replacing the file reference to '\<assemblyfilename>' in project '\<projectname1>' with a project reference to '\<projectname2>'.</span></span>

 <span data-ttu-id="0e637-106">プロジェクト内のコードが別のプロジェクトのメンバーにアクセスしていますが、ソリューションが Visual Basic コンパイラに参照の解決を許可するよう構成されていません。</span><span class="sxs-lookup"><span data-stu-id="0e637-106">Code in your project accesses a member of another project, but the configuration of your solution does not allow the Visual Basic compiler to resolve the reference.</span></span>

 <span data-ttu-id="0e637-107">別のアセンブリで定義されている型にアクセスするには、そのアセンブリへの参照を Visual Basic コンパイラが保持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0e637-107">To access a type defined in another assembly, the Visual Basic compiler must have a reference to that assembly.</span></span> <span data-ttu-id="0e637-108">これは、プロジェクト間の循環参照にならない、単一であいまいさのない参照である必要があります。</span><span class="sxs-lookup"><span data-stu-id="0e637-108">This must be a single, unambiguous reference that does not cause circular references among projects.</span></span>

 <span data-ttu-id="0e637-109">**エラー ID:** BC30971</span><span class="sxs-lookup"><span data-stu-id="0e637-109">**Error ID:** BC30971</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="0e637-110">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="0e637-110">To correct this error</span></span>

1. <span data-ttu-id="0e637-111">どのプロジェクトが、プロジェクトからの参照に最適なアセンブリを作成しているか特定します。</span><span class="sxs-lookup"><span data-stu-id="0e637-111">Determine which project produces the best assembly for your project to reference.</span></span> <span data-ttu-id="0e637-112">この判断には、ファイル アクセスの容易さや更新の頻度などの基準を使用できます。</span><span class="sxs-lookup"><span data-stu-id="0e637-112">For this decision, you might use criteria such as ease of file access and frequency of updates.</span></span>

2. <span data-ttu-id="0e637-113">プロジェクトのプロパティに、使用する型が定義されているアセンブリを含むプロジェクトへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="0e637-113">In your project properties, add a reference to the project that contains the assembly that defines the type you are using.</span></span>

## <a name="see-also"></a><span data-ttu-id="0e637-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="0e637-114">See also</span></span>

- [<span data-ttu-id="0e637-115">プロジェクト内の参照の管理</span><span class="sxs-lookup"><span data-stu-id="0e637-115">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="0e637-116">宣言された要素の参照</span><span class="sxs-lookup"><span data-stu-id="0e637-116">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [<span data-ttu-id="0e637-117">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="0e637-117">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="0e637-118">壊れた参照のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="0e637-118">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
