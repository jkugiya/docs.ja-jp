---
description: '詳細情報: WriteStartHeaders メソッド'
title: WriteStartHeaders メソッド (System.servicemodel. Channels)
ms.date: 11/01/2019
topic_type:
- apiref
api_name:
- System.ServiceModel.Channels.Message.WriteStartHeaders
api_location:
- system.servicemodel.dll
api_type:
- Assembly
ms.openlocfilehash: 20cadf5f1eecf6d8e02c5dc4597889abaef4ec36
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699364"
---
# <a name="messagewritestartheaders-method"></a><span data-ttu-id="8c01e-103">WriteStartHeaders メソッド</span><span class="sxs-lookup"><span data-stu-id="8c01e-103">Message.WriteStartHeaders Method</span></span>

<span data-ttu-id="8c01e-104">メソッドを呼び出すことによって、開始ヘッダーを XML ファイルに書き込み <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="8c01e-104">Writes the start header into an XML file by calling the <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A?displayProperty=nameWithType> method.</span></span>

```csharp
internal void WriteStartHeaders(XmlDictionaryWriter writer)
```

## <a name="parameters"></a><span data-ttu-id="8c01e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8c01e-105">Parameters</span></span>

- <span data-ttu-id="8c01e-106">`writer` <xref:System.Xml.XmlDictionaryWriter></span><span class="sxs-lookup"><span data-stu-id="8c01e-106">`writer` <xref:System.Xml.XmlDictionaryWriter></span></span>\
  <span data-ttu-id="8c01e-107">開始ヘッダーを XML ファイルに書き込むために使用するライター。</span><span class="sxs-lookup"><span data-stu-id="8c01e-107">The writer that is used to write the start header into an XML file.</span></span>

## <a name="remarks"></a><span data-ttu-id="8c01e-108">解説</span><span class="sxs-lookup"><span data-stu-id="8c01e-108">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="8c01e-109">`Message.WriteStartHeaders`メソッドは内部であり、コードで直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="8c01e-109">The `Message.WriteStartHeaders` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="8c01e-110">Microsoft では、どのような状況でも、実稼働アプリケーションでこの方法を使用することはサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="8c01e-110">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="8c01e-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="8c01e-111">Requirements</span></span>

<span data-ttu-id="8c01e-112">**名前空間:** <xref:System.ServiceModel.Channels></span><span class="sxs-lookup"><span data-stu-id="8c01e-112">**Namespace:** <xref:System.ServiceModel.Channels></span></span>

<span data-ttu-id="8c01e-113">**アセンブリ:** System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="8c01e-113">**Assembly:** System.ServiceModel.dll</span></span>

<span data-ttu-id="8c01e-114">**.NET Framework のバージョン:** 3.0 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="8c01e-114">**.NET Framework versions:** Available since 3.0.</span></span>
