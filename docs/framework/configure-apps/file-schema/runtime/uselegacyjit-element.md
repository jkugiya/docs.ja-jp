---
description: '詳細情報: <useLegacyJit> 要素'
title: <useLegacyJit> 要素
ms.date: 04/26/2017
ms.assetid: c2cf97f0-9262-4f1f-a754-5568b51110ad
ms.openlocfilehash: a1449cbc69f0aa1b91cc427fbfc5b984bf605169
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640005"
---
# <a name="uselegacyjit-element"></a><span data-ttu-id="8ae11-103">\<useLegacyJit> 要素</span><span class="sxs-lookup"><span data-stu-id="8ae11-103">\<useLegacyJit> Element</span></span>

<span data-ttu-id="8ae11-104">共通言語ランタイムが Just-In-Time コンパイルの従来の 64 ビット JIT コンパイラを使用するかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="8ae11-104">Determines whether the common language runtime uses the legacy 64-bit JIT compiler for just-in-time compilation.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<useLegacyJit>**  
  
## <a name="syntax"></a><span data-ttu-id="8ae11-105">構文</span><span class="sxs-lookup"><span data-stu-id="8ae11-105">Syntax</span></span>  
  
```xml
<useLegacyJit enabled=0|1 />
```

<span data-ttu-id="8ae11-106">要素名 `useLegacyJit` は大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="8ae11-106">The element name `useLegacyJit` is case-sensitive.</span></span>
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8ae11-107">属性と要素</span><span class="sxs-lookup"><span data-stu-id="8ae11-107">Attributes and elements</span></span>

<span data-ttu-id="8ae11-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="8ae11-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8ae11-109">属性</span><span class="sxs-lookup"><span data-stu-id="8ae11-109">Attributes</span></span>  
  
| <span data-ttu-id="8ae11-110">属性</span><span class="sxs-lookup"><span data-stu-id="8ae11-110">Attribute</span></span> | <span data-ttu-id="8ae11-111">説明</span><span class="sxs-lookup"><span data-stu-id="8ae11-111">Description</span></span>                                                                                   |  
| --------- | --------------------------------------------------------------------------------------------- |  
| `enabled` | <span data-ttu-id="8ae11-112">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="8ae11-112">Required attribute.</span></span><br><br><span data-ttu-id="8ae11-113">ランタイムがレガシ64ビット JIT コンパイラを使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="8ae11-113">Specifies whether the runtime uses the legacy 64-bit JIT compiler.</span></span> |  
  
### <a name="enabled-attribute"></a><span data-ttu-id="8ae11-114">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="8ae11-114">enabled attribute</span></span>  
  
| <span data-ttu-id="8ae11-115">値</span><span class="sxs-lookup"><span data-stu-id="8ae11-115">Value</span></span> | <span data-ttu-id="8ae11-116">説明</span><span class="sxs-lookup"><span data-stu-id="8ae11-116">Description</span></span>                                                                                                         |  
| ----- | ------------------------------------------------------------------------------------------------------------------- |  
| <span data-ttu-id="8ae11-117">0</span><span class="sxs-lookup"><span data-stu-id="8ae11-117">0</span></span>     | <span data-ttu-id="8ae11-118">共通言語ランタイムは、.NET Framework 4.6 以降のバージョンに含まれる新しい64ビット JIT コンパイラを使用します。</span><span class="sxs-lookup"><span data-stu-id="8ae11-118">The common language runtime uses the new 64-bit JIT compiler included in the .NET Framework 4.6 and later versions.</span></span> |  
| <span data-ttu-id="8ae11-119">1</span><span class="sxs-lookup"><span data-stu-id="8ae11-119">1</span></span>     | <span data-ttu-id="8ae11-120">共通言語ランタイムは、古い64ビット JIT コンパイラを使用します。</span><span class="sxs-lookup"><span data-stu-id="8ae11-120">The common language runtime uses the older 64-bit JIT compiler.</span></span>                                                     |  
  
### <a name="child-elements"></a><span data-ttu-id="8ae11-121">子要素</span><span class="sxs-lookup"><span data-stu-id="8ae11-121">Child elements</span></span>

<span data-ttu-id="8ae11-122">なし</span><span class="sxs-lookup"><span data-stu-id="8ae11-122">None</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="8ae11-123">親要素</span><span class="sxs-lookup"><span data-stu-id="8ae11-123">Parent elements</span></span>  
  
| <span data-ttu-id="8ae11-124">要素</span><span class="sxs-lookup"><span data-stu-id="8ae11-124">Element</span></span>         | <span data-ttu-id="8ae11-125">説明</span><span class="sxs-lookup"><span data-stu-id="8ae11-125">Description</span></span>                                                                                                       |  
| --------------- | ----------------------------------------------------------------------------------------------------------------- |  
| `configuration` | <span data-ttu-id="8ae11-126">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="8ae11-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |  
| `runtime`       | <span data-ttu-id="8ae11-127">ランタイム初期化オプションに関する情報を含んでいます。</span><span class="sxs-lookup"><span data-stu-id="8ae11-127">Contains information about runtime initialization options.</span></span>                                                        |  
  
## <a name="remarks"></a><span data-ttu-id="8ae11-128">解説</span><span class="sxs-lookup"><span data-stu-id="8ae11-128">Remarks</span></span>  

<span data-ttu-id="8ae11-129">.NET Framework 4.6 以降、共通言語ランタイムは、Just-in-time (JIT) コンパイルに新しい64ビットコンパイラを既定で使用します。</span><span class="sxs-lookup"><span data-stu-id="8ae11-129">Starting with the .NET Framework 4.6, the common language runtime uses a new 64-bit compiler for Just-In-Time (JIT) compilation by default.</span></span> <span data-ttu-id="8ae11-130">場合によっては、以前のバージョンの64ビット JIT コンパイラによって JIT コンパイルされたアプリケーションコードとの動作が異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="8ae11-130">In some cases, this may result in a difference in behavior from application code that was JIT-compiled by the previous version of the 64-bit JIT compiler.</span></span> <span data-ttu-id="8ae11-131">`enabled`要素の属性をに設定 `<useLegacyJit>` する `1` と、新しい64ビット jit コンパイラを無効にし、代わりに従来の64ビット jit コンパイラを使用してアプリをコンパイルできます。</span><span class="sxs-lookup"><span data-stu-id="8ae11-131">By setting the `enabled` attribute of the `<useLegacyJit>` element to `1`, you can disable the new 64-bit JIT compiler and instead compile your app using the legacy 64-bit JIT compiler.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8ae11-132">要素は、 `<useLegacyJit>` 64 ビットの JIT コンパイルのみに影響します。</span><span class="sxs-lookup"><span data-stu-id="8ae11-132">The `<useLegacyJit>` element affects 64-bit JIT compilation only.</span></span> <span data-ttu-id="8ae11-133">32ビットの JIT コンパイラでのコンパイルは影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="8ae11-133">Compilation with the 32-bit JIT compiler is unaffected.</span></span>  
  
<span data-ttu-id="8ae11-134">構成ファイルの設定を使用する代わりに、次の2つの方法で従来の64ビット JIT コンパイラを有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="8ae11-134">Instead of using a configuration file setting, you can enable the legacy 64-bit JIT compiler in two other ways:</span></span>  
  
- <span data-ttu-id="8ae11-135">環境変数の設定</span><span class="sxs-lookup"><span data-stu-id="8ae11-135">Setting an environment variable</span></span>

  <span data-ttu-id="8ae11-136">`COMPLUS_useLegacyJit`環境変数を、 `0` (新しい64ビット jit コンパイラを使用) または `1` (古い64ビット jit コンパイラを使用) のいずれかに設定します。</span><span class="sxs-lookup"><span data-stu-id="8ae11-136">Set the `COMPLUS_useLegacyJit` environment variable to either `0` (use the new 64-bit JIT compiler) or `1` (use the older 64-bit JIT compiler):</span></span>
  
  ```env  
  COMPLUS_useLegacyJit=0|1  
  ```  
  
  <span data-ttu-id="8ae11-137">環境変数には *グローバルスコープ* があります。これは、コンピューター上で実行されるすべてのアプリケーションに影響を与えることを意味します。</span><span class="sxs-lookup"><span data-stu-id="8ae11-137">The environment variable has *global scope*, which means that it affects all applications run on the machine.</span></span> <span data-ttu-id="8ae11-138">設定されている場合は、アプリケーション構成ファイルの設定によって上書きできます。</span><span class="sxs-lookup"><span data-stu-id="8ae11-138">If set, it can be overridden by the application configuration file setting.</span></span> <span data-ttu-id="8ae11-139">環境変数の名前では大文字と小文字は区別されません。</span><span class="sxs-lookup"><span data-stu-id="8ae11-139">The environment variable name is not case-sensitive.</span></span>
  
- <span data-ttu-id="8ae11-140">レジストリキーの追加</span><span class="sxs-lookup"><span data-stu-id="8ae11-140">Adding a registry key</span></span>

  <span data-ttu-id="8ae11-141">`REG_DWORD` `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` レジストリ内のまたはキーのいずれかに値を追加することで、レガシ64ビット JIT コンパイラを有効にすることができ `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` ます。</span><span class="sxs-lookup"><span data-stu-id="8ae11-141">You can enable the legacy 64-bit JIT compiler by adding a `REG_DWORD` value to either the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` or `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key in the registry.</span></span> <span data-ttu-id="8ae11-142">値にはという名前が付けられ `useLegacyJit` ます。</span><span class="sxs-lookup"><span data-stu-id="8ae11-142">The value is named `useLegacyJit`.</span></span> <span data-ttu-id="8ae11-143">値が0の場合は、新しいコンパイラが使用されます。</span><span class="sxs-lookup"><span data-stu-id="8ae11-143">If the value is 0, the new compiler is used.</span></span> <span data-ttu-id="8ae11-144">値が1の場合、レガシ64ビット JIT コンパイラが有効になります。</span><span class="sxs-lookup"><span data-stu-id="8ae11-144">If the value is 1, the legacy 64-bit JIT compiler is enabled.</span></span> <span data-ttu-id="8ae11-145">レジストリ値の名前では大文字と小文字は区別されません。</span><span class="sxs-lookup"><span data-stu-id="8ae11-145">The registry value name is not case-sensitive.</span></span>
  
  <span data-ttu-id="8ae11-146">キーに値を追加すると `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` 、コンピューター上で実行されているすべてのアプリに影響します。</span><span class="sxs-lookup"><span data-stu-id="8ae11-146">Adding the value to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` key affects all apps running on the machine.</span></span> <span data-ttu-id="8ae11-147">キーに値を追加すると、 `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` 現在のユーザーが実行しているすべてのアプリに影響します。</span><span class="sxs-lookup"><span data-stu-id="8ae11-147">Adding the value to the `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key affects all apps run by the current user.</span></span> <span data-ttu-id="8ae11-148">コンピューターに複数のユーザーアカウントが構成されている場合、その値が他のユーザーのレジストリキーにも追加されない限り、現在のユーザーが実行しているアプリのみが影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="8ae11-148">If a machine is configured with multiple user accounts, only apps run by the current user are affected, unless the value is added to the registry keys for other users as well.</span></span> <span data-ttu-id="8ae11-149">`<useLegacyJit>`構成ファイルに要素を追加すると、レジストリ設定が存在する場合はその設定が上書きされます。</span><span class="sxs-lookup"><span data-stu-id="8ae11-149">Adding the `<useLegacyJit>` element to a configuration file overrides the registry settings, if they're present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ae11-150">例</span><span class="sxs-lookup"><span data-stu-id="8ae11-150">Example</span></span>  

<span data-ttu-id="8ae11-151">次の構成ファイルは、新しい64ビット JIT コンパイラでのコンパイルを無効にし、代わりに従来の64ビット JIT コンパイラを使用します。</span><span class="sxs-lookup"><span data-stu-id="8ae11-151">The following configuration file disables compilation with the new 64-bit JIT compiler and instead uses the legacy 64-bit JIT compiler.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
  <runtime>  
    <useLegacyJit enabled="1" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8ae11-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="8ae11-152">See also</span></span>

- [<span data-ttu-id="8ae11-153">\<runtime> 要素</span><span class="sxs-lookup"><span data-stu-id="8ae11-153">\<runtime> Element</span></span>](runtime-element.md)
- [<span data-ttu-id="8ae11-154">\<configuration> 要素</span><span class="sxs-lookup"><span data-stu-id="8ae11-154">\<configuration> Element</span></span>](../configuration-element.md)
- [<span data-ttu-id="8ae11-155">軽減策:新しい 64 ビット JIT コンパイラ</span><span class="sxs-lookup"><span data-stu-id="8ae11-155">Mitigation: New 64-bit JIT Compiler</span></span>](../../../migration-guide/mitigation-new-64-bit-jit-compiler.md)
