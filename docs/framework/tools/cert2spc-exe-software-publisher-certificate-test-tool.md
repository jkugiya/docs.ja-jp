---
title: Cert2spc.exe (ソフトウェア発行元証明書テスト ツール)
description: "Cert2spc.exe (ソフトウェア発行元証明書テスト ツール) を使用します。 このツールによって、1 つまたは複数の X.509 証明書からソフトウェア発行元証明書 (SPC: Software Publisher's Certificate) が作成されます。"
ms.date: 03/30/2017
helpviewer_keywords:
- SPC
- Software Publisher Certificate Test tool
- Software Publisher Certificate
- Cert2spc.exe
- certificates, Software Publisher's Certificate
ms.assetid: be434d7d-9c0d-46e7-8392-58a9b542d11d
ms.openlocfilehash: d2bd0fdc07b87a9b21b281669a213a048a407595
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2021
ms.locfileid: "104654207"
---
# <a name="cert2spcexe-software-publisher-certificate-test-tool"></a>Cert2spc.exe (ソフトウェア発行元証明書テスト ツール)

ソフトウェア発行元証明書テスト ツールは、1 つ以上の X.509 証明書からソフトウェア発行元証明書 (SPC: Software Publisher's Certificate) を作成します。 Cert2spc.exe はテスト専用のツールです。 有効な SPC は、VeriSign や Thawte などの証明書発行機関から入手できます。 X.509 証明書の作成の詳細については、「[Makecert.exe (証明書作成ツール)](/windows/desktop/SecCrypto/makecert)」を参照してください。  
  
 このツールは、Visual Studio と共に自動的にインストールされます。 ツールを実行するには、[、Visual Studio 開発者コマンド プロンプトまたは Visual Studio Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell) を使用します。  
  
 コマンド プロンプトに次のように入力します。  
  
## <a name="syntax"></a>構文  
  
```console  
cert2spc cert1.cer | crl1.crl [... certN.cer | crlN.crl] outputSPCfile.spc  
```  
  
## <a name="parameters"></a>パラメーター  
  
|引数|説明|  
|--------------|-----------------|  
|`certN.cer`|SPC ファイルに組み込む X.509 証明書の名前。 スペースで区切ることによって、複数の名前を指定できます。|  
|`crlN.crl`|SPC ファイルに組み込む証明書失効リストの名前。 スペースで区切ることによって、複数の名前を指定できます。|  
|`outputSPCfile.spc`|X.509 証明書が格納される PKCS #7 オブジェクトの名前。|  
  
|オプション|説明|  
|------------|-----------------|  
|**/?**|このツールのコマンド構文とオプションを表示します。|  
  
## <a name="examples"></a>使用例  

 `myCertificate.cer` から SPC を作成し、`mySPCFile.spc` に格納するコマンドを次に示します。  
  
```console
cert2spc myCertificate.cer mySPCFile.spc  
```  
  
 `oneCertificate.cer` と `twoCertificate.cer` から SPC を作成し、`mySPCFile.spc` に格納するコマンドを次に示します。  
  
```console
cert2spc oneCertificate.cer twoCertificate.cer mySPCFile.spc  
```  
  
## <a name="see-also"></a>関連項目

- [ツール](index.md)
- [Makecert.exe (証明書作成ツール)](/windows/desktop/SecCrypto/makecert)
- [開発者コマンドライン シェル](/visualstudio/ide/reference/command-prompt-powershell)
