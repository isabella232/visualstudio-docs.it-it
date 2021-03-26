---
title: Scenari di installazione di VSPackage | Microsoft Docs
description: Informazioni sulle procedure consigliate per il supporto di installazioni side-by-side di Visual Studio con installazioni condivise o affiancate del pacchetto VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, deployment considerations
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2d305d03e17d0e55c2366e71452c4391ccc0ff57
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060744"
---
# <a name="vspackage-setup-scenarios"></a>Scenari di installazione di pacchetti VSPackage

È importante progettare il programma di installazione VSPackage per la flessibilità. Ad esempio, potrebbe essere necessario rilasciare una patch di sicurezza in futuro oppure modificare una strategia aziendale che richiede un supporto completo per il controllo delle versioni side-by-side.

Per [supportare più versioni di Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md), è possibile leggere i vantaggi e i problemi di supporto delle installazioni affiancate di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] con installazioni condivise o affiancate del pacchetto VSPackage. In breve, i pacchetti VSPackage affiancati offrono la massima flessibilità per supportare le nuove funzionalità di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

Gli scenari illustrati in questo argomento non sono le uniche opzioni disponibili, ma vengono presentati come procedure consigliate.

## <a name="components-privacy-and-sharing"></a>Componenti, privacy e condivisione

### <a name="make-your-components-independent"></a>Rendere i componenti indipendenti

Quando si identifica e si popola un componente, si assegna un oggetto `GUID` e si distribuisce il componente, non è possibile modificarne la composizione. Se si modifica la composizione di un componente, il componente risultante deve essere un nuovo componente con un nuovo `GUID` . In base a questi fatti, la maggiore flessibilità di controllo delle versioni viene garantita rendendo indipendente ogni componente. Per ulteriori informazioni sulle regole che disciplinano i componenti, vedere [modifica del codice componente](/windows/desktop/Msi/changing-the-component-code) e [cosa accade se le regole dei componenti sono interrotte?](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken).

### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>Non combinare risorse condivise e private in un componente

Il conteggio dei riferimenti viene eseguito a livello di componente. Di conseguenza, la combinazione di risorse condivise e private in un componente rende impossibile l'aggiornamento delle risorse private, ad esempio un file eseguibile, senza sovrascrivere le risorse condivise. Questo scenario crea problemi di compatibilità con le versioni precedenti e limita la creazione di funzionalità side-by-side.

Ad esempio, i valori del registro di sistema usati per registrare il pacchetto VSPackage con [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] devono essere conservati in un componente separato da quello usato per registrare il pacchetto VSPackage con Visual Studio. I file condivisi o i valori del registro di sistema vengono inseriti in un altro componente.

## <a name="scenario-1-shared-vspackage"></a>Scenario 1: pacchetto VSPackage condiviso

In questo scenario, un pacchetto VSPackage condiviso (un singolo file binario che supporta più versioni di Visual Studio viene fornito in un pacchetto di Windows Installer. La registrazione a ogni versione di Visual Studio è controllata dalle funzionalità selezionabili dall'utente. Indica inoltre che, quando vengono assegnate funzionalità separate, ogni componente può essere selezionato singolarmente per l'installazione o la disinstallazione, consentendo all'utente di controllare l'integrazione del pacchetto VSPackage in versioni diverse di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Per ulteriori informazioni sull'utilizzo delle funzionalità di Windows Installer pacchetti, vedere [Windows Installer funzionalità](/windows/desktop/Msi/windows-installer-features) .

![Programma di installazione di VS Shared VSPackage](../../extensibility/internals/media/vs_sharedpackage.gif "VS_SharedPackage")

Come illustrato nell'illustrazione, i componenti condivisi vengono creati parte della funzionalità Feat_Common, che è sempre installata. Rendendo visibili le funzionalità di Feat_VS2002 e Feat_VS2003, gli utenti possono scegliere in fase di installazione in quali versioni di Visual Studio vogliono integrare il pacchetto VSPackage. Gli utenti possono anche usare Windows Installer modalità manutenzione per aggiungere o rimuovere funzionalità, che in questo caso aggiungono o rimuovono le informazioni di registrazione VSPackage da versioni diverse di Visual Studio.

> [!NOTE]
> Se si imposta la colonna di visualizzazione di una funzionalità su 0, questa viene nascosta. Un valore di colonna di basso livello, ad esempio 1, garantisce che venga sempre installato. Per ulteriori informazioni, vedere la pagina relativa alla [Proprietà INSTALLLEVEL](/windows/desktop/Msi/installlevel) e alla [tabella delle funzionalità](/windows/desktop/Msi/feature-table).

## <a name="scenario-2-shared-vspackage-update"></a>Scenario 2: aggiornamento VSPackage condiviso

In questo scenario viene spedita una versione aggiornata del programma di installazione VSPackage nello scenario 1. Per quanto riguarda la discussione, l'aggiornamento aggiunge il supporto per Visual Studio, ma potrebbe anche essere una patch di sicurezza più semplice o una correzione di bug Service Pack. Le regole di Windows Installer per l'installazione di componenti più recenti richiedono che i componenti non modificati già presenti nel sistema non vengano ricopiati. In questo caso, un sistema con versione 1,0 già presente sovrascriverà il componente aggiornato Comp_MyVSPackage.dll e consentirà agli utenti di scegliere di aggiungere la nuova funzionalità Feat_VS2005 con il componente Comp_VS2005_Reg.

> [!CAUTION]
> Ogni volta che un pacchetto VSPackage è condiviso tra più versioni di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , è essenziale che le versioni successive del pacchetto VSPackage mantengano la compatibilità con le versioni precedenti di Visual Studio. Laddove non è possibile mantenere la compatibilità con le versioni precedenti, è necessario utilizzare i pacchetti VSPackage privati affiancati. Per altre informazioni, vedere [supporto di più versioni di Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).

![Programma di installazione dell'aggiornamento del pacchetto vs condiviso](../../extensibility/internals/media/vs_sharedpackageupdate.gif "VS_SharedPackageUpdate")

Questo scenario presenta un nuovo programma di installazione VSPackage, sfruttando i vantaggi del supporto di Windows Installer per gli aggiornamenti secondari. Gli utenti installano semplicemente la versione 1,1 e aggiorna la versione 1,0. Tuttavia, non è necessario avere la versione 1,0 nel sistema. Lo stesso programma di installazione installerà la versione 1,1 in un sistema senza la versione 1,0. Il vantaggio di fornire aggiornamenti secondari in questo modo è che non è necessario eseguire il lavoro di sviluppo di un programma di installazione di aggiornamento e di un programma di installazione completo del prodotto. Un programma di installazione esegue entrambi i processi. Una soluzione di sicurezza o Service Pack può invece sfruttare i vantaggi delle patch di Windows Installer. Per ulteriori informazioni, vedere applicazione di [patch e aggiornamenti](/windows/desktop/Msi/patching-and-upgrades).

## <a name="scenario-3-side-by-side-vspackage"></a>Scenario 3: VSPackage affiancato

Questo scenario presenta due programmi di installazione VSPackage, uno per ogni versione di Visual Studio .NET 2003 e Visual Studio. Ogni programma di installazione installa un pacchetto VSPackage affiancato, o privato, che viene compilato e installato in modo specifico per una determinata versione di Visual Studio. Ogni pacchetto VSPackage si trova nel proprio componente. Di conseguenza, ogni servizio può essere gestito individualmente con patch o versioni di manutenzione. Poiché la DLL del pacchetto VSPackage è ora specifica della versione, è possibile includere le informazioni di registrazione nello stesso componente della DLL.

![Programma di installazione side-by-side di Visual Studio](../../extensibility/internals/media/vs_sbys_package.gif "VS_SbyS_Package")

Ogni programma di installazione include anche codice condiviso tra i due programmi di installazione. Se il codice condiviso viene installato in un percorso comune, l'installazione di entrambi i file MSI installerà il codice condiviso una sola volta. Il secondo programma di installazione incrementa semplicemente un conteggio dei riferimenti sul componente. Il conteggio dei riferimenti garantisce che se uno dei pacchetti VSPackage viene disinstallato, il codice condiviso rimarrà per l'altro VSPackage. Se viene disinstallato anche il secondo pacchetto VSPackage, il codice condiviso verrà rimosso.

## <a name="scenario-4-side-by-side-vspackage-update"></a>Scenario 4: aggiornamento di VSPackage affiancato

In questo scenario, il pacchetto VSPackage per Visual Studio ha subito una vulnerabilità di sicurezza ed è necessario eseguire un aggiornamento. Come nello scenario 2, è possibile creare un nuovo file con estensione msi che aggiorna un'installazione esistente per includere la correzione per la sicurezza, nonché distribuire nuove installazioni con la correzione della sicurezza già in vigore.

In questo caso, il pacchetto VSPackage è un pacchetto VSPackage gestito installato nella Global Assembly Cache (GAC). Quando si ricompila la correzione per includere la correzione per la sicurezza, è necessario modificare la parte relativa al numero di revisione del numero di versione dell'assembly. Le informazioni di registrazione per il nuovo numero di versione dell'assembly sovrascrivono la versione precedente, causando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] il caricamento dell'assembly fisso.

![Programma di installazione di Visual Studio side-by-side e aggiornamento pacchetti](../../extensibility/internals/media/vs_sbys_packageupdate.gif "VS_SbyS_PackageUpdate")

Per altre informazioni sulla distribuzione di assembly affiancati, vedere [semplificare la distribuzione e la risoluzione di dll Hello con la .NET Framework](/previous-versions/dotnet/articles/ms973843(v=msdn.10)).

## <a name="see-also"></a>Vedi anche

- [Windows Installer](/windows/desktop/Msi/windows-installer-portal)
- [Supporto di più versioni di Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)