---
description: '詳細については、「方法: .NET Framework 4 で実行されている IIS で .NET Framework 3.5 で記述された WCF サービスをホストする」を参照してください。'
title: '方法: .NET Framework 4 で実行されている IIS 内の .NET Framework 3.5 で作成された WCF サービスをホストする'
ms.date: 03/30/2017
ms.assetid: 9aabc785-068d-4d32-8841-3ef39308d8d6
ms.openlocfilehash: 3ea46b589df293b39369521a133cf9facad97d93
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755968"
---
# <a name="how-to-host-a-wcf-service-written-with-net-framework-35-in-iis-running-under-net-framework-4"></a><span data-ttu-id="f5fc5-103">方法: .NET Framework 4 で実行されている IIS 内の .NET Framework 3.5 で作成された WCF サービスをホストする</span><span class="sxs-lookup"><span data-stu-id="f5fc5-103">How to: Host a WCF Service Written with .NET Framework 3.5 in IIS Running Under .NET Framework 4</span></span>

<span data-ttu-id="f5fc5-104">.NET Framework 4 を実行しているコンピューター上で .NET Framework 3.5 で記述された Windows Communication Foundation (WCF) サービスをホストすると、次のテキストが表示される場合があり <xref:System.ServiceModel.ProtocolException> ます。</span><span class="sxs-lookup"><span data-stu-id="f5fc5-104">When hosting a Windows Communication Foundation (WCF) service written with .NET Framework 3.5 on a machine running .NET Framework 4, you may get a <xref:System.ServiceModel.ProtocolException> with the following text.</span></span>
  
```output  
Unhandled Exception: System.ServiceModel.ProtocolException: The content type text/html; charset=utf-8 of the response message does not match the content type of the binding (application/soap+xml; charset=utf-8). If using a custom encoder, be sure that the IsContentTypeSupported method is implemented properly. The first 1024 bytes of the response were: '<html>    <head>        <title>The application domain or application pool is currently running version 4.0 or later of the .NET Framework. This can occur if IIS settings have been set to 4.0 or later for this Web application, or if you are using version 4.0 or later of the ASP.NET Web Development Server. The <compilation> element in the Web.config file for this Web application does not contain the required 'targetFrameworkMoniker' attribute for this version of the .NET Framework (for example, '<compilation targetFrameworkMoniker=".NETFramework,Version=v4.0">'). Update the Web.config file with this attribute, or configure the Web application to use a different version of the .NET Framework.</title>...  
```  
  
 <span data-ttu-id="f5fc5-105">または、サービスの .svc ファイルを参照する際に、次のテキストのエラー ページが表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="f5fc5-105">Or if you try to browse to the service's .svc file you may see an error page with the following text.</span></span>  
  
```output  
The application domain or application pool is currently running version 4.0 or later of the .NET Framework. This can occur if IIS settings have been set to 4.0 or later for this Web application, or if you are using version 4.0 or later of the ASP.NET Web Development Server. The <compilation> element in the Web.config file for this Web application does not contain the required 'targetFrameworkMoniker' attribute for this version of the .NET Framework (for example, '<compilation targetFrameworkMoniker=".NETFramework,Version=v4.0">'). Update the Web.config file with this attribute, or configure the Web application to use a different version of the .NET Framework.  
```  
  
 <span data-ttu-id="f5fc5-106">このようなエラーが発生するのは、IIS が実行されているアプリケーションドメインが .NET Framework 4 で実行されており、WCF サービスが .NET Framework 3.5 で実行されることを想定しているためです。</span><span class="sxs-lookup"><span data-stu-id="f5fc5-106">These errors occur because the application domain IIS is running within is running .NET Framework 4 and the WCF service is expecting to run under .NET Framework 3.5.</span></span> <span data-ttu-id="f5fc5-107">このトピックでは、このサービスを実行するために必要な変更について説明します。</span><span class="sxs-lookup"><span data-stu-id="f5fc5-107">This topic explains the modifications required to get the service to run.</span></span>
  
 <span data-ttu-id="f5fc5-108">次に、<`compilers`> 要素を検索し、CompilerVersion provider オプションの値を4.0 に変更します。</span><span class="sxs-lookup"><span data-stu-id="f5fc5-108">Next find the <`compilers`> element and change the CompilerVersion provider option to have a value of 4.0.</span></span> <span data-ttu-id="f5fc5-109">既定では、 `compiler` <> 要素の下に2つの <> 要素があり `compilers` ます。</span><span class="sxs-lookup"><span data-stu-id="f5fc5-109">By default, there are two <`compiler`> elements under the <`compilers`> element.</span></span> <span data-ttu-id="f5fc5-110">次の例に示すように、両方の CompilerVersion プロバイダー オプションを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f5fc5-110">You must update the CompilerVersion provider option for both as shown in the following example.</span></span>  
  
```xml  
<system.codedom>  
      <compilers>  
        <compiler language="c#;cs;csharp" extension=".cs" warningLevel="4"  
                  type="Microsoft.CSharp.CSharpCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
          <providerOption name="CompilerVersion" value="v3.5"/>  
          <providerOption name="WarnAsError" value="false"/>  
        </compiler>  
        <compiler language="vb;vbs;visualbasic;vbscript" extension=".vb" warningLevel="4"  
                  type="Microsoft.VisualBasic.VBCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
          <providerOption name="CompilerVersion" value="v3.5"/>  
          <providerOption name="OptionInfer" value="true"/>  
          <providerOption name="WarnAsError" value="false"/>  
        </compiler>  
      </compilers>  
    </system.codedom>  
```  
  
### <a name="add-the-required-targetframework-attribute"></a><span data-ttu-id="f5fc5-111">必要な targetFramework 属性の追加</span><span class="sxs-lookup"><span data-stu-id="f5fc5-111">Add the required targetFramework attribute</span></span>  
  
1. <span data-ttu-id="f5fc5-112">サービスの Web.config ファイルを開き、<`compilation`> 要素を探します。</span><span class="sxs-lookup"><span data-stu-id="f5fc5-112">Open the service's Web.config file and look for the <`compilation`> element.</span></span>  
  
2. <span data-ttu-id="f5fc5-113">次の `targetFramework` 例に示すように、属性を <> 要素に追加し `compilation` ます。</span><span class="sxs-lookup"><span data-stu-id="f5fc5-113">Add the `targetFramework` attribute to the <`compilation`> element as shown in the following example.</span></span>  
  
    ```xml  
    <compilation debug="false"  
            targetFramework="4.0">  
  
            <assemblies>  
              <add assembly="System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
              <add assembly="System.Xml.Linq, Version=3.5.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
              <add assembly="System.Web.Extensions, Version=3.5.0.0, Culture=neutral, PublicKeyToken=31BF3856AD364E35"/>  
              <add assembly="System.Data.DataSetExtensions, Version=3.5.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
            </assemblies>  
  
          </compilation>  
    ```  
  
3. <span data-ttu-id="f5fc5-114"><`compilers`> 要素を検索し、CompilerVersion provider オプションの値を4.0 に変更します。</span><span class="sxs-lookup"><span data-stu-id="f5fc5-114">Find the <`compilers`> element and change the CompilerVersion provider option to have a value of 4.0.</span></span> <span data-ttu-id="f5fc5-115">既定では、 `compiler` <> 要素の下に2つの <> 要素があり `compilers` ます。</span><span class="sxs-lookup"><span data-stu-id="f5fc5-115">By default, there are two <`compiler`> elements under the <`compilers`> element.</span></span> <span data-ttu-id="f5fc5-116">次の例に示すように、両方の CompilerVersion プロバイダー オプションを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f5fc5-116">You must update the CompilerVersion provider option for both as shown in the following example.</span></span>  
  
    ```xml  
    <system.codedom>  
          <compilers>  
            <compiler language="c#;cs;csharp" extension=".cs" warningLevel="4"  
                      type="Microsoft.CSharp.CSharpCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
              <providerOption name="CompilerVersion" value="v3.5"/>  
              <providerOption name="WarnAsError" value="false"/>  
            </compiler>  
            <compiler language="vb;vbs;visualbasic;vbscript" extension=".vb" warningLevel="4"  
                      type="Microsoft.VisualBasic.VBCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
              <providerOption name="CompilerVersion" value="v3.5"/>  
              <providerOption name="OptionInfer" value="true"/>  
              <providerOption name="WarnAsError" value="false"/>  
            </compiler>  
          </compilers>  
        </system.codedom>  
    ```
