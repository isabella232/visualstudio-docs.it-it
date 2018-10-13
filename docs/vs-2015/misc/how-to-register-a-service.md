---
title: 'Procedura: registrare un servizio | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- services, registering
ms.assetid: d086be78-ec3c-43cc-b799-5180a71e19f1
caps.latest.revision: 16
manager: douge
ms.openlocfilehash: a1f8026a648b2a0809af17664d4399f815c329be
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49206258"
---
# <a name="how-to-register-a-service"></a>Procedura: Registrare un servizio
Il framework di pacchetto gestito (MPF) fornisce gli attributi per controllare la registrazione dei servizi gestiti. L'utilità RegPkg usa questi attributi per registrare un servizio con [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="example"></a>Esempio  
 Il codice che segue proviene [esempi di VSSDK](../misc/vssdk-samples.md).  
  
 [!code-csharp[VSSDKRegisterService#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkregisterservice/cs/vssdkregisterservicepackage.cs#1)]
 [!code-vb[VSSDKRegisterService#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkregisterservice/vb/vssdkregisterservicepackage.vb#1)]  
  
 L'attributo <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> registra il servizio SMyGlobalService con [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Per altre informazioni sulle <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> e <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>, vedere [la registrazione e annullamento della registrazione dei pacchetti VSPackage](../extensibility/registering-and-unregistering-vspackages.md).  
  
 Per registrare un servizio che sostituisce un altro servizio con lo stesso nome, usare l'attributo <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute> anziché l'attributo <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>.  
  
## <a name="robust-programming"></a>Programmazione efficiente  
 Per semplificare la ricompilazione di un provider di servizi senza modificare il client del servizio, o viceversa, è possibile definire il servizio e le relative interfacce in un modulo di assembly separato. Il codice seguente proviene dal file IMyGlobalService.cs nell'esempio Reference.Services (C#).  
  
 [!code-csharp[VSSDKRegisterService#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkregisterservice/cs/vssdkregisterservicepackage.cs#2)]
 [!code-vb[VSSDKRegisterService#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkregisterservice/vb/vssdkregisterservicepackage.vb#2)]  
  
 L'attributo <xref:System.Runtime.InteropServices.ComVisibleAttribute> è necessario per ottenere l'interfaccia dal codice non gestito.  
  
> [!NOTE]
>  Nonostante sia possibile usare lo stesso tipo o GUID per il servizio e l'interfaccia, è consigliabile separarli perché un servizio può esporre interfacce diverse.  
  
## <a name="see-also"></a>Vedere anche  
 [Registrazione di pacchetti VSPackage](http://msdn.microsoft.com/en-us/31e6050f-1457-4849-944a-a3c36b76f3dd)   
 [Nozioni fondamentali sui servizi](../extensibility/internals/service-essentials.md)