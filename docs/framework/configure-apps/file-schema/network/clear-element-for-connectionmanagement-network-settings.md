---
description: '詳細情報: <clear> connectionManagement の要素 (ネットワーク設定)'
title: connectionManagement の <clear> 要素 (ネットワーク設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- <clear> element, connectionManagement
- connectionManagement, clear element
- clear element, connectionManagement
- <connectionManagement>, clear element
ms.assetid: fb259282-84c4-4dc4-a226-78d904a6edc3
ms.openlocfilehash: e6e756e1065e48e79d59e02858963ded70d30f7e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698588"
---
# <a name="clear-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="e9779-103">connectionManagement の \<clear> 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="e9779-103">\<clear> Element for connectionManagement (Network Settings)</span></span>

<span data-ttu-id="e9779-104">接続管理の一覧をクリアします。</span><span class="sxs-lookup"><span data-stu-id="e9779-104">Clears the connection management list.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="e9779-105">構文</span><span class="sxs-lookup"><span data-stu-id="e9779-105">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e9779-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="e9779-106">Attributes and Elements</span></span>  

 <span data-ttu-id="e9779-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="e9779-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e9779-108">属性</span><span class="sxs-lookup"><span data-stu-id="e9779-108">Attributes</span></span>  

 <span data-ttu-id="e9779-109">なし。</span><span class="sxs-lookup"><span data-stu-id="e9779-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e9779-110">子要素</span><span class="sxs-lookup"><span data-stu-id="e9779-110">Child Elements</span></span>  

 <span data-ttu-id="e9779-111">なし。</span><span class="sxs-lookup"><span data-stu-id="e9779-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e9779-112">親要素</span><span class="sxs-lookup"><span data-stu-id="e9779-112">Parent Elements</span></span>  
  
|<span data-ttu-id="e9779-113">**要素**</span><span class="sxs-lookup"><span data-stu-id="e9779-113">**Element**</span></span>|<span data-ttu-id="e9779-114">**説明**</span><span class="sxs-lookup"><span data-stu-id="e9779-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e9779-115">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="e9779-115">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="e9779-116">ネットワーク ホストへの接続の最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="e9779-116">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9779-117">解説</span><span class="sxs-lookup"><span data-stu-id="e9779-117">Remarks</span></span>  

 <span data-ttu-id="e9779-118">要素は、 `clear` 接続管理リストからすべてのエントリを削除します。</span><span class="sxs-lookup"><span data-stu-id="e9779-118">The `clear` element clears all entries from the connection management list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="e9779-119">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="e9779-119">Configuration Files</span></span>  

 <span data-ttu-id="e9779-120">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="e9779-120">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9779-121">例</span><span class="sxs-lookup"><span data-stu-id="e9779-121">Example</span></span>  

 <span data-ttu-id="e9779-122">次の例では、接続管理の一覧をクリアし、サーバー `www.contoso.com` とその他のすべてのネットワークホストの新しい接続管理エントリを追加します。</span><span class="sxs-lookup"><span data-stu-id="e9779-122">The following example clears the connection management list and then adds new connection management entries for the server `www.contoso.com` and all other network hosts.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <clear/>  
      <add address = "http://www.contoso.com" maxconnection = "4" />  
      <add address = "*" maxconnection = "2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e9779-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="e9779-123">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="e9779-124">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="e9779-124">Network Settings Schema</span></span>](index.md)
