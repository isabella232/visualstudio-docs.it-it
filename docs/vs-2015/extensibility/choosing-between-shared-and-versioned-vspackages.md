---
title: Scelta tra VSPackage condivisi e con versione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- SxS
- side-by-side installation
- installation [Visual Studio SDK], side-by-side
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 289e506d3cd404bba9a3a63d97179b89a948d381
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "67821972"
---
# <a name="choosing-between-shared-and-versioned-vspackages"></a>Scelta tra pacchetti VSPackage condivisi e con versione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diverse versioni di Visual Studio possono coesistere nello stesso computer. I pacchetti VSPackage possono supportare qualsiasi combinazione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] versioni.  
  
 È possibile abilitare installazioni affiancate dei pacchetti VSPackage tramite una delle due strategie, la strategia condivisa o la strategia con versione. Entrambi gli adattano la presenza di più versioni di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e delle versioni associate di [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .  
  
 Nella strategia condivisa, un pacchetto VSPackage viene registrato per l'uso in più versioni di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Nella strategia con versione sono installate più dll VSPackage, una per ogni versione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] supportata.  
  
## <a name="shared-vspackages"></a>Pacchetti VSPackage condivisi  
 L'uso di un pacchetto VSPackage condiviso è adatto quando si usa lo stesso pacchetto VSPackage in più versioni di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Per implementare un pacchetto VSPackage condiviso, è necessario eseguire i passaggi seguenti:  
  
- Rendere compatibile il pacchetto VSPackage con più versioni di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Sono disponibili due modi per eseguire questa operazione:  
  
  - Limitare il pacchetto VSPackage a utilizzando solo le funzionalità della versione più recente di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] supportata.  

  - Programmare il pacchetto VSPackage per adattarsi alla versione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] in cui è in esecuzione. Se quindi le query per i servizi più recenti hanno esito negativo, il pacchetto VSPackage può offrire altri servizi supportati nelle versioni precedenti di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
- Registrare il pacchetto VSPackage in modo appropriato. Per ulteriori informazioni, vedere la pagina relativa alla registrazione [VSPackage](../extensibility/internals/vspackage-registration.md) e alla [registrazione di VSPackage gestita](https://msdn.microsoft.com/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1).  
  
- Registrare le estensioni di file in modo appropriato. Per ulteriori informazioni, vedere [la pagina relativa alla registrazione delle estensioni di file per le distribuzioni side-by-side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
- Creare un programma di installazione che distribuisce il pacchetto VSPackage per le versioni appropriate di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Per altre informazioni, vedere [installazione di VSPackage con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) e [gestione dei componenti](../extensibility/internals/component-management.md).  
  
- Risolvere il problema dei conflitti di registrazione. Per ulteriori informazioni, vedere la pagina relativa alla [registrazione di VSPackage](../extensibility/internals/vspackage-registration.md).  
  
- Assicurarsi che i file condivisi e con versione rispettino il conteggio dei riferimenti per consentire l'installazione e la rimozione sicure di più versioni. Per ulteriori informazioni, vedere [gestione dei componenti](../extensibility/internals/component-management.md).  
  
## <a name="versioned-vspackages"></a>Pacchetti VSPackage con versione  
 Con la strategia VSPackage con versione è possibile creare un pacchetto VSPackage per ogni versione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] supportata. Questa operazione è appropriata quando si prevede di sfruttare i servizi forniti dalle versioni successive di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , perché ogni VSPackage può evolvere senza influire sugli altri. Tuttavia, la strategia con versione per la creazione di più file binari, da una singola codebase o da più basi di codice indipendenti, può comportare uno sviluppo iniziale maggiore rispetto alla strategia condivisa. Inoltre, potrebbe essere necessario un lavoro di installazione aggiuntivo perché è necessario creare una configurazione separata per ogni versione o una singola installazione che rilevi le versioni di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] installate e supportate dal pacchetto VSPackage.  
  
## <a name="binary-compatibility"></a>Compatibilità binaria  
 In genere, la compatibilità binaria consente ai pacchetti VSPackage di codice nativo sviluppati con versioni precedenti di Visual Studio di essere eseguiti nelle versioni successive di Visual Studio. Tuttavia, esistono tre eccezioni importanti:  
  
- Se il pacchetto VSPackage si basa su una versione specifica del Common Language Runtime, è necessario determinare in quale versione di è in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] esecuzione.  
  
- Un pacchetto VSPackage può avere una dipendenza da una funzionalità specifica di un altro pacchetto VSPackage o di un altro prodotto. Di conseguenza, il pacchetto VSPackage può essere eseguito solo quando la dipendenza viene soddisfatta.  
  
- Un pacchetto VSPackage potrebbe essere influenzato da una correzione di sicurezza in una [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Service Pack o in una versione successiva di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . In questi casi, un pacchetto VSPackage sviluppato con una versione precedente di [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] potrebbe non essere eseguito nelle versioni di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dopo l'applicazione della correzione di sicurezza. Tuttavia, è possibile ricompilare il pacchetto con la versione più recente ed eseguirlo anche nelle versioni precedenti.  
  
  I pacchetti VSPackage gestiti devono essere compilati utilizzando una versione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] che corrisponda alla versione di destinazione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
  Oltre a pianificare la compatibilità binaria per i file binari VSPackage, è necessario considerare anche i formati di file di soluzione e di progetto. Se il pacchetto VSPackage crea un nuovo tipo di progetto, è necessario decidere se può essere eseguito in una sola versione o in più versioni di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Per ulteriori informazioni, vedere [aggiornamento di progetti personalizzati](../misc/upgrading-custom-projects.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Installazione di VSPackage con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md)   
 [Gestione dei componenti](../extensibility/internals/component-management.md)
