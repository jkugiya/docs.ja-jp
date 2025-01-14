---
title: .NET Core と .NET 5 以降でサポートされていない API
titleSuffix: ''
description: .Net Core と .NET 5 以降のバージョンで常に例外をスローする .NET API について学習します。
ms.date: 10/13/2020
ms.openlocfilehash: b0dc425bf5f7d8f2a44f51ffe75ffcb0c8a5a7ae
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256258"
---
# <a name="apis-that-always-throw-exceptions-on-net-core-and-net-5"></a>.NET Core と .NET 5 以降で常に例外をスローする API

次の API を使用すると、プラットフォームのすべてまたはサブセットの .NET 5 以降 (.NET Core のすべてのバージョンを含む) で、<xref:System.PlatformNotSupportedException> が常にスローされます。

この記事では、影響を受ける API を名前空間別に整理しています。

> [!NOTE]
>
> - この記事は、作業中です。 .NET 5 以降で例外をスローする API の完全な一覧ではありません。
> - この記事には、.NET 5 以降でスローされるバイナリ シリアル化用の明示的なインターフェイス実装は含まれていません。 詳細については、[.NET Core でのバイナリ シリアル化](../../standard/serialization/binary-serialization.md#net-core)に関する記事を参照してください。

## <a name="system"></a>システム

| メンバー | スローするプラットフォーム |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | All |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | すべて |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | Linux と macOS |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | Linux と macOS |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | すべて |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | All |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | All |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | All |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | All |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | すべて |

## <a name="systemcodedomcompiler"></a>System.CodeDom.Compiler

| メンバー | スローするプラットフォーム |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | All |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | All |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | すべて |

## <a name="systemcollectionsspecialized"></a>System.Collections.Specialized

| メンバー | スローするプラットフォーム |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | All |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | All |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | すべて |

## <a name="systemconfiguration"></a>System.Configuration

| メンバー | スローするプラットフォーム |
| - | - |
| <xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (すべてのメンバー) | すべて |

## <a name="systemconsole"></a>System.Console

| メンバー | スローするプラットフォーム |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | Linux と macOS |
| <xref:System.Console.BufferHeight?displayProperty=nameWithType> (set のみ) | Linux と macOS |
| <xref:System.Console.BufferWidth?displayProperty=nameWithType> (set のみ) | Linux と macOS |
| <xref:System.Console.CursorSize?displayProperty=nameWithType> (set のみ) | Linux と macOS |
| <xref:System.Console.CursorVisible?displayProperty=nameWithType> (get のみ) | Linux と macOS |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | Linux と macOS |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | Linux と macOS |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | Linux と macOS |
| <xref:System.Console.Title?displayProperty=nameWithType> (get のみ) | Linux と macOS |
| <xref:System.Console.WindowHeight?displayProperty=nameWithType> (set のみ) | Linux と macOS |
| <xref:System.Console.WindowLeft?displayProperty=nameWithType> (set のみ) | Linux と macOS |
| <xref:System.Console.WindowTop?displayProperty=nameWithType> (set のみ) | Linux と macOS |
| <xref:System.Console.WindowWidth?displayProperty=nameWithType> (set のみ) | Linux と macOS |

## <a name="systemdatacommon"></a>System.Data.Common

| メンバー | スローするプラットフォーム |
| - | - |
| <xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (<xref:System.NotSupportedException> をスローする) | すべて |

## <a name="systemdiagnosticsprocess"></a>System.Diagnostics.Process

| メンバー | スローするプラットフォーム |
| - | - |
| <xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set のみ) | Linux |
| <xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set のみ) | Linux |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | macOS |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | Linux と macOS |
| <xref:System.Diagnostics.Process.Start(System.String,System.String,System.String,System.Security.SecureString,System.String)?displayProperty=nameWithType> | Linux と macOS |
| <xref:System.Diagnostics.Process.Start(System.String,System.String,System.Security.SecureString,System.String)?displayProperty=nameWithType> | Linux と macOS |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | Linux と macOS |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | Linux と macOS |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | Linux と macOS |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | Linux と macOS |
| <xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set のみ) | Linux と macOS |
| <xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get のみ) | macOS |
| <xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set のみ) | Linux と macOS |

## <a name="systemio"></a>System.IO

| メンバー | スローするプラットフォーム |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | All |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | すべて |

## <a name="systemiopipes"></a>System.IO.Pipes

| メンバー | スローするプラットフォーム |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | Linux と macOS |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | Linux と macOS |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | Linux と macOS |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | Linux と macOS |
| <xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set のみ) | Linux と macOS |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | Linux と macOS |

## <a name="systemmedia"></a>System.Media

| メンバー | スローするプラットフォーム |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | すべて |

## <a name="systemnet"></a>System.Net

| メンバー | スローするプラットフォーム |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | All |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | All |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | All |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | All |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | All |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | All |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | All |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | All |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | All |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | All |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | All |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | All |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | All |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | All |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | All |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | All |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | すべて |

## <a name="systemnetnetworkinformation"></a>System.Net.NetworkInformation

| メンバー | スローするプラットフォーム |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | Windows (UWP) |

## <a name="systemnetsockets"></a>System.Net.Sockets

| メンバー | スローするプラットフォーム |
| - | - |
| <xref:System.Net.Sockets.Socket.%23ctor(System.Net.Sockets.SocketInformation)> | All |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | すべて |

## <a name="systemnetwebsockets"></a>System.Net.WebSockets

| メンバー | スローするプラットフォーム |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | すべて |

## <a name="systemreflection"></a>System.Reflection

| メンバー | スローするプラットフォーム |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | All |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | All |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | All |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | All |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)> | All |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | All |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | すべて |

## <a name="systemruntimecompilerservices"></a>System.Runtime.CompilerServices

| メンバー | スローするプラットフォーム |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | すべて |

## <a name="systemruntimeinteropservices"></a>System.Runtime.InteropServices

| メンバー | スローするプラットフォーム |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | All |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | All |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | All |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | すべて |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | Linux と macOS |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | Linux と macOS |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | Linux と macOS |

## <a name="systemruntimeserialization"></a>System.Runtime.Serialization

| メンバー | スローするプラットフォーム |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | すべて |

## <a name="systemsecurity"></a>System.Security

| メンバー | スローするプラットフォーム |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | All |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | All |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | All |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | All |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | All |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | All |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | All |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | All |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | All |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | All |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | All |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | All |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | All |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | すべて |

## <a name="systemsecurityclaims"></a>System.Security.Claims

| メンバー | スローするプラットフォーム |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | All |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | All |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)> | All |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | All |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | すべて |

## <a name="systemsecuritycryptography"></a>System.Security.Cryptography

| メンバー | スローするプラットフォーム |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | すべて |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A> | Linux と macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | Linux と macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | Linux と macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | Linux と macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | Linux と macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | Linux と macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | Linux と macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | Linux と macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | Linux と macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | Linux と macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | Linux と macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | Linux と macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | Linux と macOS |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | すべて |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | All |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | All |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | All |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | All |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | All |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | All |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | すべて |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | Linux と macOS |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | Linux と macOS |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | すべて |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | All |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | All |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | すべて |

## <a name="systemsecuritycryptographypkcs"></a>System.Security.Cryptography.Pkcs

| メンバー | スローするプラットフォーム |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)> | All |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | すべて |

## <a name="systemsecuritycryptographyx509certificates"></a>System.Security.Cryptography.X509Certificates

| メンバー | スローするプラットフォーム |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | All |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | All |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | すべて |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set のみ) | すべて |

## <a name="systemsecurityauthenticationextendedprotection"></a>System.Security.Authentication.ExtendedProtection

| メンバー | スローするプラットフォーム |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | すべて |

## <a name="systemsecuritypolicy"></a>System.Security.Policy

| メンバー | スローするプラットフォーム |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | すべて |

## <a name="systemserviceprocessservicecontroller"></a>System.ServiceProcess.ServiceController

| メンバー | スローするプラットフォーム |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | すべて |

## <a name="systemtextregularexpressions"></a>System.Text.RegularExpressions

| メンバー | スローするプラットフォーム |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | すべて |

## <a name="systemthreading"></a>System.Threading

| メンバー | スローするプラットフォーム |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | All |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | All |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | All |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | All |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | All |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | すべて |

## <a name="systemxml"></a>System.Xml

| メンバー | スローするプラットフォーム |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | All |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | All |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | すべて |

## <a name="see-also"></a>関連項目

- [.NET Framework から .NET Core への移行の破壊的変更](fx-core.md)
- [.NET Core でのバイナリ シリアル化](../../standard/serialization/binary-serialization.md#net-core)
- [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md)
