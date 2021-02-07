---
description: MSMQ の詳細情報
title: MSMQ
ms.date: 03/30/2017
ms.assetid: d9fca29f-fa44-4ec4-bb48-b10800694500
ms.openlocfilehash: 3d694fdab202cd2b3b03c377f72d93c22cbae263
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99720580"
---
# <a name="msmq"></a><span data-ttu-id="1f060-103">MSMQ</span><span class="sxs-lookup"><span data-stu-id="1f060-103">MSMQ</span></span>

<span data-ttu-id="1f060-104">MSMQ アプリケーションでは、キューに置かれたチャネルから MSMQに、および MSMQ からキューに置かれたチャネルに追加アクティビティは転送されません。</span><span class="sxs-lookup"><span data-stu-id="1f060-104">In an MSMQ application, no additional activity is transferred from the queued channel to MSMQ and from MSMQ to the queued channel.</span></span>  
  
 <span data-ttu-id="1f060-105">さらに、MSMQ メッセージ ID と SOAP メッセージ ID (および、存在する場合はアクティビティ ID) は、キューに置かれたチャネルのトレースの一部として送信操作を追跡されます。</span><span class="sxs-lookup"><span data-stu-id="1f060-105">In addition, MSMQ Message ID and SOAP message ID (along with Activity ID, if one exists) are traced as part of queued channel traces on a Send operation.</span></span>  
  
 <span data-ttu-id="1f060-106">MSMQ メッセージ ID と SOAP メッセージ ID (および、存在する場合はアクティビティ ID) は、キューに置かれたチャネルのトレースの一部として受信操作を追跡されます。</span><span class="sxs-lookup"><span data-stu-id="1f060-106">MSMQ Message ID and SOAP message ID (along with activity ID, if one exists) are traced as part of queued channel traces on a Receive operation.</span></span>  
  
 <span data-ttu-id="1f060-107">受信操作で必要な転送については、他のトランスポートと同様に実行されます (受信バイト->プロセス メッセージ-> 操作)。</span><span class="sxs-lookup"><span data-stu-id="1f060-107">The required transfers on the Receive operation are executed similarly to any other transport (receive bytes->Process message-> operation).</span></span>
