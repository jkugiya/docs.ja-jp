---
description: '詳細情報: <bindingExtensions>'
title: <bindingExtensions>
ms.date: 03/30/2017
ms.assetid: 8373f94d-d095-486f-8f1e-4ac2f72b58c7
ms.openlocfilehash: e568c7dd2da509709e5c85d3181d1808b1c636df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639407"
---
# \<bindingExtensions>

<span data-ttu-id="d1eed-102">このセクションは、コンピューターまたはアプリケーションの構成ファイルからユーザー定義のバインディングを使用できます。</span><span class="sxs-lookup"><span data-stu-id="d1eed-102">This section enables the use of a user defined binding from a machine or application configuration file.</span></span> <span data-ttu-id="d1eed-103">このコレクションにユーザー定義のバインディングを追加するには、`add` キーワードを使用し、要素の `type` 属性をユーザー定義のバインディングに設定して、`name` 属性をユーザー定義のバインディングの名前に設定します。</span><span class="sxs-lookup"><span data-stu-id="d1eed-103">You can add a user defined binding to this collection by using the `add` keyword, and setting the `type` attribute of the element to a user defined binding, as well as the `name` attribute to the name of the user defined binding.</span></span>

<span data-ttu-id="d1eed-104">バインディングの拡張により、ユーザーは、エンドポイント構成の一部として使用するユーザー定義のバインディングを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d1eed-104">Binding extensions enable the user to create user-defined bindings for use as part an endpoint configuration.</span></span> <span data-ttu-id="d1eed-105">プログラムではバインディング拡張は、抽象クラス <xref:System.ServiceModel.Channels.Binding> を実装する型です。</span><span class="sxs-lookup"><span data-stu-id="d1eed-105">Programmatically, a binding extension is a type that implements the abstract class <xref:System.ServiceModel.Channels.Binding>.</span></span>

<span data-ttu-id="d1eed-106">次の例では、要素と属性を使用して、 `add` `name` 構成ファイルのセクションにバインド拡張機能を追加し `bindingExtensions` ます。</span><span class="sxs-lookup"><span data-stu-id="d1eed-106">The following example uses the `add` element, as well as the `name` attribute to add a binding extension to the `bindingExtensions` section of the configuration file:</span></span>

```xml
<system.serviceModel>
  <extensions>
    <bindingExtensions>
      <add name="MyBinding"
           type="Microsoft.ServiceModel.Samples.MyBinding, MyBinding,
                 Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
    </bindingExtensions>
  </extensions>
</system.serviceModel>
```

<span data-ttu-id="d1eed-107">構成機能を要素に追加するには、ユーザーは `bindingSection` を記述して登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1eed-107">To add configuration abilities to the element, the user needs to write and register a `bindingSection` element.</span></span> <span data-ttu-id="d1eed-108">詳細については、<xref:System.Configuration> を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1eed-108">For more information on this, see the <xref:System.Configuration> documentation.</span></span>

<span data-ttu-id="d1eed-109">要素とその構成の種類を定義した後、次の例に示すように、エンドポイントの一部として拡張機能を使用できます。</span><span class="sxs-lookup"><span data-stu-id="d1eed-109">After the element and its configuration type are defined, the extension can be used as part of an endpoint as shown in the following example:</span></span>

```xml
<services>
  <service name="MyService">
    <endpoint address="myAddress"
              binding="MyBinding" />
  </service>
</services>
```

## <a name="see-also"></a><span data-ttu-id="d1eed-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="d1eed-110">See also</span></span>

- [<span data-ttu-id="d1eed-111">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="d1eed-111">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
