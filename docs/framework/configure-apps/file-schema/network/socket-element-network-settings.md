---
description: '詳細情報: <socket> 要素 (ネットワーク設定)'
title: <socket> 要素 (ネットワーク設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/socket
- http://schemas.microsoft.com/.NetConfiguration/v2.0#socket
helpviewer_keywords:
- <socket> element
- socket element
ms.assetid: 366c634c-7d16-478f-aedf-053eda94a1a0
ms.openlocfilehash: 564d6566bf6f6b1997b986cb6c0d85f841195e55
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740133"
---
# <a name="socket-element-network-settings"></a><span data-ttu-id="be242-103">\<socket> 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="be242-103">\<socket> Element (Network Settings)</span></span>

<span data-ttu-id="be242-104">ソケット操作が完了ポートを使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="be242-104">Specifies whether socket operations use completion ports.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<socket>**

## <a name="syntax"></a><span data-ttu-id="be242-105">構文</span><span class="sxs-lookup"><span data-stu-id="be242-105">Syntax</span></span>  
  
```xml  
<socket  
  alwaysUseCompletionPortsForConnect="true|false"  
  alwaysUseCompletionPortsForAccept="true|false"  
  ipProtectionLevel="EdgeRestricted|Restricted|Unrestricted|Unspecified"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="be242-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="be242-106">Attributes and Elements</span></span>  

 <span data-ttu-id="be242-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="be242-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="be242-108">属性</span><span class="sxs-lookup"><span data-stu-id="be242-108">Attributes</span></span>  
  
|<span data-ttu-id="be242-109">**属性**</span><span class="sxs-lookup"><span data-stu-id="be242-109">**Attribute**</span></span>|<span data-ttu-id="be242-110">**説明**</span><span class="sxs-lookup"><span data-stu-id="be242-110">**Description**</span></span>|  
|-------------------|---------------------|  
|`alwaysUseCompletionPortsForAccept`|<span data-ttu-id="be242-111">Accept メソッド呼び出しに対して、ソケットが常に完了ポートを使用する必要があるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="be242-111">Indicates whether the socket should always use completion ports for Accept method calls.</span></span> <span data-ttu-id="be242-112">既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="be242-112">The default value is `false`.</span></span>|  
|`alwaysUseCompletionPortsForConnect`|<span data-ttu-id="be242-113">接続メソッドの呼び出しで、ソケットが常に完了ポートを使用する必要があるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="be242-113">Indicates whether the socket should always use completion ports for Connect method calls.</span></span> <span data-ttu-id="be242-114">既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="be242-114">The default value is `false`.</span></span>|  
|`ipProtectionLevel`|<span data-ttu-id="be242-115">ソケットに使用する既定のを指定し <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="be242-115">Specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="be242-116">既定値は、Windows のバージョンによって異なります。</span><span class="sxs-lookup"><span data-stu-id="be242-116">The default value depends on the version of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="be242-117">子要素</span><span class="sxs-lookup"><span data-stu-id="be242-117">Child Elements</span></span>  

 <span data-ttu-id="be242-118">なし。</span><span class="sxs-lookup"><span data-stu-id="be242-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="be242-119">親要素</span><span class="sxs-lookup"><span data-stu-id="be242-119">Parent Elements</span></span>  
  
|<span data-ttu-id="be242-120">**要素**</span><span class="sxs-lookup"><span data-stu-id="be242-120">**Element**</span></span>|<span data-ttu-id="be242-121">**説明**</span><span class="sxs-lookup"><span data-stu-id="be242-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="be242-122">設定</span><span class="sxs-lookup"><span data-stu-id="be242-122">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="be242-123"><xref:System.Net> 名前空間の基本的なネットワーク オプションを構成します。</span><span class="sxs-lookup"><span data-stu-id="be242-123">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be242-124">解説</span><span class="sxs-lookup"><span data-stu-id="be242-124">Remarks</span></span>  

 <span data-ttu-id="be242-125">`alwaysUseCompletionPortsForAccept`属性と `alwaysUseCompletionPortsForConnect` 属性は、名前空間のクラスによる完了ポートの使用に関する既定の動作を指定するために使用されます。 <xref:System.Net.Sockets?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="be242-125">The `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes are used to specify the default behavior regarding the use of completion ports by the classes in the <xref:System.Net.Sockets?displayProperty=nameWithType>.namespace.</span></span> <span data-ttu-id="be242-126">ハイパフォーマンスサーバーアプリケーションでは、完了ポートをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="be242-126">Completion ports are recommended for high performance server applications.</span></span>  
  
 <span data-ttu-id="be242-127">`alwaysUseCompletionPortsForAccept`属性と属性の既定値 `alwaysUseCompletionPortsForConnect` は **false** です。</span><span class="sxs-lookup"><span data-stu-id="be242-127">The default value for the `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes is **false**.</span></span>  
  
 <span data-ttu-id="be242-128">は、 <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> 適用可能な `alwaysUseCompletionPortsForAccept` 構成ファイルから属性の現在の値を取得するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="be242-128">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> can be used to get the current value of the `alwaysUseCompletionPortsForAccept` attribute from applicable configuration files.</span></span> <span data-ttu-id="be242-129">は、 <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> 適用可能な `alwaysUseCompletionPortsForConnect` 構成ファイルから属性の現在の値を取得するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="be242-129">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> can be used to get the current value of the `alwaysUseCompletionPortsForConnect` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="be242-130">属性は、 `ipProtectionLevel` ソケットに使用する既定のを指定し <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="be242-130">The `ipProtectionLevel` attribute specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="be242-131"><xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A>プロパティを使用すると、同じリンクローカルまたはサイトローカルプレフィックスを持つアドレスなど、指定されたスコープに IPv6 ソケットの制限を構成できます。</span><span class="sxs-lookup"><span data-stu-id="be242-131">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property enables configuration of a restriction for an IPv6 socket to a specified scope, such as addresses with the same link local or site local prefix.</span></span> <span data-ttu-id="be242-132">このオプションを使用すると、アプリケーションは IPv6 ソケットにアクセス制限を設けることができます。</span><span class="sxs-lookup"><span data-stu-id="be242-132">This option enables applications to place access restrictions on IPv6 sockets.</span></span> <span data-ttu-id="be242-133">この制限により、プライベート LAN で実行されるアプリケーションを外部からの攻撃に対して簡単かつ堅牢に強化できます。</span><span class="sxs-lookup"><span data-stu-id="be242-133">Such restrictions enable an application running on a private LAN to simply and robustly harden itself against external attacks.</span></span> <span data-ttu-id="be242-134">このオプションは、リッスンしているソケットの範囲を拡大または縮小し、必要に応じてパブリックユーザーおよびプライベートユーザーからの無制限のアクセスを有効にするか、必要に応じて同じサイトへのアクセスのみを制限します。</span><span class="sxs-lookup"><span data-stu-id="be242-134">This option widens or narrows the scope of a listening socket, enabling unrestricted access from public and private users when appropriate, or restricting access only to the same site, as required.</span></span>  
  
 <span data-ttu-id="be242-135">この `ipProtectionLevel` 属性設定は、初期の受信トラフィックのみに影響します。</span><span class="sxs-lookup"><span data-stu-id="be242-135">This `ipProtectionLevel` attribute setting affects only initial incoming traffic:</span></span>  
  
- <span data-ttu-id="be242-136">ソケットで着信接続をリッスンしている TCP サーバー。</span><span class="sxs-lookup"><span data-stu-id="be242-136">A TCP server listening for incoming connections on a socket.</span></span>  
  
- <span data-ttu-id="be242-137">ソケットでパケットを受信する UDP アプリケーション。</span><span class="sxs-lookup"><span data-stu-id="be242-137">A UDP application receiving a packet on a socket.</span></span>  
  
 <span data-ttu-id="be242-138">この構成設定は、既に確立されている TCP 接続には影響しません (トラフィックは両方向に制限されません)。また、UDP パケットを送信するアプリケーションには影響しません。</span><span class="sxs-lookup"><span data-stu-id="be242-138">This configuration setting does not affect already established TCP connections (traffic is unrestricted in both directions) and does not affect an application sending UDP packets.</span></span>  
  
 <span data-ttu-id="be242-139">属性の設定に使用できる値は、次のよう `ipProtectionLevel` に、列挙で指定されている定義済みの保護レベルに対応してい <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="be242-139">The possible values for the `ipProtectionLevel` attribute setting correspond with the defined protection levels specified in the <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> enumeration as follows:</span></span>  
  
|<span data-ttu-id="be242-140">**属性の値**</span><span class="sxs-lookup"><span data-stu-id="be242-140">**Attribute Value**</span></span>|<span data-ttu-id="be242-141">**説明**</span><span class="sxs-lookup"><span data-stu-id="be242-141">**Description**</span></span>|  
|-|-|  
|<span data-ttu-id="be242-142">EdgeRestricted</span><span class="sxs-lookup"><span data-stu-id="be242-142">EdgeRestricted</span></span>|<span data-ttu-id="be242-143">IP 保護レベルはエッジ制限付きです。</span><span class="sxs-lookup"><span data-stu-id="be242-143">The IP protection level is edge restricted.</span></span> <span data-ttu-id="be242-144">この値は、インターネット経由で動作するように設計されているアプリケーションによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="be242-144">This value would be used by applications designed to operate across the Internet.</span></span> <span data-ttu-id="be242-145">この設定を使用する場合、Windows Teredo 実装を使用したネットワーク アドレス変換 (NAT: Network Address Translation) トラバーサルは使用できません。</span><span class="sxs-lookup"><span data-stu-id="be242-145">This setting does not allow Network Address Translation (NAT) traversal using the Windows Teredo implementation.</span></span> <span data-ttu-id="be242-146">これらのアプリケーションは、IPv4 のファイアウォールをバイパスすることがあるため、開いているポートを対象としたインターネットからの攻撃に対して堅牢である必要があります。</span><span class="sxs-lookup"><span data-stu-id="be242-146">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="be242-147">Windows Server 2003 と Windows XP では、ソケットの IP 保護レベルの既定値はエッジ制限付きです。</span><span class="sxs-lookup"><span data-stu-id="be242-147">On Windows Server 2003 and Windows XP, the default value for the IP Protection level on a socket is edge restricted.</span></span>|  
|<span data-ttu-id="be242-148">制限付き</span><span class="sxs-lookup"><span data-stu-id="be242-148">Restricted</span></span>|<span data-ttu-id="be242-149">IP 保護レベルは制限付きです。</span><span class="sxs-lookup"><span data-stu-id="be242-149">The IP protection level is restricted.</span></span> <span data-ttu-id="be242-150">この値は、インターネットのシナリオを実装しないイントラネット アプリケーションによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="be242-150">This value would be used by intranet applications that do not implement Internet scenarios.</span></span> <span data-ttu-id="be242-151">これらのアプリケーションは、一般的に、インターネット型の攻撃に対してテストが行われていなかったり堅牢ではなかったりします。</span><span class="sxs-lookup"><span data-stu-id="be242-151">These applications are generally not tested or hardened against Internet-style attacks.</span></span> <span data-ttu-id="be242-152">この設定を使用する場合、受信トラフィックはリンクローカルのみに制限されます。</span><span class="sxs-lookup"><span data-stu-id="be242-152">This setting will limit the received traffic to link-local only.</span></span>|  
|<span data-ttu-id="be242-153">無制限</span><span class="sxs-lookup"><span data-stu-id="be242-153">Unrestricted</span></span>|<span data-ttu-id="be242-154">IP 保護レベルは無制限です。</span><span class="sxs-lookup"><span data-stu-id="be242-154">The IP protection level is unrestricted.</span></span> <span data-ttu-id="be242-155">この値は、Windows に組み込まれている IPv6 NAT Traversal 機能 (たとえば、Teredo) を使用するアプリケーションを含む、インターネット経由で動作するように設計されているアプリケーションによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="be242-155">This value would be used by applications designed to operate across the Internet, including applications taking advantage of IPv6 NAT traversal capabilities built into Windows (Teredo, for example).</span></span> <span data-ttu-id="be242-156">これらのアプリケーションは、IPv4 のファイアウォールをバイパスすることがあるため、開いているポートを対象としたインターネットからの攻撃に対して堅牢である必要があります。</span><span class="sxs-lookup"><span data-stu-id="be242-156">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="be242-157">Windows Server 2008 R2 と Windows Vista では、ソケットの IP 保護レベルの既定値は無制限です。</span><span class="sxs-lookup"><span data-stu-id="be242-157">On Windows Server 2008 R2 and Windows Vista, the default value for the IP Protection level on a socket is unrestricted.</span></span>|  
|<span data-ttu-id="be242-158">指定されていません。</span><span class="sxs-lookup"><span data-stu-id="be242-158">Unspecified</span></span>|<span data-ttu-id="be242-159">IP 保護レベルは未指定です。</span><span class="sxs-lookup"><span data-stu-id="be242-159">The IP protection level is unspecified.</span></span> <span data-ttu-id="be242-160">Windows 7 と Windows Server 2008 R2 では、ソケットの IP 保護レベルの既定値は未指定です。</span><span class="sxs-lookup"><span data-stu-id="be242-160">On Windows 7 and Windows Server 2008 R2, the default value for the IP Protection level on a socket is unspecified.</span></span>|  
  
 <span data-ttu-id="be242-161">属性の既定値 `ipProtectionLevel` は **指定** されていません。</span><span class="sxs-lookup"><span data-stu-id="be242-161">The default value for the `ipProtectionLevel` attribute is **Unspecified**.</span></span>  
  
 <span data-ttu-id="be242-162">プロパティは、 <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> `ipProtectionLevel` 適用可能な構成ファイルから属性の現在の値を取得するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="be242-162">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property can be used to get the current value of the `ipProtectionLevel` attribute from applicable configuration files.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="be242-163">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="be242-163">Configuration Files</span></span>  

 <span data-ttu-id="be242-164">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="be242-164">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="be242-165">例</span><span class="sxs-lookup"><span data-stu-id="be242-165">Example</span></span>  

 <span data-ttu-id="be242-166">次の例では、完了ポートを使用するように指定する方法と、既定値を無制限にすることを指定する方法を示し <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="be242-166">The following example shows how to specify that completion ports should be used and that the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> should be unrestricted.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <socket  
        alwaysUseCompletionPortsForAccept="true"  
        alwaysUseCompletionPortsForConnect="true"  
        ipProtectionLevel="Unrestricted"  
       />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="be242-167">関連項目</span><span class="sxs-lookup"><span data-stu-id="be242-167">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SocketElement?displayProperty=nameWithType>
- <xref:System.Net.Sockets?displayProperty=nameWithType>
- <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType>
- [<span data-ttu-id="be242-168">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="be242-168">Network Settings Schema</span></span>](index.md)
