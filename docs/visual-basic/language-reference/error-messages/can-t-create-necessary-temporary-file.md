---
description: '詳細情報: 必要な一時ファイルを作成できません。'
title: 必要な一時ファイルを作成できません。
ms.date: 07/20/2015
f1_keywords:
- vbrID322
ms.assetid: 53617b5b-eb06-4188-b4c2-8607cb9fbc79
ms.openlocfilehash: 52d68b720d9f8797183cf773da45f02ceca0224d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796822"
---
# <a name="cant-create-necessary-temporary-file"></a><span data-ttu-id="8335b-103">必要な一時ファイルを作成できません。</span><span class="sxs-lookup"><span data-stu-id="8335b-103">Can't create necessary temporary file</span></span>

<span data-ttu-id="8335b-104">TEMP 環境変数によって指定されたディレクトリを含むドライブがいっぱいになっているか、TEMP 環境変数が無効または読み取り専用のドライブまたはディレクトリを指定しています。</span><span class="sxs-lookup"><span data-stu-id="8335b-104">Either the drive is full that contains the directory specified by the TEMP environment variable, or the TEMP environment variable specifies an invalid or read-only drive or directory.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8335b-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="8335b-105">To correct this error</span></span>  
  
1. <span data-ttu-id="8335b-106">いっぱいになっている場合は、ドライブからファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="8335b-106">Delete files from the drive, if full.</span></span>  
  
2. <span data-ttu-id="8335b-107">TEMP 環境変数に別のドライブを指定します。</span><span class="sxs-lookup"><span data-stu-id="8335b-107">Specify a different drive in the TEMP environment variable.</span></span>  
  
3. <span data-ttu-id="8335b-108">TEMP 環境変数に有効なドライブを指定します。</span><span class="sxs-lookup"><span data-stu-id="8335b-108">Specify a valid drive for the TEMP environment variable.</span></span>  
  
4. <span data-ttu-id="8335b-109">現在指定されているドライブまたはディレクトリから読み取り専用の制限を削除します。</span><span class="sxs-lookup"><span data-stu-id="8335b-109">Remove the read-only restriction from the currently specified drive or directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8335b-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="8335b-110">See also</span></span>

- [<span data-ttu-id="8335b-111">エラーの種類</span><span class="sxs-lookup"><span data-stu-id="8335b-111">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
