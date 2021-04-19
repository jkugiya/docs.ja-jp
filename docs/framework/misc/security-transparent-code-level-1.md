---
title: 透過的セキュリティ コード、レベル 1
description: レベル 1 の透過性コード モデル、透過性属性、およびセキュリティ透過性の例を確認します。
ms.date: 03/30/2017
helpviewer_keywords:
- transparent
- SecurityTreatAsSafeAttribute
- SecurityTransparentAttribute
- SecurityCriticalAttribute
- security-transparent code
- security [.NET Framework], security-transparent code
ms.assetid: 5fd8f46d-3961-46a7-84af-2eb1f48e75cf
ms.openlocfilehash: 97acccdc1dcab11e42d116f4743e1182029e2dd6
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96288191"
---
# <a name="security-transparent-code-level-1"></a><span data-ttu-id="d5fb5-103">透過的セキュリティ コード、レベル 1</span><span class="sxs-lookup"><span data-stu-id="d5fb5-103">Security-Transparent Code, Level 1</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="d5fb5-104">透過性を使用すると、開発者は、部分的に信頼されるコードに機能を公開する .NET Framework ライブラリのセキュリティを強化できます。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-104">Transparency helps developers write more secure .NET Framework libraries that expose functionality to partially trusted code.</span></span> <span data-ttu-id="d5fb5-105">レベル 1 の透過性は、.NET Framework Version 2.0 で導入され、主に Microsoft 内でのみ使用されていました。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-105">Level 1 transparency was introduced in the .NET Framework version 2.0 and was primarily used only within Microsoft.</span></span> <span data-ttu-id="d5fb5-106">.NET Framework 4 以降では、[レベル 2 の透過性](security-transparent-code-level-2.md)を使用できます。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-106">Starting with the .NET Framework 4, you can use [level 2 transparency](security-transparent-code-level-2.md).</span></span> <span data-ttu-id="d5fb5-107">ただし、以前のセキュリティ規則で実行する必要があるレガシ コードを識別できるように、レベル 1 の透過性も残されています。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-107">However, level 1 transparency has been retained so that you can identify legacy code that must run with the earlier security rules.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d5fb5-108">レベル 1 の透過性は、互換性を確保するためにのみ指定してください。つまり、<xref:System.Security.AllowPartiallyTrustedCallersAttribute> を使用するか、透過性モデルを使用しない、.NET Framework 3.5 以前で開発されたコードに対してのみレベル 1 を指定してください。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-108">You should specify level 1 transparency for compatibility only; that is, specify level 1 only for code that was developed with the .NET Framework 3.5 or earlier that uses the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> or does not use the transparency model.</span></span> <span data-ttu-id="d5fb5-109">たとえば、部分的に信頼された呼び出し元からの呼び出しを許可する .NET Framework 2.0 アセンブリ (APTCA) にはレベル 1 の透過性を使用します。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-109">For example, use level 1 transparency for .NET Framework 2.0 assemblies that allow calls from partially trusted callers (APTCA).</span></span> <span data-ttu-id="d5fb5-110">.NET Framework 4 用に開発されたコードには、常にレベル 2 の透過性を使用します。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-110">For code that is developed for the .NET Framework 4, always use level 2 transparency.</span></span>  
  
 <span data-ttu-id="d5fb5-111">このトピックは、次のセクションで構成されています。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-111">This topic contains the following sections:</span></span>  
  
- [<span data-ttu-id="d5fb5-112">レベル 1 の透過性モデル</span><span class="sxs-lookup"><span data-stu-id="d5fb5-112">The Level 1 Transparency Model</span></span>](#the_level_1_transparency_model)  
  
- [<span data-ttu-id="d5fb5-113">透過性属性</span><span class="sxs-lookup"><span data-stu-id="d5fb5-113">Transparency Attributes</span></span>](#transparency_attributes)  
  
- [<span data-ttu-id="d5fb5-114">透過的セキュリティの例</span><span class="sxs-lookup"><span data-stu-id="d5fb5-114">Security Transparency Examples</span></span>](#security_transparency_examples)  
  
<a name="the_level_1_transparency_model"></a>

## <a name="the-level-1-transparency-model"></a><span data-ttu-id="d5fb5-115">レベル 1 の透過性モデル</span><span class="sxs-lookup"><span data-stu-id="d5fb5-115">The Level 1 Transparency Model</span></span>  

 <span data-ttu-id="d5fb5-116">レベル 1 の透過性を使用するときは、セキュリティ透過的、セキュリティ セーフ クリティカル、およびセキュリティ クリティカルの各方式にコードを分離するセキュリティ モデルを使用します。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-116">When you use Level 1 transparency, you are using a security model that separates code into security-transparent, security-safe-critical, and security-critical methods.</span></span>  
  
 <span data-ttu-id="d5fb5-117">アセンブリ全体、アセンブリ内の一部のクラス、またはクラス内の一部のメソッドを、セキュリティ透過的なコードとしてマークできます。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-117">You can mark a whole assembly, some classes in an assembly, or some methods in a class as security-transparent.</span></span> <span data-ttu-id="d5fb5-118">セキュリティ透過的なコードは特権を昇格することはできません。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-118">Security-transparent code cannot elevate privileges.</span></span> <span data-ttu-id="d5fb5-119">この制限により、次の 3 つの効果が生まれます。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-119">This restriction has three consequences:</span></span>  
  
- <span data-ttu-id="d5fb5-120">セキュリティ透過的なコードは、<xref:System.Security.Permissions.SecurityAction.Assert> アクションを実行できません。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-120">Security-transparent code cannot perform <xref:System.Security.Permissions.SecurityAction.Assert> actions.</span></span>  
  
- <span data-ttu-id="d5fb5-121">セキュリティ透過的なコードによって満たされるリンク確認要求は、フル アクセス要求になります。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-121">Any link demand that would be satisfied by security-transparent code becomes a full demand.</span></span>  
  
- <span data-ttu-id="d5fb5-122">セキュリティ透過的なコードで実行される必要のある安全でない (検証できない) コードは、<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> セキュリティ アクセス許可に対するフル アクセス要求を発生させます。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-122">Any unsafe (unverifiable) code that must execute in security-transparent code causes a full demand for the <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> security permission.</span></span>  
  
 <span data-ttu-id="d5fb5-123">これらの規則は、共通言語ランタイム (CLR: Common Language Runtime) による実行中に適用されます。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-123">These rules are enforced during execution by the common language runtime (CLR).</span></span> <span data-ttu-id="d5fb5-124">セキュリティ透過的なコードは、呼び出すコードのすべてのセキュリティ要件を、呼び出し元に返します。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-124">Security-transparent code passes all the security requirements of the code it calls back to its callers.</span></span> <span data-ttu-id="d5fb5-125">セキュリティ透過的なコードを流れる確認要求では、特権を昇格できません。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-125">Demands that flow through the security-transparent code cannot elevate privileges.</span></span> <span data-ttu-id="d5fb5-126">信頼性の低いアプリケーションによってセキュリティ透過的なコードが呼び出され、高い特権の確認要求が発生した場合、その確認要求は信頼性の低いコードに戻されて失敗します。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-126">If a low-trust application calls security-transparent code and causes a demand for high privilege, the demand will flow back to the low-trust code and fail.</span></span> <span data-ttu-id="d5fb5-127">セキュリティ透過的なコードはアサート アクションを実行できないので、確認要求を停止できません。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-127">The security-transparent code cannot stop the demand because it cannot perform assert actions.</span></span> <span data-ttu-id="d5fb5-128">同じセキュリティ透過的なコードが、完全に信頼されているコードから呼び出された場合、確認要求は成功します。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-128">The same security-transparent code called from full-trust code results in a successful demand.</span></span>  
  
 <span data-ttu-id="d5fb5-129">セキュリティ クリティカルは、セキュリティ透過的の反対です。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-129">Security-critical is the opposite of security-transparent.</span></span> <span data-ttu-id="d5fb5-130">セキュリティ クリティカルなコードは完全に信頼して実行され、特権が必要な操作をすべて実行できます。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-130">Security-critical code executes with full trust and can perform all privileged operations.</span></span> <span data-ttu-id="d5fb5-131">セキュリティ セーフ クリティカルなコードは、広範なセキュリティ監査を経た特権コードであり、部分的に信頼された呼び出し元がアクセスを許可されていないリソースを使用するのを許可しないことが確認されています。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-131">Security-safe-critical code is privileged code that has been through an extensive security audit to confirm that it does not allow partially trusted callers to use resources they do not have permission to access.</span></span>  
  
 <span data-ttu-id="d5fb5-132">透過性の適用は明示的に実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-132">You have to apply transparency explicitly.</span></span> <span data-ttu-id="d5fb5-133">通常、データ操作とロジックを処理するコードの大部分はセキュリティ透過的なコードとしてマークでき、特権の昇格を実行する少数のコードをセキュリティ クリティカルまたはセキュリティ セーフ クリティカルなコードとしてマークします。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-133">The majority of your code that handles data manipulation and logic can typically be marked as security-transparent, whereas the lesser amount of code that performs elevations of privileges is marked as security-critical or security-safe-critical.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d5fb5-134">レベル 1 の透過性は、アセンブリ スコープに限定されます。アセンブリ間には適用されません。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-134">Level 1 transparency is limited to assembly scope; it is not enforced between assemblies.</span></span> <span data-ttu-id="d5fb5-135">レベル 1 の透過性は、主に Microsoft 内でセキュリティ監査を目的として使用されていました。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-135">Level 1 transparency was primarily used within Microsoft for security audit purposes.</span></span> <span data-ttu-id="d5fb5-136">レベル 1 アセンブリ内のセキュリティ クリティカルな型およびメンバーには、他のアセンブリのセキュリティ透過的なコードからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-136">Security-critical types and members within a level 1 assembly can be accessed by security-transparent code in other assemblies.</span></span> <span data-ttu-id="d5fb5-137">重要なのは、すべてのレベル 1 のセキュリティ クリティカルな型およびメンバーで、完全な信頼のためにリンク確認要求を実行することです。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-137">It is important that you perform link demands for full trust in all your level 1 security-critical types and members.</span></span> <span data-ttu-id="d5fb5-138">また、セキュリティ セーフ クリティカルな型およびメンバーでも、それらの型またはメンバーがアクセスする保護リソースに対するアクセス許可を呼び出し元が有していることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-138">Security-safe-critical types and members must also confirm that callers have permissions for protected resources that are accessed by the type or member.</span></span>  
  
 <span data-ttu-id="d5fb5-139">以前のバージョンの .NET Framework との下位互換性を維持するため、透過性属性の注釈が付けられていないメンバーはすべてセキュリティ セーフ クリティカルと見なされます。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-139">For backward compatibility with earlier versions of the .NET Framework, all members that are not annotated with transparency attributes are considered to be security-safe-critical.</span></span> <span data-ttu-id="d5fb5-140">注釈が付けられていない型はすべて透過的と見なされます。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-140">All types that are not annotated are considered to be transparent.</span></span> <span data-ttu-id="d5fb5-141">透過性を検証するためのスタティック分析規則はありません。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-141">There are no static analysis rules to validate transparency.</span></span> <span data-ttu-id="d5fb5-142">したがって、透過性エラーを実行時にデバッグすることが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-142">Therefore, you may need to debug transparency errors at run time.</span></span>  
  
<a name="transparency_attributes"></a>

## <a name="transparency-attributes"></a><span data-ttu-id="d5fb5-143">透過性属性</span><span class="sxs-lookup"><span data-stu-id="d5fb5-143">Transparency Attributes</span></span>  

 <span data-ttu-id="d5fb5-144">コードの透過性を指定するために使用する 3 つの属性の説明を、次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-144">The following table describes the three attributes that you use to annotate your code for transparency.</span></span>  
  
|<span data-ttu-id="d5fb5-145">属性</span><span class="sxs-lookup"><span data-stu-id="d5fb5-145">Attribute</span></span>|<span data-ttu-id="d5fb5-146">説明</span><span class="sxs-lookup"><span data-stu-id="d5fb5-146">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.Security.SecurityTransparentAttribute>|<span data-ttu-id="d5fb5-147">アセンブリ レベルでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-147">Allowed only at the assembly level.</span></span> <span data-ttu-id="d5fb5-148">アセンブリ内のすべての型とメンバーをセキュリティ透過的として指定します。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-148">Identifies all types and members in the assembly as security-transparent.</span></span> <span data-ttu-id="d5fb5-149">このアセンブリにセキュリティ クリティカルなコードを含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-149">The assembly cannot contain any security-critical code.</span></span>|  
|<xref:System.Security.SecurityCriticalAttribute>|<span data-ttu-id="d5fb5-150"><xref:System.Security.SecurityCriticalAttribute.Scope%2A> プロパティを設定せずにアセンブリ レベルで使用すると、アセンブリ内のすべてのコードは既定でセキュリティ透過的と指定されますが、アセンブリはセキュリティ クリティカルなコードを含むこともできると指定されます。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-150">When used at the assembly level without the <xref:System.Security.SecurityCriticalAttribute.Scope%2A> property, identifies all code in the assembly as security-transparent by default, but indicates that the assembly may contain security-critical code.</span></span><br /><br /> <span data-ttu-id="d5fb5-151">クラス レベルで使用すると、クラスまたはメソッドはセキュリティ クリティカルになりますが、クラスのメンバーはセキュリティ クリティカルになりません。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-151">When used at the class level, identifies the class or method as security-critical, but not the members of the class.</span></span> <span data-ttu-id="d5fb5-152">すべてのメンバーをセキュリティ クリティカルにするには、<xref:System.Security.SecurityCriticalAttribute.Scope%2A> プロパティを <xref:System.Security.SecurityCriticalScope.Everything> に設定します。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-152">To make all the members security-critical, set the <xref:System.Security.SecurityCriticalAttribute.Scope%2A> property to <xref:System.Security.SecurityCriticalScope.Everything>.</span></span><br /><br /> <span data-ttu-id="d5fb5-153">メンバー レベルで使用した場合、この属性はそのメンバーのみに適用されます。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-153">When used at the member level, the attribute applies only to that member.</span></span><br /><br /> <span data-ttu-id="d5fb5-154">セキュリティ クリティカルなクラスまたはメンバーは、特権の昇格を実行できます。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-154">The class or member identified as security-critical can perform elevations of privilege.</span></span> <span data-ttu-id="d5fb5-155">**重要:** レベル 1 の透過性では、セキュリティ クリティカルな型およびメンバーは、アセンブリの外部から呼び出された場合に、セキュリティ セーフ クリティカルとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-155">**Important:**  In level 1 transparency, security-critical types and members are treated as security-safe-critical when they are called from outside the assembly.</span></span> <span data-ttu-id="d5fb5-156">承認のない特権の昇格を防ぐために、セキュリティ クリティカルな型およびメンバーを完全な信頼のためのリンク確認要求で保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-156">You should protect security-critical types and members with a link demand for full trust to avoid unauthorized elevation of privilege.</span></span>|  
|<xref:System.Security.SecuritySafeCriticalAttribute>|<span data-ttu-id="d5fb5-157">アセンブリ内のセキュリティ透過的なコードからアクセスできるセキュリティ クリティカルなコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-157">Identifies security-critical code that can be accessed by security-transparent code in the assembly.</span></span> <span data-ttu-id="d5fb5-158">この属性を指定しない場合、セキュリティ透過的なコードは、同じアセンブリ内のプライベートまたは内部のセキュリティ クリティカルなメンバーにアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-158">Otherwise, security-transparent code cannot access private or internal security-critical members in the same assembly.</span></span> <span data-ttu-id="d5fb5-159">この属性を指定した場合、セキュリティ クリティカルなコードに影響が出て、予期しない特権の引き上げが可能になります。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-159">Doing so would influence security-critical code and make unexpected elevations of privilege possible.</span></span> <span data-ttu-id="d5fb5-160">セキュリティ セーフ クリティカルなコードについては、厳しいセキュリティ監査を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-160">Security-safe-critical code should undergo a rigorous security audit.</span></span> <span data-ttu-id="d5fb5-161">**注:** セキュリティ セーフ クリティカルな型およびメンバーでは、呼び出し元のアクセス許可を確認して、保護リソースにアクセスする権限が呼び出し元にあるかどうかを判断する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-161">**Note:**  Security-safe-critical types and members must validate the permissions of callers to determine whether the caller has authority to access protected resources.</span></span>|  
  
 <span data-ttu-id="d5fb5-162"><xref:System.Security.SecuritySafeCriticalAttribute> 属性を使用すると、セキュリティ透過的なコードが、同じアセンブリ内のセキュリティ クリティカルなメンバーにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-162">The <xref:System.Security.SecuritySafeCriticalAttribute> attribute enables security-transparent code to access security-critical members in the same assembly.</span></span> <span data-ttu-id="d5fb5-163">1 つのアセンブリに含まれるセキュリティ透過的なコードとセキュリティ クリティカルなコードは、2 つのアセンブリに分離されていると見なせます。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-163">Consider the security-transparent and security-critical code in your assembly as separated into two assemblies.</span></span> <span data-ttu-id="d5fb5-164">セキュリティ透過的なコードは、セキュリティ クリティカルなコードのプライベートまたは内部のメンバーを参照できません。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-164">The security-transparent code would not be able to see the private or internal members of the security-critical code.</span></span> <span data-ttu-id="d5fb5-165">さらに、セキュリティ クリティカルなコードは、通常、そのコードのパブリック インターフェイスへのアクセスについて監査を受けます。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-165">Additionally, the security-critical code is generally audited for access to its public interface.</span></span> <span data-ttu-id="d5fb5-166">プライベートまたは内部の状態にアセンブリの外部からアクセスすることはできず、状態は分離されていると想定できます。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-166">You would not expect a private or internal state to be accessible outside the assembly; you would want to keep the state isolated.</span></span> <span data-ttu-id="d5fb5-167"><xref:System.Security.SecuritySafeCriticalAttribute> 属性を使用すると、透過的セキュリティ コードとセキュリティ クリティカルなコードの間で状態の分離を維持しながら、必要なときには分離をオーバーライドできるようになります。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-167">The <xref:System.Security.SecuritySafeCriticalAttribute> attribute maintains the isolation of state between security-transparent and security-critical code while providing the ability to override the isolation when it is necessary.</span></span> <span data-ttu-id="d5fb5-168">セキュリティ クリティカルなコードのプライベートまたは内部のメンバーが <xref:System.Security.SecuritySafeCriticalAttribute> でマークされていない場合、セキュリティ透過的なコードはそのコードにアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-168">Security-transparent code cannot access private or internal security-critical code unless those members have been marked with <xref:System.Security.SecuritySafeCriticalAttribute>.</span></span> <span data-ttu-id="d5fb5-169"><xref:System.Security.SecuritySafeCriticalAttribute> を適用する場合は、事前に、パブリックに公開された場合と同じようにしてメンバーを監査してください。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-169">Before applying the <xref:System.Security.SecuritySafeCriticalAttribute>, audit that member as if it were publicly exposed.</span></span>  
  
### <a name="assembly-wide-annotation"></a><span data-ttu-id="d5fb5-170">アセンブリ全体の注釈</span><span class="sxs-lookup"><span data-stu-id="d5fb5-170">Assembly-wide Annotation</span></span>  

 <span data-ttu-id="d5fb5-171">アセンブリ レベルでセキュリティ属性を使用することの効果について次の表で説明します。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-171">The following table describes the effects of using security attributes at the assembly level.</span></span>  
  
|<span data-ttu-id="d5fb5-172">Assembly 属性</span><span class="sxs-lookup"><span data-stu-id="d5fb5-172">Assembly attribute</span></span>|<span data-ttu-id="d5fb5-173">アセンブリの状態</span><span class="sxs-lookup"><span data-stu-id="d5fb5-173">Assembly state</span></span>|  
|------------------------|--------------------|  
|<span data-ttu-id="d5fb5-174">部分的に信頼されたアセンブリで属性なし</span><span class="sxs-lookup"><span data-stu-id="d5fb5-174">No attribute on a partially trusted assembly</span></span>|<span data-ttu-id="d5fb5-175">すべての型およびメンバーは透過的です。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-175">All types and members are transparent.</span></span>|  
|<span data-ttu-id="d5fb5-176">完全に信頼されたアセンブリ (グローバル アセンブリ キャッシュに存在または `AppDomain` で完全な信頼として指定) で属性なし。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-176">No attribute on a fully trusted assembly (in the global assembly cache or identified as full trust in the `AppDomain`)</span></span>|<span data-ttu-id="d5fb5-177">すべての型は透過的であり、すべてのメンバーはセキュリティ セーフ クリティカルです。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-177">All types are transparent and all members are security-safe-critical.</span></span>|  
|`SecurityTransparent`|<span data-ttu-id="d5fb5-178">すべての型およびメンバーは透過的です。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-178">All types and members are transparent.</span></span>|  
|`SecurityCritical(SecurityCriticalScope.Everything)`|<span data-ttu-id="d5fb5-179">すべての型およびメンバーはセキュリティ クリティカルです。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-179">All types and members are security-critical.</span></span>|  
|`SecurityCritical`|<span data-ttu-id="d5fb5-180">すべてのコードは既定で透過的になります。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-180">All code defaults to transparent.</span></span> <span data-ttu-id="d5fb5-181">ただし、個々の型やメンバーに他の属性を設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-181">However, individual types and members can have other attributes.</span></span>|  
  
<a name="security_transparency_examples"></a>

## <a name="security-transparency-examples"></a><span data-ttu-id="d5fb5-182">透過的セキュリティの例</span><span class="sxs-lookup"><span data-stu-id="d5fb5-182">Security Transparency Examples</span></span>  

 <span data-ttu-id="d5fb5-183">.NET Framework 2.0 の透過性規則 (レベル 1 の透過性) を使用するには、次のアセンブリ注釈を使用します。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-183">To use the .NET Framework 2.0 transparency rules (level 1 transparency), use the following assembly annotation:</span></span>  
  
```csharp
[assembly: SecurityRules(SecurityRuleSet.Level1)]  
```  
  
 <span data-ttu-id="d5fb5-184">アセンブリ全体を透過的にして、アセンブリがクリティカルなコードを含まず、どのような方法でも特権を昇格しないことを示す必要がある場合は、次の属性を使用して、アセンブリに透過性を明示的に追加できます。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-184">If you want to make a whole assembly transparent to indicate that the assembly does not contain any critical code and does not elevate privileges in any way, you can explicitly add transparency to the assembly with the following attribute:</span></span>  
  
```csharp  
[assembly: SecurityTransparent]  
```  
  
 <span data-ttu-id="d5fb5-185">同じアセンブリの中にクリティカルなコードと透過的なコードを混在させる場合は、次に示すように、最初に <xref:System.Security.SecurityCriticalAttribute> 属性をアセンブリにマークして、アセンブリがクリティカルなコードを含むことができることを示します。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-185">If you want to mix critical and transparent code in the same assembly, start by marking the assembly with the <xref:System.Security.SecurityCriticalAttribute> attribute to indicate that the assembly can contain critical code, as follows:</span></span>  
  
```csharp  
[assembly: SecurityCritical]  
```  
  
 <span data-ttu-id="d5fb5-186">セキュリティ クリティカルな操作を実行する場合は、次のコード例で示すように、別の <xref:System.Security.SecurityCriticalAttribute> 属性を使用して、クリティカルな操作を実行するコードを明示的にマークする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-186">If you want to perform security-critical actions, you must explicitly mark the code that will perform the critical action with another <xref:System.Security.SecurityCriticalAttribute> attribute, as shown in the following code example:</span></span>  
  
```csharp  
[assembly: SecurityCritical]  
public class A  
{  
    [SecurityCritical]  
    private void Critical()  
    {  
        // critical  
    }  
  
    public int SomeProperty  
    {  
        get {/* transparent */ }  
        set {/* transparent */ }  
    }  
}  
public class B  
{
    internal string SomeOtherProperty  
    {  
        get { /* transparent */ }  
        set { /* transparent */ }  
    }  
}  
```  
  
 <span data-ttu-id="d5fb5-187">上記のコードは、`Critical` メソッドを明示的にセキュリティ クリティカルとしてマークしている以外は、透過的です。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-187">The previous code is transparent except for the `Critical` method, which is explicitly marked as security-critical.</span></span> <span data-ttu-id="d5fb5-188">アセンブリ レベルで <xref:System.Security.SecurityCriticalAttribute> 属性が指定されていても、既定の設定は透過的です。</span><span class="sxs-lookup"><span data-stu-id="d5fb5-188">Transparency is the default setting, even with the assembly-level <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5fb5-189">関連項目</span><span class="sxs-lookup"><span data-stu-id="d5fb5-189">See also</span></span>

- [<span data-ttu-id="d5fb5-190">透過的セキュリティ コード、レベル 2</span><span class="sxs-lookup"><span data-stu-id="d5fb5-190">Security-Transparent Code, Level 2</span></span>](security-transparent-code-level-2.md)
- [<span data-ttu-id="d5fb5-191">セキュリティの変更</span><span class="sxs-lookup"><span data-stu-id="d5fb5-191">Security Changes</span></span>](/previous-versions/dotnet/framework/security/security-changes)
