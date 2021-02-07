---
description: '詳細情報: AppDomainInfo'
title: AppDomainInfo
ms.date: 03/30/2017
ms.assetid: 6610b7d8-81eb-4bec-a543-9b72ad7b6f73
ms.openlocfilehash: 1e527f2a25c48a3bf35d974e3ac192d937a8a86e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757970"
---
# <a name="appdomaininfo"></a><span data-ttu-id="49a21-103">AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="49a21-103">AppDomainInfo</span></span>

<span data-ttu-id="49a21-104">アプリケーション ドメイン情報</span><span class="sxs-lookup"><span data-stu-id="49a21-104">Application domain information</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49a21-105">構文</span><span class="sxs-lookup"><span data-stu-id="49a21-105">Syntax</span></span>  
  
```csharp
class AppDomainInfo  
{  
  sint32 AppDomainId;  
  boolean IsDefault;  
  boolean LogMalformedMessages;  
  boolean LogMessagesAtServiceLevel;  
  boolean LogMessagesAtTransportLevel;  
  TraceListener MessageLoggingTraceListeners[];  
  string Name;  
  string PerformanceCounters;  
  sint32 ProcessId;  
  string ServiceConfigPath;  
  string TraceLevel;  
  TraceListener wmiTraceListeners[];  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="49a21-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="49a21-106">Methods</span></span>  

 <span data-ttu-id="49a21-107">AppDomainInfo クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="49a21-107">The AppDomainInfo class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="49a21-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="49a21-108">Properties</span></span>  

 <span data-ttu-id="49a21-109">AppDomainInfo クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="49a21-109">The AppDomainInfo class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="49a21-110">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="49a21-110">AppDomainId</span></span>  

 <span data-ttu-id="49a21-111">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="49a21-111">Data type: sint32</span></span>  
  
 <span data-ttu-id="49a21-112">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="49a21-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="49a21-113">AppDomain の ID です。</span><span class="sxs-lookup"><span data-stu-id="49a21-113">The Id of the appdomain.</span></span>  
  
### <a name="isdefault"></a><span data-ttu-id="49a21-114">IsDefault</span><span class="sxs-lookup"><span data-stu-id="49a21-114">IsDefault</span></span>  

 <span data-ttu-id="49a21-115">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="49a21-115">Data type: boolean</span></span>  
  
 <span data-ttu-id="49a21-116">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="49a21-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="49a21-117">AppDomain が既定の AppDomain かどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="49a21-117">Indicates whether the appdomain is the default appdomain.</span></span>  
  
### <a name="logmalformedmessages"></a><span data-ttu-id="49a21-118">LogMalformedMessages</span><span class="sxs-lookup"><span data-stu-id="49a21-118">LogMalformedMessages</span></span>  

 <span data-ttu-id="49a21-119">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="49a21-119">Data type: boolean</span></span>  
  
 <span data-ttu-id="49a21-120">アクセスの種類 : 読み取り/書き込み</span><span class="sxs-lookup"><span data-stu-id="49a21-120">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="49a21-121">非整形式メッセージをログに記録するかどうかを指定する値です。</span><span class="sxs-lookup"><span data-stu-id="49a21-121">A value that specifies whether malformed messages are logged.</span></span>  
  
### <a name="logmessagesatservicelevel"></a><span data-ttu-id="49a21-122">LogMessagesAtServiceLevel</span><span class="sxs-lookup"><span data-stu-id="49a21-122">LogMessagesAtServiceLevel</span></span>  

 <span data-ttu-id="49a21-123">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="49a21-123">Data type: boolean</span></span>  
  
 <span data-ttu-id="49a21-124">アクセスの種類 : 読み取り/書き込み</span><span class="sxs-lookup"><span data-stu-id="49a21-124">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="49a21-125">メッセージをサービス レベルでトレースするかどうかを指定する値です (暗号化およびトランスポート関連の変換前)。</span><span class="sxs-lookup"><span data-stu-id="49a21-125">A value that specifies whether messages are traced at the service level (before encryption and transport-related transforms).</span></span>  
  
### <a name="logmessagesattransportlevel"></a><span data-ttu-id="49a21-126">LogMessagesAtTransportLevel</span><span class="sxs-lookup"><span data-stu-id="49a21-126">LogMessagesAtTransportLevel</span></span>  

 <span data-ttu-id="49a21-127">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="49a21-127">Data type: boolean</span></span>  
  
 <span data-ttu-id="49a21-128">アクセスの種類 : 読み取り/書き込み</span><span class="sxs-lookup"><span data-stu-id="49a21-128">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="49a21-129">メッセージをトランスポート レベルでトレースするかどうかを指定する値です。</span><span class="sxs-lookup"><span data-stu-id="49a21-129">A value that specifies whether messages are traced at the transport level.</span></span>  
  
### <a name="messageloggingtracelisteners"></a><span data-ttu-id="49a21-130">MessageLoggingTraceListeners</span><span class="sxs-lookup"><span data-stu-id="49a21-130">MessageLoggingTraceListeners</span></span>  

 <span data-ttu-id="49a21-131">データ型 : TraceListener 配列</span><span class="sxs-lookup"><span data-stu-id="49a21-131">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="49a21-132">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="49a21-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="49a21-133">System.Wmi.MessageLogging トレース ソースをリッスンするコレクション トレース リスナーです。</span><span class="sxs-lookup"><span data-stu-id="49a21-133">The collection trace listeners that listen to the System.Wmi.MessageLogging trace source.</span></span>  
  
### <a name="name"></a><span data-ttu-id="49a21-134">名前</span><span class="sxs-lookup"><span data-stu-id="49a21-134">Name</span></span>  

 <span data-ttu-id="49a21-135">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="49a21-135">Data type: string</span></span>  
  
 <span data-ttu-id="49a21-136">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="49a21-136">Access type: Read-only</span></span>  
  
 <span data-ttu-id="49a21-137">AppDomain の名前です。</span><span class="sxs-lookup"><span data-stu-id="49a21-137">The name of the appdomain.</span></span>  
  
### <a name="performancecounters"></a><span data-ttu-id="49a21-138">PerformanceCounters</span><span class="sxs-lookup"><span data-stu-id="49a21-138">PerformanceCounters</span></span>  

 <span data-ttu-id="49a21-139">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="49a21-139">Data type: string</span></span>  
  
 <span data-ttu-id="49a21-140">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="49a21-140">Access type: Read-only</span></span>  
  
 <span data-ttu-id="49a21-141">AppDomain におけるアクティブなパフォーマンス カウンターのスコープです。</span><span class="sxs-lookup"><span data-stu-id="49a21-141">The scope of active performance counters in the appdomain.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="49a21-142">ProcessId</span><span class="sxs-lookup"><span data-stu-id="49a21-142">ProcessId</span></span>  

 <span data-ttu-id="49a21-143">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="49a21-143">Data type: sint32</span></span>  
  
 <span data-ttu-id="49a21-144">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="49a21-144">Access type: Read-only</span></span>  
  
 <span data-ttu-id="49a21-145">プロセス ID です。</span><span class="sxs-lookup"><span data-stu-id="49a21-145">The process Id.</span></span>  
  
### <a name="serviceconfigpath"></a><span data-ttu-id="49a21-146">ServiceConfigPath</span><span class="sxs-lookup"><span data-stu-id="49a21-146">ServiceConfigPath</span></span>  

 <span data-ttu-id="49a21-147">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="49a21-147">Data type: string</span></span>  
  
 <span data-ttu-id="49a21-148">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="49a21-148">Access type: Read-only</span></span>  
  
 <span data-ttu-id="49a21-149">サービスの構成へのパスです。</span><span class="sxs-lookup"><span data-stu-id="49a21-149">The path to the configuration of the service.</span></span>  
  
### <a name="tracelevel"></a><span data-ttu-id="49a21-150">TraceLevel</span><span class="sxs-lookup"><span data-stu-id="49a21-150">TraceLevel</span></span>  

 <span data-ttu-id="49a21-151">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="49a21-151">Data type: string</span></span>  
  
 <span data-ttu-id="49a21-152">アクセスの種類 : 読み取り/書き込み</span><span class="sxs-lookup"><span data-stu-id="49a21-152">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="49a21-153">System.Wmi トレース ソースのトレース レベル。</span><span class="sxs-lookup"><span data-stu-id="49a21-153">The trace level of the System.Wmi trace source.</span></span>  
  
### <a name="servicemodeltracelisteners"></a><span data-ttu-id="49a21-154">ServiceModelTraceListeners</span><span class="sxs-lookup"><span data-stu-id="49a21-154">ServiceModelTraceListeners</span></span>  

 <span data-ttu-id="49a21-155">データ型 : TraceListener 配列</span><span class="sxs-lookup"><span data-stu-id="49a21-155">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="49a21-156">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="49a21-156">Access type: Read-only</span></span>  
  
 <span data-ttu-id="49a21-157">System.ServiceModel トレース ソースのリスナーのコレクション。</span><span class="sxs-lookup"><span data-stu-id="49a21-157">A collection of listeners from the System.ServiceModel trace source.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49a21-158">要件</span><span class="sxs-lookup"><span data-stu-id="49a21-158">Requirements</span></span>  
  
|<span data-ttu-id="49a21-159">MOF</span><span class="sxs-lookup"><span data-stu-id="49a21-159">MOF</span></span>|<span data-ttu-id="49a21-160">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="49a21-160">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="49a21-161">名前空間</span><span class="sxs-lookup"><span data-stu-id="49a21-161">Namespace</span></span>|<span data-ttu-id="49a21-162">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="49a21-162">Defined in root\ServiceModel</span></span>|
