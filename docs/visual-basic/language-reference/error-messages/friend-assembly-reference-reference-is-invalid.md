---
description: '詳細情報: BC31535:フレンド アセンブリ参照 <reference> は無効です'
title: フレンド アセンブリ参照 <reference> は無効です
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: e3e08edede9bee4710c415a61592857229ea4f35
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796198"
---
# <a name="bc31535-friend-assembly-reference-reference-is-invalid"></a><span data-ttu-id="84dfe-103">BC31535:フレンド アセンブリ参照 \<reference> は無効です</span><span class="sxs-lookup"><span data-stu-id="84dfe-103">BC31535: Friend assembly reference \<reference> is invalid</span></span>

<span data-ttu-id="84dfe-104">フレンド アセンブリ参照 \<reference> は無効です。</span><span class="sxs-lookup"><span data-stu-id="84dfe-104">Friend assembly reference \<reference> is invalid.</span></span> <span data-ttu-id="84dfe-105">厳密な名前の署名つきアセンブリはその InternalsVisibleTo 宣言内で公開キーを指定しなければなりません。</span><span class="sxs-lookup"><span data-stu-id="84dfe-105">Strong-name signed assemblies must specify a public key in their InternalsVisibleTo declarations.</span></span>

 <span data-ttu-id="84dfe-106"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性コンストラクターに渡されたアセンブリ名は、厳密な名前のアセンブリを識別しますが、`PublicKey` 属性を含みません。</span><span class="sxs-lookup"><span data-stu-id="84dfe-106">The assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor identifies a strong-named assembly, but it does not include a `PublicKey` attribute.</span></span>

 <span data-ttu-id="84dfe-107">**エラー ID:** BC31535</span><span class="sxs-lookup"><span data-stu-id="84dfe-107">**Error ID:** BC31535</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="84dfe-108">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="84dfe-108">To correct this error</span></span>

1. <span data-ttu-id="84dfe-109">厳密な名前のフレンド アセンブリの公開キーを調べます。</span><span class="sxs-lookup"><span data-stu-id="84dfe-109">Determine the public key for the strong-named friend assembly.</span></span> <span data-ttu-id="84dfe-110">`PublicKey` 属性を使用して <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性コンストラクターに渡されるアセンブリ名の一部として、公開キーを含めます。</span><span class="sxs-lookup"><span data-stu-id="84dfe-110">Include the public key as part of the assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor by using the `PublicKey` attribute.</span></span>

## <a name="see-also"></a><span data-ttu-id="84dfe-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="84dfe-111">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- [<span data-ttu-id="84dfe-112">フレンド アセンブリ</span><span class="sxs-lookup"><span data-stu-id="84dfe-112">Friend Assemblies</span></span>](../../../standard/assembly/friend.md)
