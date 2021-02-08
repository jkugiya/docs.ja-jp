---
description: '詳細情報: Silverlight デバッグ'
title: Silverlight デバッグ
ms.date: 03/30/2017
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 5e903e04-17d0-4014-ac9a-a43330ec8b1c
ms.openlocfilehash: 54a3f7f4b2de867509ff94dafa25c067a78b3ee6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800540"
---
# <a name="silverlight-debugging"></a><span data-ttu-id="e69b0-103">Silverlight デバッグ</span><span class="sxs-lookup"><span data-stu-id="e69b0-103">Silverlight Debugging</span></span>

<span data-ttu-id="e69b0-104">このセクションのトピックでは、Windows オペレーティング システム上または Macintosh プラットフォーム上で動作している Silverlight ベースのアプリケーションのデバッグをサポートするために共通言語ランタイム (CLR: Common Language Runtime) で提供される環境とインターフェイスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="e69b0-104">The topics in this section describe the environment and interfaces that the common language runtime (CLR) provides to support debugging Silverlight-based applications that are running on the Windows operating system, or on the Macintosh platform.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e69b0-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="e69b0-105">In This Section</span></span>  

 [<span data-ttu-id="e69b0-106">EnumerateCLRs 関数</span><span class="sxs-lookup"><span data-stu-id="e69b0-106">EnumerateCLRs Function</span></span>](enumerateclrs-function.md)  
 <span data-ttu-id="e69b0-107">プロセスで CLR を列挙するメカニズムを提供します。</span><span class="sxs-lookup"><span data-stu-id="e69b0-107">Provides a mechanism for enumerating the CLRs in a process.</span></span>  
  
 [<span data-ttu-id="e69b0-108">CloseCLREnumeration 関数</span><span class="sxs-lookup"><span data-stu-id="e69b0-108">CloseCLREnumeration Function</span></span>](closeclrenumeration-function.md)  
 <span data-ttu-id="e69b0-109">[列挙型 Ateclrs 関数](enumerateclrs-function.md)によって返されたハンドルの配列にある有効な CLR 継続スタートアップイベントを閉じ、ハンドルおよび文字列パス配列のメモリを解放します。</span><span class="sxs-lookup"><span data-stu-id="e69b0-109">Closes any valid CLR continue-startup events located in an array of handles returned by the [EnumerateCLRs Function](enumerateclrs-function.md), and frees the memory for the handle and string path arrays.</span></span>  
  
 [<span data-ttu-id="e69b0-110">CreateCoreClrDebugTarget 関数</span><span class="sxs-lookup"><span data-stu-id="e69b0-110">CreateCoreClrDebugTarget Function</span></span>](createcoreclrdebugtarget-function.md)  
 <span data-ttu-id="e69b0-111">プロセスおよびランタイムの列挙のためのリモート ターゲットへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="e69b0-111">Creates a connection to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="e69b0-112">CreateCordbObject 関数</span><span class="sxs-lookup"><span data-stu-id="e69b0-112">CreateCordbObject Function</span></span>](createcordbobject-function.md)  
 <span data-ttu-id="e69b0-113">リモート プロセスでマネージド デバッグ セッションをインスタンス化するための機能を提供するデバッガー インターフェイスを作成します。</span><span class="sxs-lookup"><span data-stu-id="e69b0-113">Creates a debugger interface that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
 [<span data-ttu-id="e69b0-114">CreateVersionStringFromModule 関数</span><span class="sxs-lookup"><span data-stu-id="e69b0-114">CreateVersionStringFromModule Function</span></span>](createversionstringfrommodule-function.md)  
 <span data-ttu-id="e69b0-115">対象プロセス内の CLR パスからバージョン文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="e69b0-115">Creates a version string from a CLR path in a target process.</span></span>  
  
 [<span data-ttu-id="e69b0-116">CreateDebuggingInterfaceFromVersion 関数</span><span class="sxs-lookup"><span data-stu-id="e69b0-116">CreateDebuggingInterfaceFromVersion Function</span></span>](createdebugginginterfacefromversion-function-for-silverlight.md)  
 <span data-ttu-id="e69b0-117">[Createversionstringfrommodule 関数](createversionstringfrommodule-function.md)関数から返された CLR バージョン文字列を受け取り、対応するデバッガーインターフェイスを返します。</span><span class="sxs-lookup"><span data-stu-id="e69b0-117">Accepts a CLR version string returned from [CreateVersionStringFromModule Function](createversionstringfrommodule-function.md)function, and returns a corresponding debugger interface.</span></span>  
  
 [<span data-ttu-id="e69b0-118">CoreClrDebugProcInfo 構造体</span><span class="sxs-lookup"><span data-stu-id="e69b0-118">CoreClrDebugProcInfo Structure</span></span>](coreclrdebugprocinfo-structure.md)  
 <span data-ttu-id="e69b0-119">リモート コンピューターで実行されているプロセスを表します。</span><span class="sxs-lookup"><span data-stu-id="e69b0-119">Represents a process that is running on a remote machine.</span></span>  
  
 [<span data-ttu-id="e69b0-120">CoreClrDebugRuntimeInfo 構造体</span><span class="sxs-lookup"><span data-stu-id="e69b0-120">CoreClrDebugRuntimeInfo Structure</span></span>](coreclrdebugruntimeinfo-structure.md)  
 <span data-ttu-id="e69b0-121">リモート コンピューター上のプロセスに読み込まれる CLR インスタンスを表します。</span><span class="sxs-lookup"><span data-stu-id="e69b0-121">Represents a CLR instance that is loaded in a process on a remote machine.</span></span>  
  
 [<span data-ttu-id="e69b0-122">GetStartupNotificationEvent 関数</span><span class="sxs-lookup"><span data-stu-id="e69b0-122">GetStartupNotificationEvent Function</span></span>](getstartupnotificationevent-function.md)  
 <span data-ttu-id="e69b0-123">指定された対象プロセスに読み込まれている任意の共通言語ランタイム (CLR: Common Language Runtime) によって通知されるイベント ハンドルを作成または開きます。</span><span class="sxs-lookup"><span data-stu-id="e69b0-123">Creates or opens an event handle that will be signaled upon by any common language runtime (CLR) that is loading in the specified target process.</span></span>  
  
 [<span data-ttu-id="e69b0-124">ICoreClrDebugTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e69b0-124">ICoreClrDebugTarget Interface</span></span>](icoreclrdebugtarget-interface.md)  
 <span data-ttu-id="e69b0-125">プロセスおよびランタイムの列挙のためのリモート ターゲットへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="e69b0-125">Creates a connection to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="e69b0-126">InitDbgTransportManager 関数</span><span class="sxs-lookup"><span data-stu-id="e69b0-126">InitDbgTransportManager Function</span></span>](initdbgtransportmanager-function.md)  
 <span data-ttu-id="e69b0-127">プロセスおよびランタイムの列挙のためにリモート ターゲットに接続するよう、トランスポート マネージャーを初期化します。</span><span class="sxs-lookup"><span data-stu-id="e69b0-127">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="e69b0-128">ShutdownDbgTransportManager 関数</span><span class="sxs-lookup"><span data-stu-id="e69b0-128">ShutdownDbgTransportManager Function</span></span>](shutdowndbgtransportmanager-function.md)  
 <span data-ttu-id="e69b0-129">リモート ターゲット コンピューターへの接続のためにトランスポート マネージャーをシャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="e69b0-129">Shuts down the transport manager for a connection to a remote target machine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e69b0-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="e69b0-130">See also</span></span>

- [<span data-ttu-id="e69b0-131">デバッグ コクラス</span><span class="sxs-lookup"><span data-stu-id="e69b0-131">Debugging Coclasses</span></span>](debugging-coclasses.md)
- [<span data-ttu-id="e69b0-132">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="e69b0-132">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="e69b0-133">デバッグ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="e69b0-133">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
- [<span data-ttu-id="e69b0-134">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="e69b0-134">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="e69b0-135">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="e69b0-135">Debugging Structures</span></span>](debugging-structures.md)
