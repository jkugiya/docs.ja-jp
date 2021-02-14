---
description: "詳細情報: BC30712:クラス '<classname>' の情報を読み込めません"
title: クラス '<classname>' の情報を読み込めません。
ms.date: 07/20/2015
f1_keywords:
- vbc30712
- bc30712
helpviewer_keywords:
- BC30712
ms.assetid: c7ffbd6d-05c6-4261-b44b-1bcd521bb350
ms.openlocfilehash: 5e96df57b83b32b70a2d0d6eca1578b5d15ec065
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99674832"
---
# <a name="bc30712-unable-to-load-information-for-class-classname"></a><span data-ttu-id="94bc1-103">BC30712:クラス '\<classname>' の情報を読み込めません。</span><span class="sxs-lookup"><span data-stu-id="94bc1-103">BC30712: Unable to load information for class '\<classname>'</span></span>

<span data-ttu-id="94bc1-104">使用可能ではないクラスが参照されました。</span><span class="sxs-lookup"><span data-stu-id="94bc1-104">A reference was made to a class that is not available.</span></span>

 <span data-ttu-id="94bc1-105">**エラー ID:** BC30712</span><span class="sxs-lookup"><span data-stu-id="94bc1-105">**Error ID:** BC30712</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="94bc1-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="94bc1-106">To correct this error</span></span>

1. <span data-ttu-id="94bc1-107">クラスが定義されていること、およびその名前を正しく入力したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="94bc1-107">Verify that the class is defined and that you spelled the name correctly.</span></span>

2. <span data-ttu-id="94bc1-108">モジュールで宣言されたいずれかのメンバーにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="94bc1-108">Try accessing one of the members declared in the module.</span></span> <span data-ttu-id="94bc1-109">宣言されているモジュールがまだ読み込まれていないために、デバッグ環境ではメンバーを特定できないという場合もあります。</span><span class="sxs-lookup"><span data-stu-id="94bc1-109">In some cases, the debugging environment cannot locate members because the modules where they are declared have not been loaded yet.</span></span>

## <a name="see-also"></a><span data-ttu-id="94bc1-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="94bc1-110">See also</span></span>

- [<span data-ttu-id="94bc1-111">Visual Studio でのデバッグ</span><span class="sxs-lookup"><span data-stu-id="94bc1-111">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugger-feature-tour)
