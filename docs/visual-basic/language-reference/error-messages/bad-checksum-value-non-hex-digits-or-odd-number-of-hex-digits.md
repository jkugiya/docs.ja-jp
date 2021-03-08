---
description: '詳細情報: BC42033:不適切なチェックサム値です。16 進数ではないか、または奇数の 16 進数です。'
title: 不適切なチェックサム値です。16 進数ではないか、または奇数の 16 進数です。
ms.date: 07/20/2015
f1_keywords:
- bc42033
- vbc42033
helpviewer_keywords:
- BC42033
ms.assetid: 4575554d-3615-46e4-9c6a-18e9c338e4ed
ms.openlocfilehash: 051ee0e8ec8b87be4d5feeac8298c0e7a71baea7
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102103882"
---
# <a name="bc42033-bad-checksum-value-non-hex-digits-or-odd-number-of-hex-digits"></a><span data-ttu-id="0152b-103">BC42033:不適切なチェックサム値です。16 進数ではないか、または奇数の 16 進数です。</span><span class="sxs-lookup"><span data-stu-id="0152b-103">BC42033: Bad checksum value, non hex digits or odd number of hex digits</span></span>

<span data-ttu-id="0152b-104">チェックサムの値に無効な 16 進数が含まれるか、桁数が奇数です。</span><span class="sxs-lookup"><span data-stu-id="0152b-104">A checksum value contains invalid hexadecimal digits or has an odd number of digits.</span></span>

 <span data-ttu-id="0152b-105">ASP.NET は Visual Basic のソース ファイル (拡張子 .vb) を生成するとき、チェックサムを計算して `#externalchecksum` で指定された隠しソース ファイルに格納します。</span><span class="sxs-lookup"><span data-stu-id="0152b-105">When ASP.NET generates a Visual Basic source file (extension .vb), it calculates a checksum and places it in a hidden source file identified by `#externalchecksum`.</span></span> <span data-ttu-id="0152b-106">ユーザーが同じ目的で .vb ファイルを生成することもできますが、このプロセスは内部使用のままにしておくことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="0152b-106">It is possible for a user generating a .vb file to do this also, but this process is best left to internal use.</span></span>

 <span data-ttu-id="0152b-107">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="0152b-107">By default, this message is a warning.</span></span> <span data-ttu-id="0152b-108">警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0152b-108">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="0152b-109">**エラー ID:** BC42033</span><span class="sxs-lookup"><span data-stu-id="0152b-109">**Error ID:** BC42033</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="0152b-110">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="0152b-110">To correct this error</span></span>

1. <span data-ttu-id="0152b-111">ASP.NET が Visual Basic ソース ファイルを生成している場合は、プロジェクト ビルドを再起動してください。</span><span class="sxs-lookup"><span data-stu-id="0152b-111">If ASP.NET is generating the Visual Basic source file, restart the project build.</span></span>

2. <span data-ttu-id="0152b-112">再起動してもこの警告が続く場合は、ASP.NET をインストールし直してもう一度ビルドしてください。</span><span class="sxs-lookup"><span data-stu-id="0152b-112">If this warning persists after restarting, reinstall ASP.NET and try the build again.</span></span>

3. <span data-ttu-id="0152b-113">それでも警告が続くか、ASP.NET を使用していない場合は、状況に関する情報を収集し、マイクロソフト プロダクト サポート サービスに通知してください。</span><span class="sxs-lookup"><span data-stu-id="0152b-113">If the warning still persists, or if you are not using ASP.NET, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="0152b-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="0152b-114">See also</span></span>

- [<span data-ttu-id="0152b-115">ASP.NET の概要</span><span class="sxs-lookup"><span data-stu-id="0152b-115">ASP.NET Overview</span></span>](/aspnet/overview)
- [<span data-ttu-id="0152b-116">Visual Studio フィードバック オプション</span><span class="sxs-lookup"><span data-stu-id="0152b-116">Visual Studio feedback options</span></span>](/visualstudio/ide/feedback-options)
