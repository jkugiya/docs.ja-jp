---
description: '詳細情報: OLE DB スキーマ コレクション'
title: OLE DB スキーマ コレクション
ms.date: 03/30/2017
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
ms.openlocfilehash: d4d4bae5387575bdaeaf013ed690e95aa3259068
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672622"
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="b1a92-103">OLE DB スキーマ コレクション</span><span class="sxs-lookup"><span data-stu-id="b1a92-103">OLE DB Schema Collections</span></span>

<span data-ttu-id="b1a92-104">ここでは、Microsoft SQL Server、Oracle、および Microsoft Jet 用の各 OLE DB プロバイダーでのスキーマ コレクションのサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b1a92-104">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="b1a92-105">Microsoft SQL Server OLE DB Provider</span><span class="sxs-lookup"><span data-stu-id="b1a92-105">Microsoft SQL Server OLE DB Provider</span></span>  

 <span data-ttu-id="b1a92-106">Microsoft SQL Server OLE DB Driver では、共通のスキーマ コレクションに加えて、次の特定のスキーマ コレクションがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="b1a92-106">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="b1a92-107">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="b1a92-107">Tables</span></span>  
  
- <span data-ttu-id="b1a92-108">列</span><span class="sxs-lookup"><span data-stu-id="b1a92-108">Columns</span></span>  
  
- <span data-ttu-id="b1a92-109">プロシージャ</span><span class="sxs-lookup"><span data-stu-id="b1a92-109">Procedures</span></span>  
  
- <span data-ttu-id="b1a92-110">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="b1a92-110">ProcedureParameters</span></span>  
  
- <span data-ttu-id="b1a92-111">Catalog</span><span class="sxs-lookup"><span data-stu-id="b1a92-111">Catalog</span></span>  
  
- <span data-ttu-id="b1a92-112">Indexes</span><span class="sxs-lookup"><span data-stu-id="b1a92-112">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="b1a92-113">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="b1a92-113">Tables</span></span>  
  
|<span data-ttu-id="b1a92-114">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b1a92-114">ColumnName</span></span>|<span data-ttu-id="b1a92-115">DataType</span><span class="sxs-lookup"><span data-stu-id="b1a92-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b1a92-116">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1a92-116">TABLE_CATALOG</span></span>|<span data-ttu-id="b1a92-117">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-117">String</span></span>|  
|<span data-ttu-id="b1a92-118">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1a92-118">TABLE_SCHEMA</span></span>|<span data-ttu-id="b1a92-119">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-119">String</span></span>|  
|<span data-ttu-id="b1a92-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b1a92-120">TABLE_NAME</span></span>|<span data-ttu-id="b1a92-121">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-121">String</span></span>|  
|<span data-ttu-id="b1a92-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b1a92-122">TABLE_TYPE</span></span>|<span data-ttu-id="b1a92-123">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-123">String</span></span>|  
|<span data-ttu-id="b1a92-124">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="b1a92-124">TABLE_GUID</span></span>|<span data-ttu-id="b1a92-125">GUID</span><span class="sxs-lookup"><span data-stu-id="b1a92-125">Guid</span></span>|  
|<span data-ttu-id="b1a92-126">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b1a92-126">DESCRIPTION</span></span>|<span data-ttu-id="b1a92-127">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-127">String</span></span>|  
|<span data-ttu-id="b1a92-128">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="b1a92-128">TABLE_PROPID</span></span>|<span data-ttu-id="b1a92-129">Int64</span><span class="sxs-lookup"><span data-stu-id="b1a92-129">Int64</span></span>|  
|<span data-ttu-id="b1a92-130">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="b1a92-130">DATE_CREATED</span></span>|<span data-ttu-id="b1a92-131">DateTime</span><span class="sxs-lookup"><span data-stu-id="b1a92-131">DateTime</span></span>|  
|<span data-ttu-id="b1a92-132">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="b1a92-132">DATE_MODIFIED</span></span>|<span data-ttu-id="b1a92-133">DateTime</span><span class="sxs-lookup"><span data-stu-id="b1a92-133">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="b1a92-134">列</span><span class="sxs-lookup"><span data-stu-id="b1a92-134">Columns</span></span>  
  
|<span data-ttu-id="b1a92-135">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b1a92-135">ColumnName</span></span>|<span data-ttu-id="b1a92-136">DataType</span><span class="sxs-lookup"><span data-stu-id="b1a92-136">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b1a92-137">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1a92-137">TABLE_CATALOG</span></span>|<span data-ttu-id="b1a92-138">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-138">String</span></span>|  
|<span data-ttu-id="b1a92-139">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1a92-139">TABLE_SCHEMA</span></span>|<span data-ttu-id="b1a92-140">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-140">String</span></span>|  
|<span data-ttu-id="b1a92-141">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b1a92-141">TABLE_NAME</span></span>|<span data-ttu-id="b1a92-142">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-142">String</span></span>|  
|<span data-ttu-id="b1a92-143">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b1a92-143">COLUMN_NAME</span></span>|<span data-ttu-id="b1a92-144">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-144">String</span></span>|  
|<span data-ttu-id="b1a92-145">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="b1a92-145">COLUMN_GUID</span></span>|<span data-ttu-id="b1a92-146">GUID</span><span class="sxs-lookup"><span data-stu-id="b1a92-146">Guid</span></span>|  
|<span data-ttu-id="b1a92-147">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="b1a92-147">COLUMN_PROPID</span></span>|<span data-ttu-id="b1a92-148">Int64</span><span class="sxs-lookup"><span data-stu-id="b1a92-148">Int64</span></span>|  
|<span data-ttu-id="b1a92-149">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b1a92-149">ORDINAL_POSITION</span></span>|<span data-ttu-id="b1a92-150">Int64</span><span class="sxs-lookup"><span data-stu-id="b1a92-150">Int64</span></span>|  
|<span data-ttu-id="b1a92-151">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="b1a92-151">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="b1a92-152">ブール型</span><span class="sxs-lookup"><span data-stu-id="b1a92-152">Boolean</span></span>|  
|<span data-ttu-id="b1a92-153">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="b1a92-153">COLUMN_DEFAULT</span></span>|<span data-ttu-id="b1a92-154">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-154">String</span></span>|  
|<span data-ttu-id="b1a92-155">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="b1a92-155">COLUMN_FLAGS</span></span>|<span data-ttu-id="b1a92-156">Int64</span><span class="sxs-lookup"><span data-stu-id="b1a92-156">Int64</span></span>|  
|<span data-ttu-id="b1a92-157">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b1a92-157">IS_NULLABLE</span></span>|<span data-ttu-id="b1a92-158">ブール型</span><span class="sxs-lookup"><span data-stu-id="b1a92-158">Boolean</span></span>|  
|<span data-ttu-id="b1a92-159">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b1a92-159">DATA_TYPE</span></span>|<span data-ttu-id="b1a92-160">Int32</span><span class="sxs-lookup"><span data-stu-id="b1a92-160">Int32</span></span>|  
|<span data-ttu-id="b1a92-161">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="b1a92-161">TYPE_GUID</span></span>|<span data-ttu-id="b1a92-162">GUID</span><span class="sxs-lookup"><span data-stu-id="b1a92-162">Guid</span></span>|  
|<span data-ttu-id="b1a92-163">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b1a92-163">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="b1a92-164">Int64</span><span class="sxs-lookup"><span data-stu-id="b1a92-164">Int64</span></span>|  
|<span data-ttu-id="b1a92-165">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b1a92-165">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="b1a92-166">Int64</span><span class="sxs-lookup"><span data-stu-id="b1a92-166">Int64</span></span>|  
|<span data-ttu-id="b1a92-167">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="b1a92-167">NUMERIC_PRECISION</span></span>|<span data-ttu-id="b1a92-168">Int32</span><span class="sxs-lookup"><span data-stu-id="b1a92-168">Int32</span></span>|  
|<span data-ttu-id="b1a92-169">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="b1a92-169">NUMERIC_SCALE</span></span>|<span data-ttu-id="b1a92-170">Int16</span><span class="sxs-lookup"><span data-stu-id="b1a92-170">Int16</span></span>|  
|<span data-ttu-id="b1a92-171">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="b1a92-171">DATETIME_PRECISION</span></span>|<span data-ttu-id="b1a92-172">Int64</span><span class="sxs-lookup"><span data-stu-id="b1a92-172">Int64</span></span>|  
|<span data-ttu-id="b1a92-173">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1a92-173">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="b1a92-174">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-174">String</span></span>|  
|<span data-ttu-id="b1a92-175">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1a92-175">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="b1a92-176">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-176">String</span></span>|  
|<span data-ttu-id="b1a92-177">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="b1a92-177">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="b1a92-178">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-178">String</span></span>|  
|<span data-ttu-id="b1a92-179">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1a92-179">COLLATION_CATALOG</span></span>|<span data-ttu-id="b1a92-180">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-180">String</span></span>|  
|<span data-ttu-id="b1a92-181">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1a92-181">COLLATION_SCHEMA</span></span>|<span data-ttu-id="b1a92-182">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-182">String</span></span>|  
|<span data-ttu-id="b1a92-183">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="b1a92-183">COLLATION_NAME</span></span>|<span data-ttu-id="b1a92-184">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-184">String</span></span>|  
|<span data-ttu-id="b1a92-185">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1a92-185">DOMAIN_CATALOG</span></span>|<span data-ttu-id="b1a92-186">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-186">String</span></span>|  
|<span data-ttu-id="b1a92-187">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1a92-187">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="b1a92-188">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-188">String</span></span>|  
|<span data-ttu-id="b1a92-189">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="b1a92-189">DOMAIN_NAME</span></span>|<span data-ttu-id="b1a92-190">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-190">String</span></span>|  
|<span data-ttu-id="b1a92-191">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b1a92-191">DESCRIPTION</span></span>|<span data-ttu-id="b1a92-192">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-192">String</span></span>|  
|<span data-ttu-id="b1a92-193">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="b1a92-193">COLUMN_LCID</span></span>|<span data-ttu-id="b1a92-194">Int32</span><span class="sxs-lookup"><span data-stu-id="b1a92-194">Int32</span></span>|  
|<span data-ttu-id="b1a92-195">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="b1a92-195">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="b1a92-196">Int32</span><span class="sxs-lookup"><span data-stu-id="b1a92-196">Int32</span></span>|  
|<span data-ttu-id="b1a92-197">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="b1a92-197">COLUMN_SORTID</span></span>|<span data-ttu-id="b1a92-198">Int32</span><span class="sxs-lookup"><span data-stu-id="b1a92-198">Int32</span></span>|  
|<span data-ttu-id="b1a92-199">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="b1a92-199">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="b1a92-200">Byte[]</span><span class="sxs-lookup"><span data-stu-id="b1a92-200">Byte[]</span></span>|  
|<span data-ttu-id="b1a92-201">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="b1a92-201">IS_COMPUTED</span></span>|<span data-ttu-id="b1a92-202">ブール型</span><span class="sxs-lookup"><span data-stu-id="b1a92-202">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="b1a92-203">プロシージャ</span><span class="sxs-lookup"><span data-stu-id="b1a92-203">Procedures</span></span>  
  
|<span data-ttu-id="b1a92-204">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b1a92-204">ColumnName</span></span>|<span data-ttu-id="b1a92-205">DataType</span><span class="sxs-lookup"><span data-stu-id="b1a92-205">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b1a92-206">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1a92-206">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="b1a92-207">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-207">String</span></span>|  
|<span data-ttu-id="b1a92-208">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1a92-208">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="b1a92-209">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-209">String</span></span>|  
|<span data-ttu-id="b1a92-210">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b1a92-210">PROCEDURE_NAME</span></span>|<span data-ttu-id="b1a92-211">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-211">String</span></span>|  
|<span data-ttu-id="b1a92-212">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b1a92-212">PROCEDURE_TYPE</span></span>|<span data-ttu-id="b1a92-213">Int16</span><span class="sxs-lookup"><span data-stu-id="b1a92-213">Int16</span></span>|  
|<span data-ttu-id="b1a92-214">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="b1a92-214">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="b1a92-215">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-215">String</span></span>|  
|<span data-ttu-id="b1a92-216">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b1a92-216">DESCRIPTION</span></span>|<span data-ttu-id="b1a92-217">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-217">String</span></span>|  
|<span data-ttu-id="b1a92-218">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="b1a92-218">DATE_CREATED</span></span>|<span data-ttu-id="b1a92-219">DateTime</span><span class="sxs-lookup"><span data-stu-id="b1a92-219">DateTime</span></span>|  
|<span data-ttu-id="b1a92-220">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="b1a92-220">DATE_MODIFIED</span></span>|<span data-ttu-id="b1a92-221">DateTime</span><span class="sxs-lookup"><span data-stu-id="b1a92-221">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="b1a92-222">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="b1a92-222">ProcedureParameters</span></span>  
  
|<span data-ttu-id="b1a92-223">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b1a92-223">ColumnName</span></span>|<span data-ttu-id="b1a92-224">DataType</span><span class="sxs-lookup"><span data-stu-id="b1a92-224">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b1a92-225">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1a92-225">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="b1a92-226">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-226">String</span></span>|  
|<span data-ttu-id="b1a92-227">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1a92-227">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="b1a92-228">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-228">String</span></span>|  
|<span data-ttu-id="b1a92-229">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b1a92-229">PROCEDURE_NAME</span></span>|<span data-ttu-id="b1a92-230">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-230">String</span></span>|  
|<span data-ttu-id="b1a92-231">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="b1a92-231">PARAMETER_NAME</span></span>|<span data-ttu-id="b1a92-232">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-232">String</span></span>|  
|<span data-ttu-id="b1a92-233">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b1a92-233">ORDINAL_POSITION</span></span>|<span data-ttu-id="b1a92-234">Int32</span><span class="sxs-lookup"><span data-stu-id="b1a92-234">Int32</span></span>|  
|<span data-ttu-id="b1a92-235">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="b1a92-235">PARAMETER_TYPE</span></span>|<span data-ttu-id="b1a92-236">Int32</span><span class="sxs-lookup"><span data-stu-id="b1a92-236">Int32</span></span>|  
|<span data-ttu-id="b1a92-237">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="b1a92-237">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="b1a92-238">ブール型</span><span class="sxs-lookup"><span data-stu-id="b1a92-238">Boolean</span></span>|  
|<span data-ttu-id="b1a92-239">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="b1a92-239">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="b1a92-240">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-240">String</span></span>|  
|<span data-ttu-id="b1a92-241">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b1a92-241">IS_NULLABLE</span></span>|<span data-ttu-id="b1a92-242">ブール型</span><span class="sxs-lookup"><span data-stu-id="b1a92-242">Boolean</span></span>|  
|<span data-ttu-id="b1a92-243">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b1a92-243">DATA_TYPE</span></span>|<span data-ttu-id="b1a92-244">Int32</span><span class="sxs-lookup"><span data-stu-id="b1a92-244">Int32</span></span>|  
|<span data-ttu-id="b1a92-245">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b1a92-245">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="b1a92-246">Int64</span><span class="sxs-lookup"><span data-stu-id="b1a92-246">Int64</span></span>|  
|<span data-ttu-id="b1a92-247">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b1a92-247">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="b1a92-248">Int64</span><span class="sxs-lookup"><span data-stu-id="b1a92-248">Int64</span></span>|  
|<span data-ttu-id="b1a92-249">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="b1a92-249">NUMERIC_PRECISION</span></span>|<span data-ttu-id="b1a92-250">Int32</span><span class="sxs-lookup"><span data-stu-id="b1a92-250">Int32</span></span>|  
|<span data-ttu-id="b1a92-251">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="b1a92-251">NUMERIC_SCALE</span></span>|<span data-ttu-id="b1a92-252">Int16</span><span class="sxs-lookup"><span data-stu-id="b1a92-252">Int16</span></span>|  
|<span data-ttu-id="b1a92-253">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b1a92-253">DESCRIPTION</span></span>|<span data-ttu-id="b1a92-254">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-254">String</span></span>|  
|<span data-ttu-id="b1a92-255">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="b1a92-255">TYPE_NAME</span></span>|<span data-ttu-id="b1a92-256">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-256">String</span></span>|  
|<span data-ttu-id="b1a92-257">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="b1a92-257">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="b1a92-258">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-258">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="b1a92-259">Catalog</span><span class="sxs-lookup"><span data-stu-id="b1a92-259">Catalog</span></span>  
  
|<span data-ttu-id="b1a92-260">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b1a92-260">ColumnName</span></span>|<span data-ttu-id="b1a92-261">DataType</span><span class="sxs-lookup"><span data-stu-id="b1a92-261">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b1a92-262">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="b1a92-262">CATALOG_NAME</span></span>|<span data-ttu-id="b1a92-263">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-263">String</span></span>|  
|<span data-ttu-id="b1a92-264">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b1a92-264">DESCRIPTION</span></span>|<span data-ttu-id="b1a92-265">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-265">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="b1a92-266">Indexes</span><span class="sxs-lookup"><span data-stu-id="b1a92-266">Indexes</span></span>  
  
|<span data-ttu-id="b1a92-267">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b1a92-267">ColumnName</span></span>|<span data-ttu-id="b1a92-268">DataType</span><span class="sxs-lookup"><span data-stu-id="b1a92-268">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b1a92-269">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1a92-269">TABLE_CATALOG</span></span>|<span data-ttu-id="b1a92-270">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-270">String</span></span>|  
|<span data-ttu-id="b1a92-271">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1a92-271">TABLE_SCHEMA</span></span>|<span data-ttu-id="b1a92-272">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-272">String</span></span>|  
|<span data-ttu-id="b1a92-273">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b1a92-273">TABLE_NAME</span></span>|<span data-ttu-id="b1a92-274">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-274">String</span></span>|  
|<span data-ttu-id="b1a92-275">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1a92-275">INDEX_CATALOG</span></span>|<span data-ttu-id="b1a92-276">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-276">String</span></span>|  
|<span data-ttu-id="b1a92-277">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1a92-277">INDEX_SCHEMA</span></span>|<span data-ttu-id="b1a92-278">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-278">String</span></span>|  
|<span data-ttu-id="b1a92-279">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="b1a92-279">INDEX_NAME</span></span>|<span data-ttu-id="b1a92-280">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-280">String</span></span>|  
|<span data-ttu-id="b1a92-281">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="b1a92-281">PRIMARY_KEY</span></span>|<span data-ttu-id="b1a92-282">ブール型</span><span class="sxs-lookup"><span data-stu-id="b1a92-282">Boolean</span></span>|  
|<span data-ttu-id="b1a92-283">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="b1a92-283">UNIQUE</span></span>|<span data-ttu-id="b1a92-284">ブール型</span><span class="sxs-lookup"><span data-stu-id="b1a92-284">Boolean</span></span>|  
|<span data-ttu-id="b1a92-285">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="b1a92-285">CLUSTERED</span></span>|<span data-ttu-id="b1a92-286">ブール型</span><span class="sxs-lookup"><span data-stu-id="b1a92-286">Boolean</span></span>|  
|<span data-ttu-id="b1a92-287">TYPE</span><span class="sxs-lookup"><span data-stu-id="b1a92-287">TYPE</span></span>|<span data-ttu-id="b1a92-288">Int32</span><span class="sxs-lookup"><span data-stu-id="b1a92-288">Int32</span></span>|  
|<span data-ttu-id="b1a92-289">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="b1a92-289">FILL_FACTOR</span></span>|<span data-ttu-id="b1a92-290">Int32</span><span class="sxs-lookup"><span data-stu-id="b1a92-290">Int32</span></span>|  
|<span data-ttu-id="b1a92-291">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="b1a92-291">INITIAL_SIZE</span></span>|<span data-ttu-id="b1a92-292">Int32</span><span class="sxs-lookup"><span data-stu-id="b1a92-292">Int32</span></span>|  
|<span data-ttu-id="b1a92-293">NULLS</span><span class="sxs-lookup"><span data-stu-id="b1a92-293">NULLS</span></span>|<span data-ttu-id="b1a92-294">Int32</span><span class="sxs-lookup"><span data-stu-id="b1a92-294">Int32</span></span>|  
|<span data-ttu-id="b1a92-295">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="b1a92-295">SORT_BOOKMARKS</span></span>|<span data-ttu-id="b1a92-296">ブール型</span><span class="sxs-lookup"><span data-stu-id="b1a92-296">Boolean</span></span>|  
|<span data-ttu-id="b1a92-297">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="b1a92-297">AUTO_UPDATE</span></span>|<span data-ttu-id="b1a92-298">ブール型</span><span class="sxs-lookup"><span data-stu-id="b1a92-298">Boolean</span></span>|  
|<span data-ttu-id="b1a92-299">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="b1a92-299">NULL_COLLATION</span></span>|<span data-ttu-id="b1a92-300">Int32</span><span class="sxs-lookup"><span data-stu-id="b1a92-300">Int32</span></span>|  
|<span data-ttu-id="b1a92-301">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b1a92-301">ORDINAL_POSITION</span></span>|<span data-ttu-id="b1a92-302">Int64</span><span class="sxs-lookup"><span data-stu-id="b1a92-302">Int64</span></span>|  
|<span data-ttu-id="b1a92-303">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b1a92-303">COLUMN_NAME</span></span>|<span data-ttu-id="b1a92-304">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-304">String</span></span>|  
|<span data-ttu-id="b1a92-305">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="b1a92-305">COLUMN_GUID</span></span>|<span data-ttu-id="b1a92-306">GUID</span><span class="sxs-lookup"><span data-stu-id="b1a92-306">Guid</span></span>|  
|<span data-ttu-id="b1a92-307">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="b1a92-307">COLUMN_PROPID</span></span>|<span data-ttu-id="b1a92-308">Int64</span><span class="sxs-lookup"><span data-stu-id="b1a92-308">Int64</span></span>|  
|<span data-ttu-id="b1a92-309">COLLATION</span><span class="sxs-lookup"><span data-stu-id="b1a92-309">COLLATION</span></span>|<span data-ttu-id="b1a92-310">Int16</span><span class="sxs-lookup"><span data-stu-id="b1a92-310">Int16</span></span>|  
|<span data-ttu-id="b1a92-311">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="b1a92-311">CARDINALITY</span></span>|<span data-ttu-id="b1a92-312">Decimal (10 進数型)</span><span class="sxs-lookup"><span data-stu-id="b1a92-312">Decimal</span></span>|  
|<span data-ttu-id="b1a92-313">PAGES</span><span class="sxs-lookup"><span data-stu-id="b1a92-313">PAGES</span></span>|<span data-ttu-id="b1a92-314">Int32</span><span class="sxs-lookup"><span data-stu-id="b1a92-314">Int32</span></span>|  
|<span data-ttu-id="b1a92-315">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="b1a92-315">FILTER_CONDITION</span></span>|<span data-ttu-id="b1a92-316">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-316">String</span></span>|  
|<span data-ttu-id="b1a92-317">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="b1a92-317">INTEGRATED</span></span>|<span data-ttu-id="b1a92-318">ブール型</span><span class="sxs-lookup"><span data-stu-id="b1a92-318">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="b1a92-319">Microsoft Oracle OLE DB Provider</span><span class="sxs-lookup"><span data-stu-id="b1a92-319">Microsoft Oracle OLE DB Provider</span></span>  

 <span data-ttu-id="b1a92-320">Microsoft Oracle OLE DB Driver は、共通のスキーマ コレクションに加えて次のスキーマ コレクションをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="b1a92-320">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="b1a92-321">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="b1a92-321">Tables</span></span>  
  
- <span data-ttu-id="b1a92-322">列</span><span class="sxs-lookup"><span data-stu-id="b1a92-322">Columns</span></span>  
  
- <span data-ttu-id="b1a92-323">プロシージャ</span><span class="sxs-lookup"><span data-stu-id="b1a92-323">Procedures</span></span>  
  
- <span data-ttu-id="b1a92-324">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="b1a92-324">ProcedureColumns</span></span>  
  
- <span data-ttu-id="b1a92-325">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="b1a92-325">ProcedureParameters</span></span>  
  
- <span data-ttu-id="b1a92-326">Views</span><span class="sxs-lookup"><span data-stu-id="b1a92-326">Views</span></span>  
  
- <span data-ttu-id="b1a92-327">Indexes</span><span class="sxs-lookup"><span data-stu-id="b1a92-327">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="b1a92-328">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="b1a92-328">Tables</span></span>  
  
|<span data-ttu-id="b1a92-329">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b1a92-329">ColumnName</span></span>|<span data-ttu-id="b1a92-330">DataType</span><span class="sxs-lookup"><span data-stu-id="b1a92-330">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b1a92-331">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1a92-331">TABLE_CATALOG</span></span>|<span data-ttu-id="b1a92-332">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-332">String</span></span>|  
|<span data-ttu-id="b1a92-333">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1a92-333">TABLE_SCHEMA</span></span>|<span data-ttu-id="b1a92-334">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-334">String</span></span>|  
|<span data-ttu-id="b1a92-335">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b1a92-335">TABLE_NAME</span></span>|<span data-ttu-id="b1a92-336">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-336">String</span></span>|  
|<span data-ttu-id="b1a92-337">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b1a92-337">TABLE_TYPE</span></span>|<span data-ttu-id="b1a92-338">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-338">String</span></span>|  
|<span data-ttu-id="b1a92-339">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="b1a92-339">TABLE_GUID</span></span>|<span data-ttu-id="b1a92-340">GUID</span><span class="sxs-lookup"><span data-stu-id="b1a92-340">Guid</span></span>|  
|<span data-ttu-id="b1a92-341">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b1a92-341">DESCRIPTION</span></span>|<span data-ttu-id="b1a92-342">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-342">String</span></span>|  
|<span data-ttu-id="b1a92-343">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="b1a92-343">TABLE_PROPID</span></span>|<span data-ttu-id="b1a92-344">Int64</span><span class="sxs-lookup"><span data-stu-id="b1a92-344">Int64</span></span>|  
|<span data-ttu-id="b1a92-345">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="b1a92-345">DATE_CREATED</span></span>|<span data-ttu-id="b1a92-346">DateTime</span><span class="sxs-lookup"><span data-stu-id="b1a92-346">DateTime</span></span>|  
|<span data-ttu-id="b1a92-347">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="b1a92-347">DATE_MODIFIED</span></span>|<span data-ttu-id="b1a92-348">DateTime</span><span class="sxs-lookup"><span data-stu-id="b1a92-348">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="b1a92-349">列</span><span class="sxs-lookup"><span data-stu-id="b1a92-349">Columns</span></span>  
  
|<span data-ttu-id="b1a92-350">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b1a92-350">ColumnName</span></span>|<span data-ttu-id="b1a92-351">DataType</span><span class="sxs-lookup"><span data-stu-id="b1a92-351">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b1a92-352">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1a92-352">TABLE_CATALOG</span></span>|<span data-ttu-id="b1a92-353">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-353">String</span></span>|  
|<span data-ttu-id="b1a92-354">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1a92-354">TABLE_SCHEMA</span></span>|<span data-ttu-id="b1a92-355">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-355">String</span></span>|  
|<span data-ttu-id="b1a92-356">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b1a92-356">TABLE_NAME</span></span>|<span data-ttu-id="b1a92-357">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-357">String</span></span>|  
|<span data-ttu-id="b1a92-358">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b1a92-358">COLUMN_NAME</span></span>|<span data-ttu-id="b1a92-359">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-359">String</span></span>|  
|<span data-ttu-id="b1a92-360">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="b1a92-360">COLUMN_GUID</span></span>|<span data-ttu-id="b1a92-361">GUID</span><span class="sxs-lookup"><span data-stu-id="b1a92-361">Guid</span></span>|  
|<span data-ttu-id="b1a92-362">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="b1a92-362">COLUMN_PROPID</span></span>|<span data-ttu-id="b1a92-363">Int64</span><span class="sxs-lookup"><span data-stu-id="b1a92-363">Int64</span></span>|  
|<span data-ttu-id="b1a92-364">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b1a92-364">ORDINAL_POSITION</span></span>|<span data-ttu-id="b1a92-365">Int64</span><span class="sxs-lookup"><span data-stu-id="b1a92-365">Int64</span></span>|  
|<span data-ttu-id="b1a92-366">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="b1a92-366">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="b1a92-367">ブール型</span><span class="sxs-lookup"><span data-stu-id="b1a92-367">Boolean</span></span>|  
|<span data-ttu-id="b1a92-368">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="b1a92-368">COLUMN_DEFAULT</span></span>|<span data-ttu-id="b1a92-369">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-369">String</span></span>|  
|<span data-ttu-id="b1a92-370">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="b1a92-370">COLUMN_FLAGS</span></span>|<span data-ttu-id="b1a92-371">Int64</span><span class="sxs-lookup"><span data-stu-id="b1a92-371">Int64</span></span>|  
|<span data-ttu-id="b1a92-372">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b1a92-372">IS_NULLABLE</span></span>|<span data-ttu-id="b1a92-373">ブール型</span><span class="sxs-lookup"><span data-stu-id="b1a92-373">Boolean</span></span>|  
|<span data-ttu-id="b1a92-374">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b1a92-374">DATA_TYPE</span></span>|<span data-ttu-id="b1a92-375">Int32</span><span class="sxs-lookup"><span data-stu-id="b1a92-375">Int32</span></span>|  
|<span data-ttu-id="b1a92-376">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="b1a92-376">TYPE_GUID</span></span>|<span data-ttu-id="b1a92-377">GUID</span><span class="sxs-lookup"><span data-stu-id="b1a92-377">Guid</span></span>|  
|<span data-ttu-id="b1a92-378">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b1a92-378">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="b1a92-379">Int64</span><span class="sxs-lookup"><span data-stu-id="b1a92-379">Int64</span></span>|  
|<span data-ttu-id="b1a92-380">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b1a92-380">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="b1a92-381">Int64</span><span class="sxs-lookup"><span data-stu-id="b1a92-381">Int64</span></span>|  
|<span data-ttu-id="b1a92-382">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="b1a92-382">NUMERIC_PRECISION</span></span>|<span data-ttu-id="b1a92-383">Int32</span><span class="sxs-lookup"><span data-stu-id="b1a92-383">Int32</span></span>|  
|<span data-ttu-id="b1a92-384">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="b1a92-384">NUMERIC_SCALE</span></span>|<span data-ttu-id="b1a92-385">Int16</span><span class="sxs-lookup"><span data-stu-id="b1a92-385">Int16</span></span>|  
|<span data-ttu-id="b1a92-386">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="b1a92-386">DATETIME_PRECISION</span></span>|<span data-ttu-id="b1a92-387">Int64</span><span class="sxs-lookup"><span data-stu-id="b1a92-387">Int64</span></span>|  
|<span data-ttu-id="b1a92-388">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1a92-388">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="b1a92-389">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-389">String</span></span>|  
|<span data-ttu-id="b1a92-390">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1a92-390">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="b1a92-391">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-391">String</span></span>|  
|<span data-ttu-id="b1a92-392">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="b1a92-392">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="b1a92-393">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-393">String</span></span>|  
|<span data-ttu-id="b1a92-394">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1a92-394">COLLATION_CATALOG</span></span>|<span data-ttu-id="b1a92-395">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-395">String</span></span>|  
|<span data-ttu-id="b1a92-396">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1a92-396">COLLATION_SCHEMA</span></span>|<span data-ttu-id="b1a92-397">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-397">String</span></span>|  
|<span data-ttu-id="b1a92-398">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="b1a92-398">COLLATION_NAME</span></span>|<span data-ttu-id="b1a92-399">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-399">String</span></span>|  
|<span data-ttu-id="b1a92-400">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1a92-400">DOMAIN_CATALOG</span></span>|<span data-ttu-id="b1a92-401">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-401">String</span></span>|  
|<span data-ttu-id="b1a92-402">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1a92-402">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="b1a92-403">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-403">String</span></span>|  
|<span data-ttu-id="b1a92-404">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="b1a92-404">DOMAIN_NAME</span></span>|<span data-ttu-id="b1a92-405">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-405">String</span></span>|  
|<span data-ttu-id="b1a92-406">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b1a92-406">DESCRIPTION</span></span>|<span data-ttu-id="b1a92-407">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-407">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="b1a92-408">プロシージャ</span><span class="sxs-lookup"><span data-stu-id="b1a92-408">Procedures</span></span>  
  
|<span data-ttu-id="b1a92-409">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b1a92-409">ColumnName</span></span>|<span data-ttu-id="b1a92-410">DataType</span><span class="sxs-lookup"><span data-stu-id="b1a92-410">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b1a92-411">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1a92-411">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="b1a92-412">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-412">String</span></span>|  
|<span data-ttu-id="b1a92-413">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1a92-413">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="b1a92-414">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-414">String</span></span>|  
|<span data-ttu-id="b1a92-415">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b1a92-415">PROCEDURE_NAME</span></span>|<span data-ttu-id="b1a92-416">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-416">String</span></span>|  
|<span data-ttu-id="b1a92-417">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b1a92-417">PROCEDURE_TYPE</span></span>|<span data-ttu-id="b1a92-418">Int16</span><span class="sxs-lookup"><span data-stu-id="b1a92-418">Int16</span></span>|  
|<span data-ttu-id="b1a92-419">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="b1a92-419">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="b1a92-420">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-420">String</span></span>|  
|<span data-ttu-id="b1a92-421">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b1a92-421">DESCRIPTION</span></span>|<span data-ttu-id="b1a92-422">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-422">String</span></span>|  
|<span data-ttu-id="b1a92-423">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="b1a92-423">DATE_CREATED</span></span>|<span data-ttu-id="b1a92-424">DateTime</span><span class="sxs-lookup"><span data-stu-id="b1a92-424">DateTime</span></span>|  
|<span data-ttu-id="b1a92-425">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="b1a92-425">DATE_MODIFIED</span></span>|<span data-ttu-id="b1a92-426">DateTime</span><span class="sxs-lookup"><span data-stu-id="b1a92-426">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="b1a92-427">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="b1a92-427">ProcedureColumns</span></span>  
  
|<span data-ttu-id="b1a92-428">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b1a92-428">ColumnName</span></span>|<span data-ttu-id="b1a92-429">DataType</span><span class="sxs-lookup"><span data-stu-id="b1a92-429">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b1a92-430">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1a92-430">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="b1a92-431">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-431">String</span></span>|  
|<span data-ttu-id="b1a92-432">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1a92-432">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="b1a92-433">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-433">String</span></span>|  
|<span data-ttu-id="b1a92-434">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b1a92-434">PROCEDURE_NAME</span></span>|<span data-ttu-id="b1a92-435">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-435">String</span></span>|  
|<span data-ttu-id="b1a92-436">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b1a92-436">COLUMN_NAME</span></span>|<span data-ttu-id="b1a92-437">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-437">String</span></span>|  
|<span data-ttu-id="b1a92-438">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="b1a92-438">COLUMN_GUID</span></span>|<span data-ttu-id="b1a92-439">GUID</span><span class="sxs-lookup"><span data-stu-id="b1a92-439">Guid</span></span>|  
|<span data-ttu-id="b1a92-440">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="b1a92-440">COLUMN_PROPID</span></span>|<span data-ttu-id="b1a92-441">Int64</span><span class="sxs-lookup"><span data-stu-id="b1a92-441">Int64</span></span>|  
|<span data-ttu-id="b1a92-442">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="b1a92-442">ROWSET_NUMBER</span></span>|<span data-ttu-id="b1a92-443">Int64</span><span class="sxs-lookup"><span data-stu-id="b1a92-443">Int64</span></span>|  
|<span data-ttu-id="b1a92-444">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b1a92-444">ORDINAL_POSITION</span></span>|<span data-ttu-id="b1a92-445">Int64</span><span class="sxs-lookup"><span data-stu-id="b1a92-445">Int64</span></span>|  
|<span data-ttu-id="b1a92-446">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b1a92-446">IS_NULLABLE</span></span>|<span data-ttu-id="b1a92-447">ブール型</span><span class="sxs-lookup"><span data-stu-id="b1a92-447">Boolean</span></span>|  
|<span data-ttu-id="b1a92-448">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b1a92-448">DATA_TYPE</span></span>|<span data-ttu-id="b1a92-449">Int32</span><span class="sxs-lookup"><span data-stu-id="b1a92-449">Int32</span></span>|  
|<span data-ttu-id="b1a92-450">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="b1a92-450">TYPE_GUID</span></span>|<span data-ttu-id="b1a92-451">GUID</span><span class="sxs-lookup"><span data-stu-id="b1a92-451">Guid</span></span>|  
|<span data-ttu-id="b1a92-452">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b1a92-452">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="b1a92-453">Int64</span><span class="sxs-lookup"><span data-stu-id="b1a92-453">Int64</span></span>|  
|<span data-ttu-id="b1a92-454">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b1a92-454">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="b1a92-455">Int64</span><span class="sxs-lookup"><span data-stu-id="b1a92-455">Int64</span></span>|  
|<span data-ttu-id="b1a92-456">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="b1a92-456">NUMERIC_PRECISION</span></span>|<span data-ttu-id="b1a92-457">Int32</span><span class="sxs-lookup"><span data-stu-id="b1a92-457">Int32</span></span>|  
|<span data-ttu-id="b1a92-458">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="b1a92-458">NUMERIC_SCALE</span></span>|<span data-ttu-id="b1a92-459">Int16</span><span class="sxs-lookup"><span data-stu-id="b1a92-459">Int16</span></span>|  
|<span data-ttu-id="b1a92-460">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b1a92-460">DESCRIPTION</span></span>|<span data-ttu-id="b1a92-461">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-461">String</span></span>|  
|<span data-ttu-id="b1a92-462">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="b1a92-462">OVERLOAD</span></span>|<span data-ttu-id="b1a92-463">Int16</span><span class="sxs-lookup"><span data-stu-id="b1a92-463">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="b1a92-464">Views</span><span class="sxs-lookup"><span data-stu-id="b1a92-464">Views</span></span>  
  
|<span data-ttu-id="b1a92-465">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b1a92-465">ColumnName</span></span>|<span data-ttu-id="b1a92-466">DataType</span><span class="sxs-lookup"><span data-stu-id="b1a92-466">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b1a92-467">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1a92-467">TABLE_CATALOG</span></span>|<span data-ttu-id="b1a92-468">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-468">String</span></span>|  
|<span data-ttu-id="b1a92-469">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1a92-469">TABLE_SCHEMA</span></span>|<span data-ttu-id="b1a92-470">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-470">String</span></span>|  
|<span data-ttu-id="b1a92-471">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b1a92-471">TABLE_NAME</span></span>|<span data-ttu-id="b1a92-472">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-472">String</span></span>|  
|<span data-ttu-id="b1a92-473">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="b1a92-473">VIEW_DEFINITION</span></span>|<span data-ttu-id="b1a92-474">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-474">String</span></span>|  
|<span data-ttu-id="b1a92-475">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="b1a92-475">CHECK_OPTION</span></span>|<span data-ttu-id="b1a92-476">ブール型</span><span class="sxs-lookup"><span data-stu-id="b1a92-476">Boolean</span></span>|  
|<span data-ttu-id="b1a92-477">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="b1a92-477">IS_UPDATABLE</span></span>|<span data-ttu-id="b1a92-478">ブール型</span><span class="sxs-lookup"><span data-stu-id="b1a92-478">Boolean</span></span>|  
|<span data-ttu-id="b1a92-479">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b1a92-479">DESCRIPTION</span></span>|<span data-ttu-id="b1a92-480">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-480">String</span></span>|  
|<span data-ttu-id="b1a92-481">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="b1a92-481">DATE_CREATED</span></span>|<span data-ttu-id="b1a92-482">DateTime</span><span class="sxs-lookup"><span data-stu-id="b1a92-482">DateTime</span></span>|  
|<span data-ttu-id="b1a92-483">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="b1a92-483">DATE_MODIFIED</span></span>|<span data-ttu-id="b1a92-484">DateTime</span><span class="sxs-lookup"><span data-stu-id="b1a92-484">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="b1a92-485">Indexes</span><span class="sxs-lookup"><span data-stu-id="b1a92-485">Indexes</span></span>  
  
|<span data-ttu-id="b1a92-486">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b1a92-486">ColumnName</span></span>|<span data-ttu-id="b1a92-487">DataType</span><span class="sxs-lookup"><span data-stu-id="b1a92-487">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b1a92-488">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1a92-488">TABLE_CATALOG</span></span>|<span data-ttu-id="b1a92-489">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-489">String</span></span>|  
|<span data-ttu-id="b1a92-490">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1a92-490">TABLE_SCHEMA</span></span>|<span data-ttu-id="b1a92-491">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-491">String</span></span>|  
|<span data-ttu-id="b1a92-492">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b1a92-492">TABLE_NAME</span></span>|<span data-ttu-id="b1a92-493">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-493">String</span></span>|  
|<span data-ttu-id="b1a92-494">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1a92-494">INDEX_CATALOG</span></span>|<span data-ttu-id="b1a92-495">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-495">String</span></span>|  
|<span data-ttu-id="b1a92-496">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1a92-496">INDEX_SCHEMA</span></span>|<span data-ttu-id="b1a92-497">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-497">String</span></span>|  
|<span data-ttu-id="b1a92-498">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="b1a92-498">INDEX_NAME</span></span>|<span data-ttu-id="b1a92-499">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-499">String</span></span>|  
|<span data-ttu-id="b1a92-500">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="b1a92-500">PRIMARY_KEY</span></span>|<span data-ttu-id="b1a92-501">ブール型</span><span class="sxs-lookup"><span data-stu-id="b1a92-501">Boolean</span></span>|  
|<span data-ttu-id="b1a92-502">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="b1a92-502">UNIQUE</span></span>|<span data-ttu-id="b1a92-503">ブール型</span><span class="sxs-lookup"><span data-stu-id="b1a92-503">Boolean</span></span>|  
|<span data-ttu-id="b1a92-504">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="b1a92-504">CLUSTERED</span></span>|<span data-ttu-id="b1a92-505">ブール型</span><span class="sxs-lookup"><span data-stu-id="b1a92-505">Boolean</span></span>|  
|<span data-ttu-id="b1a92-506">TYPE</span><span class="sxs-lookup"><span data-stu-id="b1a92-506">TYPE</span></span>|<span data-ttu-id="b1a92-507">Int32</span><span class="sxs-lookup"><span data-stu-id="b1a92-507">Int32</span></span>|  
|<span data-ttu-id="b1a92-508">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="b1a92-508">FILL_FACTOR</span></span>|<span data-ttu-id="b1a92-509">Int32</span><span class="sxs-lookup"><span data-stu-id="b1a92-509">Int32</span></span>|  
|<span data-ttu-id="b1a92-510">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="b1a92-510">INITIAL_SIZE</span></span>|<span data-ttu-id="b1a92-511">Int32</span><span class="sxs-lookup"><span data-stu-id="b1a92-511">Int32</span></span>|  
|<span data-ttu-id="b1a92-512">NULLS</span><span class="sxs-lookup"><span data-stu-id="b1a92-512">NULLS</span></span>|<span data-ttu-id="b1a92-513">Int32</span><span class="sxs-lookup"><span data-stu-id="b1a92-513">Int32</span></span>|  
|<span data-ttu-id="b1a92-514">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="b1a92-514">SORT_BOOKMARKS</span></span>|<span data-ttu-id="b1a92-515">ブール型</span><span class="sxs-lookup"><span data-stu-id="b1a92-515">Boolean</span></span>|  
|<span data-ttu-id="b1a92-516">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="b1a92-516">AUTO_UPDATE</span></span>|<span data-ttu-id="b1a92-517">ブール型</span><span class="sxs-lookup"><span data-stu-id="b1a92-517">Boolean</span></span>|  
|<span data-ttu-id="b1a92-518">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="b1a92-518">NULL_COLLATION</span></span>|<span data-ttu-id="b1a92-519">Int32</span><span class="sxs-lookup"><span data-stu-id="b1a92-519">Int32</span></span>|  
|<span data-ttu-id="b1a92-520">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b1a92-520">ORDINAL_POSITION</span></span>|<span data-ttu-id="b1a92-521">Int64</span><span class="sxs-lookup"><span data-stu-id="b1a92-521">Int64</span></span>|  
|<span data-ttu-id="b1a92-522">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b1a92-522">COLUMN_NAME</span></span>|<span data-ttu-id="b1a92-523">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-523">String</span></span>|  
|<span data-ttu-id="b1a92-524">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="b1a92-524">COLUMN_GUID</span></span>|<span data-ttu-id="b1a92-525">GUID</span><span class="sxs-lookup"><span data-stu-id="b1a92-525">Guid</span></span>|  
|<span data-ttu-id="b1a92-526">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="b1a92-526">COLUMN_PROPID</span></span>|<span data-ttu-id="b1a92-527">Int64</span><span class="sxs-lookup"><span data-stu-id="b1a92-527">Int64</span></span>|  
|<span data-ttu-id="b1a92-528">COLLATION</span><span class="sxs-lookup"><span data-stu-id="b1a92-528">COLLATION</span></span>|<span data-ttu-id="b1a92-529">Int16</span><span class="sxs-lookup"><span data-stu-id="b1a92-529">Int16</span></span>|  
|<span data-ttu-id="b1a92-530">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="b1a92-530">CARDINALITY</span></span>|<span data-ttu-id="b1a92-531">Decimal (10 進数型)</span><span class="sxs-lookup"><span data-stu-id="b1a92-531">Decimal</span></span>|  
|<span data-ttu-id="b1a92-532">PAGES</span><span class="sxs-lookup"><span data-stu-id="b1a92-532">PAGES</span></span>|<span data-ttu-id="b1a92-533">Int32</span><span class="sxs-lookup"><span data-stu-id="b1a92-533">Int32</span></span>|  
|<span data-ttu-id="b1a92-534">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="b1a92-534">FILTER_CONDITION</span></span>|<span data-ttu-id="b1a92-535">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-535">String</span></span>|  
|<span data-ttu-id="b1a92-536">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="b1a92-536">INTEGRATED</span></span>|<span data-ttu-id="b1a92-537">ブール型</span><span class="sxs-lookup"><span data-stu-id="b1a92-537">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="b1a92-538">Microsoft Jet OLE DB Provider</span><span class="sxs-lookup"><span data-stu-id="b1a92-538">Microsoft Jet OLE DB Provider</span></span>  

 <span data-ttu-id="b1a92-539">Microsoft Jet OLE DB Driver は、共通のスキーマ コレクションに加えて次のスキーマ コレクションをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="b1a92-539">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="b1a92-540">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="b1a92-540">Tables</span></span>  
  
- <span data-ttu-id="b1a92-541">列</span><span class="sxs-lookup"><span data-stu-id="b1a92-541">Columns</span></span>  
  
- <span data-ttu-id="b1a92-542">プロシージャ</span><span class="sxs-lookup"><span data-stu-id="b1a92-542">Procedures</span></span>  
  
- <span data-ttu-id="b1a92-543">Views</span><span class="sxs-lookup"><span data-stu-id="b1a92-543">Views</span></span>  
  
- <span data-ttu-id="b1a92-544">Indexes</span><span class="sxs-lookup"><span data-stu-id="b1a92-544">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="b1a92-545">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="b1a92-545">Tables</span></span>  
  
|<span data-ttu-id="b1a92-546">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b1a92-546">ColumnName</span></span>|<span data-ttu-id="b1a92-547">DataType</span><span class="sxs-lookup"><span data-stu-id="b1a92-547">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b1a92-548">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1a92-548">TABLE_CATALOG</span></span>|<span data-ttu-id="b1a92-549">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-549">String</span></span>|  
|<span data-ttu-id="b1a92-550">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1a92-550">TABLE_SCHEMA</span></span>|<span data-ttu-id="b1a92-551">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-551">String</span></span>|  
|<span data-ttu-id="b1a92-552">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b1a92-552">TABLE_NAME</span></span>|<span data-ttu-id="b1a92-553">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-553">String</span></span>|  
|<span data-ttu-id="b1a92-554">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b1a92-554">TABLE_TYPE</span></span>|<span data-ttu-id="b1a92-555">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-555">String</span></span>|  
|<span data-ttu-id="b1a92-556">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="b1a92-556">TABLE_GUID</span></span>|<span data-ttu-id="b1a92-557">GUID</span><span class="sxs-lookup"><span data-stu-id="b1a92-557">Guid</span></span>|  
|<span data-ttu-id="b1a92-558">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b1a92-558">DESCRIPTION</span></span>|<span data-ttu-id="b1a92-559">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-559">String</span></span>|  
|<span data-ttu-id="b1a92-560">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="b1a92-560">TABLE_PROPID</span></span>|<span data-ttu-id="b1a92-561">Int64</span><span class="sxs-lookup"><span data-stu-id="b1a92-561">Int64</span></span>|  
|<span data-ttu-id="b1a92-562">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="b1a92-562">DATE_CREATED</span></span>|<span data-ttu-id="b1a92-563">DateTime</span><span class="sxs-lookup"><span data-stu-id="b1a92-563">DateTime</span></span>|  
|<span data-ttu-id="b1a92-564">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="b1a92-564">DATE_MODIFIED</span></span>|<span data-ttu-id="b1a92-565">DateTime</span><span class="sxs-lookup"><span data-stu-id="b1a92-565">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="b1a92-566">列</span><span class="sxs-lookup"><span data-stu-id="b1a92-566">Columns</span></span>  
  
|<span data-ttu-id="b1a92-567">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b1a92-567">ColumnName</span></span>|<span data-ttu-id="b1a92-568">DataType</span><span class="sxs-lookup"><span data-stu-id="b1a92-568">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b1a92-569">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1a92-569">TABLE_CATALOG</span></span>|<span data-ttu-id="b1a92-570">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-570">String</span></span>|  
|<span data-ttu-id="b1a92-571">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1a92-571">TABLE_SCHEMA</span></span>|<span data-ttu-id="b1a92-572">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-572">String</span></span>|  
|<span data-ttu-id="b1a92-573">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b1a92-573">TABLE_NAME</span></span>|<span data-ttu-id="b1a92-574">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-574">String</span></span>|  
|<span data-ttu-id="b1a92-575">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b1a92-575">COLUMN_NAME</span></span>|<span data-ttu-id="b1a92-576">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-576">String</span></span>|  
|<span data-ttu-id="b1a92-577">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="b1a92-577">COLUMN_GUID</span></span>|<span data-ttu-id="b1a92-578">GUID</span><span class="sxs-lookup"><span data-stu-id="b1a92-578">Guid</span></span>|  
|<span data-ttu-id="b1a92-579">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="b1a92-579">COLUMN_PROPID</span></span>|<span data-ttu-id="b1a92-580">Int64</span><span class="sxs-lookup"><span data-stu-id="b1a92-580">Int64</span></span>|  
|<span data-ttu-id="b1a92-581">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b1a92-581">ORDINAL_POSITION</span></span>|<span data-ttu-id="b1a92-582">Int64</span><span class="sxs-lookup"><span data-stu-id="b1a92-582">Int64</span></span>|  
|<span data-ttu-id="b1a92-583">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="b1a92-583">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="b1a92-584">ブール型</span><span class="sxs-lookup"><span data-stu-id="b1a92-584">Boolean</span></span>|  
|<span data-ttu-id="b1a92-585">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="b1a92-585">COLUMN_DEFAULT</span></span>|<span data-ttu-id="b1a92-586">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-586">String</span></span>|  
|<span data-ttu-id="b1a92-587">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="b1a92-587">COLUMN_FLAGS</span></span>|<span data-ttu-id="b1a92-588">Int64</span><span class="sxs-lookup"><span data-stu-id="b1a92-588">Int64</span></span>|  
|<span data-ttu-id="b1a92-589">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b1a92-589">IS_NULLABLE</span></span>|<span data-ttu-id="b1a92-590">ブール型</span><span class="sxs-lookup"><span data-stu-id="b1a92-590">Boolean</span></span>|  
|<span data-ttu-id="b1a92-591">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b1a92-591">DATA_TYPE</span></span>|<span data-ttu-id="b1a92-592">Int32</span><span class="sxs-lookup"><span data-stu-id="b1a92-592">Int32</span></span>|  
|<span data-ttu-id="b1a92-593">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="b1a92-593">TYPE_GUID</span></span>|<span data-ttu-id="b1a92-594">GUID</span><span class="sxs-lookup"><span data-stu-id="b1a92-594">Guid</span></span>|  
|<span data-ttu-id="b1a92-595">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b1a92-595">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="b1a92-596">Int64</span><span class="sxs-lookup"><span data-stu-id="b1a92-596">Int64</span></span>|  
|<span data-ttu-id="b1a92-597">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b1a92-597">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="b1a92-598">Int64</span><span class="sxs-lookup"><span data-stu-id="b1a92-598">Int64</span></span>|  
|<span data-ttu-id="b1a92-599">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="b1a92-599">NUMERIC_PRECISION</span></span>|<span data-ttu-id="b1a92-600">Int32</span><span class="sxs-lookup"><span data-stu-id="b1a92-600">Int32</span></span>|  
|<span data-ttu-id="b1a92-601">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="b1a92-601">NUMERIC_SCALE</span></span>|<span data-ttu-id="b1a92-602">Int16</span><span class="sxs-lookup"><span data-stu-id="b1a92-602">Int16</span></span>|  
|<span data-ttu-id="b1a92-603">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="b1a92-603">DATETIME_PRECISION</span></span>|<span data-ttu-id="b1a92-604">Int64</span><span class="sxs-lookup"><span data-stu-id="b1a92-604">Int64</span></span>|  
|<span data-ttu-id="b1a92-605">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1a92-605">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="b1a92-606">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-606">String</span></span>|  
|<span data-ttu-id="b1a92-607">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1a92-607">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="b1a92-608">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-608">String</span></span>|  
|<span data-ttu-id="b1a92-609">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="b1a92-609">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="b1a92-610">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-610">String</span></span>|  
|<span data-ttu-id="b1a92-611">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1a92-611">COLLATION_CATALOG</span></span>|<span data-ttu-id="b1a92-612">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-612">String</span></span>|  
|<span data-ttu-id="b1a92-613">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1a92-613">COLLATION_SCHEMA</span></span>|<span data-ttu-id="b1a92-614">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-614">String</span></span>|  
|<span data-ttu-id="b1a92-615">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="b1a92-615">COLLATION_NAME</span></span>|<span data-ttu-id="b1a92-616">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-616">String</span></span>|  
|<span data-ttu-id="b1a92-617">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1a92-617">DOMAIN_CATALOG</span></span>|<span data-ttu-id="b1a92-618">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-618">String</span></span>|  
|<span data-ttu-id="b1a92-619">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1a92-619">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="b1a92-620">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-620">String</span></span>|  
|<span data-ttu-id="b1a92-621">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="b1a92-621">DOMAIN_NAME</span></span>|<span data-ttu-id="b1a92-622">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-622">String</span></span>|  
|<span data-ttu-id="b1a92-623">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b1a92-623">DESCRIPTION</span></span>|<span data-ttu-id="b1a92-624">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-624">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="b1a92-625">プロシージャ</span><span class="sxs-lookup"><span data-stu-id="b1a92-625">Procedures</span></span>  
  
|<span data-ttu-id="b1a92-626">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b1a92-626">ColumnName</span></span>|<span data-ttu-id="b1a92-627">DataType</span><span class="sxs-lookup"><span data-stu-id="b1a92-627">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b1a92-628">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1a92-628">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="b1a92-629">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-629">String</span></span>|  
|<span data-ttu-id="b1a92-630">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1a92-630">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="b1a92-631">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-631">String</span></span>|  
|<span data-ttu-id="b1a92-632">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b1a92-632">PROCEDURE_NAME</span></span>|<span data-ttu-id="b1a92-633">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-633">String</span></span>|  
|<span data-ttu-id="b1a92-634">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b1a92-634">PROCEDURE_TYPE</span></span>|<span data-ttu-id="b1a92-635">Int16</span><span class="sxs-lookup"><span data-stu-id="b1a92-635">Int16</span></span>|  
|<span data-ttu-id="b1a92-636">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="b1a92-636">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="b1a92-637">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-637">String</span></span>|  
|<span data-ttu-id="b1a92-638">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b1a92-638">DESCRIPTION</span></span>|<span data-ttu-id="b1a92-639">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-639">String</span></span>|  
|<span data-ttu-id="b1a92-640">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="b1a92-640">DATE_CREATED</span></span>|<span data-ttu-id="b1a92-641">DateTime</span><span class="sxs-lookup"><span data-stu-id="b1a92-641">DateTime</span></span>|  
|<span data-ttu-id="b1a92-642">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="b1a92-642">DATE_MODIFIED</span></span>|<span data-ttu-id="b1a92-643">DateTime</span><span class="sxs-lookup"><span data-stu-id="b1a92-643">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="b1a92-644">Views</span><span class="sxs-lookup"><span data-stu-id="b1a92-644">Views</span></span>  
  
|<span data-ttu-id="b1a92-645">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b1a92-645">ColumnName</span></span>|<span data-ttu-id="b1a92-646">DataType</span><span class="sxs-lookup"><span data-stu-id="b1a92-646">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b1a92-647">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1a92-647">TABLE_CATALOG</span></span>|<span data-ttu-id="b1a92-648">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-648">String</span></span>|  
|<span data-ttu-id="b1a92-649">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1a92-649">TABLE_SCHEMA</span></span>|<span data-ttu-id="b1a92-650">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-650">String</span></span>|  
|<span data-ttu-id="b1a92-651">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b1a92-651">TABLE_NAME</span></span>|<span data-ttu-id="b1a92-652">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-652">String</span></span>|  
|<span data-ttu-id="b1a92-653">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="b1a92-653">VIEW_DEFINITION</span></span>|<span data-ttu-id="b1a92-654">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-654">String</span></span>|  
|<span data-ttu-id="b1a92-655">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="b1a92-655">CHECK_OPTION</span></span>|<span data-ttu-id="b1a92-656">ブール型</span><span class="sxs-lookup"><span data-stu-id="b1a92-656">Boolean</span></span>|  
|<span data-ttu-id="b1a92-657">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="b1a92-657">IS_UPDATABLE</span></span>|<span data-ttu-id="b1a92-658">ブール型</span><span class="sxs-lookup"><span data-stu-id="b1a92-658">Boolean</span></span>|  
|<span data-ttu-id="b1a92-659">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b1a92-659">DESCRIPTION</span></span>|<span data-ttu-id="b1a92-660">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-660">String</span></span>|  
|<span data-ttu-id="b1a92-661">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="b1a92-661">DATE_CREATED</span></span>|<span data-ttu-id="b1a92-662">DateTime</span><span class="sxs-lookup"><span data-stu-id="b1a92-662">DateTime</span></span>|  
|<span data-ttu-id="b1a92-663">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="b1a92-663">DATE_MODIFIED</span></span>|<span data-ttu-id="b1a92-664">DateTime</span><span class="sxs-lookup"><span data-stu-id="b1a92-664">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="b1a92-665">Indexes</span><span class="sxs-lookup"><span data-stu-id="b1a92-665">Indexes</span></span>  
  
|<span data-ttu-id="b1a92-666">ColumnName</span><span class="sxs-lookup"><span data-stu-id="b1a92-666">ColumnName</span></span>|<span data-ttu-id="b1a92-667">DataType</span><span class="sxs-lookup"><span data-stu-id="b1a92-667">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b1a92-668">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1a92-668">TABLE_CATALOG</span></span>|<span data-ttu-id="b1a92-669">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-669">String</span></span>|  
|<span data-ttu-id="b1a92-670">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1a92-670">TABLE_SCHEMA</span></span>|<span data-ttu-id="b1a92-671">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-671">String</span></span>|  
|<span data-ttu-id="b1a92-672">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b1a92-672">TABLE_NAME</span></span>|<span data-ttu-id="b1a92-673">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-673">String</span></span>|  
|<span data-ttu-id="b1a92-674">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1a92-674">INDEX_CATALOG</span></span>|<span data-ttu-id="b1a92-675">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-675">String</span></span>|  
|<span data-ttu-id="b1a92-676">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1a92-676">INDEX_SCHEMA</span></span>|<span data-ttu-id="b1a92-677">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-677">String</span></span>|  
|<span data-ttu-id="b1a92-678">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="b1a92-678">INDEX_NAME</span></span>|<span data-ttu-id="b1a92-679">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-679">String</span></span>|  
|<span data-ttu-id="b1a92-680">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="b1a92-680">PRIMARY_KEY</span></span>|<span data-ttu-id="b1a92-681">ブール型</span><span class="sxs-lookup"><span data-stu-id="b1a92-681">Boolean</span></span>|  
|<span data-ttu-id="b1a92-682">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="b1a92-682">UNIQUE</span></span>|<span data-ttu-id="b1a92-683">ブール型</span><span class="sxs-lookup"><span data-stu-id="b1a92-683">Boolean</span></span>|  
|<span data-ttu-id="b1a92-684">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="b1a92-684">CLUSTERED</span></span>|<span data-ttu-id="b1a92-685">ブール型</span><span class="sxs-lookup"><span data-stu-id="b1a92-685">Boolean</span></span>|  
|<span data-ttu-id="b1a92-686">TYPE</span><span class="sxs-lookup"><span data-stu-id="b1a92-686">TYPE</span></span>|<span data-ttu-id="b1a92-687">Int32</span><span class="sxs-lookup"><span data-stu-id="b1a92-687">Int32</span></span>|  
|<span data-ttu-id="b1a92-688">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="b1a92-688">FILL_FACTOR</span></span>|<span data-ttu-id="b1a92-689">Int32</span><span class="sxs-lookup"><span data-stu-id="b1a92-689">Int32</span></span>|  
|<span data-ttu-id="b1a92-690">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="b1a92-690">INITIAL_SIZE</span></span>|<span data-ttu-id="b1a92-691">Int32</span><span class="sxs-lookup"><span data-stu-id="b1a92-691">Int32</span></span>|  
|<span data-ttu-id="b1a92-692">NULLS</span><span class="sxs-lookup"><span data-stu-id="b1a92-692">NULLS</span></span>|<span data-ttu-id="b1a92-693">Int32</span><span class="sxs-lookup"><span data-stu-id="b1a92-693">Int32</span></span>|  
|<span data-ttu-id="b1a92-694">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="b1a92-694">SORT_BOOKMARKS</span></span>|<span data-ttu-id="b1a92-695">ブール型</span><span class="sxs-lookup"><span data-stu-id="b1a92-695">Boolean</span></span>|  
|<span data-ttu-id="b1a92-696">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="b1a92-696">AUTO_UPDATE</span></span>|<span data-ttu-id="b1a92-697">ブール型</span><span class="sxs-lookup"><span data-stu-id="b1a92-697">Boolean</span></span>|  
|<span data-ttu-id="b1a92-698">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="b1a92-698">NULL_COLLATION</span></span>|<span data-ttu-id="b1a92-699">Int32</span><span class="sxs-lookup"><span data-stu-id="b1a92-699">Int32</span></span>|  
|<span data-ttu-id="b1a92-700">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b1a92-700">ORDINAL_POSITION</span></span>|<span data-ttu-id="b1a92-701">Int64</span><span class="sxs-lookup"><span data-stu-id="b1a92-701">Int64</span></span>|  
|<span data-ttu-id="b1a92-702">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b1a92-702">COLUMN_NAME</span></span>|<span data-ttu-id="b1a92-703">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-703">String</span></span>|  
|<span data-ttu-id="b1a92-704">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="b1a92-704">COLUMN_GUID</span></span>|<span data-ttu-id="b1a92-705">GUID</span><span class="sxs-lookup"><span data-stu-id="b1a92-705">Guid</span></span>|  
|<span data-ttu-id="b1a92-706">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="b1a92-706">COLUMN_PROPID</span></span>|<span data-ttu-id="b1a92-707">Int64</span><span class="sxs-lookup"><span data-stu-id="b1a92-707">Int64</span></span>|  
|<span data-ttu-id="b1a92-708">COLLATION</span><span class="sxs-lookup"><span data-stu-id="b1a92-708">COLLATION</span></span>|<span data-ttu-id="b1a92-709">Int16</span><span class="sxs-lookup"><span data-stu-id="b1a92-709">Int16</span></span>|  
|<span data-ttu-id="b1a92-710">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="b1a92-710">CARDINALITY</span></span>|<span data-ttu-id="b1a92-711">Decimal (10 進数型)</span><span class="sxs-lookup"><span data-stu-id="b1a92-711">Decimal</span></span>|  
|<span data-ttu-id="b1a92-712">PAGES</span><span class="sxs-lookup"><span data-stu-id="b1a92-712">PAGES</span></span>|<span data-ttu-id="b1a92-713">Int32</span><span class="sxs-lookup"><span data-stu-id="b1a92-713">Int32</span></span>|  
|<span data-ttu-id="b1a92-714">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="b1a92-714">FILTER_CONDITION</span></span>|<span data-ttu-id="b1a92-715">String</span><span class="sxs-lookup"><span data-stu-id="b1a92-715">String</span></span>|  
|<span data-ttu-id="b1a92-716">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="b1a92-716">INTEGRATED</span></span>|<span data-ttu-id="b1a92-717">ブール型</span><span class="sxs-lookup"><span data-stu-id="b1a92-717">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b1a92-718">関連項目</span><span class="sxs-lookup"><span data-stu-id="b1a92-718">See also</span></span>

- [<span data-ttu-id="b1a92-719">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="b1a92-719">ADO.NET Overview</span></span>](ado-net-overview.md)
