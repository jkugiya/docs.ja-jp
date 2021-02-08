---
description: '詳細情報: MtomMessageEncodingBindingElement'
title: MtomMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 4a9c6c3d-e561-4b2d-a693-7e84bdd3534a
ms.openlocfilehash: f06e3d7266c4f7e6f9b4639f7d82941cbabb5dd3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803140"
---
# <a name="mtommessageencodingbindingelement"></a><span data-ttu-id="8c7c3-103">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="8c7c3-103">MtomMessageEncodingBindingElement</span></span>

<span data-ttu-id="8c7c3-104">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="8c7c3-104">MtomMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c7c3-105">構文</span><span class="sxs-lookup"><span data-stu-id="8c7c3-105">Syntax</span></span>  
  
```csharp
class MtomMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="8c7c3-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="8c7c3-106">Methods</span></span>  

 <span data-ttu-id="8c7c3-107">MtomMessageEncodingBindingElement クラスで定義されているメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="8c7c3-107">The MtomMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="8c7c3-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="8c7c3-108">Properties</span></span>  

 <span data-ttu-id="8c7c3-109">MtomMessageEncodingBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="8c7c3-109">The MtomMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="8c7c3-110">エンコード</span><span class="sxs-lookup"><span data-stu-id="8c7c3-110">Encoding</span></span>  

 <span data-ttu-id="8c7c3-111">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="8c7c3-111">Data type: string</span></span>  
  
 <span data-ttu-id="8c7c3-112">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="8c7c3-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8c7c3-113">バインディングでメッセージの送信に使用される文字セット エンコーディング。</span><span class="sxs-lookup"><span data-stu-id="8c7c3-113">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="8c7c3-114">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="8c7c3-114">MaxReadPoolSize</span></span>  

 <span data-ttu-id="8c7c3-115">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="8c7c3-115">Data type: sint32</span></span>  
  
 <span data-ttu-id="8c7c3-116">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="8c7c3-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8c7c3-117">新しいリーダーを割り当てずに同時に読み取り可能なメッセージの数を定義する整数です。</span><span class="sxs-lookup"><span data-stu-id="8c7c3-117">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="8c7c3-118">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="8c7c3-118">MaxWritePoolSize</span></span>  

 <span data-ttu-id="8c7c3-119">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="8c7c3-119">Data type: sint32</span></span>  
  
 <span data-ttu-id="8c7c3-120">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="8c7c3-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8c7c3-121">新しいライターを割り当てずに同時に送信可能なメッセージの数を定義する整数です。</span><span class="sxs-lookup"><span data-stu-id="8c7c3-121">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="8c7c3-122">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="8c7c3-122">ReaderQuotas</span></span>  

 <span data-ttu-id="8c7c3-123">データ型 : XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="8c7c3-123">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="8c7c3-124">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="8c7c3-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8c7c3-125">リーダのクォータ。</span><span class="sxs-lookup"><span data-stu-id="8c7c3-125">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c7c3-126">要件</span><span class="sxs-lookup"><span data-stu-id="8c7c3-126">Requirements</span></span>  
  
|<span data-ttu-id="8c7c3-127">MOF</span><span class="sxs-lookup"><span data-stu-id="8c7c3-127">MOF</span></span>|<span data-ttu-id="8c7c3-128">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="8c7c3-128">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="8c7c3-129">名前空間</span><span class="sxs-lookup"><span data-stu-id="8c7c3-129">Namespace</span></span>|<span data-ttu-id="8c7c3-130">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="8c7c3-130">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8c7c3-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="8c7c3-131">See also</span></span>

- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
