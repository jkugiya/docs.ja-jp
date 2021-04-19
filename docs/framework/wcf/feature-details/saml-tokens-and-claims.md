---
title: SAML トークンとクレーム
description: WFC により、SAML トークンを使用してステートメント (特定のエンティティによって他のエンティティに関して作成されるクレームのセット) がどのように伝達されるかを説明します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
- issued tokens
- SAML token
ms.assetid: 930b6e34-9eab-4e95-826c-4e06659bb977
ms.openlocfilehash: a1de58ae28041b8e89822120c9369612217eb3b7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96288517"
---
# <a name="saml-tokens-and-claims"></a>SAML トークンとクレーム

SAML (Security Assertion Markup Language) "*トークン*" は、クレームの XML 表現です。 既定では、フェデレーション セキュリティのシナリオで使用される SAML トークン Windows Communication Foundation (WCF) は、"*発行済みトークン*" です。  
  
 SAML トークンは、ステートメント (特定のエンティティによって他のエンティティに関して作成されるクレームのセット) を伝達します。 たとえば、フェデレーション セキュリティ シナリオでは、ステートメントがセキュリティ トークン サービスによって、システム内の特定のユーザーに関して作成されます。 セキュリティ トークン サービスは、トークンに含まれるステートメントの信憑性を示すために SAML トークンに署名します。 また、SAML トークンは、SAML トークンのユーザーが証明として提示する暗号化キー マテリアルに関連付けられています。 これが証拠となり、証明書利用者は、SAML トークンが実際にそのユーザーに対して発行されたことを確認できます。 一般的なシナリオでの例を次に示します。  
  
1. クライアントは、セキュリティ トークン サービスから SAML トークンを要求し、Windows 資格情報を使用して、そのセキュリティ トークン サービスに対して認証を行います。  
  
2. セキュリティ トークン サービスは、SAML トークンをクライアントに発行します。 SAML トークンは、セキュリティ トークン サービスに関連付けられた証明書を使用して署名され、ターゲット サービス用に暗号化された証明キーを含んでいます。  
  
3. クライアントにより、"*証明キー*" のコピーの受け取りも行われます。 クライアントにより、SAML トークンがアプリケーション サービス ("*証明書利用者*") に提示され、その証明キーを使用したメッセージへの署名が行われます。  
  
4. SAML トークンの署名は、そのトークンがセキュリティ トークン サービスによって発行されたことを証明書利用者に示します。 また、証明キーを使用して作成されたメッセージ署名は、トークンがそのクライアントに対して発行されたことを示します。  
  
## <a name="from-claims-to-samlattributes"></a>クレームから SamlAttributes  

 WCF では、SAML トークン内のステートメントは <xref:System.IdentityModel.Tokens.SamlAttribute> オブジェクトとしてモデル化されています。<xref:System.IdentityModel.Claims.Claim> オブジェクトが <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> の <xref:System.IdentityModel.Claims.Claim.Right%2A> プロパティを持ち、<xref:System.IdentityModel.Claims.Claim.Resource%2A> プロパティが <xref:System.String> 型である場合、これは <xref:System.IdentityModel.Claims.Claim> オブジェクトから直接設定できます。 次に例を示します。  
  
 [!code-csharp[c_CreateSTS#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#8)]
 [!code-vb[c_CreateSTS#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#8)]  
  
> [!NOTE]
> セキュリティ トークン サービスによって発行されたか、または認証の一部としてクライアントからサービスに提示されたときに、SAML トークンがメッセージ内にシリアル化される場合、メッセージの最大クォータ サイズが、SAML トークンおよびメッセージの他の部分を格納できるだけの大きさである必要があります。 通常は、既定のメッセージ クォータ サイズで十分です。 ただし、何百ものクレームを含んでいるために SAML トークンのサイズが大きい場合には、シリアル化されたトークンを格納できるように、クォータを増やす必要が生じることがあります。 詳しくは、「[データに関するセキュリティ上の考慮事項](security-considerations-for-data.md)」をご覧ください。  
  
## <a name="from-samlattributes-to-claims"></a>SamlAttributes からクレーム  

 SAML トークンがメッセージで受信されると、SAML トークン内のさまざまなステートメントは、 <xref:System.IdentityModel.Policy.IAuthorizationPolicy> オブジェクトに変換され、<xref:System.IdentityModel.Policy.AuthorizationContext> に配置されます。 各 SAML ステートメントのクレームは <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> の <xref:System.IdentityModel.Policy.AuthorizationContext> プロパティによって返され、これを調べることによってユーザーの認証と承認を行うかどうかを決定できます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.IdentityModel.Policy.AuthorizationContext>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- <xref:System.IdentityModel.Claims.ClaimSet>
- [フェデレーション](federation.md)
- [方法: フェデレーション クライアントを作成する](how-to-create-a-federated-client.md)
- [方法: フェデレーション サービスで資格情報を設定する](how-to-configure-credentials-on-a-federation-service.md)
- [ID モデルを使用したクレームと承認の管理](managing-claims-and-authorization-with-the-identity-model.md)
- [クレームとトークン](claims-and-tokens.md)
- [クレームの作成とリソース値](claim-creation-and-resource-values.md)
- [方法: カスタム クレームを作成する](../extending/how-to-create-a-custom-claim.md)
