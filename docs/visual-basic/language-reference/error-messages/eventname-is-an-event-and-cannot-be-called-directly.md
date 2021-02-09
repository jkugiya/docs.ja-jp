---
description: "詳細情報: BC32022: '<eventname>' はイベントであるため、直接呼び出すことはできません"
title: "'<eventname>' はイベントであるため、直接呼び出すことはできません。"
ms.date: 07/20/2015
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords:
- BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
ms.openlocfilehash: f9d4b8fe54e1101e7963933f871cf5af2c1af903
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796445"
---
# <a name="bc32022-eventname-is-an-event-and-cannot-be-called-directly"></a><span data-ttu-id="ab70a-103">BC32022: '\<eventname>' はイベントであるため、直接呼び出すことはできません</span><span class="sxs-lookup"><span data-stu-id="ab70a-103">BC32022: '\<eventname>' is an event, and cannot be called directly</span></span>

<span data-ttu-id="ab70a-104">'<`eventname`>' はイベントであるため、直接呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="ab70a-104">'<`eventname`>' is an event, and so cannot be called directly.</span></span> <span data-ttu-id="ab70a-105">`RaiseEvent` ステートメントを使用して、イベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="ab70a-105">Use a `RaiseEvent` statement to raise an event.</span></span>

 <span data-ttu-id="ab70a-106">プロシージャ呼び出しは、プロシージャ名のイベントを指定します。</span><span class="sxs-lookup"><span data-stu-id="ab70a-106">A procedure call specifies an event for the procedure name.</span></span> <span data-ttu-id="ab70a-107">イベント ハンドラーはプロシージャですが、イベント自体はシグナル通知デバイスであり、これを発生させて処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ab70a-107">An event handler is a procedure, but the event itself is a signaling device, which must be raised and handled.</span></span>

 <span data-ttu-id="ab70a-108">**エラー ID:** BC32022</span><span class="sxs-lookup"><span data-stu-id="ab70a-108">**Error ID:** BC32022</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="ab70a-109">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="ab70a-109">To correct this error</span></span>

- <span data-ttu-id="ab70a-110">`RaiseEvent` ステートメントを使用して、イベントを通知し、それを処理するプロシージャを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="ab70a-110">Use a `RaiseEvent` statement to signal an event and invoke the procedure or procedures that handle it.</span></span>

## <a name="see-also"></a><span data-ttu-id="ab70a-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="ab70a-111">See also</span></span>

- [<span data-ttu-id="ab70a-112">RaiseEvent ステートメント</span><span class="sxs-lookup"><span data-stu-id="ab70a-112">RaiseEvent Statement</span></span>](../statements/raiseevent-statement.md)
