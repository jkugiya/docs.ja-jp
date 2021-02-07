---
description: '詳細: Message. BodyToString メソッド'
title: Message. BodyToString メソッド (System.servicemodel)
ms.date: 11/01/2019
topic_type:
- apiref
api_name:
- System.ServiceModel.Channels.Message.BodyToString
api_location:
- system.servicemodel.dll
api_type:
- Assembly
ms.openlocfilehash: babcd881d191ff46b98e9999c4ff04166479a68d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699377"
---
# <a name="messagebodytostring-method"></a><span data-ttu-id="a19fb-103">Message. BodyToString メソッド</span><span class="sxs-lookup"><span data-stu-id="a19fb-103">Message.BodyToString Method</span></span>

<span data-ttu-id="a19fb-104">メソッドを呼び出すことによって、メッセージ本文を文字列に変換し <xref:System.ServiceModel.Channels.Message.OnBodyToString%2A?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="a19fb-104">Converts the message body into a string by calling the <xref:System.ServiceModel.Channels.Message.OnBodyToString%2A?displayProperty=nameWithType> method.</span></span>

```csharp
internal void BodyToString(XmlDictionaryWriter writer);
```

## <a name="parameters"></a><span data-ttu-id="a19fb-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a19fb-105">Parameters</span></span>

- <span data-ttu-id="a19fb-106">`writer` <xref:System.Xml.XmlDictionaryWriter></span><span class="sxs-lookup"><span data-stu-id="a19fb-106">`writer` <xref:System.Xml.XmlDictionaryWriter></span></span>\
  <span data-ttu-id="a19fb-107">メッセージ本文を文字列に変換するために使用されるライター。</span><span class="sxs-lookup"><span data-stu-id="a19fb-107">The writer that is used to convert the message body to a string.</span></span>

## <a name="remarks"></a><span data-ttu-id="a19fb-108">解説</span><span class="sxs-lookup"><span data-stu-id="a19fb-108">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="a19fb-109">`Message.BodyToString`メソッドは内部であり、コードで直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="a19fb-109">The `Message.BodyToString` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="a19fb-110">Microsoft では、どのような状況でも、実稼働アプリケーションでこの方法を使用することはサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="a19fb-110">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="a19fb-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="a19fb-111">Requirements</span></span>

<span data-ttu-id="a19fb-112">**名前空間:** <xref:System.ServiceModel.Channels></span><span class="sxs-lookup"><span data-stu-id="a19fb-112">**Namespace:** <xref:System.ServiceModel.Channels></span></span>

<span data-ttu-id="a19fb-113">**アセンブリ:** System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="a19fb-113">**Assembly:** System.ServiceModel.dll</span></span>

<span data-ttu-id="a19fb-114">**.NET Framework のバージョン:** 3.0 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="a19fb-114">**.NET Framework versions:** Available since 3.0.</span></span>
