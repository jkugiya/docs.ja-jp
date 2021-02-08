---
description: '詳細情報: Net.tcp ポート共有サービスの構成'
title: Net.TCP ポート共有サービスを構成する
ms.date: 03/30/2017
ms.assetid: b6dd81fa-68b7-4e1b-868e-88e5901b7ea0
ms.openlocfilehash: 9e6a09c1dd986bc96a9d518d25226dd211b3e6ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780701"
---
# <a name="configuring-the-nettcp-port-sharing-service"></a><span data-ttu-id="695fc-103">Net.TCP ポート共有サービスを構成する</span><span class="sxs-lookup"><span data-stu-id="695fc-103">Configuring the Net.TCP Port Sharing Service</span></span>

<span data-ttu-id="695fc-104">Net.TCP トランスポートを使用する自己ホスト型サービスは、`ListenBacklog` や `MaxPendingAccepts` など、いくつかの高度な設定を制御できます。これらは、ネットワーク通信で使用される、ベースである TCP ソケットの動作をコンロトールします。</span><span class="sxs-lookup"><span data-stu-id="695fc-104">Self-hosted services that use the Net.TCP transport can control several advanced settings, such as `ListenBacklog` and `MaxPendingAccepts`, which govern the behavior of the underlying TCP socket used for network communication.</span></span> <span data-ttu-id="695fc-105">ただし、各ソケットに対するこれらの設定は、トランスポート バインディングでポート共有が無効化されている場合 (既定では有効) に、バインディング レベルでのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="695fc-105">However, these settings for each socket only apply at the binding level if the transport binding has disabled port sharing, which is enabled by default.</span></span>  
  
 <span data-ttu-id="695fc-106">net.tcp バインディングは、(トランスポート バインド要素で `portSharingEnabled =true` を設定することで) ポート共有が有効化されている場合、外部プロセス (Net.TCP ポート共有サービスをホストする SMSvcHost.exe) に対し、自身の代わりに TCP ソケットを管理することを暗黙的に許可しています。</span><span class="sxs-lookup"><span data-stu-id="695fc-106">When a net.tcp binding enables port sharing (by setting `portSharingEnabled =true` on the transport binding element), it implicitly allows an external process (namely the SMSvcHost.exe, which hosts the Net.TCP Port Sharing Service) to manage the TCP socket on its behalf.</span></span> <span data-ttu-id="695fc-107">たとえば、TCP を使用している場合は次のように指定します。</span><span class="sxs-lookup"><span data-stu-id="695fc-107">For example, when using TCP, specify:</span></span>  
  
```xml  
<tcpTransport portSharingEnabled="true"  />  
```  
  
 <span data-ttu-id="695fc-108">この方法で設定すると、サービスのトランスポート バインド要素に指定したソケット設定は無視され、SMSvcHost.exe で指定されたソケット設定が採用されます。</span><span class="sxs-lookup"><span data-stu-id="695fc-108">When configured in this way, any socket settings specified on the service's transport binding element are ignored in favor of the socket settings specified by SMSvcHost.exe.</span></span>  
  
 <span data-ttu-id="695fc-109">SMSvcHost.exe を構成するには、SmSvcHost.exe.config という XML 構成ファイルを作成し、SMSvcHost.exe 実行可能ファイルと同じ物理ディレクトリ (たとえば、C:\Windows\Microsoft.NET\Framework\v4.5) に配置します。</span><span class="sxs-lookup"><span data-stu-id="695fc-109">To configure the SMSvcHost.exe, create an XML configuration file named SmSvcHost.exe.config and place it in the same physical directory as the SMSvcHost.exe executable (for example, C:\Windows\Microsoft.NET\Framework\v4.5).</span></span>  
  
 <span data-ttu-id="695fc-110">次の例では、すべての構成可能値の既定値を明示的に指定した SMSvcHost.exe.config のサンプルを示します。</span><span class="sxs-lookup"><span data-stu-id="695fc-110">The following example illustrates a sample SMSvcHost.exe.config, with the default settings for all configurable values stated explicitly.</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <net.tcp listenBacklog="16" <!-- 16 * # of processors -->  
          maxPendingAccepts="4"<!-- 4 * # of processors -->  
          maxPendingConnections="100"  
          receiveTimeout="00:00:30" <!-- 30 seconds -->  
          teredoEnabled="false">  
          <allowAccounts>  
             <!-- LocalSystem account -->  
             <add securityIdentifier="S-1-5-18"/>  
             <!-- LocalService account -->  
             <add securityIdentifier="S-1-5-19"/>  
             <!-- Administrators account -->  
             <add securityIdentifier="S-1-5-20"/>  
             <!-- Network Service account -->  
             <add securityIdentifier="S-1-5-32-544" />  
             <!-- IIS_IUSRS account (Vista only) -->  
             <add securityIdentifier="S-1-5-32-568"/>  
           </allowAccounts>  
       </net.tcp>  
    </system.serviceModel.activation>
</configuration>  
```  
  
## <a name="when-to-modify-smsvchostexeconfig"></a><span data-ttu-id="695fc-111">SMSvcHost.exe.config を変更する場合</span><span class="sxs-lookup"><span data-stu-id="695fc-111">When to Modify SMSvcHost.exe.config</span></span>  

 <span data-ttu-id="695fc-112">一般的に、SMSvcHost.exe.config ファイルの内容を変更する際には、このファイルに指定するすべての構成設定は、Net.TCP ポート共有サービスを使用するコンピューターのすべてのサービスに影響するため、注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="695fc-112">In general, care should be taken when modifying the contents of the SMSvcHost.exe.config file, because any configuration settings specified in this file affect all of the services on a computer that uses the Net.TCP Port Sharing Service.</span></span> <span data-ttu-id="695fc-113">これには、windows プロセスアクティブ化サービス (WAS) の TCP アクティブ化機能を使用する Windows Vista のアプリケーションが含まれます。</span><span class="sxs-lookup"><span data-stu-id="695fc-113">This includes applications on Windows Vista that use the TCP Activation features of the Windows Process Activation Service (WAS).</span></span>  
  
 <span data-ttu-id="695fc-114">ただし、Net.TCP ポート共有サービスの既定の構成を変更する必要のある状況もあります。</span><span class="sxs-lookup"><span data-stu-id="695fc-114">However, sometimes you may need to change the default configuration for the Net.TCP Port Sharing Service.</span></span> <span data-ttu-id="695fc-115">たとえば、`maxPendingAccepts` の既定値は 4 \* プロセッサ数です。</span><span class="sxs-lookup"><span data-stu-id="695fc-115">For example, the default value for `maxPendingAccepts` is 4 \* number of processors.</span></span> <span data-ttu-id="695fc-116">ポート共有を使用する多数のサービスをホストするサーバーでは、この値を大きくして、最大のスループットを実現することができます。</span><span class="sxs-lookup"><span data-stu-id="695fc-116">Servers that host a large number of services that use port sharing may increase this value to achieve maximum throughput.</span></span> <span data-ttu-id="695fc-117">`maxPendingConnections` の既定値は 100 です。</span><span class="sxs-lookup"><span data-stu-id="695fc-117">The default value for `maxPendingConnections` is 100.</span></span> <span data-ttu-id="695fc-118">サービスを呼び出すクライアントが同時に複数存在し、サービスがクライアント接続を切断する場合も、この値を大きくすることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="695fc-118">You should consider increasing this value also if there are multiple concurrent clients calling the service and the service is dropping client connections.</span></span>  
  
 <span data-ttu-id="695fc-119">SMSvcHost.exe.config には、ポート共有サービスを使用する可能性のあるプロセス ID に関する情報も含まれています。</span><span class="sxs-lookup"><span data-stu-id="695fc-119">SMSvcHost.exe.config also contains information about the process identities that may make use of the port sharing service.</span></span> <span data-ttu-id="695fc-120">プロセスが、共有 TCP ポートを使用するためにポート共有サービスに接続すると、そのプロセスのプロセス ID が、ポート共有サービスの使用が許可されている ID のリストに照合されます。</span><span class="sxs-lookup"><span data-stu-id="695fc-120">When a process connects to the port sharing service to make use of a shared TCP port, the process identity of the connecting process is checked against a list of identities that are permitted to make use of the port sharing service.</span></span> <span data-ttu-id="695fc-121">これらの id は \<allowAccounts> 、SMSvcHost.exe.config ファイルのセクションでセキュリティ識別子 (sid) として指定されます。</span><span class="sxs-lookup"><span data-stu-id="695fc-121">These identities are specified as security identifiers (SIDs) in the \<allowAccounts> section of the SMSvcHost.exe.config file.</span></span> <span data-ttu-id="695fc-122">既定では、ポート共有サービスへのアクセス許可は、システム アカウント (LocalService、LocalSystem、NetworkService) や管理者グループのメンバーに与えられます。</span><span class="sxs-lookup"><span data-stu-id="695fc-122">By default, permission to use the port sharing service is granted to system accounts (LocalService, LocalSystem, and NetworkService) as well as members of the Administrators group.</span></span> <span data-ttu-id="695fc-123">ポート共有サービスに接続するために別の ID (ユーザー ID など) でプロセスが実行されることを許可しているアプリケーションでは、適切な SID を SMSvcHost.exe.config に明示的に追加する必要があります (これらの変更は SMSvc.exe プロセスが再起動されるまで適用されません)。</span><span class="sxs-lookup"><span data-stu-id="695fc-123">Applications that allow a process running as another identity (for example, a user identity) to connect to the port sharing service must explicitly add the appropriate SID to the SMSvcHost.exe.config (these changes are not applied until the SMSvc.exe process is restarted).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="695fc-124">ユーザーアカウント制御 (UAC) が有効になっている Windows Vista システムでは、ローカルユーザーのアカウントが Administrators グループのメンバーであっても、昇格されたアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="695fc-124">On Windows Vista systems with User Account Control (UAC) enabled, local users require elevated permissions even if their account is a member of the Administrators group.</span></span> <span data-ttu-id="695fc-125">これらのユーザーが昇格せずにポート共有サービスを使用できるようにするには、ユーザーの SID (または、ユーザーがメンバーであるグループの SID) を SMSvcHost.exe.config のセクションに明示的に追加する必要があり \<allowAccounts> ます。</span><span class="sxs-lookup"><span data-stu-id="695fc-125">To allow these users to make use of the port sharing service without elevation, the user's SID (or the SID of a group in which the user is a member) must be explicitly added to the \<allowAccounts> section of SMSvcHost.exe.config.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="695fc-126">既定の SMSvcHost.exe.config ファイルは、カスタムの `etwProviderId` を指定することによって、SMSvcHost.exe のトレースの影響がサービス トレースに及ぶのを防ぎます。</span><span class="sxs-lookup"><span data-stu-id="695fc-126">The default SMSvcHost.exe.config file specifies a custom `etwProviderId` to prevent SMSvcHost.exe tracing from interfering with service traces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="695fc-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="695fc-127">See also</span></span>

- [\<net.tcp>](../../configure-apps/file-schema/wcf/net-tcp.md)
