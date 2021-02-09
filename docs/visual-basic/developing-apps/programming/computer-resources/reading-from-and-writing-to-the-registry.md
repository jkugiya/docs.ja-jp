---
description: '詳細情報: レジストリからの読み取りとレジストリへの書き込み (Visual Basic)'
title: レジストリからの読み取りとレジストリへの書き込み
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.Registry object, tasks
- registry [Visual Basic], writing to
- registry [Visual Basic], reading
ms.assetid: a13da106-185b-41d7-b23c-416da65e21e4
ms.openlocfilehash: 0a9e32480845e617f6e4fde2f31c58eea8da4ee7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701548"
---
# <a name="reading-from-and-writing-to-the-registry-visual-basic"></a><span data-ttu-id="ec13f-103">レジストリからの読み取りとレジストリへの書き込み (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ec13f-103">Reading from and Writing to the Registry (Visual Basic)</span></span>

<span data-ttu-id="ec13f-104">このトピックでは、レジストリに関連するタスクおよび概念説明のトピックについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ec13f-104">This topic describes task and conceptual topics that are associated with the registry.</span></span>  
  
 <span data-ttu-id="ec13f-105">Visual Basic のプログラミングでレジストリにアクセスするときは、Visual Basic で提供されている関数を使用するか、または.NET のレジストリ クラスを使用するかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="ec13f-105">When programming in Visual Basic, you can choose to access the registry by means of either the functions provided by Visual Basic or the registry classes of .NET.</span></span> <span data-ttu-id="ec13f-106">レジストリは、オペレーティング システムからの情報と、コンピューターにホストされるアプリケーションからの情報をホストします。</span><span class="sxs-lookup"><span data-stu-id="ec13f-106">The registry hosts information from the operating system as well as information from applications hosted on the machine.</span></span> <span data-ttu-id="ec13f-107">レジストリを操作すると、システム リソースや保護情報への不適切なアクセスが許可され、セキュリティが損なわれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="ec13f-107">Working with the registry may compromise security by allowing inappropriate access to system resources or protected information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ec13f-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="ec13f-108">In This Section</span></span>  

 [<span data-ttu-id="ec13f-109">方法: レジストリ キーを作成し、その値を設定する</span><span class="sxs-lookup"><span data-stu-id="ec13f-109">How to: Create a Registry Key and Set Its Value</span></span>](how-to-create-a-registry-key-and-set-its-value.md)  
 <span data-ttu-id="ec13f-110">`My.Computer.Registry` オブジェクトの `CreateSubKey` および `SetValue` メソッドを使用して、レジストリ キーを作成し、その値を設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ec13f-110">Describes how to use the `CreateSubKey` and `SetValue` methods of the `My.Computer.Registry` object to create a registry key and set its value.</span></span>  
  
 [<span data-ttu-id="ec13f-111">方法 : レジストリ キーから値を読み取る</span><span class="sxs-lookup"><span data-stu-id="ec13f-111">How to: Read a Value from a Registry Key</span></span>](how-to-read-a-value-from-a-registry-key.md)  
 <span data-ttu-id="ec13f-112">`My.Computer.Registry` オブジェクトの `GetValue` メソッドを使用して、レジストリ キーから値を読み取る方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ec13f-112">Describes how to use the `GetValue` method of the `My.Computer.Registry` object to read a value from a registry key.</span></span>  
  
 [<span data-ttu-id="ec13f-113">方法: レジストリ キーを削除する</span><span class="sxs-lookup"><span data-stu-id="ec13f-113">How to: Delete a Registry Key</span></span>](how-to-delete-a-registry-key.md)  
 <span data-ttu-id="ec13f-114">`My.Computer.Registry.CurrentUser` プロパティの `DeleteSubKey` メソッドを使用して、レジストリ キーを削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ec13f-114">Describes how to use the `DeleteSubKey` method of the `My.Computer.Registry.CurrentUser` property to delete a registry key.</span></span>  
  
 [<span data-ttu-id="ec13f-115">Microsoft.Win32 名前空間を使用したレジストリの読み取りと書き込み</span><span class="sxs-lookup"><span data-stu-id="ec13f-115">Reading from and Writing to the Registry Using the Microsoft.Win32 Namespace</span></span>](reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace.md)  
 <span data-ttu-id="ec13f-116">.NET の `Registry` および `RegistryKey` クラスを使用してレジストリにアクセスする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ec13f-116">Describes how to use the `Registry` and `RegistryKey` classes of .NET to access the registry.</span></span>  
  
 [<span data-ttu-id="ec13f-117">セキュリティとレジストリ</span><span class="sxs-lookup"><span data-stu-id="ec13f-117">Security and the Registry</span></span>](security-and-the-registry.md)  
 <span data-ttu-id="ec13f-118">レジストリに関連するセキュリティの問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="ec13f-118">Discusses security issues involving the registry.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ec13f-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="ec13f-119">Related Sections</span></span>  

 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 <span data-ttu-id="ec13f-120">`My.Computer.Registry` オブジェクトのメンバーをリストして説明します。</span><span class="sxs-lookup"><span data-stu-id="ec13f-120">Lists and explains members of the `My.Computer.Registry` object.</span></span>  
  
 <xref:Microsoft.Win32.Registry>  
 <span data-ttu-id="ec13f-121">`Registry` クラスの概要と、個々のキーおよびメンバーへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="ec13f-121">Presents an overview of the `Registry` class, along with links to individual keys and members.</span></span>
