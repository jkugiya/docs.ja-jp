---
description: 詳細については、クライアントでのデバッグに関するページを参照してください。
title: クライアントでのデバッグ
ms.date: 03/30/2017
ms.assetid: 56f9ad05-ea1b-4ef6-85f2-890f7ed71567
ms.openlocfilehash: 45eb76b30eb7243f961ba9764e48d25b6c9dbb35
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99759459"
---
# <a name="debugging-on-the-client"></a><span data-ttu-id="add38-103">クライアントでのデバッグ</span><span class="sxs-lookup"><span data-stu-id="add38-103">Debugging on the Client</span></span>

<span data-ttu-id="add38-104">ユーザーが WCF サービスのクライアントアプリケーションを簡単に作成できるようにするには、サービス [\<serviceDebug>](../../../configure-apps/file-schema/wcf/servicedebug.md) の構成ファイルにサービスの動作を追加します。</span><span class="sxs-lookup"><span data-stu-id="add38-104">To make it easier for users to write client applications for your WCF service, you can add the [\<serviceDebug>](../../../configure-apps/file-schema/wcf/servicedebug.md) service behavior to the configuration file of your service.</span></span> <span data-ttu-id="add38-105">この動作は、ヘルプ ページを公開し、クライアントに返される SOAP エラーの詳細にマネージド例外情報を表示するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="add38-105">This behavior can be used to publish help pages, and return managed exception information in the details of SOAP faults returned to the client.</span></span>
