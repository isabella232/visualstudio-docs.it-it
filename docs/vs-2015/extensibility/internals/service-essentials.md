---
title: Servizi essenziali | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 407dda2f203b7be20b19c0e296caa9ce1c95b32c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696072"
---
# <a name="service-essentials"></a>Nozioni fondamentali sui servizi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un servizio è un contratto tra due pacchetti VSPackage. Un pacchetto VSPackage fornisce un set specifico di interfacce per l'utilizzo da parte di un altro VSPackage. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] è a sua volta una raccolta di pacchetti VSPackage che fornisce servizi ad altri pacchetti VSPackage.  
  
 Ad esempio, è possibile usare il servizio SVsActivityLog per ottenere un'interfaccia IVsActivityLog, che può essere usata per scrivere nel log attività. Per altre informazioni, vedere [procedura: usare il log attività](../../extensibility/how-to-use-the-activity-log.md).  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] fornisce anche alcuni servizi predefiniti che non sono registrati. I pacchetti VSPackage possono sostituire i servizi predefiniti o altri fornendo un override del servizio. Per qualsiasi servizio è consentita una sola sostituzione del servizio.  
  
 I servizi non hanno individuabilità. Pertanto, è necessario essere a conoscenza dell'identificatore del servizio (SID) di un servizio che si desidera utilizzare ed è necessario stabilire quali interfacce sono disponibili. La documentazione di riferimento per il servizio fornisce queste informazioni.  
  
- I pacchetti VSPackage che forniscono servizi sono detti provider di servizi.  
  
- I servizi forniti ad altri pacchetti VSPackage sono denominati servizi globali.  
  
- I servizi disponibili solo per il pacchetto VSPackage che li implementa, o per qualsiasi oggetto creato, sono denominati servizi locali.  
  
- I servizi che sostituiscono i servizi o i servizi predefiniti forniti da altri pacchetti sono detti override del servizio.  
  
- I servizi o le sostituzioni dei servizi vengono caricati su richiesta, ovvero il provider di servizi viene caricato quando il servizio fornito viene richiesto da un altro pacchetto VSPackage.  
  
- Per supportare il caricamento su richiesta, un provider di servizi registra i servizi globali con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Per ulteriori informazioni, vedere la pagina relativa alla [registrazione dei servizi](../../misc/registering-services.md).  
  
- Dopo aver ottenuto un servizio, usare [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) (codice non gestito) o eseguire il cast (codice gestito) per ottenere l'interfaccia desiderata, ad esempio:  
  
    ```vb  
    TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
    ```  
  
    ```csharp  
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
  
    ```  
  
- Il codice gestito fa riferimento a un servizio in base al relativo tipo, mentre il codice non gestito fa riferimento a un servizio in base al relativo GUID.  
  
- Quando [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] carica un pacchetto VSPackage, passa un provider di servizi al pacchetto VSPackage per concedere all'accesso VSPackage ai servizi globali. Questa operazione è detta "Ubicazione" del pacchetto VSPackage.  
  
- I pacchetti VSPackage possono essere provider di servizi per gli oggetti creati. Un modulo, ad esempio, potrebbe inviare una richiesta per un servizio color al relativo frame, che potrebbe passare la richiesta a [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
- Gli oggetti gestiti che sono annidati in modo approfondito o che non sono in alcun sito possono chiamare <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> per l'accesso diretto ai servizi globali. Per altre informazioni, vedere [procedura: usare GetGlobalService](../../misc/how-to-use-getglobalservice.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Elenco dei servizi disponibili](../../extensibility/internals/list-of-available-services.md)   
 [Uso e fornitura di servizi](../../extensibility/using-and-providing-services.md)   
 [Cast e conversioni di tipi](https://msdn.microsoft.com/library/568df58a-d292-4b55-93ba-601578722878)   
 [Cast](https://msdn.microsoft.com/library/3dbeb06e-2f4b-4693-832d-624bc8ec95de)
