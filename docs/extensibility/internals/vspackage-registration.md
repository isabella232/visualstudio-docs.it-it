---
title: Registrazione vspackage | Microsoft Docs
description: Informazioni sulla registrazione di VSPackage, in cui i pacchetti Visual Studio che sono installati e devono essere caricati scrivendo informazioni nel Registro di sistema.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122117631"
---
# <a name="vspackage-registration"></a>Registrazione di pacchetti VSPackage
I pacchetti VSPackage devono [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] avvisare che sono installati e devono essere caricati. Questo processo viene ottenuto scrivendo informazioni nel Registro di sistema. Si tratta di un processo tipico di un programma di installazione.

> [!NOTE]
> È una procedura accettata durante lo sviluppo di VSPackage usare la registrazione automatica. Tuttavia, [!INCLUDE[vsipprvsip](../../extensibility/includes/vsipprvsip_md.md)] i partner non possono spedire i propri prodotti usando la registrazione automatica come parte della configurazione.

 Le voci del Registro di sistema in un Windows installer vengono in genere effettuate nella tabella Registro di sistema. È anche possibile registrare le estensioni di file nella tabella Registro di sistema. Tuttavia, Windows Installer fornisce il supporto incorporato tramite le tabelle identificatore a livello di codice (ProgId), classe, estensione e verbo. Per altre informazioni, vedere [Tabelle di database](/windows/desktop/Msi/database-tables).

 Assicurarsi che le voci del Registro di sistema siano associate al componente appropriato per la strategia side-by-side scelta. Ad esempio, le voci del Registro di sistema per un file condiviso devono essere associate al componente Windows installer del file. Analogamente, le voci del Registro di sistema per un file specifico della versione devono essere associate al componente del file. In caso contrario, l'installazione o la disinstallazione del pacchetto VSPackage per una versione di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] potrebbe interrompere il pacchetto VSPackage in altre versioni. Per altre informazioni, vedere [Supporto di più versioni di Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).

> [!NOTE]
> Il modo più semplice per gestire la registrazione è usare gli stessi dati negli stessi file sia per la registrazione per sviluppatori che per la registrazione in fase di installazione. Alcuni strumenti di sviluppo del programma di installazione, ad esempio, possono utilizzare file in formato reg in fase di compilazione. Se gli sviluppatori mantengono i file con estensione reg per lo sviluppo e il debug quotidiani, questi stessi file possono essere inclusi automaticamente nel programma di installazione. Se non è possibile condividere automaticamente i dati di registrazione, è necessario assicurarsi che la copia dei dati di registrazione del programma di installazione sia corrente.

## <a name="registering-unmanaged-vspackages"></a>Registrazione di VSPackage non gestiti
 I pacchetti VSPackage non gestiti (inclusi quelli generati dal modello di pacchetto Visual Studio) usano file con estensione rgs di tipo ATL per archiviare le informazioni di registrazione. Il formato di file con estensione rgs è specifico di ATL e in genere non può essere utilizzato così come è da uno strumento di creazione dell'installazione. Le informazioni di registrazione per il programma di installazione di VSPackage devono essere gestite separatamente. Ad esempio, gli sviluppatori possono mantenere i file in formato reg sincronizzati con le modifiche ai file con estensione rgs. I file con estensione reg possono essere uniti a RegEdit per il lavoro di sviluppo o utilizzati da un programma di installazione.

## <a name="registering-managed-vspackages"></a>Registrazione di VSPackage gestiti
 Lo strumento RegPkg legge gli attributi di registrazione da un VSPackage gestito e può scrivere le informazioni direttamente nel Registro di sistema o scrivere file in formato reg che possono essere utilizzati da un programma di installazione.

> [!NOTE]
> Lo strumento RegPkg non è ridistribuibile e non può essere usato per registrare un VSPackage nel sistema di un utente.

## <a name="why-vspackages-should-not-self-register-at-install-time"></a>Perché i pacchetti VSPackage non devono Self-Register in fase di installazione
 I programmi di installazione di VSPackage non devono basarsi sulla registrazione automatica. A prima vista, mantenere i valori del Registro di sistema di un VSPackage solo nel pacchetto VSPackage stesso sembra una buona idea. Poiché gli sviluppatori necessitano dei valori del Registro di sistema disponibili per il lavoro e i test di routine, è opportuno evitare di mantenere una copia separata dei dati del Registro di sistema nel programma di installazione. Il programma di installazione può basarsi sul pacchetto VSPackage stesso per scrivere i valori del Registro di sistema.

 Sebbene buona in teoria, la registrazione automatica presenta diversi difetti che lo rendono inadatto per l'installazione di VSPackage:

- Per supportare correttamente l'installazione, la disinstallazione, il rollback dell'installazione e il rollback della disinstallazione, è necessario creare quattro azioni personalizzate per ogni VSPackage gestito che si registra automaticamente chiamando RegPkg.

- L'approccio al supporto side-by-side potrebbe richiedere la creazione di quattro azioni personalizzate che richiamano RegSvr32 o RegPkg per ogni versione supportata di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- Non è possibile eseguire il rollback sicuro di un'installazione con moduli auto registrati perché non è possibile determinare se le chiavi auto-registrate vengono usate da un'altra funzionalità o applicazione.

- Le DLL auto-registrate a volte si collegano a DLL ausiliarie che non sono presenti o sono la versione errata. Al contrario, Windows installer può registrare le DLL usando le tabelle del Registro di sistema senza alcuna dipendenza dallo stato corrente del sistema.

- Al codice di auto-registrazione può essere negato l'accesso alle risorse di rete, ad esempio le librerie dei tipi, se un componente è specificato come run-from-source ed è elencato nella tabella SelfReg. Ciò può causare l'esito negativo dell'installazione del componente durante un'installazione amministrativa.

## <a name="see-also"></a>Vedi anche
- [Windows Installer](/windows/desktop/Msi/windows-installer-portal)
- [Registrazione del pacchetto gestito](/previous-versions/bb166783(v=vs.100))