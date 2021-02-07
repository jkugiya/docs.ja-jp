---
description: '詳細情報: TextMessageEncodingBindingElement'
title: TextMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 885e2d7a-3436-4093-bc5f-0a404c62acdc
ms.openlocfilehash: 9848f1660642f92c4bce3542fbd404f463b8c84d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757346"
---
# <a name="textmessageencodingbindingelement"></a><span data-ttu-id="450f8-103">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="450f8-103">TextMessageEncodingBindingElement</span></span>

<span data-ttu-id="450f8-104">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="450f8-104">TextMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="450f8-105">構文</span><span class="sxs-lookup"><span data-stu-id="450f8-105">Syntax</span></span>  
  
```csharp
class TextMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="450f8-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="450f8-106">Methods</span></span>  

 <span data-ttu-id="450f8-107">TextMessageEncodingBindingElement クラスで定義されているメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="450f8-107">The TextMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="450f8-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="450f8-108">Properties</span></span>  

 <span data-ttu-id="450f8-109">TextMessageEncodingBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="450f8-109">The TextMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="450f8-110">エンコード</span><span class="sxs-lookup"><span data-stu-id="450f8-110">Encoding</span></span>  

 <span data-ttu-id="450f8-111">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="450f8-111">Data type: string</span></span>  
  
 <span data-ttu-id="450f8-112">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="450f8-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="450f8-113">バインディングでメッセージの送信に使用される文字セット エンコーディング。</span><span class="sxs-lookup"><span data-stu-id="450f8-113">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="450f8-114">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="450f8-114">MaxReadPoolSize</span></span>  

 <span data-ttu-id="450f8-115">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="450f8-115">Data type: sint32</span></span>  
  
 <span data-ttu-id="450f8-116">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="450f8-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="450f8-117">新しいリーダーを割り当てずに同時に読み取り可能なメッセージの数を定義する整数です。</span><span class="sxs-lookup"><span data-stu-id="450f8-117">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="450f8-118">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="450f8-118">MaxWritePoolSize</span></span>  

 <span data-ttu-id="450f8-119">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="450f8-119">Data type: sint32</span></span>  
  
 <span data-ttu-id="450f8-120">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="450f8-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="450f8-121">新しいライターを割り当てずに同時に送信可能なメッセージの数を定義する整数です。</span><span class="sxs-lookup"><span data-stu-id="450f8-121">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="450f8-122">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="450f8-122">ReaderQuotas</span></span>  

 <span data-ttu-id="450f8-123">データ型 : XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="450f8-123">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="450f8-124">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="450f8-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="450f8-125">リーダのクォータ。</span><span class="sxs-lookup"><span data-stu-id="450f8-125">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="450f8-126">要件</span><span class="sxs-lookup"><span data-stu-id="450f8-126">Requirements</span></span>  
  
|<span data-ttu-id="450f8-127">MOF</span><span class="sxs-lookup"><span data-stu-id="450f8-127">MOF</span></span>|<span data-ttu-id="450f8-128">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="450f8-128">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="450f8-129">名前空間</span><span class="sxs-lookup"><span data-stu-id="450f8-129">Namespace</span></span>|<span data-ttu-id="450f8-130">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="450f8-130">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="450f8-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="450f8-131">See also</span></span>

- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
