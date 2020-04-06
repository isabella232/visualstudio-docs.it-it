---
title: Scenari di installazione di VSPackage - Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, deployment considerations
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 01279666642adb729d4350b8a497c42d78159120
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703979"
---
# <a name="vspackage-setup-scenarios"></a>Scenari di installazione di pacchetti VSPackage

È importante progettare il programma di installazione di VSPackage per la flessibilità. Ad esempio, potrebbe essere necessario rilasciare una patch di protezione in futuro oppure modificare una strategia aziendale che richiede un supporto completo del controllo delle versioni side-by-side.

In [Supporto di più versioni di Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md), è possibile leggere i [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vantaggi e i problemi del supporto di installazioni side-by-side con installazioni condivise o side-by-side del pacchetto VSPackage. In breve, side-by-side VSPackage offrono la massima flessibilità per supportare le nuove funzionalità di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

Gli scenari illustrati in questo argomento non sono le uniche scelte, ma vengono presentati come procedure consigliate consigliate.

## <a name="components-privacy-and-sharing"></a>Componenti, Privacy e Condivisione

### <a name="make-your-components-independent"></a>Rendi indipendenti i tuoi componenti

Una volta identificato e popolato `GUID`un componente, assegnato un e distribuirlo, non potete modificarne la composizione. Se modificate la composizione di un componente, il componente risultante `GUID`deve essere un nuovo componente con un nuovo oggetto . Alla base di questi fatti, la massima flessibilità di controllo delle versioni è garantita rendendo ogni componente indipendente, unità autosufficiente. Per ulteriori informazioni sulle regole che regolano i componenti, vedere [Modifica del codice del componente](/windows/desktop/Msi/changing-the-component-code) e Cosa accade se le regole dei componenti vengono [interrotte?](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken).

### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>Non combinare risorse condivise e private in un componente

Il conteggio dei riferimenti si verifica a livello di componente. Di conseguenza, la combinazione di risorse condivise e private in un componente rende impossibile aggiornare le risorse private, ad esempio un file eseguibile, senza sovrascrivere anche le risorse condivise. Questo scenario crea problemi di compatibilità con le versioni precedenti e impedisce la creazione di funzionalità side-by-side.

Ad esempio, i valori del Registro [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] di sistema utilizzati per registrare il pacchetto VSPackage con il deve essere mantenuto in un componente separato da quello utilizzato per registrare il pacchetto VSPackage con Visual Studio.For example, registry values used to register your VSPackage with the should be kept in a component separate from one used to register your VSPackage with Visual Studio. I file condivisi o i valori del Registro di sistema vengono riprodotti in un altro componente.

## <a name="scenario-1-shared-vspackage"></a>Scenario 1: Shared VSPackage

In questo scenario, un VSPackage condiviso (un singolo binario che supporta più versioni di Visual Studio viene fornito in un pacchetto di Windows Installer. La registrazione con ogni versione di Visual Studio è controllata da funzionalità selezionabili dall'utente. Significa anche che quando assegnato a funzionalità separate, ogni componente può essere selezionato singolarmente per l'installazione o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]la disinstallazione, mettendo l'utente nel controllo dell'integrazione del pacchetto VSPackage in diverse versioni di . Per ulteriori informazioni sull'utilizzo dei pacchetti di Windows Installer, vedere Funzionalità di [Windows Installer.](/windows/desktop/Msi/windows-installer-features)

![Programma di installazione VS Shared VSPackage](../../extensibility/internals/media/vs_sharedpackage.gif "VS_SharedPackage")

Come illustrato nella figura, i componenti condivisi fanno parte della funzionalità Feat_Common, che viene sempre installata. Rendendo visibili le funzionalità Feat_VS2002 e Feat_VS2003, gli utenti possono scegliere in fase di installazione in quali versioni di Visual Studio si desidera integrare il pacchetto VSPackage. Gli utenti possono anche utilizzare la modalità di manutenzione di Windows Installer per aggiungere o rimuovere funzionalità, che in questo caso aggiunge o rimuove le informazioni di registrazione VSPackage da versioni diverse di Visual Studio.Users can also use Windows Installer maintenance mode to add or remove features, which in this case adds or removes the VSPackage registration information from different versions of Visual Studio.

> [!NOTE]
> L'impostazione della colonna Visualizzazione di una feature su 0 la nasconde. Un valore di colonna di livello basso, ad esempio 1, garantisce che verrà sempre installato. Per ulteriori informazioni, vedere [INSTALLLEVEL Property](/windows/desktop/Msi/installlevel) and [Feature Table](/windows/desktop/Msi/feature-table).

## <a name="scenario-2-shared-vspackage-update"></a>Scenario 2: Shared VSPackage Update

In questo scenario, viene fornita una versione aggiornata del programma di installazione VSPackage nello scenario 1. Per motivi di discussione, l'aggiornamento aggiunge il supporto per Visual Studio, ma potrebbe anche essere una patch di protezione più semplice o un service pack per la correzione di bug. Le regole di Windows Installer per l'installazione di componenti più recenti richiedono che i componenti non modificati già presenti nel sistema non vengano copiati nuovamente. In questo caso, un sistema con la versione 1.0 già presente sovrascriverà il componente aggiornato Comp_MyVSPackage.dll e consentirà agli utenti di scegliere di aggiungere la nuova funzionalità Feat_VS2005 con il componente Comp_VS2005_Reg.

> [!CAUTION]
> Ogni volta che un pacchetto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]VSPackage viene condiviso tra più versioni di , è essenziale che le versioni successive del pacchetto VSPackage mantenere la compatibilità con le versioni precedenti di Visual Studio. Dove non è possibile mantenere la compatibilità con le versioni precedenti, è necessario utilizzare side-by-side, VSPackage privati. Per ulteriori informazioni, vedere [Supporto di più versioni di Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).

![Programma di installazione dell'aggiornamento del pacchetto VS condiviso VS](../../extensibility/internals/media/vs_sharedpackageupdate.gif "VS_SharedPackageUpdate")

Questo scenario presenta un nuovo programma di installazione VSPackage, sfruttando il supporto di Windows Installer per gli aggiornamenti minori. Gli utenti installano semplicemente la versione 1.1 e aggiorna la versione 1.0. Tuttavia, non è necessario disporre della versione 1.0 nel sistema. Lo stesso programma di installazione installerà la versione 1.1 su un sistema senza versione 1.0. Il vantaggio di fornire aggiornamenti minori in questo modo è che non è necessario passare attraverso il lavoro di sviluppo di un programma di installazione di aggiornamento e un programma di installazione completo del prodotto. Un programma di installazione esegue entrambi i processi. Una correzione di protezione o un service pack potrebbe invece sfruttare le patch di Windows Installer. Per ulteriori informazioni, vedere [Applicazione di patch e aggiornamenti](/windows/desktop/Msi/patching-and-upgrades).

## <a name="scenario-3-side-by-side-vspackage"></a>Scenario 3: Side-by-Side VSPackage

In questo scenario vengono presentate due programmi di installazione VSPackage, uno per ogni versione di Visual Studio .NET 2003 e Visual Studio. Ogni programma di installazione installa un pacchetto VSPackage side-by-side o privato (uno creato e installato in modo specifico per una particolare versione di Visual Studio). Ogni VSPackage è nel proprio componente. Di conseguenza, ognuno può essere servito singolarmente con patch o rilasci di manutenzione. Poiché la DLL VSPackage è ora specifica della versione, è possibile includere le informazioni di registrazione nello stesso componente della DLL.

![Programma di installazione del pacchetto VS side-by-side VS VS](../../extensibility/internals/media/vs_sbys_package.gif "VS_SbyS_Package")

Ogni programma di installazione include anche il codice condiviso tra i due programmi di installazione. Se il codice condiviso viene installato in un percorso comune, l'installazione di entrambi i file con estensione msi installerà il codice condiviso una sola volta. Il secondo programma di installazione incrementa solo un conteggio dei riferimenti sul componente. Il conteggio dei riferimenti garantisce che se uno dei package VS viene disinstallato, il codice condiviso rimarrà per l'altro VSPackage. Se viene disinstallato anche il secondo VSPackage, il codice condiviso verrà rimosso.

## <a name="scenario-4-side-by-side-vspackage-update"></a>Scenario 4: Side-by-Side VSPackage Update

In questo scenario, il pacchetto VSPackage per Visual Studio ha sofferto di una vulnerabilità di sicurezza ed è necessario rilasciare un aggiornamento. Come nello scenario 2, è possibile creare un nuovo file con estensione msi che aggiorna un'installazione esistente per includere la correzione di sicurezza, nonché distribuire nuove installazioni con la correzione di sicurezza già presente.

In questo caso, il pacchetto VSPackage è un VSPackage gestito installato nella Global Assembly Cache (GAC). Quando si ricompila per includere la correzione di sicurezza, è necessario modificare la parte relativa al numero di revisione del numero di versione dell'assembly. Le informazioni di registrazione per il nuovo numero [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di versione dell'assembly sovrascrive la versione precedente, causando il caricamento dell'assembly fisso.

![Programma di installazione dell'aggiornamento dei pacchetti VS side-by-side VS](../../extensibility/internals/media/vs_sbys_packageupdate.gif "VS_SbyS_PackageUpdate")

Per ulteriori informazioni sulla distribuzione di assembly side-by-side, vedere [Semplificazione della distribuzione e risoluzione dell'aggiornamento](https://msdn.microsoft.com/library/ms973843.aspx)delle DLL con .NET Framework .

## <a name="see-also"></a>Vedere anche

- [Programma di installazione di Windows](/windows/desktop/Msi/windows-installer-portal)
- [Supporto di più versioni di Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)
