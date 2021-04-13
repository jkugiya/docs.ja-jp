---
title: '方法: X.509 証明書を WCF からアクセス可能にする'
description: X.509 証明書を WCF からアクセス可能にする方法について説明します。 アプリケーション コードでは、証明書ストアの名前と場所を指定する必要があります。 他の要件がある可能性もあります。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- X.509 certificates [WCF]
- certificates [WCF], making X.509 certificates accessible to WCF
- X.509 certificates [WCF], making accessible to WCF
ms.assetid: a54e407c-c2b5-4319-a648-60e43413664b
ms.openlocfilehash: 06a6167f0ad352955eb6b764ef8bfdb1394f4ed9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96279741"
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a>方法: X.509 証明書を WCF からアクセス可能にする

Windows Communication Foundation (WCF) から X.509 証明書にアクセスできるようにするには、アプリケーション コードで証明書ストアの名前と場所を指定する必要があります。 特定の状況では、X.509 証明書に関連付けられた秘密キーを格納しているファイルにプロセス ID がアクセスできる必要があります。 証明書ストア内の X.509 証明書に関連付けられている秘密キーを取得するには、それを行うためのアクセス許可が WCF に必要になります。 既定では、所有者と System アカウントだけが証明書の秘密キーにアクセスできます。  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a>X.509 証明書を WCF からアクセス可能にするには  
  
1. WCF が実行されているアカウントに対して、X.509 証明書に関連付けられている秘密キーを格納しているファイルへの読み取りアクセス権を与えます。  
  
    1. WCF に X.509 証明書の秘密キーへの読み取りアクセス権が必要かどうかを判断します。  
  
         次の表は、X.509 証明書を使用する際に秘密キーを使用できる必要があるかどうかを示しています。  
  
        |X.509 証明書の使用法|秘密キー|  
        |---------------------------|-----------------|  
        |送信 SOAP メッセージにデジタル署名する。|はい|  
        |受信 SOAP メッセージの署名を検証する。|いいえ|  
        |送信 SOAP メッセージを暗号化する。|いいえ|  
        |受信 SOAP メッセージを復号化する。|はい|  
  
    2. 証明書が格納されている証明書ストアの場所と名前を決定します。  
  
         証明書が格納されている証明書ストアは、アプリケーション コードまたは構成で指定します。 たとえば、次の例では、証明書が `CurrentUser` という名前の `My` 証明書ストア内に存在することを指定します。  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3. [FindPrivateKey](../samples/findprivatekey.md) ツールを使用して、証明書の秘密キーがコンピューター上のどこに存在するかを確認します。  
  
         [FindPrivateKey](../samples/findprivatekey.md) ツールには、証明書ストアの名前、証明書ストアの場所、および証明書を一意に識別する情報を指定する必要があります。 このツールは、証明書のサブジェクト名または拇印を一意の識別子として受け入れます。 証明書の拇印を確認する方法の詳細については、「[方法: 証明書のサムプリントを取得する](how-to-retrieve-the-thumbprint-of-a-certificate.md)」を参照してください。  
  
         次のコード例では、[FindPrivateKey](../samples/findprivatekey.md) ツールを使用して、`CurrentUser` の `My` ストア内に存在する、拇印 `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d` を持つ証明書の秘密キーの場所を特定します。  
  
        ```console
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4. WCF が実行されているアカウントを確認します。  
  
         次の表は、特定のシナリオで WCF が実行されているアカウントの詳細を示しています。  
  
        |シナリオ|プロセス ID|  
        |--------------|----------------------|  
        |クライアント (コンソールまたは WinForms アプリケーション)|現在ログインしているユーザー|  
        |自己ホスト型のサービス|現在ログインしているユーザー|  
        |IIS 6.0 (Windows Server 2003) または IIS 7.0 (Windows Vista) でホストされているサービス。|NETWORK SERVICE|  
        |IIS 5.X (Windows XP) でホストされているサービス。|Machine.config ファイル内の `<processModel>` 要素によって制御されます。 既定のアカウントは ASPNET です。|  
  
    5. icacls.exe などのツールを使用して、WCF が実行されているアカウントに、秘密キーを格納しているファイルへの読み取りアクセス権を与えます。  
  
         次のコード例では、指定したファイルの随意アクセス制御リスト (DACL) を編集して、NETWORK SERVICE アカウントにそのファイルへの読み取り (:R) アクセス権を与えます。  
  
        ```console
        icacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /grant "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a>関連項目

- [FindPrivateKey](../samples/findprivatekey.md)
- [方法: 証明書のサムプリントを取得する](how-to-retrieve-the-thumbprint-of-a-certificate.md)
- [証明書の使用](working-with-certificates.md)
