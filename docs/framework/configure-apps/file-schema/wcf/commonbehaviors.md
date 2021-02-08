---
description: '詳細情報: <commonBehaviors>'
title: <commonBehaviors>
ms.date: 03/30/2017
ms.assetid: 5260aeca-388d-4e82-94c0-124fa8054cf5
ms.openlocfilehash: 2fa7397a2833623728bcca286682178d1cf3e1df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802321"
---
# \<commonBehaviors>

<span data-ttu-id="41aab-102">`commonBehaviors` セクションは、machine.config ファイルでだけ定義できます。</span><span class="sxs-lookup"><span data-stu-id="41aab-102">The `commonBehaviors` section can only be defined in the machine.config file.</span></span> <span data-ttu-id="41aab-103">このセクションは、`endpointBehaviors` と`serviceBehaviors` という 2 つの子コレクションを定義します。</span><span class="sxs-lookup"><span data-stu-id="41aab-103">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="41aab-104">各コレクションは、コンピューター上のすべての WCF エンドポイントとサービスによって使用される動作要素を定義します。</span><span class="sxs-lookup"><span data-stu-id="41aab-104">Each collection defines behavior elements consumed by all WCF endpoints and services on the machine respectively.</span></span> <span data-ttu-id="41aab-105">`endpointBehaviors` で定義される動作はクライアントだけに適用され、`serviceBehaviors` で定義される動作はサービスだけに適用されます。</span><span class="sxs-lookup"><span data-stu-id="41aab-105">Behaviors defined in `endpointBehaviors` are only applied to clients, and behaviors defined in `serviceBehaviors` are only applied to services.</span></span> <span data-ttu-id="41aab-106">ある動作が `commonBehaviors` と `behaviors` の両方のセクションで定義されている場合は、`behaviors` セクション内の動作が優先されます。</span><span class="sxs-lookup"><span data-stu-id="41aab-106">If a behavior is defined in both `commonBehaviors` and `behaviors` sections, the behavior in the `behaviors` section is given preference.</span></span>
