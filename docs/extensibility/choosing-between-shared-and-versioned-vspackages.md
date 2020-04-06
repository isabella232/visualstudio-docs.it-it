---
title: Scelta tra package VS condivisi e con versione Documenti Microsoft
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
ms.openlocfilehash: 21fefb776fceeeef4db6997a5bd12a8b987af7d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739881"
---
# <a name="choose-between-shared-and-versioned-vspackages"></a>Scegliere tra package VS condivisi e con controllo delle versioni
Versioni diverse di Visual Studio possono coesistere nello stesso computer. VSPackage possono supportare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] qualsiasi combinazione di versioni.

 È possibile abilitare le installazioni side-by-side di VSPackage tramite una delle due strategie, la strategia condivisa o la strategia con controllo delle versioni. Entrambi supportano la presenza [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] di più versioni di e versioni associate di .NET Framework.

 Nella strategia condivisa, un VSPackage viene registrato [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]per l'utilizzo in più versioni di . Nella strategia con controllo delle versioni, vengono installate più [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] DLL VSPackage, una per ogni versione di supporto.

## <a name="shared-vspackages"></a>VSPackage condivisi
 L'utilizzo di un pacchetto VSPackage condiviso è appropriato [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]quando si utilizza lo stesso VSPackage in più versioni di . Per implementare un VSPackage condiviso, è necessario eseguire la procedura seguente:To implement a shared VSPackage, you must take the following steps:

- Rendere il pacchetto VSPackage compatibile con più versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Sono disponibili due modi per farlo:

  - Limitare il pacchetto VSPackage per l'utilizzo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solo delle funzionalità della versione meno recente di tale supporto.

  - Programmare il pacchetto VSPackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per adattarsi alla versione di in cui è in esecuzione. Quindi, se le query per i servizi più recenti hanno esito [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]negativo, il pacchetto VSPackage può offrire altri servizi supportati nelle versioni precedenti di .

- Registrare il pacchetto VSPackage in modo appropriato. Per ulteriori informazioni, vedere [registrazione VSPackage](../extensibility/internals/vspackage-registration.md) e [registrazione VSPackage gestita](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1).

- Registrare le estensioni dei file in modo appropriato. Per ulteriori informazioni, vedere Registrazione delle estensioni di [file per le distribuzioni side-by-side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).

- Creare un programma di installazione che distribuisce [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]il pacchetto VSPackage per le versioni appropriate di . Per ulteriori informazioni, vedere [Installazione di pacchetti VSPackage con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) e gestione dei [componenti](../extensibility/internals/component-management.md).

- Risolvere il problema delle collisioni di registrazione. Per ulteriori informazioni, vedere [Registrazione VSPackage](../extensibility/internals/vspackage-registration.md).

- Assicurarsi che i file condivisi e con controllo delle versioni rispettino il conteggio dei riferimenti per consentire l'installazione e la rimozione sicure di più versioni. Per ulteriori informazioni, vedere [Gestione dei componenti](../extensibility/internals/component-management.md).

## <a name="versioned-vspackages"></a>Pacchetti VS con versione
 Sotto la strategia VSPackage con controllo delle versioni, si crea un VSPackage per ogni versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] supporto. Questa operazione è appropriata quando si prevede di sfruttare i servizi forniti dalle versioni successive di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], perché ogni VSPackage può evolvere senza influire sugli altri. Tuttavia, la strategia con controllo delle versioni di creazione di più file binari, da una singola base di codice o da più basi di codice indipendenti, potrebbe comportare un maggiore sviluppo iniziale rispetto alla strategia condivisa. Inoltre, potrebbe essere necessario ulteriore lavoro di installazione perché è necessario creare un'installazione [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] separata per ogni versione o una singola installazione che rileva le versioni di che sono installate e che supporta il pacchetto VSPackage.

## <a name="binary-compatibility"></a>Compatibilità binaria
 In genere, la compatibilità binaria consente agli VSPackage in codice nativo sviluppati con versioni precedenti di Visual Studio di essere eseguiti nelle versioni successive di Visual Studio. Tuttavia, ci sono tre importanti eccezioni:

- Se il pacchetto VSPackage si basa su una particolare versione di Common [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Language Runtime, è necessario determinare in quale versione è in esecuzione.

- Un pacchetto VSPackage potrebbe avere una dipendenza da una funzionalità specifica di un altro VSPackage o un altro prodotto. Di conseguenza, il pacchetto VSPackage può essere eseguito solo dove viene soddisfatta la dipendenza.

- Un pacchetto VSPackage potrebbe essere interessato da una correzione di sicurezza in un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] service pack o una versione successiva di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. In questi casi, un pacchetto VSPackage [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] sviluppato con una [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] versione precedente del potrebbe non essere eseguito nelle versioni di dopo l'applicazione della correzione di sicurezza. Tuttavia, è possibile ricompilare il pacchetto con la versione successiva e fare in modo che venga eseguito anche nelle versioni precedenti.

  I package VS gestiti devono [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] essere [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] compilati utilizzando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]una versione di e quelli che corrispondono alla versione di destinazione di .

  Oltre alla pianificazione per la compatibilità binaria per i file binari VSPackage, è necessario considerare anche i formati di file di soluzione e progetto. Se il pacchetto VSPackage crea un nuovo tipo di progetto, è necessario [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]decidere se può essere eseguito in una sola versione o in più versioni di . Per ulteriori informazioni, consultate [Aggiornamento di progetti personalizzati.](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects)

## <a name="see-also"></a>Vedere anche
- [Installazione di pacchetti VSPackage con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md)
- [Gestione dei componenti](../extensibility/internals/component-management.md)
