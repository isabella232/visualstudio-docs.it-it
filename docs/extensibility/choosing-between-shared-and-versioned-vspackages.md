---
title: Scelta tra VSPackage condivisi e con versione | Microsoft Docs
description: Informazioni sulle installazioni affiancate dei pacchetti VSPackage tramite strategie condivise o con versioni con più versioni di Visual Studio e del .NET Framework.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SxS
- side-by-side installation
- installation [Visual Studio SDK], side-by-side
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 725dd8368bd4db9509426fa1a98ce56ef85bc3c0
ms.sourcegitcommit: 5027eb5c95e1d2da6d08d208fd6883819ef52d05
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2020
ms.locfileid: "94974399"
---
# <a name="choose-between-shared-and-versioned-vspackages"></a>Scegliere tra VSPackage condivisi e con versione
Diverse versioni di Visual Studio possono coesistere nello stesso computer. I pacchetti VSPackage possono supportare qualsiasi combinazione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] versioni.

 È possibile abilitare installazioni affiancate dei pacchetti VSPackage tramite una delle due strategie, la strategia condivisa o la strategia con versione. Entrambi gli adattano la presenza di più versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e delle versioni associate del .NET Framework.

 Nella strategia condivisa, un pacchetto VSPackage viene registrato per l'uso in più versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Nella strategia con versione sono installate più dll VSPackage, una per ogni versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] supportata.

## <a name="shared-vspackages"></a>Pacchetti VSPackage condivisi
 L'uso di un pacchetto VSPackage condiviso è adatto quando si usa lo stesso pacchetto VSPackage in più versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Per implementare un pacchetto VSPackage condiviso, è necessario eseguire i passaggi seguenti:

- Rendere compatibile il pacchetto VSPackage con più versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Sono disponibili due modi per eseguire questa operazione:

  - Limitare il pacchetto VSPackage a utilizzando solo le funzionalità della versione più recente di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] supportata.

  - Programmare il pacchetto VSPackage per adattarsi alla versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] in cui è in esecuzione. Se quindi le query per i servizi più recenti hanno esito negativo, il pacchetto VSPackage può offrire altri servizi supportati nelle versioni precedenti di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

- Registrare il pacchetto VSPackage in modo appropriato. Per ulteriori informazioni, vedere la pagina relativa alla registrazione [VSPackage](../extensibility/internals/vspackage-registration.md) e alla [registrazione di VSPackage gestita](/previous-versions/bb166783(v=vs.100)).

- Registrare le estensioni di file in modo appropriato. Per ulteriori informazioni, vedere [la pagina relativa alla registrazione delle estensioni di file per le distribuzioni side-by-side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).

- Creare un programma di installazione che distribuisce il pacchetto VSPackage per le versioni appropriate di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Per altre informazioni, vedere [installazione di VSPackage con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) e [gestione dei componenti](../extensibility/internals/component-management.md).

- Risolvere il problema dei conflitti di registrazione. Per ulteriori informazioni, vedere la pagina relativa alla [registrazione di VSPackage](../extensibility/internals/vspackage-registration.md).

- Assicurarsi che i file condivisi e con versione rispettino il conteggio dei riferimenti per consentire l'installazione e la rimozione sicure di più versioni. Per ulteriori informazioni, vedere [gestione dei componenti](../extensibility/internals/component-management.md).

## <a name="versioned-vspackages"></a>Pacchetti VSPackage con versione
 Con la strategia VSPackage con versione è possibile creare un pacchetto VSPackage per ogni versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] supportata. Questa operazione è appropriata quando si prevede di sfruttare i servizi forniti dalle versioni successive di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , perché ogni VSPackage può evolvere senza influire sugli altri. Tuttavia, la strategia con versione per la creazione di più file binari, da una singola codebase o da più basi di codice indipendenti, può comportare uno sviluppo iniziale maggiore rispetto alla strategia condivisa. Inoltre, potrebbe essere necessario un lavoro di installazione aggiuntivo perché è necessario creare una configurazione separata per ogni versione o una singola installazione che rilevi le versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] installate e supportate dal pacchetto VSPackage.

## <a name="binary-compatibility"></a>Compatibilità binaria
 In genere, la compatibilità binaria consente ai pacchetti VSPackage di codice nativo sviluppati con versioni precedenti di Visual Studio di essere eseguiti nelle versioni successive di Visual Studio. Tuttavia, esistono tre eccezioni importanti:

- Se il pacchetto VSPackage si basa su una versione specifica del Common Language Runtime, è necessario determinare in quale versione di è in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] esecuzione.

- Un pacchetto VSPackage può avere una dipendenza da una funzionalità specifica di un altro pacchetto VSPackage o di un altro prodotto. Di conseguenza, il pacchetto VSPackage può essere eseguito solo quando la dipendenza viene soddisfatta.

- Un pacchetto VSPackage potrebbe essere influenzato da una correzione di sicurezza in una [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Service Pack o in una versione successiva di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . In questi casi, un pacchetto VSPackage sviluppato con una versione precedente di [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] potrebbe non essere eseguito nelle versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dopo l'applicazione della correzione di sicurezza. Tuttavia, è possibile ricompilare il pacchetto con la versione più recente ed eseguirlo anche nelle versioni precedenti.

  I pacchetti VSPackage gestiti devono essere compilati utilizzando una versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] che corrisponda alla versione di destinazione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

  Oltre a pianificare la compatibilità binaria per i file binari VSPackage, è necessario considerare anche i formati di file di soluzione e di progetto. Se il pacchetto VSPackage crea un nuovo tipo di progetto, è necessario decidere se può essere eseguito in una sola versione o in più versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Per ulteriori informazioni, vedere [aggiornamento di progetti personalizzati](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects).

## <a name="see-also"></a>Vedere anche
- [Installazione di VSPackage con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md)
- [Gestione dei componenti](../extensibility/internals/component-management.md)