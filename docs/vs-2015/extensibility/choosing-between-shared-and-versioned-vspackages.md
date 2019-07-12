---
title: Scelta tra pacchetti VSPackage condivisi e con controllo delle versioni | Microsoft Docs
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
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2019
ms.locfileid: "67821972"
---
# <a name="choosing-between-shared-and-versioned-vspackages"></a>Scelta tra pacchetti VSPackage condivisi e con versione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Versioni diverse di Visual Studio possono coesistere nello stesso computer. I pacchetti VSPackage possono supportare qualsiasi combinazione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] versioni.  
  
 È possibile abilitare le installazioni side-by-side di pacchetti VSPackage tramite una delle due strategie, la strategia condivisa o la strategia di controllo delle versioni. Entrambi contenere la presenza di più versioni di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e versioni di associati il [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].  
  
 Nella strategia di condiviso, un pacchetto VSPackage è registrato per l'uso in più versioni di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Nella strategia di controllo delle versioni, sono installate più DLL di VSPackage, uno per ogni versione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] supportate.  
  
## <a name="shared-vspackages"></a>Pacchetti VSPackage condivisi  
 Usando un pacchetto VSPackage condiviso è appropriato quando si usa il pacchetto VSPackage stesso in più versioni di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Per implementare un package VS condivisi, è necessario eseguire i passaggi seguenti:  
  
- Rendere compatibili con più versioni del pacchetto VSPackage [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Due modalità di esecuzione sono pertanto disponibili:  
  
  - Limitare il pacchetto VSPackage per usare solo le funzionalità dalla versione meno recente di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] supportate.  

  - Programmare il pacchetto VSPackage per adattarsi alla versione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] in cui è in esecuzione. Quindi, se le query per i servizi più recenti hanno esito negativo, il pacchetto VSPackage può offrire altri servizi che sono supportati nelle versioni precedenti di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
- Registrare il VSPackage in modo appropriato. Per altre informazioni, vedere [registrazione di pacchetti VSPackage](../extensibility/internals/vspackage-registration.md) e [registrazione di pacchetti VSPackage gestiti](https://msdn.microsoft.com/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1).  
  
- Registrare le estensioni di file in modo appropriato. Per altre informazioni, vedere [la registrazione di estensioni di File per le distribuzioni Side-By-Side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
- Creare un programma di installazione che consente di distribuire il pacchetto VSPackage per le versioni appropriate di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Per altre informazioni, vedere [installazione di pacchetti VSPackage con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) e [gestione dei componenti](../extensibility/internals/component-management.md).  
  
- Risolvere il problema dei conflitti di registrazione. Per altre informazioni, vedere [registrazione di pacchetti VSPackage](../extensibility/internals/vspackage-registration.md).  
  
- Assicurarsi che i file sia condivisi sia con controllo delle versioni rispettino per consentire l'installazione sicura e la rimozione di più versioni di conteggio dei riferimenti. Per altre informazioni, vedere [gestione dei componenti](../extensibility/internals/component-management.md).  
  
## <a name="versioned-vspackages"></a>Pacchetti VSPackage con controllo delle versioni  
 Sotto la strategia di VSPackage con controllo delle versioni, si crea un pacchetto VSPackage per ogni versione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] supportate. Questa operazione è appropriata se si prevede di sfruttare i vantaggi dei servizi forniti dalle versioni più recenti di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], perché ogni pacchetto VSPackage può evolversi senza influire sulle altre. Tuttavia, la strategia di creazione di più file binari, da una singola codebase o da più basi di codice indipendenti, con controllo delle versioni può comportare ulteriori attività iniziali di sviluppo più la strategia condivisa. Inoltre, operazioni di configurazione aggiuntivi potrebbero essere necessari perché è necessario creare un programma di installazione separato per ogni versione né di un unico programma di installazione che rileva le versioni di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] che siano installati e che supporta il pacchetto VSPackage.  
  
## <a name="binary-compatibility"></a>Compatibilità binaria  
 In generale, la compatibilità binaria consente codice nativo i pacchetti VSPackage sviluppati con versioni precedenti di Visual Studio per l'esecuzione nelle versioni più recenti di Visual Studio. Tuttavia, esistono tre importanti eccezioni:  
  
- Se il pacchetto VSPackage si basa su una particolare versione di common language runtime, quindi è necessario determinare in quale versione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] è in esecuzione.  
  
- Un pacchetto VSPackage potrebbe avere una dipendenza su una funzionalità specifica di un altro VSPackage o di un altro prodotto. Di conseguenza, il pacchetto VSPackage può essere eseguito solo in cui la dipendenza viene soddisfatta.  
  
- Un pacchetto VSPackage può essere influenzato da una correzione di sicurezza in un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] service pack o una versione successiva di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. In questi casi, un pacchetto VSPackage sviluppati con una versione precedente del [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] potrebbe non funzionare nelle versioni di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dopo la correzione di sicurezza è stata applicata. Tuttavia, è possibile ricompilare il pacchetto con la versione più recente e anche eseguirlo nelle versioni precedenti.  
  
  I VSPackage gestiti devono essere creati usando una versione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e il [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] che corrisponde alla versione di destinazione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
  Oltre alla pianificazione per la compatibilità binaria per i file binari del pacchetto VSPackage, è anche necessario prendere in considerazione soluzioni e formati di file di progetto. Se il pacchetto VSPackage viene creato un nuovo tipo di progetto, è necessario decidere se può essere eseguito solo una versione o in più versioni di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Per altre informazioni, vedere [l'aggiornamento dei progetti personalizzati](../misc/upgrading-custom-projects.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Installazione di pacchetti VSPackage con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md)   
 [Gestione dei componenti](../extensibility/internals/component-management.md)
