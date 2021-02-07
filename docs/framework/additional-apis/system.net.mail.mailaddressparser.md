---
description: '詳細情報: Mailaddressparc Ser クラス'
title: Mailaddressparc Ser クラス (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Mail.MailAddressParser
- System.Net.Mail.MailAddressParser.ParseAddress
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 5ad534e731e283f5449b3b8cc8e87628716da9b0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699767"
---
# <a name="mailaddressparser-class"></a><span data-ttu-id="881d9-103">MailAddressParser クラス</span><span class="sxs-lookup"><span data-stu-id="881d9-103">MailAddressParser class</span></span>

<span data-ttu-id="881d9-104">RFC 2822 で説明されているように、電子メールアドレスを解析します。</span><span class="sxs-lookup"><span data-stu-id="881d9-104">Parses email addresses as described in RFC 2822.</span></span> <span data-ttu-id="881d9-105">このクラスは継承できません。</span><span class="sxs-lookup"><span data-stu-id="881d9-105">This class cannot be inherited.</span></span>

```csharp
internal static class MailAddressParser
```

> [!WARNING]
> <span data-ttu-id="881d9-106">このクラスは内部的なものであり、コードで直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="881d9-106">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="881d9-107">Microsoft では、どのような状況でも、実稼働アプリケーションでのこのクラスの使用はサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="881d9-107">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="parseaddress-method"></a><span data-ttu-id="881d9-108">ParseAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="881d9-108">ParseAddress method</span></span>

<span data-ttu-id="881d9-109">指定した文字列から1つの電子メールアドレスを解析します。</span><span class="sxs-lookup"><span data-stu-id="881d9-109">Parses a single email address from the specified string.</span></span>

```csharp
internal static MailAddress ParseAddress(string data)
```

### <a name="parameters"></a><span data-ttu-id="881d9-110">パラメーター</span><span class="sxs-lookup"><span data-stu-id="881d9-110">Parameters</span></span>

<span data-ttu-id="881d9-111">`data` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="881d9-111">`data` <xref:System.String></span></span>

<span data-ttu-id="881d9-112">解析する電子メールアドレスを含む文字列。</span><span class="sxs-lookup"><span data-stu-id="881d9-112">The string that contains an email address to be parsed.</span></span>

### <a name="return-value"></a><span data-ttu-id="881d9-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="881d9-113">Return value</span></span>

<xref:System.Net.Mail.MailAddress>

<span data-ttu-id="881d9-114">有効な電子メールアドレス。</span><span class="sxs-lookup"><span data-stu-id="881d9-114">A valid email address.</span></span>

### <a name="exceptions"></a><span data-ttu-id="881d9-115">例外</span><span class="sxs-lookup"><span data-stu-id="881d9-115">Exceptions</span></span>

<xref:System.FormatException?displayProperty=nameWithType>

<span data-ttu-id="881d9-116">電子メールアドレスが無効です。</span><span class="sxs-lookup"><span data-stu-id="881d9-116">The email address is invalid.</span></span>

## <a name="requirements"></a><span data-ttu-id="881d9-117">必要条件</span><span class="sxs-lookup"><span data-stu-id="881d9-117">Requirements</span></span>

<span data-ttu-id="881d9-118">**名前空間:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="881d9-118">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="881d9-119">**アセンブリ:** システム (System.dll)</span><span class="sxs-lookup"><span data-stu-id="881d9-119">**Assembly:** System (in System.dll)</span></span>
