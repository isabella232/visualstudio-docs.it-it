---
title: Scenari di installazione di VSPackage | Microsoft Docs
description: Informazioni sulle procedure consigliate per il supporto di installazioni side-by-side di Visual Studio con installazioni condivise o side-by-side del pacchetto VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, deployment considerations
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: e75851e8a2775fda80a4bcb6ffefa93558c4f786
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122069624"
---
# <a name="vspackage-setup-scenarios"></a>Scenari di installazione di pacchetti VSPackage

È importante progettare il programma di installazione di VSPackage per una maggiore flessibilità. Ad esempio, potrebbe essere necessario rilasciare una patch di sicurezza in futuro oppure modificare una strategia aziendale che richiede un supporto completo del controllo delle versioni side-by-side.

In Supporto di più versioni di [Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)è possibile leggere i vantaggi e i problemi relativi al supporto di installazioni side-by-side di con installazioni condivise o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] side-by-side del pacchetto VSPackage. In breve, i pacchetti VSPackage side-by-side offrono la massima flessibilità per supportare le nuove funzionalità di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

Gli scenari illustrati in questo argomento non sono le uniche opzioni disponibili, ma vengono presentati come procedure consigliate consigliate.

## <a name="components-privacy-and-sharing"></a>Componenti, privacy e condivisione

### <a name="make-your-components-independent"></a>Rendere indipendenti i componenti

Dopo aver identificato e popolato un componente, assegnato e distribuito il componente, non è possibile `GUID` modificarne la composizione. Se si modifica la composizione di un componente, il componente risultante deve essere un nuovo componente con un nuovo `GUID` . Alla base di questi fatti, la massima flessibilità di controllo delle versioni è assicurata rendendo ogni componente indipendente, unità autonoma. Per altre informazioni sulle regole che regolano i componenti, vedere [Modifica del](/windows/desktop/Msi/changing-the-component-code) codice del componente e Cosa accade se le regole dei componenti vengono [interrotte?](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken).

### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>Non combinare risorse condivise e private in un componente

Il conteggio dei riferimenti viene eseguito a livello di componente. Di conseguenza, la combinazione di risorse condivise e private in un componente rende impossibile aggiornare le risorse private, ad esempio un file eseguibile, senza sovrascrivere anche le risorse condivise. Questo scenario crea problemi di compatibilità con le versioni precedenti e impedisce di creare funzionalità side-by-side.

Ad esempio, i valori del Registro di sistema usati per registrare il pacchetto VSPackage con devono essere mantenuti in un componente separato da quello usato per registrare il [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] pacchetto VSPackage con Visual Studio. I file condivisi o i valori del Registro di sistema sono ancora presenti in un altro componente.

## <a name="scenario-1-shared-vspackage"></a>Scenario 1: VSPackage condiviso

In questo scenario, un pacchetto VSPackage condiviso (un singolo file binario che supporta più versioni di Visual Studio viene fornito in un pacchetto Windows Installer. La registrazione con ogni versione di Visual Studio è controllata dalle funzionalità selezionabili dall'utente. Ciò significa anche che quando viene assegnato a funzionalità separate, ogni componente può essere selezionato singolarmente per l'installazione o la disinstallazione, in modo che l'utente possa integrare il pacchetto VSPackage in versioni diverse di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Per altre [Windows sull'uso](/windows/desktop/Msi/windows-installer-features) delle funzionalità nei pacchetti Windows Installer.

![Programma di installazione VS Shared VSPackage](../../extensibility/internals/media/vs_sharedpackage.gif "VS_SharedPackage")

Come illustrato nella figura, i componenti condivisi fanno parte della funzionalità Feat_Common, che viene sempre installata. Rendendo visibili le Feat_VS2002 e Feat_VS2003, gli utenti possono scegliere in fase di installazione in quali versioni di Visual Studio desiderano integrare il pacchetto VSPackage. Gli utenti possono anche usare la Windows di manutenzione del programma di installazione per aggiungere o rimuovere funzionalità, che in questo caso aggiunge o rimuove le informazioni di registrazione vspackage da versioni diverse di Visual Studio.

> [!NOTE]
> L'impostazione della colonna Visualizzazione di una funzionalità su 0 la nasconde. Un valore di colonna di livello basso, ad esempio 1, garantisce che sia sempre installato. Per altre informazioni, vedere [Proprietà INSTALLLEVEL e](/windows/desktop/Msi/installlevel) [Tabella delle funzionalità](/windows/desktop/Msi/feature-table).

## <a name="scenario-2-shared-vspackage-update"></a>Scenario 2: Aggiornamento VSPackage condiviso

In questo scenario viene fornita una versione aggiornata del programma di installazione di VSPackage nello scenario 1. Per motivi di discussione, l'aggiornamento aggiunge il supporto per Visual Studio, ma potrebbe anche essere un Service Pack per la correzione di bug o una patch di sicurezza più semplice. Windows Le regole del programma di installazione per l'installazione di componenti più nuovi richiedono che i componenti invariati già presenti nel sistema non siano ricopiati. In questo caso, un sistema con la versione 1.0 già presente sovrascriverà il Comp_MyVSPackage.dll del componente aggiornato e consente agli utenti di scegliere di aggiungere la nuova funzionalità Feat_VS2005 con il Comp_VS2005_Reg.

> [!CAUTION]
> Ogni volta che un VSPackage viene condiviso tra più versioni di , è essenziale che le versioni successive del pacchetto VSPackage mantengano la compatibilità con le versioni precedenti di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Visual Studio. Se non è possibile mantenere la compatibilità con le versioni precedenti, è necessario usare VSPackage privati side-by-side. Per altre informazioni, vedere [Supporto di più versioni di Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).

![Programma di installazione dell'aggiornamento del pacchetto VS Condiviso di Visual Studio](../../extensibility/internals/media/vs_sharedpackageupdate.gif "VS_SharedPackageUpdate")

Questo scenario presenta un nuovo programma di installazione vspackage, sfruttando Windows del programma di installazione per gli aggiornamenti secondari. Gli utenti installano semplicemente la versione 1.1 e aggiornano la versione 1.0. Tuttavia, non è necessario avere la versione 1.0 nel sistema. Lo stesso programma di installazione installerà la versione 1.1 in un sistema senza la versione 1.0. Il vantaggio di fornire aggiornamenti secondari in questo modo è che non è necessario eseguire il lavoro di sviluppo di un programma di installazione dell'aggiornamento e di un programma di installazione completo del prodotto. Un programma di installazione esegue entrambi i processi. Una correzione di sicurezza o un Service Pack potrebbe invece sfruttare Windows del programma di installazione. Per altre informazioni, vedere [Applicazione di patch e aggiornamenti.](/windows/desktop/Msi/patching-and-upgrades)

## <a name="scenario-3-side-by-side-vspackage"></a>Scenario 3: Side-by-Side VSPackage

Questo scenario presenta due programmi di installazione VSPackage, uno per ogni versione Visual Studio .NET 2003 e Visual Studio. Ogni programma di installazione installa un pacchetto VSPackage side-by-side o privato( uno creato e installato in modo specifico per una particolare versione di Visual Studio). Ogni VSPackage si trova nel proprio componente. Di conseguenza, ognuno può essere utilizzato singolarmente con patch o versioni di manutenzione. Poiché la DLL VSPackage è ora specifica della versione, è possibile includere le informazioni di registrazione nello stesso componente della DLL.

![Programma di installazione del pacchetto VS side-by-side](../../extensibility/internals/media/vs_sbys_package.gif "VS_SbyS_Package")

Ogni programma di installazione include anche il codice condiviso tra i due programmi di installazione. Se il codice condiviso viene installato in un percorso comune, l'installazione di entrambi .msi file installerà il codice condiviso una sola volta. Il secondo programma di installazione incrementa semplicemente un conteggio dei riferimenti sul componente. Il conteggio dei riferimenti garantisce che se uno dei pacchetti VSPackage viene disinstallato, il codice condiviso rimarrà per l'altro VSPackage. Se viene disinstallato anche il secondo VSPackage, il codice condiviso verrà rimosso.

## <a name="scenario-4-side-by-side-vspackage-update"></a>Scenario 4: Aggiornamento side-by-side del pacchetto VSPackage

In questo scenario, il vspackage per Visual Studio ha subito una vulnerabilità di sicurezza ed è necessario eseguire un aggiornamento. Come nello scenario 2, è possibile creare un nuovo file .msi che aggiorna un'installazione esistente per includere la correzione di sicurezza, nonché distribuire nuove installazioni con la correzione di sicurezza già in atto.

In questo caso, il pacchetto VSPackage è un VSPackage gestito installato nella Global Assembly Cache (GAC). Quando si ricompila per includere la correzione di sicurezza, è necessario modificare la parte relativa al numero di revisione del numero di versione dell'assembly. Le informazioni di registrazione per il nuovo numero di versione dell'assembly sovrascrivono la versione precedente, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] causando il caricamento dell'assembly fisso.

![Programma di installazione dell'aggiornamento di vs package side-by-side](../../extensibility/internals/media/vs_sbys_packageupdate.gif "VS_SbyS_PackageUpdate")

Per altre informazioni sulla distribuzione di assembly side-by-side, vedere [Simplifying Deployment and Solving DLL Hell with the .NET Framework](/previous-versions/dotnet/articles/ms973843(v=msdn.10)).

## <a name="see-also"></a>Vedi anche

- [Windows Installer](/windows/desktop/Msi/windows-installer-portal)
- [Supporto di più versioni di Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)