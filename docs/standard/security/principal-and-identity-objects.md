---
title: プリンシパル オブジェクトと ID オブジェクト
description: .NET 内でユーザーを表す、ID オブジェクトについて説明します。 ID オブジェクトとロールの両方をカプセル化するプリンシパル オブジェクトについても説明します。
ms.date: 07/15/2020
helpviewer_keywords:
- WindowsIdentity objects
- GenericIdentity objects
- GenericPrincipal objects
- identity objects, about identity objects
- security [.NET], identity objects
- principal objects, about principal objects
- security [.NET], principals
- WindowsPrincipal objects
ms.assetid: aa5930ad-f3d7-40aa-b6f6-c6edcd5c64f7
ms.openlocfilehash: daa851e22ab70826395fa86a4d3aae9901e01be7
ms.sourcegitcommit: aab60b21144bf04b3057b5d59aa7c58edaef32d1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2021
ms.locfileid: "107494416"
---
# <a name="principal-and-identity-objects"></a>プリンシパル オブジェクトと ID オブジェクト

> [!NOTE]
> この記事は Windows に適用されます。
>
> ASP.NET Core の詳細については、「[ASP.NET Core のセキュリティ](/aspnet/core/security/)」を参照してください。

マネージド コードは、<xref:System.Security.Principal.IIdentity> オブジェクトへの参照が含まれる <xref:System.Security.Principal.IPrincipal> オブジェクトを通じてプリンシパルの ID またはロールを検出できます。 ID オブジェクトとプリンシパル オブジェクトは、ユーザーとグループ アカウントのようななじみのある概念と比較するとわかりやすいでしょう。 ほとんどのネットワーク環境で、ユーザー アカウントは人またはプログラムを表し、グループ アカウントは特定のカテゴリのユーザーやそのユーザーが所有する権限を表します。 同様に、.NET の ID オブジェクトはユーザーを表し、ロールはメンバーシップやセキュリティ コンテキストを表します。 .NET では、プリンシパル オブジェクトによって ID オブジェクトとロールの両方がカプセル化されます。 .NET アプリケーションは、その ID か、より一般的にはそのロール メンバーシップに基づいてプリンシパルに権限を付与します。  
  
## <a name="identity-objects"></a>ID オブジェクト

ID オブジェクトは、検証対象のユーザーまたはエンティティに関する情報をカプセル化します。 ID オブジェクトの最も基本的なレベルには名前と認証の種類が含まれます。 名前はユーザー名または Windows アカウント名、認証の種類は、サポートされるログオン プロトコル (Kerberos V5 など) かカスタム値になります。 .NET では、ほとんどのカスタム ログオン シナリオで使用できる <xref:System.Security.Principal.GenericIdentity> オブジェクトと、アプリケーションを Windows 認証に依存させる場合に使用できるより特殊な <xref:System.Security.Principal.WindowsIdentity> オブジェクトが定義されています。 また、カスタム ユーザー情報をカプセル化する独自の ID クラスを定義することもできます。  
  
<xref:System.Security.Principal.IIdentity> インターフェイスでは、名前と認証の種類 (Kerberos V5 や NTLM など) にアクセスするためのプロパティが定義されています。 すべての **Identity** クラスでは **IIdentity** インターフェイスが実装されます。 **ID** オブジェクトと、スレッドが現在実行している Windows プロセス トークンの間に関係は必要ありません。 ただし、**ID** オブジェクトが **WindowsIdentity** オブジェクトである場合、ID は Windows セキュリティ トークンを表すと見なされます。  
  
## <a name="principal-objects"></a>プリンシパル オブジェクト

プリンシパル オブジェクトは、コードが実行されているセキュリティ コンテキストを表します。 ロールベースのセキュリティを実装するアプリケーションは、プリンシパル オブジェクトに関連付けられたロールに基づいて権限を付与します。 ID オブジェクトと同様に、.NET では <xref:System.Security.Principal.GenericPrincipal> オブジェクトと <xref:System.Security.Principal.WindowsPrincipal> オブジェクトが提供されています。 独自のカスタム プリンシパル クラスを定義することもできます。  
  
<xref:System.Security.Principal.IPrincipal> インターフェイスでは、関連付けられた **ID** オブジェクトにアクセスするためのプロパティと、**プリンシパル** オブジェクトによって識別されるユーザーが所定のロールのメンバーかどうかを判別するためのメソッドが定義されています。 すべての **プリンシパル** クラスは、**IPrincipal** インターフェイスの他に、必要なその他のプロパティとメソッドを実装しています。 たとえば、共通言語ランタイムでは **WindowsPrincipal** クラスが提供されますが、これによってグループ メンバーシップをロールにマッピングする追加機能が実装されます。  
  
**プリンシパル** オブジェクトは、アプリケーション ドメイン (<xref:System.AppDomain>) 内の呼び出しコンテキスト (<xref:System.Runtime.Remoting.Messaging.CallContext>) オブジェクトにバインドされます。 常に既定の呼び出しコンテキストはそれぞれ新しい **AppDomain** を使用して作成されるため、**プリンシパル** オブジェクトを受け入れる呼び出しコンテキストが常に存在します。 新しいスレッドが作成されるとき、そのスレッドの **CallContext** オブジェクトも作成されます。 **プリンシパル** オブジェクトの参照は、作成スレッドから新しいスレッドの **CallContext** に自動的にコピーされます。 スレッドの作成者に所属する **プリンシパル** オブジェクトをランタイムが判別できない場合は、**プリンシパル** オブジェクトと **ID** オブジェクトの作成で既定のポリシーに従います。  
  
構成可能なアプリケーション ドメイン固有のポリシーによって、新しいアプリケーション ドメインに関連付ける **プリンシパル** オブジェクトの種類を決める規則が定義されます。 セキュリティ ポリシーによって許可される場合、ランタイムは、現在の実行スレッドに関連するオペレーティング システム トークンを反映する **プリンシパル** オブジェクトと **ID** オブジェクトを作成できます。 ランタイムは既定では、認証されていないユーザーを表す **プリンシパル** オブジェクトと **ID** オブジェクトを使用します。 このような既定の **プリンシパル** オブジェクトと **ID** オブジェクトは、コードがアクセスを試行するまでランタイムによって作成されることはありません。  
  
信頼されるコードが、アプリケーション ドメインを作成して、アプリケーション ドメイン ポリシーを作成できます。このポリシーによって、既定の **プリンシパル** オブジェクトと **ID** オブジェクトのコンストラクトが制御されます。 このアプリケーション ドメイン固有ポリシーは、そのアプリケーション ドメインのすべての実行スレッドに適用されます。 信頼されているアンマネージド ホストは本質的にこのポリシーを設定できますが、このポリシーを設定するマネージド コードはドメイン ポリシーを制御するために <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> を持つ必要があります。  
  
**プリンシパル** オブジェクトを同じプロセス内 (つまり同じコンピューター上の) アプリケーション ドメイン間で送信するとき、リモート処理インフラストラクチャが、呼び出し元のコンテキストに関連する **プリンシパル** オブジェクトへの参照を呼び出し先のコンテキストにコピーします。  
  
## <a name="see-also"></a>関連項目

- [方法: WindowsPrincipal プロジェクトを作成する](how-to-create-a-windowsprincipal-object.md)
- [方法: GenericPrincipal オブジェクトと GenericIdentity オブジェクトを作成する](how-to-create-genericprincipal-and-genericidentity-objects.md)
- [プリンシパル オブジェクトの置き換え](replacing-a-principal-object.md)
- [偽装と復帰](impersonating-and-reverting.md)
- [ロール ベースのセキュリティ](role-based-security.md)
- [セキュリティの基本概念](key-security-concepts.md)
- [ASP.NET Core のセキュリティ](/aspnet/core/security/)
