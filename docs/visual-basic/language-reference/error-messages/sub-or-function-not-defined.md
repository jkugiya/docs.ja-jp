---
description: '詳細情報: Sub または Function が定義されていません。(Visual Basic)'
title: Sub または Function が定義されていません。
ms.date: 07/20/2015
f1_keywords:
- vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
ms.openlocfilehash: 5726e8b23283b419577c468eee2344b234493425
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641383"
---
# <a name="sub-or-function-not-defined-visual-basic"></a><span data-ttu-id="1a00d-103">Sub または Function が定義されていません。(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1a00d-103">Sub or Function not defined (Visual Basic)</span></span>

<span data-ttu-id="1a00d-104">呼び出されるには、`Sub` または `Function` が定義されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a00d-104">A `Sub` or `Function` must be defined in order to be called.</span></span> <span data-ttu-id="1a00d-105">このエラーでは以下の原因が考えられます。</span><span class="sxs-lookup"><span data-stu-id="1a00d-105">Possible causes of this error include:</span></span>  
  
- <span data-ttu-id="1a00d-106">プロシージャ名のスペルが間違っています。</span><span class="sxs-lookup"><span data-stu-id="1a00d-106">Misspelling the procedure name.</span></span>  
  
- <span data-ttu-id="1a00d-107">**[参照]** ダイアログ ボックスで、プロジェクトへの参照を明示的に追加せずに、別のプロジェクトからプロシージャを呼び出そうとしています。</span><span class="sxs-lookup"><span data-stu-id="1a00d-107">Trying to call a procedure from another project without explicitly adding a reference to that project in the **References** dialog box.</span></span>  
  
- <span data-ttu-id="1a00d-108">呼び出し元のプロシージャから参照できないプロシージャを指定しています。</span><span class="sxs-lookup"><span data-stu-id="1a00d-108">Specifying a procedure that is not visible to the calling procedure.</span></span>  
  
- <span data-ttu-id="1a00d-109">指定したライブラリまたはコード リソースにない Windows ダイナミックリンク ライブラリ (DLL) ルーチンまたは Macintosh コードリソース ルーチンを宣言しています。</span><span class="sxs-lookup"><span data-stu-id="1a00d-109">Declaring a Windows dynamic-link library (DLL) routine or Macintosh code-resource routine that is not in the specified library or code resource.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1a00d-110">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="1a00d-110">To correct this error</span></span>  
  
1. <span data-ttu-id="1a00d-111">プロシージャ名のスペルが正しいことを確認します。</span><span class="sxs-lookup"><span data-stu-id="1a00d-111">Make sure that the procedure name is spelled correctly.</span></span>  
  
2. <span data-ttu-id="1a00d-112">**[参照]** ダイアログボックスで、呼び出すプロシージャを含むプロジェクトの名前を見つけます。</span><span class="sxs-lookup"><span data-stu-id="1a00d-112">Find the name of the project containing the procedure you want to call in the **References** dialog box.</span></span> <span data-ttu-id="1a00d-113">それが表示されない場合、 **[参照]** ボタンをクリックして検索します。</span><span class="sxs-lookup"><span data-stu-id="1a00d-113">If it does not appear, click the **Browse** button to search for it.</span></span> <span data-ttu-id="1a00d-114">プロジェクト名の左側にあるチェック ボックスをオンにして、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1a00d-114">Select the check box to the left of the project name, and then click **OK**.</span></span>  
  
3. <span data-ttu-id="1a00d-115">ルーチンの名前を確認します。</span><span class="sxs-lookup"><span data-stu-id="1a00d-115">Check the name of the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a00d-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="1a00d-116">See also</span></span>

- [<span data-ttu-id="1a00d-117">エラーの種類</span><span class="sxs-lookup"><span data-stu-id="1a00d-117">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="1a00d-118">プロジェクト内の参照の管理</span><span class="sxs-lookup"><span data-stu-id="1a00d-118">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="1a00d-119">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="1a00d-119">Sub Statement</span></span>](../statements/sub-statement.md)
- [<span data-ttu-id="1a00d-120">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="1a00d-120">Function Statement</span></span>](../statements/function-statement.md)
