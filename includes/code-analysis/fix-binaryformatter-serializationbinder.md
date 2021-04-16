---
ms.openlocfilehash: 557d811e2eeaf926cb958471d214fc23c50a25f2
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "96591102"
---
- 代わりに安全なシリアライザーを使用し、**攻撃者が任意の型を指定して逆シリアル化することを許可しない** でください。 詳細については、[推奨される代替手段](/dotnet/standard/serialization/binaryformatter-security-guide#preferred-alternatives)を参照してください。
- シリアル化されたデータを改ざん防止にします。 シリアル化後に、シリアル化されたデータに暗号化署名します。 逆シリアル化する前に、暗号化署名を検証します。 暗号化キーの開示を防止し、キーのローテーションを設計します。
- このオプションを使用すると、サービス拒否攻撃やリモート コード実行攻撃に対してコードが脆弱になります。 詳細については、「[BinaryFormatter セキュリティ ガイド](/dotnet/standard/serialization/binaryformatter-security-guide)」をご覧ください。 逆シリアル化された型を制限します。 カスタムの <xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType> を実装します。 逆シリアル化する前に、すべてのコード パスで、`Binder` プロパティをカスタムの <xref:System.Runtime.Serialization.SerializationBinder> インスタンスに設定します。 オーバーライドした <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> メソッドで、予期しない型の場合は例外をスローして、逆シリアル化を停止します。
