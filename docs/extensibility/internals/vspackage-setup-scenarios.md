---
title: Scenari di installazione di pacchetti VSPackage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, deployment considerations
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f92e2b3d73c29896153df9f1496e286ffcca752b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54921999"
---
# <a name="vspackage-setup-scenarios"></a>Scenari di installazione di pacchetti VSPackage

È importante progettare il programma di installazione di VSPackage per la flessibilità. Ad esempio, potrebbe essere necessario rilasciare una patch di sicurezza in futuro oppure è possibile modificare una strategia di business che richiede il supporto del controllo delle versioni side-by-side completa.

Nelle [supporto di più versioni di Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md), è possibile leggere sui vantaggi e i problemi di supportare le installazioni side-by-side di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] le installazioni dei componenti condivisi o side-by-side di un VSPackage. In breve, i pacchetti VSPackage side-by-side offrono la massima flessibilità per supportare nuove funzionalità di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

Gli scenari descritti in questo argomento non sono le uniche scelte a disposizione, ma sono presentati come procedure consigliate.

## <a name="components-privacy-and-sharing"></a>I componenti, Privacy e la condivisione

### <a name="make-your-components-independent"></a>Creazione di componenti indipendenti

Dopo avere identificato e compilare un componente, assegnare un `GUID`e distribuire il componente, non è possibile modificare la composizione. Se si modifica la composizione del componente, il componente risulta deve essere un nuovo componente con un nuovo `GUID`. La maggiore flessibilità nel versionamento dato questi fatti, si applicano apportando ogni unità indipendenti, radicato componente. Per altre informazioni sulle regole che controllano i componenti, vedere [modifica del codice del componente](/windows/desktop/Msi/changing-the-component-code) e [cosa accade se le regole di componente vengono interrotti?](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken).

### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>Non combinare risorse condivise e private in un componente

Il conteggio dei riferimenti si verifica a livello di componente. Di conseguenza, combinandole condivisi e privati in un singolo componente rende Impossibile aggiornare le risorse private, ad esempio un file eseguibile, senza sovrascrivere anche le risorse condivise. Questo scenario consente di creare problemi di compatibilità e limita la possibilità di creazione di funzionalità side-by-side.

I valori del Registro di sistema, ad esempio, consente di registrare il pacchetto VSPackage con il [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] deve essere mantenuto in un componente separato da quello utilizzato per registrare il pacchetto VSPackage con Visual Studio. File condivisi o i valori del Registro di sistema passa in un altro componente.

## <a name="scenario-1-shared-vspackage"></a>Scenario 1: Package VS condivisi

In questo scenario, un pacchetto VSPackage condiviso (un singolo file binario che supporta più versioni di Visual Studio viene fornito in un pacchetto Windows Installer. La registrazione con ogni versione di Visual Studio è controllata dalle funzionalità selezionabili dall'utente. Significa anche che quando assegnato per separare le funzionalità, ogni componente possa essere selezionate singolarmente per l'installazione o la disinstallazione, inserisce l'utente controlla l'integrazione di VSPackage in versioni diverse di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. (Vedere [funzionalità di Windows Installer](/windows/desktop/Msi/windows-installer-features) per altre informazioni sull'utilizzo delle funzionalità nei pacchetti di Windows Installer.)

![Il programma di installazione di Visual Studio VSPackage condivisi](../../extensibility/internals/media/vs_sharedpackage.gif "VS_SharedPackage")

Come illustrato nella figura, i componenti condivisi diventano parte della funzionalità Feat_Common, che viene sempre installata. Rendendo le funzionalità Feat_VS2002 e Feat_VS2003 visibili, gli utenti possono scegliere in fase di installazione in quali versioni di Visual Studio il pacchetto VSPackage per l'integrazione. Gli utenti possono anche usare modalità di manutenzione di Windows Installer per aggiungere o rimuovere le funzionalità, che in questo caso aggiunge o rimuove le informazioni di registrazione di VSPackage da diverse versioni di Visual Studio.

> [!NOTE]
> Impostazione colonna da visualizzare una funzionalità su 0 per nasconderlo. Un valore di colonna di livello basso, ad esempio 1, garantisce che sarà sempre installata. Per altre informazioni, vedere [proprietà INSTALLLEVEL](/windows/desktop/Msi/installlevel) e [tabella delle funzionalità](/windows/desktop/Msi/feature-table).

## <a name="scenario-2-shared-vspackage-update"></a>Scenario 2: Update Package VS condivisi

In questo scenario, è disponibile una versione aggiornata del programma di installazione pacchetto VSPackage nello scenario 1. Ai fini di discussione, l'aggiornamento aggiunge il supporto per Visual Studio, ma potrebbe anche essere una patch di sicurezza più semplice o correzione di bug del Service pack. Le regole del programma di installazione di Windows per l'installazione dei componenti più recenti richiedono che i componenti invariati nel sistema è già non vengono ricopiati. In questo caso, un sistema con la versione 1.0 sono già presenti sovrascriverà il componente aggiornato Comp_MyVSPackage.dll e consentire agli utenti di scegliere di aggiungere la nuova funzionalità Feat_VS2005 al relativo componente Comp_VS2005_Reg.

> [!CAUTION]
> Ogni volta che un pacchetto VSPackage è condiviso tra più versioni di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], è essenziale che le versioni successive del pacchetto VSPackage mantenere la compatibilità con le versioni precedenti di Visual Studio. Dove è possibile mantenere la compatibilità con le versioni precedenti, è necessario usare i pacchetti VSPackage side-by-side e privati. Per altre informazioni, vedere [supporto di più versioni di Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).

![Il programma di installazione di Visual Studio condiviso di aggiornamento del pacchetto VS](../../extensibility/internals/media/vs_sharedpackageupdate.gif "VS_SharedPackageUpdate")

Questo scenario presenta un nuovo pacchetto VSPackage programma di installazione, sfruttando i vantaggi del supporto del programma di installazione di Windows per gli aggiornamenti secondari. Gli utenti installano la versione 1.1 e viene aggiornato alla versione 1.0. Non è tuttavia necessario avere la versione 1.0 nel sistema. Lo stesso di installazione installerà la versione 1.1 in un sistema senza versione 1.0. Il vantaggio di fornire gli aggiornamenti secondari in questo modo è che non è necessario passare attraverso il lavoro dello sviluppo di un programma di installazione aggiornamento e un programma di installazione completa del prodotto. Un programma di installazione esegue entrambi i processi. Una correzione di sicurezza o di un servizio di tipo pack potrebbe invece sfruttare le patch di Windows Installer. Per altre informazioni, vedere [applicazione di patch e aggiornamenti](/windows/desktop/Msi/patching-and-upgrades).

## <a name="scenario-3-side-by-side-vspackage"></a>Scenario 3: VSPackage side-by-Side

Questo scenario presenta due programmi di installazione del pacchetto VSPackage, ovvero uno per ogni versione di Visual Studio .NET 2003 e Visual Studio. Ogni programma di installazione installa un side-by-side privati, VSPackage (quello che viene compilato e installato per una particolare versione di Visual Studio in modo specifico). Ogni pacchetto VSPackage è nel proprio componente. Di conseguenza, ogni eseguire singolarmente la manutenzione con le patch o manutenzione rilascia. Poiché la DLL di VSPackage è ora specifici della versione, è consigliabile includere le informazioni di registrazione nel componente stesso come DLL.

![Il programma di installazione di Visual Studio il pacchetto di Visual Studio Side-by-Side](../../extensibility/internals/media/vs_sbys_package.gif "VS_SbyS_Package")

Ogni programma di installazione include anche codice che verrà condivisi tra i due programmi di installazione. Se il codice condiviso viene installato in un percorso comune, entrambi i file con estensione msi di installazione installerà il codice condiviso una sola volta. Il programma di installazione secondo incrementa semplicemente un conteggio dei riferimenti del componente. Il conteggio dei riferimenti garantisce che se uno dei VSPackage viene disinstallato, il codice condiviso rimarrà per altri VSPackage. Se viene disinstallato anche il pacchetto VSPackage secondario, verrà rimosso il codice condiviso.

## <a name="scenario-4-side-by-side-vspackage-update"></a>Scenario 4: Aggiornamento pacchetto VSPackage side-by-Side

In questo scenario, il pacchetto VSPackage per Visual Studio non ha una vulnerabilità di sicurezza e si desidera eseguire un aggiornamento. Come nello scenario 2, è possibile creare un nuovo file con estensione msi che aggiorna un'installazione esistente per includere la correzione di sicurezza, nonché di distribuire le nuove installazioni con la correzione di sicurezza già presenti.

In questo caso, il pacchetto VSPackage è un pacchetto VSPackage gestito installato nella global assembly cache (GAC). Durante la ricompilazione per includere la correzione di sicurezza, è necessario modificare la parte del numero di revisione del numero di versione di assembly. Le informazioni di registrazione per il numero di versione nuova sovrascrive quella precedente, generando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per caricare l'assembly predefinito.

![Il programma di installazione di VS Update pacchetto di Visual Studio Side-by-Side](../../extensibility/internals/media/vs_sbys_packageupdate.gif "VS_SbyS_PackageUpdate")

Per altre informazioni sulla distribuzione di assembly side-by-side, vedere [semplificando la distribuzione e la risoluzione di "DLL hell" con .NET Framework](https://msdn.microsoft.com/library/ms973843.aspx).

## <a name="see-also"></a>Vedere anche

[Windows Installer](/windows/desktop/Msi/windows-installer-portal)  
[Supporto di più versioni di Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)