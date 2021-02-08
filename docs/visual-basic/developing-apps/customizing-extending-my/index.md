---
description: '詳細情報: Visual Basic でのプロジェクトのカスタマイズと My の拡張'
title: プロジェクトのカスタマイズと My の拡張
ms.date: 07/20/2015
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: 06ca80b9-1192-4eb5-8537-8ef5edfb9be0
ms.openlocfilehash: 69a8bdff78fcfda03ab03ef89b7407fb230c17bf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775462"
---
# <a name="customizing-projects-and-extending-my-with-visual-basic"></a><span data-ttu-id="cd5d5-103">Visual Basic でのプロジェクトのカスタマイズと My の拡張</span><span class="sxs-lookup"><span data-stu-id="cd5d5-103">Customizing Projects and Extending My with Visual Basic</span></span>

<span data-ttu-id="cd5d5-104">プロジェクト テンプレートをカスタマイズして追加の `My` オブジェクトを提供することができます。</span><span class="sxs-lookup"><span data-stu-id="cd5d5-104">You can customize project templates to provide additional `My` objects.</span></span> <span data-ttu-id="cd5d5-105">これにより、お客様のオブジェクトを他の開発者が簡単に見つけて使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="cd5d5-105">This makes it easy for other developers to find and use your objects.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="cd5d5-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="cd5d5-106">In this section</span></span>

- [<span data-ttu-id="cd5d5-107">Visual Basic における My 名前空間の拡張</span><span class="sxs-lookup"><span data-stu-id="cd5d5-107">Extending the My Namespace in Visual Basic</span></span>](extending-the-my-namespace.md)  
 <span data-ttu-id="cd5d5-108">Visual Basic の `My` 名前空間にカスタム メンバーと値を追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cd5d5-108">Describes how to add custom members and values to the `My` namespace in Visual Basic.</span></span>
- [<span data-ttu-id="cd5d5-109">カスタム My 拡張のパッケージ化と配置</span><span class="sxs-lookup"><span data-stu-id="cd5d5-109">Packaging and Deploying Custom My Extensions</span></span>](packaging-and-deploying-custom-my-extensions.md)  
 <span data-ttu-id="cd5d5-110">Visual Studio テンプレートを使用して、カスタム `My` 名前空間拡張を発行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cd5d5-110">Describes how to publish custom `My` namespace extensions by using Visual Studio templates.</span></span>
- [<span data-ttu-id="cd5d5-111">Visual Basic アプリケーション モデルの拡張</span><span class="sxs-lookup"><span data-stu-id="cd5d5-111">Extending the Visual Basic Application Model</span></span>](extending-the-visual-basic-application-model.md)  
 <span data-ttu-id="cd5d5-112"><xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> クラスのメンバーをオーバーライドして、アプリケーション モデルに独自の拡張を指定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cd5d5-112">Describes how to specify your own extensions to the application model by overriding members of the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> class.</span></span>
- [<span data-ttu-id="cd5d5-113">My で利用可能なオブジェクトのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="cd5d5-113">Customizing Which Objects are Available in My</span></span>](customizing-which-objects-are-available-in-my.md)  
 <span data-ttu-id="cd5d5-114">プロジェクトの \_ 条件付きコンパイル定数を設定して、どの `My` オブジェクトを有効にするかを制御する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cd5d5-114">Describes how to control which `My` objects are enabled by setting your project's \_MYTYPE conditional-compilation constant.</span></span>

## <a name="related-sections"></a><span data-ttu-id="cd5d5-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="cd5d5-115">Related sections</span></span>

- [<span data-ttu-id="cd5d5-116">My による開発</span><span class="sxs-lookup"><span data-stu-id="cd5d5-116">Development with My</span></span>](../development-with-my/index.md)  
 <span data-ttu-id="cd5d5-117">既定で、さまざまなプロジェクト タイプで使用できる `My` オブジェクトについて説明します。</span><span class="sxs-lookup"><span data-stu-id="cd5d5-117">Describes which `My` objects are available in different project types by default.</span></span>
- [<span data-ttu-id="cd5d5-118">Visual Basic アプリケーション モデルの概要</span><span class="sxs-lookup"><span data-stu-id="cd5d5-118">Overview of the Visual Basic Application Model</span></span>](../development-with-my/overview-of-the-visual-basic-application-model.md)  
 <span data-ttu-id="cd5d5-119">Windows フォーム アプリケーションの動作を制御するための Visual Basic のモデルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="cd5d5-119">Describes Visual Basic's model for controlling the behavior of Windows Forms applications.</span></span>
- [<span data-ttu-id="cd5d5-120">プロジェクトの種類に応じた My の機能</span><span class="sxs-lookup"><span data-stu-id="cd5d5-120">How My Depends on Project Type</span></span>](../development-with-my/how-my-depends-on-project-type.md)  
 <span data-ttu-id="cd5d5-121">既定で、さまざまなプロジェクト タイプで使用できる `My` オブジェクトについて説明します。</span><span class="sxs-lookup"><span data-stu-id="cd5d5-121">Describes which `My` objects are available in different project types by default.</span></span>
- [<span data-ttu-id="cd5d5-122">条件付きコンパイル</span><span class="sxs-lookup"><span data-stu-id="cd5d5-122">Conditional Compilation</span></span>](../../programming-guide/program-structure/conditional-compilation.md)  
 <span data-ttu-id="cd5d5-123">コンパイラで条件付きコンパイルを使用して、コンパイルするコードの特定のセクションを選択し、他のセクションを除外する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cd5d5-123">Discusses how the compiler uses conditional-compilation to select particular sections of code to compile and exclude other sections.</span></span>
- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>  
 <span data-ttu-id="cd5d5-124">現在のアプリケーションに関連するプロパティ、メソッド、およびイベントを提供する `My` オブジェクトについて説明します。</span><span class="sxs-lookup"><span data-stu-id="cd5d5-124">Describes the `My` object that provides properties, methods, and events related to the current application.</span></span>

## <a name="see-also"></a><span data-ttu-id="cd5d5-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="cd5d5-125">See also</span></span>

- [<span data-ttu-id="cd5d5-126">Visual Basic でのアプリケーションの開発</span><span class="sxs-lookup"><span data-stu-id="cd5d5-126">Developing Applications with Visual Basic</span></span>](../index.md)
