---
description: '詳細情報: <bindingElementExtensions>'
title: <bindingElementExtensions>
ms.date: 03/30/2017
ms.assetid: bb597fc0-c947-451c-afda-bf23d42f4f4d
ms.openlocfilehash: 4c1b4b924906b1a6dc143588a057129ca5ce8f40
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639420"
---
# \<bindingElementExtensions>

<span data-ttu-id="78483-102">このセクションは、コンピューターまたはアプリケーションの構成ファイルからカスタム バインディング要素を使用できます。</span><span class="sxs-lookup"><span data-stu-id="78483-102">This section enables the use of a custom binding element from a machine or application configuration file.</span></span> <span data-ttu-id="78483-103">このコレクションにカスタム バインド要素を追加するには、`add` キーワードを使用し、要素の `type` 属性をバインド要素拡張に設定して、`name` 属性をカスタム バインド要素に設定します。</span><span class="sxs-lookup"><span data-stu-id="78483-103">You can add a custom binding element to this collection by using the `add` keyword, and setting the `type` attribute of the element to a binding element extension, as well as the `name` attribute to the custom binding element.</span></span>  
  
 <span data-ttu-id="78483-104">バインディングの拡張により、ユーザーは、カスタム バインドの一部として使用するユーザー定義のバインド要素を作成できます。</span><span class="sxs-lookup"><span data-stu-id="78483-104">Binding extensions enable the user to create user-defined binding elements for use as part of custom bindings.</span></span> <span data-ttu-id="78483-105">プログラムではバインディング拡張は、抽象クラス <xref:System.ServiceModel.Channels.BindingElement> を実装する型です。</span><span class="sxs-lookup"><span data-stu-id="78483-105">Programmatically, a binding extension is a type that implements the abstract class <xref:System.ServiceModel.Channels.BindingElement>.</span></span> <span data-ttu-id="78483-106">構成ファイルでは、`bindingElementExtensions` セクションは、拡張要素を定義するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="78483-106">In the configuration file, the `bindingElementExtensions` section is used to define an extension element.</span></span>  
  
 <span data-ttu-id="78483-107">次の例は、`add` 要素と `name` 属性を使用して、構成ファイルの `bindingElementExtensions` セクションにバインディング拡張を追加します。</span><span class="sxs-lookup"><span data-stu-id="78483-107">The following example uses the `add` element, as well as the `name` attribute to add a binding extension to the `bindingElementExtensions` section of the configuration file.</span></span>  
  
```xml  
<system.serviceModel>
  <extensions>
    <bindingElementExtensions>
      <add name="udpTransport"
           type="Microsoft.ServiceModel.Samples.UdpTransportSection, UdpTransport,
                 Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
    </bindingElementExtensions>
  </extensions>
</system.serviceModel>
```  
  
 <span data-ttu-id="78483-108">構成機能を要素に追加するには、ユーザーは `bindingElementExtensionSection` を記述して登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="78483-108">To add configuration abilities to the element, the user needs to write and register a `bindingElementExtensionSection` element.</span></span> <span data-ttu-id="78483-109">詳細については、<xref:System.Configuration> を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78483-109">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="78483-110">要素とその構成の型を定義したら、次の例に示すように拡張をカスタム バインドの一部として使用できます。</span><span class="sxs-lookup"><span data-stu-id="78483-110">After the element and its configuration type are defined, the extension can be used as part of a custom binding as shown in the following example.</span></span>  
  
```xml  
<customBinding>
  <binding name="test2">
    <udpTransport />
    <binaryMessageEncoding maxReadPoolSize="211"
                           maxWritePoolSize="2132"
                           maxSessionSize="3141" />
  </binding>
</customBinding>
```  
  
## <a name="see-also"></a><span data-ttu-id="78483-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="78483-111">See also</span></span>

- <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>
- [<span data-ttu-id="78483-112">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="78483-112">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
