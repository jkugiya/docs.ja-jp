---
title: メッセージ キュー (MSMQ) のインストール
description: 1 回限りのセットアップ手順の一部として、WFC サンプルで使用するメッセージ キュー 4.0 とメッセージ キュー 3.0 をインストールする方法について説明します。
ms.date: 03/30/2017
ms.assetid: 7ddcd497-3e04-427e-bc04-3610ad98b01e
ms.openlocfilehash: bf33a5cd899bf2d7ef4947c51ac1723c8eb80c29
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96281873"
---
# <a name="installing-message-queuing-msmq"></a><span data-ttu-id="070a4-103">メッセージ キュー (MSMQ) のインストール</span><span class="sxs-lookup"><span data-stu-id="070a4-103">Installing Message Queuing (MSMQ)</span></span>

<span data-ttu-id="070a4-104">メッセージ キュー 4.0 およびメッセージ キュー 3.0 をインストールする方法を次の手順に示します。</span><span class="sxs-lookup"><span data-stu-id="070a4-104">The following procedures show how to install Message Queuing 4.0 and Message Queuing 3.0.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="070a4-105">Windows XP および Windows Server 2003 では、メッセージ キュー 4.0 は使用できません。</span><span class="sxs-lookup"><span data-stu-id="070a4-105">Message Queuing 4.0 is not available in Windows XP and Windows Server 2003.</span></span>  
  
#### <a name="to-install-message-queuing-40-on-windows-server-2008-or-windows-server-2008-r2"></a><span data-ttu-id="070a4-106">Windows Server 2008 または Windows Server 2008 R2 にメッセージ キュー 4.0 をインストールするには</span><span class="sxs-lookup"><span data-stu-id="070a4-106">To install Message Queuing 4.0 on Windows Server 2008 or Windows Server 2008 R2</span></span>  
  
1. <span data-ttu-id="070a4-107">サーバー マネージャーで **[機能]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="070a4-107">In Server Manager, click **Features**.</span></span>  
  
2. <span data-ttu-id="070a4-108">**[機能の概要]** の右側のペインで、 **[機能の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="070a4-108">In the right-hand pane under **Features Summary**, click **Add Features**.</span></span>  
  
3. <span data-ttu-id="070a4-109">表示されたウィンドウで **[メッセージ キュー]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="070a4-109">In the resulting window, expand **Message Queuing**.</span></span>  
  
4. <span data-ttu-id="070a4-110">**[メッセージ キュー サービス]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="070a4-110">Expand **Message Queuing Services**.</span></span>  
  
5. <span data-ttu-id="070a4-111">**[ディレクトリ サービス統合]** をクリックし (ドメインに参加するコンピューターの場合)、 **[HTTP サポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="070a4-111">Click **Directory Services Integration** (for computers joined to a Domain), then click **HTTP Support**.</span></span>  
  
6. <span data-ttu-id="070a4-112">**[次へ]** をクリックし、 **[インストール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="070a4-112">Click **Next**,then click **Install**.</span></span>  
  
#### <a name="to-install-message-queuing-40-on-windows-7-or-windows-vista"></a><span data-ttu-id="070a4-113">Windows 7 または Windows Vista にメッセージ キュー 4.0 をインストールするには</span><span class="sxs-lookup"><span data-stu-id="070a4-113">To install Message Queuing 4.0 on Windows 7 or Windows Vista</span></span>  
  
1. <span data-ttu-id="070a4-114">**[コントロール パネル]** を開きます。</span><span class="sxs-lookup"><span data-stu-id="070a4-114">Open **Control Panel**.</span></span>  
  
2. <span data-ttu-id="070a4-115">**[プログラム]** をクリックし、 **[プログラムと機能]** の **[Windows の機能の有効化または無効化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="070a4-115">Click **Programs** and then, under **Programs and Features**, click **Turn Windows Features on and off**.</span></span>  
  
3. <span data-ttu-id="070a4-116">[Microsoft Message Queue (MSMQ) Server]、[Microsoft Message Queue (MSMQ) Server Core] の順に展開して、インストールする次のメッセージ キュー機能のチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="070a4-116">Expand Microsoft Message Queue (MSMQ) Server, expand Microsoft Message Queue (MSMQ) Server Core, and then select the check boxes for the following Message Queuing features to install:</span></span>  
  
    - <span data-ttu-id="070a4-117">[MSMQ Active Directory Domain Services Integration] (ドメインに参加するコンピューターの場合)</span><span class="sxs-lookup"><span data-stu-id="070a4-117">MSMQ Active Directory Domain Services Integration (for computers joined to a Domain).</span></span>  
  
    - <span data-ttu-id="070a4-118">[MSMQ HTTP サポート]</span><span class="sxs-lookup"><span data-stu-id="070a4-118">MSMQ HTTP Support.</span></span>  
  
4. <span data-ttu-id="070a4-119">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="070a4-119">Click **OK**.</span></span>  
  
5. <span data-ttu-id="070a4-120">コンピューターを再起動するよう求められた場合は、 **[OK]** をクリックしてインストールを完了します。</span><span class="sxs-lookup"><span data-stu-id="070a4-120">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
#### <a name="to-install-message-queuing-30-on-windows-xp-and-windows-server-2003"></a><span data-ttu-id="070a4-121">Windows XP および Windows Server 2003 にメッセージ キュー 3.0 をインストールするには</span><span class="sxs-lookup"><span data-stu-id="070a4-121">To install Message Queuing 3.0 on Windows XP and Windows Server 2003</span></span>  
  
1. <span data-ttu-id="070a4-122">**[コントロール パネル]** を開きます。</span><span class="sxs-lookup"><span data-stu-id="070a4-122">Open **Control Panel**.</span></span>  
  
2. <span data-ttu-id="070a4-123">**[プログラムの追加と削除]** 、 **[Windows コンポーネントの追加と削除]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="070a4-123">Click **Add Remove Programs** and then click **Add Windows Components**.</span></span>  
  
3. <span data-ttu-id="070a4-124">メッセージ キューを選択し、 **[詳細]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="070a4-124">Select Message Queuing and click **Details**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="070a4-125">Windows Server 2003 を実行している場合は、メッセージ キューにアクセスするアプリケーション サーバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="070a4-125">If you are running Windows Server 2003, select Application Server to access Message Queuing.</span></span>  
  
4. <span data-ttu-id="070a4-126">詳細ページで、[MSMQ HTTP サポート] オプションが選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="070a4-126">Ensure that the option MSMQ HTTP Support is selected on the details page.</span></span>  
  
5. <span data-ttu-id="070a4-127">**[OK]** をクリックして詳細ページを閉じ、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="070a4-127">Click **OK** to exit the details page, and then click **Next**.</span></span> <span data-ttu-id="070a4-128">インストールを完了します。</span><span class="sxs-lookup"><span data-stu-id="070a4-128">Complete the installation.</span></span>  
  
6. <span data-ttu-id="070a4-129">コンピューターを再起動するよう求められた場合は、 **[OK]** をクリックしてインストールを完了します。</span><span class="sxs-lookup"><span data-stu-id="070a4-129">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="070a4-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="070a4-130">See also</span></span>

- [<span data-ttu-id="070a4-131">セットアップ手順</span><span class="sxs-lookup"><span data-stu-id="070a4-131">Set-Up Instructions</span></span>](set-up-instructions.md)
