---
title: Scelta tra vspackage condivisi e con controllo delle versioni | Microsoft Docs
description: Informazioni sulle installazioni side-by-side di VSPackage tramite strategie condivise o con controllo delle versioni, con più versioni di Visual Studio e del .NET Framework.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SxS
- side-by-side installation
- installation [Visual Studio SDK], side-by-side
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 284dd28af7fb635767f00096420e0142661e4e88
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122146147"
---
# <a name="choose-between-shared-and-versioned-vspackages"></a>Scegliere tra vspackage condivisi e con controllo delle versioni
Diverse versioni di Visual Studio possono coesistere nello stesso computer. I pacchetti VSPackage possono supportare qualsiasi combinazione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] versioni.

 È possibile abilitare le installazioni side-by-side di VSPackage tramite una delle due strategie, la strategia condivisa o la strategia con controllo delle versioni. Entrambi supportano la presenza di più versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e delle versioni associate del .NET Framework.

 Nella strategia condivisa, un VSPackage viene registrato per l'uso in più versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Nella strategia con controllo delle versioni vengono installate più DLL VSPackage, una per ogni versione [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] di supportata.

## <a name="shared-vspackages"></a>VSPackage condivisi
 L'uso di un VSPackage condiviso è appropriato quando si usa lo stesso VSPackage in più versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Per implementare un VSPackage condiviso, è necessario seguire questa procedura:

- Rendere il pacchetto VSPackage compatibile con più versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Sono disponibili due modi per eseguire questa operazione:

  - Limitare il VSPackage all'uso solo delle funzionalità della versione meno recente [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] di supportata.

  - Programmare il pacchetto VSPackage per adattarlo alla versione [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] di in cui è in esecuzione. Quindi, se le query per i servizi più recenti hanno esito negativo, il pacchetto VSPackage può offrire altri servizi supportati nelle versioni precedenti di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

- Registrare il pacchetto VSPackage in modo appropriato. Per altre informazioni, vedere [Registrazione vspackage e](../extensibility/internals/vspackage-registration.md) [Registrazione VSPackage gestita.](/previous-versions/bb166783(v=vs.100))

- Registrare le estensioni di file in modo appropriato. Per altre informazioni, vedere Registrazione di estensioni di file per distribuzioni [side-by-side.](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)

- Creare un programma di installazione che distribuisce il pacchetto VSPackage per le versioni appropriate di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Per altre informazioni, vedere [Installing VSPackages with Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) and [Component management](../extensibility/internals/component-management.md).

- Risolvere il problema dei conflitti di registrazione. Per altre informazioni, vedere [Registrazione di VSPackage.](../extensibility/internals/vspackage-registration.md)

- Assicurarsi che i file condivisi e con versione rispettino il conteggio dei riferimenti per consentire l'installazione e la rimozione sicure di più versioni. Per altre informazioni, vedere [Gestione dei componenti](../extensibility/internals/component-management.md).

## <a name="versioned-vspackages"></a>VSPackage con controllo delle versioni
 In base alla strategia VSPackage con controllo delle versioni, si crea un pacchetto VSPackage per ogni versione [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] di supportata. Questa operazione è appropriata quando si prevede di sfruttare i servizi forniti dalle versioni successive di , perché ogni VSPackage può evolversi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] senza influire sulle altre. Tuttavia, la strategia con controllo delle versioni della creazione di più file binari, da una singola codebase o da più codebase indipendenti, potrebbe comportare uno sviluppo iniziale maggiore rispetto alla strategia condivisa. Inoltre, potrebbero essere necessarie operazioni di installazione aggiuntive perché è necessario creare un'installazione separata per ogni versione o una singola installazione che rileva le versioni di installate e supportate dal [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pacchetto VSPackage.

## <a name="binary-compatibility"></a>Compatibilità binaria
 In genere, la compatibilità binaria consente l'esecuzione di VSPackage di codice nativo sviluppati con versioni precedenti di Visual Studio nelle versioni successive di Visual Studio. Esistono tuttavia tre eccezioni importanti:

- Se il pacchetto VSPackage si basa su una determinata versione di Common Language Runtime, deve determinare in quale versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] è in esecuzione.

- Un VSPackage potrebbe avere una dipendenza da una funzionalità specifica di un altro VSPackage o di un altro prodotto. Di conseguenza, il pacchetto VSPackage può essere eseguito solo quando viene soddisfatta la dipendenza.

- Un VSPackage potrebbe essere interessato da una correzione di sicurezza in un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Service Pack o in una versione successiva di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . In questi casi, un VSPackage sviluppato con una versione precedente di potrebbe non essere eseguito nelle versioni di dopo l'applicazione [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] della correzione di sicurezza. È tuttavia possibile ricompilare il pacchetto con la versione successiva e eseguirlo anche nelle versioni precedenti.

  I pacchetti VSPackage gestiti devono essere compilati usando una versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] che corrispondono alla versione di destinazione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

  Oltre a pianificare la compatibilità binaria per i file binari VSPackage, è necessario prendere in considerazione anche i formati di file di soluzione e di progetto. Se il vspackage crea un nuovo tipo di progetto, è necessario decidere se può essere eseguito in una sola versione o in più versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Per altre informazioni, vedere [Aggiornamento di progetti personalizzati.](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects)

## <a name="see-also"></a>Vedi anche
- [Installazione di VSPackage con il Windows di installazione](../extensibility/internals/installing-vspackages-with-windows-installer.md)
- [Gestione dei componenti](../extensibility/internals/component-management.md)