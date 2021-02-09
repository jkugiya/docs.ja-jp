---
description: '詳細情報: ファイル エンコーディング (Visual Basic)'
title: ファイル エンコーディング
ms.date: 07/20/2015
helpviewer_keywords:
- character encodings
- files [Visual Basic], encoding
- Unicode, file encoding
- file encoding
ms.assetid: ea2c5f5f-bbb1-4150-9928-b9951fa6bc57
ms.openlocfilehash: f573b5d8f83c27cbf4ddacb9fd40474d7d1be1ae
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675365"
---
# <a name="file-encodings-visual-basic"></a><span data-ttu-id="4b556-103">ファイル エンコーディング (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4b556-103">File Encodings (Visual Basic)</span></span>

<span data-ttu-id="4b556-104">ファイル エンコーディングは、文字エンコーディングとも呼ばれ、テキストを処理するときの文字の表現方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="4b556-104">File encodings, also known as character encodings, specify how to represent characters when text processing.</span></span> <span data-ttu-id="4b556-105">言語で処理できる (または処理できない) 文字という観点から、あるエンコードが他のエンコーディングよりも望ましいということがありますが、一般的には Unicode が好まれます。</span><span class="sxs-lookup"><span data-stu-id="4b556-105">One encoding may be preferable over another in terms of which language characters it can or cannot handle, although Unicode is usually preferred.</span></span>

<span data-ttu-id="4b556-106">ファイルに対する読み取りと書き込みでは、ファイル エンコーディングが適切に一致しないと、例外が発生したり、不正な結果となる場合があります。</span><span class="sxs-lookup"><span data-stu-id="4b556-106">When reading from or writing to files, improperly matching file encodings may result in exceptions or incorrect results.</span></span>

## <a name="types-of-encodings"></a><span data-ttu-id="4b556-107">エンコーディングの種類</span><span class="sxs-lookup"><span data-stu-id="4b556-107">Types of Encodings</span></span>

<span data-ttu-id="4b556-108">ファイルを扱うときには、Unicode は最適なエンコーディングです。</span><span class="sxs-lookup"><span data-stu-id="4b556-108">Unicode is the preferred encoding when working with files.</span></span> <span data-ttu-id="4b556-109">Unicode は、世界共通の文字エンコーディング規則で、技術的な記号や出版で使用される特殊文字などを含む、現在のコンピューティングで使用されるすべての文字を、16 ビットのコード値で表します。</span><span class="sxs-lookup"><span data-stu-id="4b556-109">Unicode is a worldwide character-encoding standard that uses 16-bit code values to represent all the characters used in modern computing, including technical symbols and special characters used in publishing.</span></span>

<span data-ttu-id="4b556-110">これまでの文字エンコーディング規則は、Windows ANSI 文字セットなどの従来からある文字セットで構成されており、8 ビットのコード値や 8 ビット値の組み合わせを使用して、特定の言語や地域で使用する文字を表していました。</span><span class="sxs-lookup"><span data-stu-id="4b556-110">Previous character-encoding standards consisted of traditional character sets, such as the Windows ANSI character set that uses 8-bit code values, or combinations of 8-bit values, to represent the characters used in a specific language or geographical region.</span></span>

## <a name="encoding-class"></a><span data-ttu-id="4b556-111">Encoding クラス</span><span class="sxs-lookup"><span data-stu-id="4b556-111">Encoding Class</span></span>

<span data-ttu-id="4b556-112"><xref:System.Text.Encoding> クラスは文字エンコーディングを表します。</span><span class="sxs-lookup"><span data-stu-id="4b556-112">The <xref:System.Text.Encoding> class represents a character encoding.</span></span> <span data-ttu-id="4b556-113">次の表は、利用可能なエンコーディングの型の一覧とそれぞれの説明です。</span><span class="sxs-lookup"><span data-stu-id="4b556-113">This table lists the type of encodings available and describes each.</span></span>

|<span data-ttu-id="4b556-114">名前</span><span class="sxs-lookup"><span data-stu-id="4b556-114">Name</span></span>|<span data-ttu-id="4b556-115">Description</span><span class="sxs-lookup"><span data-stu-id="4b556-115">Description</span></span>|
|---|---|
|<xref:System.Text.ASCIIEncoding>|<span data-ttu-id="4b556-116">Unicode 文字の ASCII 文字エンコードを表します。</span><span class="sxs-lookup"><span data-stu-id="4b556-116">Represents an ASCII character encoding of Unicode characters.</span></span>|
|<xref:System.Text.UnicodeEncoding>|<span data-ttu-id="4b556-117">Unicode 文字の UTF-16 エンコーディングを表します。</span><span class="sxs-lookup"><span data-stu-id="4b556-117">Represents a UTF-16 encoding of Unicode characters.</span></span>|
|<xref:System.Text.UTF32Encoding>|<span data-ttu-id="4b556-118">Unicode 文字の UTF-32 エンコーディングを表します。</span><span class="sxs-lookup"><span data-stu-id="4b556-118">Represents a UTF-32 encoding of Unicode characters.</span></span>|
|<xref:System.Text.UTF7Encoding>|<span data-ttu-id="4b556-119">Unicode 文字の UTF-7 エンコードを表します。</span><span class="sxs-lookup"><span data-stu-id="4b556-119">Represents a UTF-7 encoding of Unicode characters.</span></span>|
|<xref:System.Text.UTF8Encoding>|<span data-ttu-id="4b556-120">Unicode 文字の UTF-8 エンコードを表します。</span><span class="sxs-lookup"><span data-stu-id="4b556-120">Represents a UTF-8 encoding of Unicode characters.</span></span>|

## <a name="see-also"></a><span data-ttu-id="4b556-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="4b556-121">See also</span></span>

- [<span data-ttu-id="4b556-122">ファイルの読み取り</span><span class="sxs-lookup"><span data-stu-id="4b556-122">Reading from Files</span></span>](reading-from-files.md)
- [<span data-ttu-id="4b556-123">ファイルへの書き込み</span><span class="sxs-lookup"><span data-stu-id="4b556-123">Writing to Files</span></span>](writing-to-files.md)
