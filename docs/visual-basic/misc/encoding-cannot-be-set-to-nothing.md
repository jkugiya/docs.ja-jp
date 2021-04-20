---
description: '詳細情報: エンコードは Nothing に設定できません'
title: エンコードは Nothing に設定できません
ms.date: 07/20/2015
ms.assetid: 59f7c731-8291-4a85-bf51-c225e48cdc84
ms.openlocfilehash: 4fa9cbd9488501b5295da8d8ace41ef06a706c12
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100462996"
---
# <a name="encoding-cannot-be-set-to-nothing"></a><span data-ttu-id="72cd4-103">エンコードは Nothing に設定できません</span><span class="sxs-lookup"><span data-stu-id="72cd4-103">Encoding cannot be set to Nothing</span></span>

<span data-ttu-id="72cd4-104">パラメーター `encoding` が `Nothing` に設定されていますが、正しい値が必要なため、ファイルへの読み取りまたは書き込みに失敗しました。</span><span class="sxs-lookup"><span data-stu-id="72cd4-104">An attempt to read from or write to a file has failed because the parameter `encoding` has been set to `Nothing` but requires a valid value.</span></span>  
  
 <span data-ttu-id="72cd4-105"><xref:System.Text.Encoding> は、ファイルへの書き込み時に使用するエンコードを判別するのに使用されます。</span><span class="sxs-lookup"><span data-stu-id="72cd4-105"><xref:System.Text.Encoding> is used to determine what encoding to use when writing to a file.</span></span> <span data-ttu-id="72cd4-106">既定は UTF-8 です。</span><span class="sxs-lookup"><span data-stu-id="72cd4-106">The default is UTF-8.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="72cd4-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="72cd4-107">To correct this error</span></span>  
  
- <span data-ttu-id="72cd4-108">正しい値を `encoding` パラメーターに指定します。</span><span class="sxs-lookup"><span data-stu-id="72cd4-108">Supply a valid value for the `encoding` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72cd4-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="72cd4-109">See also</span></span>

- [<span data-ttu-id="72cd4-110">ファイル エンコーディング</span><span class="sxs-lookup"><span data-stu-id="72cd4-110">File Encodings</span></span>](../developing-apps/programming/drives-directories-files/file-encodings.md)
- [<span data-ttu-id="72cd4-111">ファイルの読み取り</span><span class="sxs-lookup"><span data-stu-id="72cd4-111">Reading from Files</span></span>](../developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="72cd4-112">ファイルへの書き込み</span><span class="sxs-lookup"><span data-stu-id="72cd4-112">Writing to Files</span></span>](../developing-apps/programming/drives-directories-files/writing-to-files.md)
- [<span data-ttu-id="72cd4-113">My.Computer.FileSystem.ReadAllText</span><span class="sxs-lookup"><span data-stu-id="72cd4-113">My.Computer.FileSystem.ReadAllText</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A)
- [<span data-ttu-id="72cd4-114">My.Computer.FileSystem.WriteAllText</span><span class="sxs-lookup"><span data-stu-id="72cd4-114">My.Computer.FileSystem.WriteAllText</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A)
