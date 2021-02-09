---
description: "詳細情報: BC30961:型 '<typename1>' の値を '<typename2>' に変換することはできません。(複数ファイル参照)"
title: 型 '<typename1>' の値を '<typename2>' に変換することはできません。(複数ファイル参照)
ms.date: 07/20/2015
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
ms.openlocfilehash: 77f8f3c500f9f395d3998261a218175e49f0f52b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640863"
---
# <a name="bc30961-value-of-type-typename1-cannot-be-converted-to-typename2-multiple-file-references"></a><span data-ttu-id="cc5c8-103">BC30961:型 '\<typename1>' の値を '\<typename2>' に変換することはできません。(複数ファイル参照)</span><span class="sxs-lookup"><span data-stu-id="cc5c8-103">BC30961: Value of type '\<typename1>' cannot be converted to '\<typename2>' (Multiple file references)</span></span>

<span data-ttu-id="cc5c8-104">型 '\<typename1>' の値を '\<typename2>' に変換できません。</span><span class="sxs-lookup"><span data-stu-id="cc5c8-104">Value of type '\<typename1>' cannot be converted to '\<typename2>'.</span></span> <span data-ttu-id="cc5c8-105">型の不一致の原因として、プロジェクト '\<projectname1>' の '\<filepath1>' へのファイル参照と、プロジェクト '\<projectname2>' の '\<filepath2>' へのファイル参照が混在していることが考えられます。</span><span class="sxs-lookup"><span data-stu-id="cc5c8-105">Type mismatch could be due to mixing a file reference to '\<filepath1>' in project '\<projectname1>' with a file reference to '\<filepath2>' in project '\<projectname2>'.</span></span> <span data-ttu-id="cc5c8-106">両方のアセンブリが同一である場合は、これらの参照を同じ場所から参照するように置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="cc5c8-106">If both assemblies are identical, try replacing these references so both references are from the same location.</span></span>

 <span data-ttu-id="cc5c8-107">プロジェクトが 1 つのアセンブリに対して複数のファイル参照を作成する場合、コンパイラは、1 つの型を別の型に変換できることを保証できません。</span><span class="sxs-lookup"><span data-stu-id="cc5c8-107">In a situation where a project makes more than one file reference to an assembly, the compiler cannot guarantee that one type can be converted to another.</span></span>

 <span data-ttu-id="cc5c8-108">各ファイル参照は、プロジェクトの出力ファイルのファイル パスと名前を指定します (通常は DLL ファイル)。</span><span class="sxs-lookup"><span data-stu-id="cc5c8-108">Each file reference specifies a file path and name for the output file of a project (typically a DLL file).</span></span> <span data-ttu-id="cc5c8-109">コンパイラは、出力ファイルが同じソースからのものであること、または同じアセンブリの同じバージョンを表していることを保証できません。</span><span class="sxs-lookup"><span data-stu-id="cc5c8-109">The compiler cannot guarantee that the output files come from the same source, or that they represent the same version of the same assembly.</span></span> <span data-ttu-id="cc5c8-110">そのため、異なる参照内の型が同じ型であるか、またはある型を他の型に変換できるかを保証できません。</span><span class="sxs-lookup"><span data-stu-id="cc5c8-110">Therefore, it cannot guarantee that the types in the different references are the same type, or even that one can be converted to the other.</span></span>

 <span data-ttu-id="cc5c8-111">参照されるアセンブリのアセンブリ ID が同じであることがわかっている場合は、1 つのファイル参照を使用できます。</span><span class="sxs-lookup"><span data-stu-id="cc5c8-111">You can use a single file reference if you know that the referenced assemblies have the same assembly identity.</span></span> <span data-ttu-id="cc5c8-112">*アセンブリ ID* には、アセンブリの名前、バージョン、公開キー (存在する場合)、およびカルチャが含まれます。</span><span class="sxs-lookup"><span data-stu-id="cc5c8-112">The *assembly identity* includes the assembly's name, version, public key if any, and culture.</span></span> <span data-ttu-id="cc5c8-113">この情報はアセンブリを一意に識別します。</span><span class="sxs-lookup"><span data-stu-id="cc5c8-113">This information uniquely identifies the assembly.</span></span>

 <span data-ttu-id="cc5c8-114">**エラー ID:** BC30961</span><span class="sxs-lookup"><span data-stu-id="cc5c8-114">**Error ID:** BC30961</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="cc5c8-115">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="cc5c8-115">To correct this error</span></span>

- <span data-ttu-id="cc5c8-116">参照アセンブリのアセンブリ ID が同じである場合は、ファイル参照の 1 つを削除するか置き換えて、ファイル参照が 1 つだけになるようにします。</span><span class="sxs-lookup"><span data-stu-id="cc5c8-116">If the referenced assemblies have the same assembly identity, then remove or replace one of the file references so that there is only a single file reference.</span></span>

- <span data-ttu-id="cc5c8-117">参照アセンブリのアセンブリ ID が同じでない場合は、コードを変更して、一方の型のもう一方の型への変換を試みないようにします。</span><span class="sxs-lookup"><span data-stu-id="cc5c8-117">If the referenced assemblies do not have the same assembly identity, then change your code so that it does not attempt to convert a type in one to a type in the other.</span></span>

## <a name="see-also"></a><span data-ttu-id="cc5c8-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="cc5c8-118">See also</span></span>

- [<span data-ttu-id="cc5c8-119">Visual Basic における型変換</span><span class="sxs-lookup"><span data-stu-id="cc5c8-119">Type Conversions in Visual Basic</span></span>](../../programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="cc5c8-120">プロジェクト内の参照の管理</span><span class="sxs-lookup"><span data-stu-id="cc5c8-120">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
