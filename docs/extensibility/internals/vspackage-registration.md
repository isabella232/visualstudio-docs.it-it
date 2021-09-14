---
title: Registrazione vspackage | Microsoft Docs
description: Informazioni sulla registrazione del pacchetto VSPackage, in cui i Visual Studio consigliano di installare i pacchetti e devono essere caricati scrivendo informazioni nel Registro di sistema.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: f0257eb175dff65a28cc942ef4854cfdff437d5c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709492"
---
# <a name="vspackage-registration"></a>Registrazione di pacchetti VSPackage
I pacchetti VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] devono avvisare che sono installati e devono essere caricati. Questo processo viene ottenuto scrivendo informazioni nel Registro di sistema. Si tratta di un processo tipico di un programma di installazione.

> [!NOTE]
> È una procedura accettata durante lo sviluppo di pacchetti VSPackage usare la registrazione automatica. Tuttavia, [!INCLUDE[vsipprvsip](../../extensibility/includes/vsipprvsip_md.md)] i partner non possono spedire i propri prodotti usando la registrazione automatica come parte della configurazione.

 Le voci del Registro di sistema in un pacchetto Windows Installer vengono in genere effettuate nella tabella Registro di sistema. È anche possibile registrare le estensioni di file nella tabella Registro di sistema. Tuttavia, Windows Installer offre supporto incorporato tramite l'identificatore a livello di codice (ProgId), le tabelle di classi, estensioni e verbi. Per altre informazioni, vedere [Tabelle di database.](/windows/desktop/Msi/database-tables)

 Assicurarsi che le voci del Registro di sistema siano associate al componente appropriato per la strategia side-by-side scelta. Ad esempio, le voci del Registro di sistema per un file condiviso devono essere associate al componente Windows programma di installazione di tale file. Analogamente, le voci del Registro di sistema per un file specifico della versione devono essere associate al componente del file. In caso contrario, l'installazione o la disinstallazione del pacchetto VSPackage per una versione di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] potrebbe interrompere il vspackage in altre versioni. Per altre informazioni, vedere [Supporto di più versioni di Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).

> [!NOTE]
> Il modo più semplice per gestire la registrazione è usare gli stessi dati negli stessi file sia per la registrazione per sviluppatori che per la registrazione in fase di installazione. Alcuni strumenti di sviluppo del programma di installazione, ad esempio, possono utilizzare file in formato reg in fase di compilazione. Se gli sviluppatori gestiscono file con estensione reg per lo sviluppo e il debug quotidiani, questi stessi file possono essere inclusi automaticamente nel programma di installazione. Se non è possibile condividere automaticamente i dati di registrazione, è necessario assicurarsi che la copia del programma di installazione dei dati di registrazione sia corrente.

## <a name="registering-unmanaged-vspackages"></a>Registrazione di pacchetti VSPackage non gestiti
 I pacchetti VSPackage non gestiti (inclusi quelli generati dal modello di pacchetto Visual Studio) usano file con estensione rgs di tipo ATL per archiviare le informazioni di registrazione. Il formato di file rgs è specifico di ATL e in genere non può essere utilizzato così come è da uno strumento di creazione dell'installazione. Le informazioni di registrazione per il programma di installazione del pacchetto VSPackage devono essere gestite separatamente. Ad esempio, gli sviluppatori possono mantenere i file in formato reg sincronizzati con le modifiche ai file con estensione rgs. I file con estensione reg possono essere uniti a RegEdit per le attività di sviluppo o utilizzati da un programma di installazione.

## <a name="registering-managed-vspackages"></a>Registrazione di pacchetti VSPackage gestiti
 Lo strumento RegPkg legge gli attributi di registrazione da un VSPackage gestito e può scrivere le informazioni direttamente nel Registro di sistema o scrivere file in formato reg che possono essere utilizzati da un programma di installazione.

> [!NOTE]
> Lo strumento RegPkg non è ridistribuibile e non può essere usato per registrare un VSPackage nel sistema di un utente.

## <a name="why-vspackages-should-not-self-register-at-install-time"></a>Perché i pacchetti VSPackage non devono Self-Register in fase di installazione
 I programmi di installazione vspackage non devono basarsi sulla registrazione automatica. A prima vista, mantenere i valori del Registro di sistema di un VSPackage solo nel pacchetto VSPackage stesso sembra una buona idea. Dato che gli sviluppatori necessitano dei valori del Registro di sistema disponibili per le attività e i test di routine, è opportuno evitare di mantenere una copia separata dei dati del Registro di sistema nel programma di installazione. Il programma di installazione può basarsi sul pacchetto VSPackage stesso per scrivere i valori del Registro di sistema.

 Sebbene sia una buona in teoria, la registrazione automatica presenta diversi difetti che la rendono non idonea per l'installazione di VSPackage:

- Per supportare correttamente l'installazione, la disinstallazione, il rollback dell'installazione e il rollback della disinstallazione, è necessario creare quattro azioni personalizzate per ogni VSPackage gestito che si autoregistra chiamando RegPkg.

- L'approccio al supporto side-by-side potrebbe richiedere la creazione di quattro azioni personalizzate che richiamano RegSvr32 o RegPkg per ogni versione supportata di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- Non è possibile eseguire il rollback sicuro di un'installazione con moduli auto registrati perché non è possibile determinare se le chiavi auto-registrate vengono usate da un'altra funzionalità o applicazione.

- Le DLL auto-registrate a volte si collegano a DLL ausiliarie che non sono presenti o sono la versione errata. Al contrario, Windows programma di installazione può registrare DLL usando le tabelle del Registro di sistema senza alcuna dipendenza dallo stato corrente del sistema.

- Al codice di auto-registrazione può essere negato l'accesso alle risorse di rete, ad esempio le librerie dei tipi, se un componente è specificato come run-from-source ed è elencato nella tabella SelfReg. Ciò può causare l'esito negativo dell'installazione del componente durante un'installazione amministrativa.

## <a name="see-also"></a>Vedi anche
- [Windows Installer](/windows/desktop/Msi/windows-installer-portal)
- [Registrazione del pacchetto gestito](/previous-versions/bb166783(v=vs.100))