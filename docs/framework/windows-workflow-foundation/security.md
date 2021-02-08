---
description: '詳細情報: セキュリティ'
title: セキュリティ
ms.date: 03/30/2017
ms.assetid: 737ec121-bfc5-4b75-a504-2d53c2c8af39
ms.openlocfilehash: 8f095292deac77c1c72cf87a93064569f7dab982
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798096"
---
# <a name="security"></a><span data-ttu-id="2ff4e-103">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="2ff4e-103">Security</span></span>

<span data-ttu-id="2ff4e-104">SQL Workflow Instance Store は、次のデータベース セキュリティ ロールを使用して、永続性データベースのインスタンス状態情報へのアクセスをセキュリティ保護します。</span><span class="sxs-lookup"><span data-stu-id="2ff4e-104">The SQL Workflow Instance Store uses the following database security roles to secure access to instance state information in the persistence database.</span></span>  
  
- <span data-ttu-id="2ff4e-105">**System.activities.durableinstancing.instances を処理** します。</span><span class="sxs-lookup"><span data-stu-id="2ff4e-105">**System.Activities.DurableInstancing.InstanceStoreUsers**.</span></span> <span data-ttu-id="2ff4e-106">このロールには、パブリック ビューへの読み取りおよび書き込みのアクセス権と、インスタンスの作成、読み込み、保存に関連するストアド プロシージャへの実行権限があります。</span><span class="sxs-lookup"><span data-stu-id="2ff4e-106">This role has read and write access to public views and execution rights to stored procedures that are involved in creating, loading and saving instances.</span></span>  
  
- <span data-ttu-id="2ff4e-107">**System.activities.durableinstancing.instances. InstanceStoreObservers**。</span><span class="sxs-lookup"><span data-stu-id="2ff4e-107">**System.Activities.DurableInstancing.InstanceStoreObservers**.</span></span> <span data-ttu-id="2ff4e-108">このロールには、パブリック ビューへの読み取り専用アクセス権があります。</span><span class="sxs-lookup"><span data-stu-id="2ff4e-108">This role has read-only access to public views.</span></span>  
  
- <span data-ttu-id="2ff4e-109">**System.activities.durableinstancing.instances. WorkflowActivationUsers**.</span><span class="sxs-lookup"><span data-stu-id="2ff4e-109">**System.Activities.DurableInstancing.WorkflowActivationUsers**.</span></span> <span data-ttu-id="2ff4e-110">このロールには、インスタンスのアクティベーション プロセスにかかわるストアド プロシージャへの実行権限があります。</span><span class="sxs-lookup"><span data-stu-id="2ff4e-110">This role has execution rights to stored procedures that are involved in the instance activation process.</span></span> <span data-ttu-id="2ff4e-111">インスタンスのアクティブ化の詳細については、「 [インスタンスのアクティブ化](instance-activation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ff4e-111">For more information about instance activation, see [Instance Activation](instance-activation.md).</span></span> <span data-ttu-id="2ff4e-112">汎用ホスト (Windows Server AppFabric のホスト機能のワークフロー管理サービスなど) を実行するユーザーアカウントは、このデータベースロールに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2ff4e-112">The user account under which a generic host (such as the Workflow Management Service of the hosting features of Windows Server AppFabric) runs should be added to this database role.</span></span>  
  
 <span data-ttu-id="2ff4e-113">Windows Server App Fabric での永続化ストアのセキュリティの詳細については、「 [App fabric の永続ストアのセキュリティ構成](/previous-versions/appfabric/ff431727(v=azure.10))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ff4e-113">For more information about security for persistence stores with Windows Server App Fabric, see [Security Configuration for Persistence Stores in App Fabric](/previous-versions/appfabric/ff431727(v=azure.10))</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="2ff4e-114">インスタンス ストア内にある固有のインスタンス データへのアクセス権を持つクライアントは、同じインスタンス ストア内にあるその他すべてのインスタンスにもアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="2ff4e-114">A client that has access to its own instance data in the instance store has access to all other instances in the same instance store.</span></span> <span data-ttu-id="2ff4e-115">インスタンス ストアでは、インスタンス レベルでセキュリティ アクセス許可を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="2ff4e-115">The instance store does not support specifying security permissions at the instance level.</span></span> <span data-ttu-id="2ff4e-116">個別のインスタンス ストアを作成し、ストアごとに、各グループやユーザーのアクセス権を設定します。</span><span class="sxs-lookup"><span data-stu-id="2ff4e-116">You should create separate instance stores and map different groups/users to have access to different stores.</span></span>
