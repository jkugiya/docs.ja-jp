---
description: '詳細情報: Mailbnfsd ヘルパークラス'
title: MailbSystem.Net Helper クラス ()
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Mime.MailBnfHelper
- System.Net.Mime.MailBnfHelper.Ascii7bitMaxValue
- System.Net.Mime.MailBnfHelper.Atext
- System.Net.Mime.MailBnfHelper.CR
- System.Net.Mime.MailBnfHelper.Ctext
- System.Net.Mime.MailBnfHelper.Dot
- System.Net.Mime.MailBnfHelper.EndComment
- System.Net.Mime.MailBnfHelper.LF
- System.Net.Mime.MailBnfHelper.Space
- System.Net.Mime.MailBnfHelper.StartComment
- System.Net.Mime.MailBnfHelper.Tab
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 942b5c423d2f63985a8f7840f69d956bbade7582
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699650"
---
# <a name="mailbnfhelper-class"></a><span data-ttu-id="8ad69-103">MailBnfHelper クラス</span><span class="sxs-lookup"><span data-stu-id="8ad69-103">MailBnfHelper class</span></span>

<span data-ttu-id="8ad69-104">インターネットメッセージ形式の文字列を解析するためのユーティリティメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="8ad69-104">Contains utility methods for parsing internet message-formatted strings.</span></span> <span data-ttu-id="8ad69-105">このクラスは継承できません。</span><span class="sxs-lookup"><span data-stu-id="8ad69-105">This class cannot be inherited.</span></span>

```csharp
internal static class MailBnfHelper
```

> [!WARNING]
> <span data-ttu-id="8ad69-106">このクラスは内部的なものであり、コードで直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="8ad69-106">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="8ad69-107">Microsoft では、どのような状況でも、実稼働アプリケーションでのこのクラスの使用はサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="8ad69-107">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="ascii7bitmaxvalue-field"></a><span data-ttu-id="8ad69-108">Ascii7bitMaxValue フィールド</span><span class="sxs-lookup"><span data-stu-id="8ad69-108">Ascii7bitMaxValue field</span></span>

<span data-ttu-id="8ad69-109">7ビット Ascii 値の最大値を表します。</span><span class="sxs-lookup"><span data-stu-id="8ad69-109">Represents the maximum 7-bit Ascii value.</span></span>

```csharp
internal static readonly int Ascii7bitMaxValue
```

## <a name="atext-field"></a><span data-ttu-id="8ad69-110">フィールドの入力</span><span class="sxs-lookup"><span data-stu-id="8ad69-110">Atext field</span></span>

<span data-ttu-id="8ad69-111">アトムで使用できる文字を表します。</span><span class="sxs-lookup"><span data-stu-id="8ad69-111">Represents the characters allowed in atoms.</span></span>

```csharp
internal static bool[] Atext
```

## <a name="cr-field"></a><span data-ttu-id="8ad69-112">CR フィールド</span><span class="sxs-lookup"><span data-stu-id="8ad69-112">CR field</span></span>

<span data-ttu-id="8ad69-113">キャリッジリターン文字を表します。</span><span class="sxs-lookup"><span data-stu-id="8ad69-113">Represents the carriage-return character.</span></span>

```csharp
internal static readonly char CR
```

## <a name="ctext-field"></a><span data-ttu-id="8ad69-114">Ctext フィールド</span><span class="sxs-lookup"><span data-stu-id="8ad69-114">Ctext field</span></span>

<span data-ttu-id="8ad69-115">コメント内で使用できる文字を表します。</span><span class="sxs-lookup"><span data-stu-id="8ad69-115">Represents the characters allowed inside of comments.</span></span>

```csharp
internal static bool[] Ctext
```

## <a name="dot-field"></a><span data-ttu-id="8ad69-116">ドットフィールド</span><span class="sxs-lookup"><span data-stu-id="8ad69-116">Dot field</span></span>

<span data-ttu-id="8ad69-117">フルストップ文字 () を表し `.` ます。</span><span class="sxs-lookup"><span data-stu-id="8ad69-117">Represents the full-stop character (`.`).</span></span>

```csharp
internal static readonly char Dot
```

## <a name="endcomment-field"></a><span data-ttu-id="8ad69-118">EndComment フィールド</span><span class="sxs-lookup"><span data-stu-id="8ad69-118">EndComment field</span></span>

<span data-ttu-id="8ad69-119">コメントの末尾を指定する文字を表します。</span><span class="sxs-lookup"><span data-stu-id="8ad69-119">Represents the character that specifies the end of a comment.</span></span>

```csharp
internal static readonly char EndComment
```

## <a name="lf-field"></a><span data-ttu-id="8ad69-120">LF フィールド</span><span class="sxs-lookup"><span data-stu-id="8ad69-120">LF field</span></span>

<span data-ttu-id="8ad69-121">ラインフィード文字を表します。</span><span class="sxs-lookup"><span data-stu-id="8ad69-121">Represents the line-feed character.</span></span>

```csharp
internal static readonly char LF
```

## <a name="space-field"></a><span data-ttu-id="8ad69-122">スペースフィールド</span><span class="sxs-lookup"><span data-stu-id="8ad69-122">Space field</span></span>

<span data-ttu-id="8ad69-123">空白文字を表します。</span><span class="sxs-lookup"><span data-stu-id="8ad69-123">Represents the space character.</span></span>

```csharp
internal static readonly char Space
```

## <a name="startcomment-field"></a><span data-ttu-id="8ad69-124">StartComment フィールド</span><span class="sxs-lookup"><span data-stu-id="8ad69-124">StartComment field</span></span>

<span data-ttu-id="8ad69-125">コメントの先頭を指定する文字を表します。</span><span class="sxs-lookup"><span data-stu-id="8ad69-125">Represents the character that specifies the start of a comment.</span></span>

```csharp
internal static readonly char StartComment
```

## <a name="tab-field"></a><span data-ttu-id="8ad69-126">タブフィールド</span><span class="sxs-lookup"><span data-stu-id="8ad69-126">Tab field</span></span>

<span data-ttu-id="8ad69-127">タブ文字を表します。</span><span class="sxs-lookup"><span data-stu-id="8ad69-127">Represents the tab character.</span></span>

```csharp
internal static readonly char Tab
```

## <a name="requirements"></a><span data-ttu-id="8ad69-128">必要条件</span><span class="sxs-lookup"><span data-stu-id="8ad69-128">Requirements</span></span>

<span data-ttu-id="8ad69-129">**名前空間:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="8ad69-129">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="8ad69-130">**アセンブリ:** システム (System.dll)</span><span class="sxs-lookup"><span data-stu-id="8ad69-130">**Assembly:** System (in System.dll)</span></span>
