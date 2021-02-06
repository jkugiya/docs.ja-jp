---
description: '詳細情報: カスタム暗号アルゴリズムの指定'
title: カスタム暗号アルゴリズムの指定
ms.date: 03/30/2017
ms.assetid: d662a305-8e09-451d-9a59-b0f12b012f1d
ms.openlocfilehash: 4d4cb525b46b33a0d0df8dd6a3db9e9fafe84f8f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643970"
---
# <a name="specifying-a-custom-crypto-algorithm"></a><span data-ttu-id="067ac-103">カスタム暗号アルゴリズムの指定</span><span class="sxs-lookup"><span data-stu-id="067ac-103">Specifying a Custom Crypto Algorithm</span></span>

<span data-ttu-id="067ac-104">WCF では、データの暗号化やデジタル署名の計算を行う際に使用するカスタム暗号アルゴリズムを指定できます。</span><span class="sxs-lookup"><span data-stu-id="067ac-104">WCF allows you to specify a custom crypto algorithm to use when encrypting data or computing digital signatures.</span></span> <span data-ttu-id="067ac-105">そのためには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="067ac-105">This is done by the following steps:</span></span>  
  
1. <span data-ttu-id="067ac-106"><xref:System.ServiceModel.Security.SecurityAlgorithmSuite> の派生クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="067ac-106">Derive a class from <xref:System.ServiceModel.Security.SecurityAlgorithmSuite></span></span>  
  
2. <span data-ttu-id="067ac-107">アルゴリズムを登録します。</span><span class="sxs-lookup"><span data-stu-id="067ac-107">Register the algorithm</span></span>  
  
3. <span data-ttu-id="067ac-108"><xref:System.ServiceModel.Security.SecurityAlgorithmSuite> の派生クラスを使用してバインディングを構成します。</span><span class="sxs-lookup"><span data-stu-id="067ac-108">Configure the binding with the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-derived class.</span></span>  
  
## <a name="derive-a-class-from-securityalgorithmsuite"></a><span data-ttu-id="067ac-109">SecurityAlgorithmSuite の派生クラスの作成</span><span class="sxs-lookup"><span data-stu-id="067ac-109">Derive a class from SecurityAlgorithmSuite</span></span>  

 <span data-ttu-id="067ac-110"><xref:System.ServiceModel.Security.SecurityAlgorithmSuite> は、セキュリティ関連のさまざまな操作を実行する際に使用するアルゴリズムを指定できるようにする抽象基本クラスです。</span><span class="sxs-lookup"><span data-stu-id="067ac-110">The <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> is an abstract base class that allows you to specify the algorithm to use when performing various security related operations.</span></span> <span data-ttu-id="067ac-111">たとえば、デジタル署名のハッシュ計算やメッセージの暗号化などの操作です。</span><span class="sxs-lookup"><span data-stu-id="067ac-111">For example, computing a hash for a digital signature or encrypting a message.</span></span> <span data-ttu-id="067ac-112">次のコードは、<xref:System.ServiceModel.Security.SecurityAlgorithmSuite> から派生クラスを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="067ac-112">The following code shows how to derive a class from <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>:</span></span>  
  
```csharp  
public class MyCustomAlgorithmSuite : SecurityAlgorithmSuite  
    {  
        public override string DefaultAsymmetricKeyWrapAlgorithm  
        {  
            get { return SecurityAlgorithms.RsaOaepKeyWrap; }  
        }  
  
        public override string DefaultAsymmetricSignatureAlgorithm  
        {  
            get { return SecurityAlgorithms.RsaSha1Signature; }  
        }  
  
        public override string DefaultCanonicalizationAlgorithm  
        {  
            get { return SecurityAlgorithms.ExclusiveC14n; ; }  
        }  
  
        public override string DefaultDigestAlgorithm  
        {  
            get { return SecurityAlgorithms.MyCustomHashAlgorithm; }  
        }  
  
        public override string DefaultEncryptionAlgorithm  
        {  
            get { return SecurityAlgorithms.Aes128Encryption; }  
        }  
  
        public override int DefaultEncryptionKeyDerivationLength  
        {  
            get { return 128; }  
        }  
  
        public override int DefaultSignatureKeyDerivationLength  
        {  
            get { return 128; }  
        }  
  
        public override int DefaultSymmetricKeyLength  
        {  
            get { return 128; }  
        }  
  
        public override string DefaultSymmetricKeyWrapAlgorithm  
        {  
            get { return SecurityAlgorithms.Aes128Encryption; }  
        }  
  
        public override string DefaultSymmetricSignatureAlgorithm  
        {  
            get { return SecurityAlgorithms.HmacSha1Signature; }  
        }  
  
        public override bool IsAsymmetricKeyLengthSupported(int length)  
        {  
            return length >= 1024 && length <= 4096;  
        }  
  
        public override bool IsSymmetricKeyLengthSupported(int length)  
        {  
            return length >= 128 && length <= 256;  
        }  
    }  
```  
  
## <a name="register-the-custom-algorithm"></a><span data-ttu-id="067ac-113">カスタム アルゴリズムの登録</span><span class="sxs-lookup"><span data-stu-id="067ac-113">Register the Custom Algorithm</span></span>  

 <span data-ttu-id="067ac-114">登録は、構成ファイルまたは命令型コードで行うことができます。</span><span class="sxs-lookup"><span data-stu-id="067ac-114">Registration can be done in a configuration file or in imperative code.</span></span> <span data-ttu-id="067ac-115">カスタム アルゴリズムを登録するには、暗号サービス プロバイダーを実装するクラスとエイリアスの間のマッピングを作成します。</span><span class="sxs-lookup"><span data-stu-id="067ac-115">Registering a custom algorithm is done by creating a mapping between a class that implements a crypto service provider and an alias.</span></span> <span data-ttu-id="067ac-116">その後、WCF サービスのバインディングでアルゴリズムを指定する際に使用する URI にエイリアスをマップします。</span><span class="sxs-lookup"><span data-stu-id="067ac-116">The alias is then mapped to a URI which is used when specifying the algorithm in the WCF service’s binding.</span></span> <span data-ttu-id="067ac-117">次の構成スニペットは、config でカスタム アルゴリズムを登録する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="067ac-117">The following configuration snippet illustrates how to register a custom algorithm in config:</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
           <cryptoClasses>  
              <cryptoClass SHA256CSP="System.Security.Cryptography.SHA256CryptoServiceProvider, System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
           </cryptoClasses>  
           <nameEntry name="http://contoso.com/CustomAlgorithms/CustomHashAlgorithm"  
              class="SHA256CSP" />  
           </cryptoNameMapping>  
        </cryptographySettings>  
    </mscorlib>  
</configuration>  
```  
  
 <span data-ttu-id="067ac-118"><> 要素の下のセクションで、 `cryptoClasses` SHA256CryptoServiceProvider とエイリアス "SHA256CSP" の間のマッピングを作成します。</span><span class="sxs-lookup"><span data-stu-id="067ac-118">The section under the <`cryptoClasses`> element creates the mapping between the SHA256CryptoServiceProvider and the alias "SHA256CSP".</span></span> <span data-ttu-id="067ac-119"><`nameEntry`> 要素は、"SHA256CSP" エイリアスと指定した URL の間のマッピングを作成し `http://contoso.com/CustomAlgorithms/CustomHashAlgorithm` ます。</span><span class="sxs-lookup"><span data-stu-id="067ac-119">The <`nameEntry`> element creates the mapping between the "SHA256CSP" alias and the specified URL `http://contoso.com/CustomAlgorithms/CustomHashAlgorithm`.</span></span>  
  
 <span data-ttu-id="067ac-120">コードでカスタム アルゴリズムを登録するには、<xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="067ac-120">To register the custom algorithm in code use the <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])> method.</span></span> <span data-ttu-id="067ac-121">このメソッドによって、両方のマッピングを作成します。</span><span class="sxs-lookup"><span data-stu-id="067ac-121">This method creates both mappings.</span></span> <span data-ttu-id="067ac-122">次の例は、このメソッドを呼び出す方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="067ac-122">The following example shows how to call this method:</span></span>  
  
```csharp
// Register the custom URI string defined for the hashAlgorithm in MyCustomAlgorithmSuite class to create the
// SHA256CryptoServiceProvider hash algorithm object.  
CryptoConfig.AddAlgorithm(typeof(SHA256CryptoServiceProvider), "http://contoso.com/CustomAlgorithms/CustomHashAlgorithm");  
```  
  
## <a name="configure-the-binding"></a><span data-ttu-id="067ac-123">バインディングの構成</span><span class="sxs-lookup"><span data-stu-id="067ac-123">Configure the Binding</span></span>  

 <span data-ttu-id="067ac-124">バインディングを構成するには、次のコード スニペットに示すように、<xref:System.ServiceModel.Security.SecurityAlgorithmSuite> のカスタム派生クラスをバインディング設定で指定します。</span><span class="sxs-lookup"><span data-stu-id="067ac-124">You configure the binding by specifying the custom <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-derived class in the binding settings as shown in the following code snippet:</span></span>  
  
```csharp  
WSHttpBinding binding = new WSHttpBinding();  
            binding.Security.Message.AlgorithmSuite = new MyCustomAlgorithmSuite();  
```  
  
 <span data-ttu-id="067ac-125">完全なコード例については、「 [WCF セキュリティサンプルでの暗号化の俊敏性](../samples/cryptographic-agility-in-wcf-security.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="067ac-125">For a complete code example, see the [Cryptographic Agility in WCF Security](../samples/cryptographic-agility-in-wcf-security.md) sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="067ac-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="067ac-126">See also</span></span>

- [<span data-ttu-id="067ac-127">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="067ac-127">Securing Services and Clients</span></span>](../feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="067ac-128">サービスのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="067ac-128">Securing Services</span></span>](../securing-services.md)
- [<span data-ttu-id="067ac-129">セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="067ac-129">Security Overview</span></span>](../feature-details/security-overview.md)
- [<span data-ttu-id="067ac-130">セキュリティの概念</span><span class="sxs-lookup"><span data-stu-id="067ac-130">Security Concepts</span></span>](../feature-details/security-concepts.md)
