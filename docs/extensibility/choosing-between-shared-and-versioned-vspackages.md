---
title: Scelta tra pacchetti VSPackage condivisi e con controllo delle versioni | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- SxS
- side-by-side installation
- installation [Visual Studio SDK], side-by-side
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 62033dc78e5595cefdf4f3ae39a95e68c64b9ee4
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2018
ms.locfileid: "44283223"
---
# <a name="choose-between-shared-and-versioned-vspackages"></a>Scegliere tra pacchetti VSPackage condivisi e con controllo delle versioni
Versioni diverse di Visual Studio possono coesistere nello stesso computer. I pacchetti VSPackage possono supportare qualsiasi combinazione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] versioni.  
  
 È possibile abilitare le installazioni side-by-side di pacchetti VSPackage tramite una delle due strategie, la strategia condivisa o la strategia di controllo delle versioni. Entrambi contenere la presenza di più versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e versioni di associati il [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 Nella strategia di condiviso, un pacchetto VSPackage è registrato per l'uso in più versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Nella strategia di controllo delle versioni, sono installate più DLL di VSPackage, uno per ogni versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] supportate.  
  
## <a name="shared-vspackages"></a>Pacchetti VSPackage condivisi  
 Usando un pacchetto VSPackage condiviso è appropriato quando si usa il pacchetto VSPackage stesso in più versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Per implementare un package VS condivisi, è necessario eseguire i passaggi seguenti:  
  
-   Rendere compatibili con più versioni del pacchetto VSPackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Due modalità di esecuzione sono pertanto disponibili:  
  
    -   Limitare il pacchetto VSPackage per usare solo le funzionalità dalla versione meno recente di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] supportate.  
  
    -   Programmare il pacchetto VSPackage per adattarsi alla versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] in cui è in esecuzione. Quindi, se le query per i servizi più recenti hanno esito negativo, il pacchetto VSPackage può offrire altri servizi che sono supportati nelle versioni precedenti di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Registrare il VSPackage in modo appropriato. Per altre informazioni, vedere [registrazione di pacchetti VSPackage](../extensibility/internals/vspackage-registration.md) e [registrazione di pacchetti VSPackage gestiti](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1).  
  
-   Registrare le estensioni di file in modo appropriato. Per altre informazioni, vedere [la registrazione di estensioni di file per le distribuzioni side-by-side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
-   Creare un programma di installazione che consente di distribuire il pacchetto VSPackage per le versioni appropriate di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Per altre informazioni, vedere [installazione di pacchetti VSPackage con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) e [gestione dei componenti](../extensibility/internals/component-management.md).  
  
-   Risolvere il problema dei conflitti di registrazione. Per altre informazioni, vedere [registrazione di pacchetti VSPackage](../extensibility/internals/vspackage-registration.md).  
  
-   Assicurarsi che i file sia condivisi sia con controllo delle versioni rispettino per consentire l'installazione sicura e la rimozione di più versioni di conteggio dei riferimenti. Per altre informazioni, vedere [gestione dei componenti](../extensibility/internals/component-management.md).  
  
## <a name="versioned-vspackages"></a>Pacchetti VSPackage con controllo delle versioni  
 Sotto la strategia di VSPackage con controllo delle versioni, si crea un pacchetto VSPackage per ogni versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] supportate. Questa operazione è appropriata se si prevede di sfruttare i vantaggi dei servizi forniti dalle versioni più recenti di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], perché ogni pacchetto VSPackage può evolversi senza influire sulle altre. Tuttavia, la strategia di creazione di più file binari, da una singola codebase o da più basi di codice indipendenti, con controllo delle versioni può comportare ulteriori attività iniziali di sviluppo più la strategia condivisa. Inoltre, operazioni di configurazione aggiuntivi potrebbero essere necessari perché è necessario creare un programma di installazione separato per ogni versione né di un unico programma di installazione che rileva le versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] che siano installati e che supporta il pacchetto VSPackage.  
  
## <a name="binary-compatibility"></a>Compatibilità binaria  
 In generale, la compatibilità binaria consente codice nativo i pacchetti VSPackage sviluppati con versioni precedenti di Visual Studio per l'esecuzione nelle versioni più recenti di Visual Studio. Tuttavia, esistono tre importanti eccezioni:  
  
-   Se il pacchetto VSPackage si basa su una particolare versione di common language runtime, quindi è necessario determinare in quale versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] è in esecuzione.  
  
-   Un pacchetto VSPackage potrebbe avere una dipendenza su una funzionalità specifica di un altro VSPackage o di un altro prodotto. Di conseguenza, il pacchetto VSPackage può essere eseguito solo in cui la dipendenza viene soddisfatta.  
  
-   Un pacchetto VSPackage può essere influenzato da una correzione di sicurezza in un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] service pack o una versione successiva di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. In questi casi, un pacchetto VSPackage sviluppati con una versione precedente del [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] potrebbe non funzionare nelle versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dopo la correzione di sicurezza è stata applicata. Tuttavia, è possibile ricompilare il pacchetto con la versione più recente e anche eseguirlo nelle versioni precedenti.  
  
 I VSPackage gestiti devono essere creati usando una versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e il [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] che corrisponde alla versione di destinazione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Oltre alla pianificazione per la compatibilità binaria per i file binari del pacchetto VSPackage, è anche necessario prendere in considerazione soluzioni e formati di file di progetto. Se il pacchetto VSPackage viene creato un nuovo tipo di progetto, è necessario decidere se può essere eseguito solo una versione o in più versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Per altre informazioni, vedere [aggiornamento di progetti personalizzati](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects).  
  
## <a name="see-also"></a>Vedere anche  
 [Installazione di pacchetti VSPackage con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md)   
 [Gestione dei componenti](../extensibility/internals/component-management.md)