---
title: Servizio Essentials | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 90cec13c403194c70b9d44cff349b53495a0e160
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51776460"
---
# <a name="service-essentials"></a>Nozioni fondamentali sui servizi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un servizio è un contratto tra due pacchetti VSPackage. Un pacchetto VSPackage fornisce un set specifico di interfacce per un altro VSPackage da utilizzare. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] è a sua volta una raccolta di VSPackage che fornisce servizi per gli altri pacchetti VSPackage.  
  
 Ad esempio, è possibile utilizzare il servizio SVsActivityLog per ottenere un'interfaccia IVsActivityLog, che è possibile usare per scrivere nel log attività. Per altre informazioni, vedere [procedura: usare il Log attività](../../extensibility/how-to-use-the-activity-log.md).  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] fornisce anche alcuni servizi predefiniti che non sono registrati. Pacchetti VSPackage possono sostituire incorporati o altri servizi, fornendo un override del servizio. Sostituzione di un solo servizio è consentito per qualsiasi servizio.  
  
 Servizi non dispongono di alcuna esposizione al rilevamento. Pertanto, è necessario conoscere l'ID di servizio (SID) di un servizio che si desidera utilizzare, ed è necessario conoscere quali interfacce offre. La documentazione di riferimento per il servizio fornisce queste informazioni.  
  
-   Pacchetti VSPackage che forniscono servizi vengono chiamati i provider di servizi.  
  
-   I servizi forniti da altri pacchetti VSPackage sono denominati servizi globali.  
  
-   Servizi sono disponibili solo per il pacchetto VSPackage che li implementa o per tutti gli oggetti che vengono creati, sono denominati servizi locali.  
  
-   I servizi che sostituiscono i servizi incorporati o i servizi forniti da altri pacchetti, vengono chiamati servizio esegue l'override.  
  
-   I servizi o le sostituzioni di servizio, vengono caricate su richiesta, vale a dire, il provider del servizio viene caricato quando il servizio che fornisce è richiesto da un altro pacchetto VSPackage.  
  
-   Per supportare il caricamento su richiesta, un provider del servizio registra i suoi servizi globali con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Per altre informazioni, vedere [registrazione dei servizi](../../misc/registering-services.md).  
  
-   Dopo aver ottenuto un servizio, usare [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) (codice non gestito) o al cast (codice gestito) per ottenere l'interfaccia desiderata, ad esempio:  
  
    ```vb  
    TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
    ```  
  
    ```csharp  
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
  
    ```  
  
-   Codice gestito fa riferimento a un servizio in base al tipo, mentre il codice non gestito si riferisce a un servizio con il relativo GUID.  
  
-   Quando [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] carica un pacchetto VSPackage, passa un provider di servizi a VSPackage per consentire l'accesso a VSPackage per servizi globali. Ciò è detto "posizione" il pacchetto VSPackage.  
  
-   I VSPackage possono essere i provider di servizi per gli oggetti creati. Ad esempio, un modulo potrebbe inviare una richiesta per un servizio di colore per il frame, che potrà passare alla richiesta [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
-   Gli oggetti gestiti che sono molto annidati, o non individuati affatto, possono chiamare <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> per l'accesso diretto ai servizi globali. Per altre informazioni, vedere [procedura: usare GetGlobalService](../../misc/how-to-use-getglobalservice.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Elenco dei servizi disponibili](../../extensibility/internals/list-of-available-services.md)   
 [Uso e fornitura di servizi](../../extensibility/using-and-providing-services.md)   
 [Cast e conversioni di tipi](http://msdn.microsoft.com/library/568df58a-d292-4b55-93ba-601578722878)   
 [Cast](http://msdn.microsoft.com/library/3dbeb06e-2f4b-4693-832d-624bc8ec95de)

