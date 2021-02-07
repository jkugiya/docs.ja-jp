---
description: '詳細情報: BinaryMessageEncodingBindingElement'
title: BinaryMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: e2bb3cdd-3bbd-4bb5-85fe-570457500a66
ms.openlocfilehash: e2bc711416c61ca29a93fbf75e4e734137f2b4be
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757879"
---
# <a name="binarymessageencodingbindingelement"></a><span data-ttu-id="7748d-103">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="7748d-103">BinaryMessageEncodingBindingElement</span></span>

<span data-ttu-id="7748d-104">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="7748d-104">BinaryMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7748d-105">構文</span><span class="sxs-lookup"><span data-stu-id="7748d-105">Syntax</span></span>  
  
```csharp  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="7748d-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="7748d-106">Methods</span></span>  

 <span data-ttu-id="7748d-107">BinaryMessageEncodingBindingElement クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="7748d-107">The BinaryMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="7748d-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="7748d-108">Properties</span></span>  

 <span data-ttu-id="7748d-109">BinaryMessageEncodingBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="7748d-109">The BinaryMessageEncodingBindingElement class has the following properties.</span></span>  
  
## <a name="maxreadpoolsize"></a><span data-ttu-id="7748d-110">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="7748d-110">MaxReadPoolSize</span></span>  

 <span data-ttu-id="7748d-111">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="7748d-111">Data type: sint32</span></span>  
  
 <span data-ttu-id="7748d-112">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="7748d-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7748d-113">新しいリーダーを割り当てずに同時に読み取り可能なメッセージの数を定義する整数です。</span><span class="sxs-lookup"><span data-stu-id="7748d-113">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
## <a name="maxsessionsize"></a><span data-ttu-id="7748d-114">MaxSessionSize</span><span class="sxs-lookup"><span data-stu-id="7748d-114">MaxSessionSize</span></span>  

 <span data-ttu-id="7748d-115">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="7748d-115">Data type: sint32</span></span>  
  
 <span data-ttu-id="7748d-116">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="7748d-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7748d-117">エンコーディングに使用するバッファーのサイズ (バイト単位) を指定する値です。</span><span class="sxs-lookup"><span data-stu-id="7748d-117">A value that specifies the size, in bytes, of the buffer used for encoding.</span></span>  
  
## <a name="maxwritepoolsize"></a><span data-ttu-id="7748d-118">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="7748d-118">MaxWritePoolSize</span></span>  

 <span data-ttu-id="7748d-119">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="7748d-119">Data type: sint32</span></span>  
  
 <span data-ttu-id="7748d-120">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="7748d-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7748d-121">新しいライターを割り当てずに同時に送信可能なメッセージの数を定義する整数です。</span><span class="sxs-lookup"><span data-stu-id="7748d-121">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
## <a name="readerquotas"></a><span data-ttu-id="7748d-122">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="7748d-122">ReaderQuotas</span></span>  

 <span data-ttu-id="7748d-123">データ型 : XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="7748d-123">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="7748d-124">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="7748d-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7748d-125">リーダのクォータ。</span><span class="sxs-lookup"><span data-stu-id="7748d-125">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7748d-126">要件</span><span class="sxs-lookup"><span data-stu-id="7748d-126">Requirements</span></span>  
  
|<span data-ttu-id="7748d-127">MOF</span><span class="sxs-lookup"><span data-stu-id="7748d-127">MOF</span></span>|<span data-ttu-id="7748d-128">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="7748d-128">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="7748d-129">名前空間</span><span class="sxs-lookup"><span data-stu-id="7748d-129">Namespace</span></span>|<span data-ttu-id="7748d-130">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="7748d-130">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7748d-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="7748d-131">See also</span></span>

- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
