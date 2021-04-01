---
description: '詳細情報: ローカリゼーション'
title: ローカリゼーション
ms.date: 03/30/2017
helpviewer_keywords:
- culture, localization
- application development [.NET], localization
- globalization [.NET], localization
- code blocks
- international applications [.NET], localization
- global applications, localization
- world-ready applications, localization
- user interface blocks
- localization [.NET], about localization
- localizing resources
ms.assetid: 49d520d7-92d7-44ee-bb24-8b615db1d41b
ms.openlocfilehash: 0f84e406e35eb75cacf6daac32bbe26b4750738b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675794"
---
# <a name="localization"></a><span data-ttu-id="daf41-103">ローカリゼーション</span><span class="sxs-lookup"><span data-stu-id="daf41-103">Localization</span></span>

<span data-ttu-id="daf41-104">ローカリゼーションはアプリケーションのリソースを翻訳するプロセスであり、そのアプリケーションで対応するカルチャ別のバージョンが作られます。</span><span class="sxs-lookup"><span data-stu-id="daf41-104">Localization is the process of translating an application's resources into localized versions for each culture that the application will support.</span></span> <span data-ttu-id="daf41-105">[ローカライズ化の確認](localizability-review.md)手順で世界展開するアプリケーションがローカライズ可能であることを確認してから、ローカリゼーション手順に進んでください。</span><span class="sxs-lookup"><span data-stu-id="daf41-105">You should proceed to the localization step only after completing the [Localizability Review](localizability-review.md) step to verify that the globalized application is ready for localization.</span></span>

<span data-ttu-id="daf41-106">ローカライズ可能なアプリケーションは、概念的に 2 つのブロックに分けられます。すべてのユーザー インターフェイス要素を含むブロックと実行可能なコードを含むブロックです。</span><span class="sxs-lookup"><span data-stu-id="daf41-106">An application that is ready for localization is separated into two conceptual blocks: a block that contains all user interface elements and a block that contains executable code.</span></span> <span data-ttu-id="daf41-107">ユーザー インターフェイス ブロックには、ローカライズ可能なユーザー インターフェイス要素のみが含まれます。ニュートラル カルチャの場合、文字列、エラー メッセージ、ダイアログ ボックス、メニュー、埋め込みオブジェクト リソースなどです。</span><span class="sxs-lookup"><span data-stu-id="daf41-107">The user interface block contains only localizable user-interface elements such as strings, error messages, dialog boxes, menus, embedded object resources, and so on for the neutral culture.</span></span> <span data-ttu-id="daf41-108">コード ブロックには、すべての対応カルチャで使用されるアプリケーション コードのみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="daf41-108">The code block contains only the application code to be used by all supported cultures.</span></span> <span data-ttu-id="daf41-109">共通言語ランタイムは、アプリケーションの実行可能コードをそのリソースから分離させるサテライト アセンブリ リソース モデルに対応しています。</span><span class="sxs-lookup"><span data-stu-id="daf41-109">The common language runtime supports a satellite assembly resource model that separates an application's executable code from its resources.</span></span> <span data-ttu-id="daf41-110">このモデルの実装方法については、[.NET のリソース](../../framework/resources/index.md)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="daf41-110">For more information about implementing this model, see [Resources in .NET](../../framework/resources/index.md).</span></span>

<span data-ttu-id="daf41-111">アプリケーションのローカライズ バージョンごとに、ターゲット カルチャの言語に翻訳されたユーザー インターフェイス ブロックを含む新しいサテライト アセンブリを追加します。</span><span class="sxs-lookup"><span data-stu-id="daf41-111">For each localized version of your application, add a new satellite assembly that contains the localized user interface block translated into the appropriate language for the target culture.</span></span> <span data-ttu-id="daf41-112">すべてのカルチャのコード ブロックを同じにしてください。</span><span class="sxs-lookup"><span data-stu-id="daf41-112">The code block for all cultures should remain the same.</span></span> <span data-ttu-id="daf41-113">ユーザー インターフェイス ブロックのローカライズされたバージョンとコード ブロックを組み合わせることで、アプリケーションのローカライズ バージョンが作られます。</span><span class="sxs-lookup"><span data-stu-id="daf41-113">The combination of a localized version of the user interface block with the code block produces a localized version of your application.</span></span>

<span data-ttu-id="daf41-114">Windows ソフトウェア開発キット (SDK) には Windows フォーム リソース エディター (Winres.exe) があります。このエディターでは、ターゲット カルチャに合わせて Windows フォームを簡単にローカライズできます。</span><span class="sxs-lookup"><span data-stu-id="daf41-114">The Windows Software Development Kit (SDK) supplies the Windows Forms Resource Editor (Winres.exe) that allows you to quickly localize Windows Forms for target cultures.</span></span> <span data-ttu-id="daf41-115">このツールの使用方法については、「[Winres.exe (Windows フォーム リソース エディター)](../../framework/tools/winres-exe-windows-forms-resource-editor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="daf41-115">For information about using this tool, see [Winres.exe (Windows Forms Resource Editor)](../../framework/tools/winres-exe-windows-forms-resource-editor.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="daf41-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="daf41-116">See also</span></span>

- [<span data-ttu-id="daf41-117">グローバライズとローカライズ</span><span class="sxs-lookup"><span data-stu-id="daf41-117">Globalization and Localization</span></span>](index.md)
- [<span data-ttu-id="daf41-118">ローカライズ化の確認</span><span class="sxs-lookup"><span data-stu-id="daf41-118">Localizability Review</span></span>](localizability-review.md)
- [<span data-ttu-id="daf41-119">グローバリゼーション</span><span class="sxs-lookup"><span data-stu-id="daf41-119">Globalization</span></span>](globalization.md)
- [<span data-ttu-id="daf41-120">デスクトップ アプリケーションのリソース</span><span class="sxs-lookup"><span data-stu-id="daf41-120">Resources in Desktop Apps</span></span>](../../framework/resources/index.md)
