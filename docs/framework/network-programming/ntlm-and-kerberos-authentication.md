---
title: NTLM 認証および Kerberos 認証
description: .NET Framework アプリケーションに対して既定の NTLM 認証と Kerberos 認証が動作するしくみと、既定ではない NTLM 認証について説明します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- authentication [.NET Framework], NTLM
- authentication [.NET Framework], Kerberos
- user authentication, Kerberos
- user authentication, NTLM
- Kerberos authentication
- receiving data, authentication
- NTLM authentication
- Internet, authentication
- client authentication, Kerberos
- sending data, authentication
- network resources, authentication
- classes [.NET Framework], authentication
- client authentication, NTLM
ms.assetid: 9ef65560-f596-4469-bcce-f4d5407b55cd
ms.openlocfilehash: 92d9175f96fa54ccc3514ed479755f1318452bbc
ms.sourcegitcommit: aab60b21144bf04b3057b5d59aa7c58edaef32d1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2021
ms.locfileid: "107494078"
---
# <a name="ntlm-and-kerberos-authentication"></a><span data-ttu-id="9686e-103">NTLM 認証および Kerberos 認証</span><span class="sxs-lookup"><span data-stu-id="9686e-103">NTLM and Kerberos Authentication</span></span>

<span data-ttu-id="9686e-104">既定の NTLM 認証と Kerberos 認証では、呼び出し元のアプリケーションに関連付けられている Microsoft Windows ユーザー資格情報を使用して、サーバーで認証を試みます。</span><span class="sxs-lookup"><span data-stu-id="9686e-104">Default NTLM authentication and Kerberos authentication use the Microsoft Windows user credentials associated with the calling application to attempt authentication with the server.</span></span> <span data-ttu-id="9686e-105">既定以外の NTLM 認証を使用する場合、アプリケーションは認証の種類を NTLM に設定し、次の例に示すように <xref:System.Net.NetworkCredential> オブジェクトを使用して、ユーザー名、パスワード、およびドメインをホストに渡します。</span><span class="sxs-lookup"><span data-stu-id="9686e-105">When using non-default NTLM authentication, the application sets the authentication type to NTLM and uses a <xref:System.Net.NetworkCredential> object to pass the user name, password, and domain to the host, as shown in the following example.</span></span>  
  
```vb  
Dim MyURI As String = "http://www.contoso.com/"  
Dim WReq As WebRequest = WebRequest.Create(MyURI)  
WReq.Credentials = _  
    New NetworkCredential(UserName, SecurelyStoredPassword, Domain)  
```  
  
```csharp  
String MyURI = "http://www.contoso.com/";  
WebRequest WReq = WebRequest.Create (MyURI);  
WReq.Credentials =
    new NetworkCredential(UserName, SecurelyStoredPassword, Domain);  
```  
  
 <span data-ttu-id="9686e-106">アプリケーション ユーザーの資格情報を使用してインターネット サービスに接続する必要があるアプリケーションは、次の例に示すように、ユーザーの既定の資格情報を使用してこれを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="9686e-106">Applications that need to connect to Internet services using the credentials of the application user can do so with the user's default credentials, as shown in the following example.</span></span>  
  
```vb  
Dim MyURI As String = "http://www.contoso.com/"  
Dim WReq As WebRequest = WebRequest.Create(MyURI)  
WReq.Credentials = CredentialCache.DefaultCredentials  
```  
  
```csharp  
String MyURI = "http://www.contoso.com/";  
WebRequest WReq = WebRequest.Create (MyURI);  
WReq.Credentials = CredentialCache.DefaultCredentials;  
```  
  
 <span data-ttu-id="9686e-107">ネゴシエート認証モジュールは、リモート サーバーが NTLM 認証を使用しているか Kerberos 認証を使用しているかを確認し、適切な応答を送信します。</span><span class="sxs-lookup"><span data-stu-id="9686e-107">The negotiate authentication module determines whether the remote server is using NTLM or Kerberos authentication, and sends the appropriate response.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9686e-108">NTLM 認証は、プロキシ サーバー経由では機能しません。</span><span class="sxs-lookup"><span data-stu-id="9686e-108">NTLM authentication does not work through a proxy server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9686e-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="9686e-109">See also</span></span>

- [<span data-ttu-id="9686e-110">基本認証とダイジェスト認証</span><span class="sxs-lookup"><span data-stu-id="9686e-110">Basic and Digest Authentication</span></span>](basic-and-digest-authentication.md)
- [<span data-ttu-id="9686e-111">インターネット認証</span><span class="sxs-lookup"><span data-stu-id="9686e-111">Internet Authentication</span></span>](internet-authentication.md)
