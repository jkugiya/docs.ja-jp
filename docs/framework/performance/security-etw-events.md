---
title: セキュリティ ETW イベント
description: .NET での厳密な名前の検証と Authenticode の検証中に発生するセキュリティ ETW イベントについて説明します。
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
ms.openlocfilehash: 4402bf5690a53ce518077268a3e20a95aeb14e8a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272515"
---
# <a name="security-etw-events"></a><span data-ttu-id="05c39-103">セキュリティ ETW イベント</span><span class="sxs-lookup"><span data-stu-id="05c39-103">Security ETW Events</span></span>

<span data-ttu-id="05c39-104">セキュリティ イベントは、厳密な名前の検証時と Authenticode の検証時に発生します。</span><span class="sxs-lookup"><span data-stu-id="05c39-104">Security events are raised during strong name verification and Authenticode verification.</span></span>  

## <a name="strongnameverificationstart_v1-and-strongnameverificationstop_v1-events"></a><span data-ttu-id="05c39-105">StrongNameVerificationStart_V1 イベントと StrongNameVerificationStop_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="05c39-105">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  

 <span data-ttu-id="05c39-106">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="05c39-106">The following table shows the keyword and level.</span></span> <span data-ttu-id="05c39-107">(詳細については、「 [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="05c39-107">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="05c39-108">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="05c39-108">Keyword for raising the event</span></span>|<span data-ttu-id="05c39-109">レベル</span><span class="sxs-lookup"><span data-stu-id="05c39-109">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="05c39-110">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="05c39-110">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="05c39-111">情報通知 (4)</span><span class="sxs-lookup"><span data-stu-id="05c39-111">Informational(4)</span></span>|  
  
 <span data-ttu-id="05c39-112">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="05c39-112">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="05c39-113">イベント</span><span class="sxs-lookup"><span data-stu-id="05c39-113">Event</span></span>|<span data-ttu-id="05c39-114">イベント ID</span><span class="sxs-lookup"><span data-stu-id="05c39-114">Event ID</span></span>|<span data-ttu-id="05c39-115">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="05c39-115">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="05c39-116">181</span><span class="sxs-lookup"><span data-stu-id="05c39-116">181</span></span>|<span data-ttu-id="05c39-117">厳密な名前の検証の開始。</span><span class="sxs-lookup"><span data-stu-id="05c39-117">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="05c39-118">182</span><span class="sxs-lookup"><span data-stu-id="05c39-118">182</span></span>|<span data-ttu-id="05c39-119">厳密な名前の検証の終了。</span><span class="sxs-lookup"><span data-stu-id="05c39-119">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="05c39-120">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="05c39-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="05c39-121">フィールド名</span><span class="sxs-lookup"><span data-stu-id="05c39-121">Field name</span></span>|<span data-ttu-id="05c39-122">データ型</span><span class="sxs-lookup"><span data-stu-id="05c39-122">Data type</span></span>|<span data-ttu-id="05c39-123">説明</span><span class="sxs-lookup"><span data-stu-id="05c39-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="05c39-124">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="05c39-124">VerificationFlags</span></span>|<span data-ttu-id="05c39-125">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="05c39-125">win:UInt32</span></span>|<span data-ttu-id="05c39-126">検証フラグ。</span><span class="sxs-lookup"><span data-stu-id="05c39-126">The verification flags.</span></span>|  
|<span data-ttu-id="05c39-127">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="05c39-127">ErrorCode</span></span>|<span data-ttu-id="05c39-128">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="05c39-128">win:UInt32</span></span>|<span data-ttu-id="05c39-129">HResult エラー コード。</span><span class="sxs-lookup"><span data-stu-id="05c39-129">The HResult error code.</span></span>|  
|<span data-ttu-id="05c39-130">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="05c39-130">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="05c39-131">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="05c39-131">win:UnicodeString</span></span>|<span data-ttu-id="05c39-132">完全修飾アセンブリ名。</span><span class="sxs-lookup"><span data-stu-id="05c39-132">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="05c39-133">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="05c39-133">ClrInstanceID</span></span>|<span data-ttu-id="05c39-134">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="05c39-134">win:UInt16</span></span>|<span data-ttu-id="05c39-135">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="05c39-135">Unique ID for the instance of CLR or CoreCLR.</span></span>|  

## <a name="authenticodeverificationstart_v1-and-authenticodeverificationstop_v1-events"></a><span data-ttu-id="05c39-136">AuthenticodeVerificationStart_V1 イベントと AuthenticodeVerificationStop_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="05c39-136">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  

 <span data-ttu-id="05c39-137">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="05c39-137">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="05c39-138">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="05c39-138">Keyword for raising the event</span></span>|<span data-ttu-id="05c39-139">レベル</span><span class="sxs-lookup"><span data-stu-id="05c39-139">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="05c39-140">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="05c39-140">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="05c39-141">情報通知 (4)</span><span class="sxs-lookup"><span data-stu-id="05c39-141">Informational(4)</span></span>|  
  
 <span data-ttu-id="05c39-142">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="05c39-142">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="05c39-143">イベント</span><span class="sxs-lookup"><span data-stu-id="05c39-143">Event</span></span>|<span data-ttu-id="05c39-144">イベント ID</span><span class="sxs-lookup"><span data-stu-id="05c39-144">Event ID</span></span>|<span data-ttu-id="05c39-145">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="05c39-145">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="05c39-146">183</span><span class="sxs-lookup"><span data-stu-id="05c39-146">183</span></span>|<span data-ttu-id="05c39-147">Authenticode 検証の開始。</span><span class="sxs-lookup"><span data-stu-id="05c39-147">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="05c39-148">184</span><span class="sxs-lookup"><span data-stu-id="05c39-148">184</span></span>|<span data-ttu-id="05c39-149">Authenticode 検証の終了。</span><span class="sxs-lookup"><span data-stu-id="05c39-149">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="05c39-150">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="05c39-150">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="05c39-151">フィールド名</span><span class="sxs-lookup"><span data-stu-id="05c39-151">Field name</span></span>|<span data-ttu-id="05c39-152">データ型</span><span class="sxs-lookup"><span data-stu-id="05c39-152">Data type</span></span>|<span data-ttu-id="05c39-153">説明</span><span class="sxs-lookup"><span data-stu-id="05c39-153">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="05c39-154">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="05c39-154">VerificationFlags</span></span>|<span data-ttu-id="05c39-155">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="05c39-155">win:UInt32</span></span>|<span data-ttu-id="05c39-156">検証フラグ。</span><span class="sxs-lookup"><span data-stu-id="05c39-156">The verification flags.</span></span>|  
|<span data-ttu-id="05c39-157">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="05c39-157">ErrorCode</span></span>|<span data-ttu-id="05c39-158">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="05c39-158">win:UInt32</span></span>|<span data-ttu-id="05c39-159">HResult エラー コード。</span><span class="sxs-lookup"><span data-stu-id="05c39-159">The HResult error code.</span></span>|  
|<span data-ttu-id="05c39-160">ModulePath</span><span class="sxs-lookup"><span data-stu-id="05c39-160">ModulePath</span></span>|<span data-ttu-id="05c39-161">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="05c39-161">win:UnicodeString</span></span>|<span data-ttu-id="05c39-162">モジュール パス</span><span class="sxs-lookup"><span data-stu-id="05c39-162">The module path.</span></span>|  
|<span data-ttu-id="05c39-163">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="05c39-163">ClrInstanceID</span></span>|<span data-ttu-id="05c39-164">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="05c39-164">win:UInt16</span></span>|<span data-ttu-id="05c39-165">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="05c39-165">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="05c39-166">関連項目</span><span class="sxs-lookup"><span data-stu-id="05c39-166">See also</span></span>

- [<span data-ttu-id="05c39-167">CLR ETW イベント</span><span class="sxs-lookup"><span data-stu-id="05c39-167">CLR ETW Events</span></span>](clr-etw-events.md)
