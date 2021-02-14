---
description: "詳細情報: BC30007:基底クラス '<classname>' を含むアセンブリ '<assemblyname>' への参照が必要です"
title: 基本クラス '<assemblyname>' を含むアセンブリ '<classname>' への参照が必要です。参照をプロジェクトに追加してください。
ms.date: 07/20/2015
f1_keywords:
- bc30007
- vbc30007
helpviewer_keywords:
- BC30007
ms.assetid: 5f34cf47-6c6e-4954-bd8e-d6b020b75fb7
ms.openlocfilehash: f01795d3e8147015f9f46697b047a8c63099ff32
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792051"
---
# <a name="bc30007-reference-required-to-assembly-assemblyname-containing-the-base-class-classname"></a><span data-ttu-id="96221-103">BC30007:基本クラス '\<assemblyname>' を含むアセンブリ '\<classname>' への参照が必要です。参照をプロジェクトに追加してください。</span><span class="sxs-lookup"><span data-stu-id="96221-103">BC30007: Reference required to assembly '\<assemblyname>' containing the base class '\<classname>'</span></span>

<span data-ttu-id="96221-104">基底クラス '\<classname>' を含むアセンブリ '\<assemblyname>' への参照が必要です。</span><span class="sxs-lookup"><span data-stu-id="96221-104">Reference required to assembly '\<assemblyname>' containing the base class '\<classname>'.</span></span> <span data-ttu-id="96221-105">プロジェクトに参照を追加してください。</span><span class="sxs-lookup"><span data-stu-id="96221-105">Add one to your project.</span></span>

 <span data-ttu-id="96221-106">プロジェクト内で直接参照されないダイナミック リンク ライブラリ (DLL) またはアセンブリでクラスが定義されています。</span><span class="sxs-lookup"><span data-stu-id="96221-106">The class is defined in a dynamic-link library (DLL) or assembly that is not directly referenced in your project.</span></span> <span data-ttu-id="96221-107">Visual Basic コンパイラでは、クラスが複数の DLL またはアセンブリで定義されている場合に備えて、あいまいさを避けるための参照が必要になります。</span><span class="sxs-lookup"><span data-stu-id="96221-107">The Visual Basic compiler requires a reference to avoid ambiguity in case the class is defined in more than one DLL or assembly.</span></span>

 <span data-ttu-id="96221-108">**エラー ID:** BC30007</span><span class="sxs-lookup"><span data-stu-id="96221-108">**Error ID:** BC30007</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="96221-109">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="96221-109">To correct this error</span></span>

- <span data-ttu-id="96221-110">参照されない DLL またはアセンブリの名前をプロジェクト参照に含めます。</span><span class="sxs-lookup"><span data-stu-id="96221-110">Include the name of the unreferenced DLL or assembly in your project references.</span></span>

## <a name="see-also"></a><span data-ttu-id="96221-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="96221-111">See also</span></span>

- [<span data-ttu-id="96221-112">プロジェクト内の参照の管理</span><span class="sxs-lookup"><span data-stu-id="96221-112">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="96221-113">壊れた参照のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="96221-113">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
