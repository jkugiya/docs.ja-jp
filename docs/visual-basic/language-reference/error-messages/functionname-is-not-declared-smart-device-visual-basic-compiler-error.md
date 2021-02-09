---
description: "詳細情報: BC30766: '<functionname>' は宣言されていません (スマート デバイスおよび Visual Basic コンパイラ エラー)"
title: "'<functionname>' は宣言されていません (スマート デバイスおよび Visual Basic コンパイラ エラー)"
ms.date: 07/20/2015
f1_keywords:
- bc30766
- vbc30766
helpviewer_keywords:
- BC30766
ms.assetid: 13918600-6087-40d7-8134-32aa9d3bfda4
ms.openlocfilehash: 939af146656bc5e5e84b3f0672c730f6a816c043
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796159"
---
# <a name="bc30766-functionname-is-not-declared-smart-devicevisual-basic-compiler-error"></a><span data-ttu-id="ec0cf-103">BC30766: '\<functionname>' は宣言されていません (スマート デバイスおよび Visual Basic コンパイラ エラー)</span><span class="sxs-lookup"><span data-stu-id="ec0cf-103">BC30766: '\<functionname>' is not declared (Smart Device/Visual Basic Compiler Error)</span></span>

<span data-ttu-id="ec0cf-104"><`functionname`> が宣言されていません。</span><span class="sxs-lookup"><span data-stu-id="ec0cf-104"><`functionname`> is not declared.</span></span> <span data-ttu-id="ec0cf-105">通常、ファイル I/O 機能は `Microsoft.VisualBasic` 名前空間で使用できますが、.NET Compact Framework のターゲット バージョンではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="ec0cf-105">File I/O functionality is normally available in the `Microsoft.VisualBasic` namespace, but the targeted version of the .NET Compact Framework does not support it.</span></span>

 <span data-ttu-id="ec0cf-106">**エラー ID:** BC30766</span><span class="sxs-lookup"><span data-stu-id="ec0cf-106">**Error ID:** BC30766</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="ec0cf-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="ec0cf-107">To correct this error</span></span>

- <span data-ttu-id="ec0cf-108">`System.IO` 名前空間で定義された関数を使用して、ファイル操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="ec0cf-108">Perform file operations with functions defined in the `System.IO` namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="ec0cf-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="ec0cf-109">See also</span></span>

- <xref:System.IO>
- [<span data-ttu-id="ec0cf-110">Visual Basic におけるファイル アクセス</span><span class="sxs-lookup"><span data-stu-id="ec0cf-110">File Access with Visual Basic</span></span>](../../developing-apps/programming/drives-directories-files/file-access.md)
