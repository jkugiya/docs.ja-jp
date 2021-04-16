---
author: dotpaul
ms.author: paulming
ms.date: 05/01/2019
ms.topic: include
ms.openlocfilehash: cf944ae9ca200d34a1f0f32e68bf3aee73a9500a
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "96591105"
---
- <span data-ttu-id="946e9-101">可能であれば、代わりに安全なシリアライザーを使用し、**攻撃者が任意の型を指定して逆シリアル化することを許可しない** でください。</span><span class="sxs-lookup"><span data-stu-id="946e9-101">If possible, use a secure serializer instead, and **don't allow an attacker to specify an arbitrary type to deserialize**.</span></span> <span data-ttu-id="946e9-102">安全性の高いシリアライザーには次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="946e9-102">Some safer serializers include:</span></span>

  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <span data-ttu-id="946e9-103"><xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType> - <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType> を使用しません。</span><span class="sxs-lookup"><span data-stu-id="946e9-103"><xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType> - Never use <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>.</span></span> <span data-ttu-id="946e9-104">型リゾルバーを使用する必要がある場合は、逆シリアル化する型を予期されるリストに制限します。</span><span class="sxs-lookup"><span data-stu-id="946e9-104">If you must use a type resolver, restrict deserialized types to an expected list.</span></span>
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - <span data-ttu-id="946e9-105">Newtonsoft Json.NET - TypeNameHandling.None を使用します。</span><span class="sxs-lookup"><span data-stu-id="946e9-105">Newtonsoft Json.NET - Use TypeNameHandling.None.</span></span> <span data-ttu-id="946e9-106">TypeNameHandling に別の値を使用する必要がある場合は、カスタム ISerializationBinder を使用して、逆シリアル化された型を予期されるリストに制限します。</span><span class="sxs-lookup"><span data-stu-id="946e9-106">If you must use another value for TypeNameHandling, restrict deserialized types to an expected list with a custom ISerializationBinder.</span></span>
  - <span data-ttu-id="946e9-107">プロトコル バッファー</span><span class="sxs-lookup"><span data-stu-id="946e9-107">Protocol Buffers</span></span>

- <span data-ttu-id="946e9-108">シリアル化されたデータを改ざん防止にします。</span><span class="sxs-lookup"><span data-stu-id="946e9-108">Make the serialized data tamper-proof.</span></span> <span data-ttu-id="946e9-109">シリアル化後に、シリアル化されたデータに暗号化署名します。</span><span class="sxs-lookup"><span data-stu-id="946e9-109">After serialization, cryptographically sign the serialized data.</span></span> <span data-ttu-id="946e9-110">逆シリアル化する前に、暗号化署名を検証します。</span><span class="sxs-lookup"><span data-stu-id="946e9-110">Before deserialization, validate the cryptographic signature.</span></span> <span data-ttu-id="946e9-111">暗号化キーの開示を防止し、キーのローテーションを設計します。</span><span class="sxs-lookup"><span data-stu-id="946e9-111">Protect the cryptographic key from being disclosed and design for key rotations.</span></span>
