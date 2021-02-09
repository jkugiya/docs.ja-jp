---
description: '詳細情報: ファイルが多すぎます。'
title: ファイルが多すぎます。
ms.date: 07/20/2015
f1_keywords:
- vbrID67
ms.assetid: 2ff203e2-bba6-43ae-b72f-8e92a881c98f
ms.openlocfilehash: 85d246c49f765cf618bf889d75dcc9c10b780280
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641227"
---
# <a name="too-many-files"></a><span data-ttu-id="f114e-103">ファイルが多すぎます。</span><span class="sxs-lookup"><span data-stu-id="f114e-103">Too many files</span></span>

<span data-ttu-id="f114e-104">オペレーティング システムで許可されているよりも多くのファイルがルート ディレクトリに作成されているか、CONFIG.SYS ファイルの **[files=]** 設定で指定された数よりも多くのファイルが開かれています。</span><span class="sxs-lookup"><span data-stu-id="f114e-104">Either more files have been created in the root directory than the operating system permits, or more files have been opened than the number specified in the **files=** setting in your CONFIG.SYS file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f114e-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="f114e-105">To correct this error</span></span>  
  
1. <span data-ttu-id="f114e-106">プログラムがルート ディレクトリ内のファイルを開いたり、閉じたり、または保存したりしている場合は、サブディレクトリを使用するようにプログラムを変更します。</span><span class="sxs-lookup"><span data-stu-id="f114e-106">If your program is opening, closing, or saving files in the root directory, change your program so that it uses a subdirectory.</span></span>  
  
2. <span data-ttu-id="f114e-107">CONFIG.SYS ファイルの **[files=]** 設定で指定されているファイルの数を増やして、コンピューターを再起動します。</span><span class="sxs-lookup"><span data-stu-id="f114e-107">Increase the number of files specified in your **files=** setting in your CONFIG.SYS file, and restart your computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f114e-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="f114e-108">See also</span></span>

- [<span data-ttu-id="f114e-109">エラーの種類</span><span class="sxs-lookup"><span data-stu-id="f114e-109">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
