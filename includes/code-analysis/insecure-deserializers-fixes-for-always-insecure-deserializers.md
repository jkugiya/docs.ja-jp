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
- 可能であれば、代わりに安全なシリアライザーを使用し、**攻撃者が任意の型を指定して逆シリアル化することを許可しない** でください。 安全性の高いシリアライザーには次のものがあります。

  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType> - <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType> を使用しません。 型リゾルバーを使用する必要がある場合は、逆シリアル化する型を予期されるリストに制限します。
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - Newtonsoft Json.NET - TypeNameHandling.None を使用します。 TypeNameHandling に別の値を使用する必要がある場合は、カスタム ISerializationBinder を使用して、逆シリアル化された型を予期されるリストに制限します。
  - プロトコル バッファー

- シリアル化されたデータを改ざん防止にします。 シリアル化後に、シリアル化されたデータに暗号化署名します。 逆シリアル化する前に、暗号化署名を検証します。 暗号化キーの開示を防止し、キーのローテーションを設計します。
