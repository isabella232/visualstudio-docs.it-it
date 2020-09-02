---
title: Scenari di installazione di VSPackage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, deployment considerations
ms.assetid: d2928498-f27c-46b4-a9cd-cba41fd85a10
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a09b794a6cd81966df45a1b30182040d7ab9335e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696748"
---
# <a name="vspackage-setup-scenarios"></a>Scenari di installazione di pacchetti VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

È importante progettare il programma di installazione VSPackage per la flessibilità. Ad esempio, potrebbe essere necessario rilasciare una patch di sicurezza in futuro oppure modificare una strategia aziendale che richiede un supporto completo per il controllo delle versioni side-by-side.  
  
 Per [supportare più versioni di Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md), è possibile leggere i vantaggi e i problemi di supporto delle installazioni affiancate di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] con installazioni condivise o affiancate del pacchetto VSPackage. In breve, i pacchetti VSPackage affiancati offrono la massima flessibilità per supportare le nuove funzionalità di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 Gli scenari illustrati in questo argomento non sono le uniche opzioni disponibili, ma vengono presentati come procedure consigliate.  
  
## <a name="components-privacy-and-sharing"></a>Componenti, privacy e condivisione  
  
##### <a name="make-your-components-independent"></a>Rendere i componenti indipendenti  
 Quando si identifica e si popola un componente, si assegna un oggetto `GUID` e si distribuisce il componente, non è possibile modificarne la composizione. Se si modifica la composizione di un componente, il componente risultante deve essere un nuovo componente con un nuovo `GUID` . In base a questi fatti, la maggiore flessibilità di controllo delle versioni viene garantita rendendo indipendente ogni componente. Per ulteriori informazioni sulle regole che disciplinano i componenti, vedere [modifica del codice componente](https://msdn.microsoft.com/library/aa367849\(VS.85\).aspx) e [cosa accade se le regole dei componenti sono interrotte?](https://msdn.microsoft.com/library/aa372795\(VS.85\).aspx).  
  
##### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>Non combinare risorse condivise e private in un componente  
 Il conteggio dei riferimenti viene eseguito a livello di componente. Di conseguenza, la combinazione di risorse condivise e private in un componente rende impossibile l'aggiornamento delle risorse private, ad esempio un file eseguibile, senza sovrascrivere le risorse condivise. Questo scenario crea problemi di compatibilità con le versioni precedenti e limita la creazione di funzionalità side-by-side.  
  
 Ad esempio, i valori del registro di sistema usati per registrare il pacchetto VSPackage con [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] devono essere conservati in un componente separato da quello usato per registrare il pacchetto VSPackage con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . I file condivisi o i valori del registro di sistema vengono inseriti in un altro componente.  
  
## <a name="scenario-1-shared-vspackage"></a>Scenario 1: pacchetto VSPackage condiviso  
 In questo scenario, un pacchetto VSPackage condiviso (un singolo file binario che supporta più versioni di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ) viene fornito in un pacchetto di Windows Installer. La registrazione a ogni versione di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] è controllata dalle funzionalità selezionabili dall'utente. Indica inoltre che, quando vengono assegnate funzionalità separate, ogni componente può essere selezionato singolarmente per l'installazione o la disinstallazione, consentendo all'utente di controllare l'integrazione del pacchetto VSPackage in versioni diverse di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Per ulteriori informazioni sull'utilizzo delle funzionalità di Windows Installer pacchetti, vedere [Windows Installer funzionalità](https://msdn.microsoft.com/library/aa372840\(VS.85\).aspx) .  
  
 ![Rappresentazione grafica dei prodotti del package VS condivisi](../../extensibility/internals/media/vs-sharedpackage.gif "VS_SharedPackage")  
Programma di installazione di VSPackage condiviso  
  
 Come illustrato nell'illustrazione, i componenti condivisi vengono creati parte della funzionalità Feat_Common, che è sempre installata. Rendendo visibili le funzionalità di Feat_VS2002 e Feat_VS2003, gli utenti possono scegliere in fase di installazione in quali versioni [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] desiderano integrare il pacchetto VSPackage. Gli utenti possono inoltre utilizzare Windows Installer modalità manutenzione per aggiungere o rimuovere funzionalità, che in questo caso aggiungono o rimuovono le informazioni di registrazione VSPackage da versioni diverse di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
> [!NOTE]
> Se si imposta la colonna di visualizzazione di una funzionalità su 0, questa viene nascosta. Un valore di colonna di basso livello, ad esempio 1, garantisce che venga sempre installato. Per ulteriori informazioni, vedere la pagina relativa alla [Proprietà INSTALLLEVEL](https://msdn.microsoft.com/library/aa369536\(VS.85\).aspx) e alla [tabella delle funzionalità](https://msdn.microsoft.com/library/aa368585.aspx).  
  
## <a name="scenario-2-shared-vspackage-update"></a>Scenario 2: aggiornamento VSPackage condiviso  
 In questo scenario viene spedita una versione aggiornata del programma di installazione VSPackage nello scenario 1. Per quanto riguarda la discussione, l'aggiornamento aggiunge il supporto per [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , ma potrebbe anche essere una patch di sicurezza più semplice o una correzione di bug Service Pack. Le regole di Windows Installer per l'installazione di componenti più recenti richiedono che i componenti non modificati già presenti nel sistema non vengano ricopiati. In questo caso, un sistema con versione 1,0 già presente sovrascriverà il componente aggiornato Comp_MyVSPackage.dll e consentirà agli utenti di scegliere di aggiungere la nuova funzionalità Feat_VS2005 con il componente Comp_VS2005_Reg.  
  
> [!CAUTION]
> Ogni volta che un pacchetto VSPackage viene condiviso tra più versioni di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , è essenziale che le versioni successive del pacchetto VSPackage mantengano la compatibilità con le versioni precedenti di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Laddove non è possibile mantenere la compatibilità con le versioni precedenti, è necessario utilizzare i pacchetti VSPackage privati affiancati. Per altre informazioni, vedere [supporto di più versioni di Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).  
  
 ![Immagine dell'aggiornamento dei prodotti del package VS condivisi](../../extensibility/internals/media/vs-sharedpackageupdate.gif "VS_SharedPackageUpdate")  
Programma di installazione dell'aggiornamento VSPackage condiviso  
  
 Questo scenario presenta un nuovo programma di installazione VSPackage, sfruttando i vantaggi del supporto di Windows Installer per gli aggiornamenti secondari. Gli utenti installano semplicemente la versione 1,1 e aggiorna la versione 1,0. Tuttavia, non è necessario avere la versione 1,0 nel sistema. Lo stesso programma di installazione installerà la versione 1,1 in un sistema senza la versione 1,0. Il vantaggio di fornire aggiornamenti secondari in questo modo è che non è necessario eseguire il lavoro di sviluppo di un programma di installazione di aggiornamento e di un programma di installazione completo del prodotto. Un programma di installazione esegue entrambi i processi. Una soluzione di sicurezza o Service Pack può invece sfruttare i vantaggi delle patch di Windows Installer. Per ulteriori informazioni, vedere applicazione di [patch e aggiornamenti](https://msdn.microsoft.com/library/aa370579\(VS.85\).aspx).  
  
## <a name="scenario-3-side-by-side-vspackage"></a>Scenario 3: VSPackage affiancato  
 Questo scenario presenta due programmi di installazione VSPackage, uno per ogni versione di Visual Studio .NET 2003 e [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Ogni programma di installazione installa un pacchetto VSPackage affiancato, o privato, che viene compilato e installato in modo specifico per una determinata versione di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Ogni pacchetto VSPackage si trova nel proprio componente. Di conseguenza, ogni servizio può essere gestito individualmente con patch o versioni di manutenzione. Poiché la DLL del pacchetto VSPackage è ora specifica della versione, è possibile includere le informazioni di registrazione nello stesso componente della DLL.  
  
 ![Rappresentazione grafica di vs lato&#45;per&#45;](../../extensibility/internals/media/vs-sbys-package.gif "VS_SbyS_Package")  
Programma di installazione side-by-side VSPackage  
  
 Ogni programma di installazione include anche codice condiviso tra i due programmi di installazione. Se il codice condiviso viene installato in un percorso comune, l'installazione di entrambi i file MSI installerà il codice condiviso una sola volta. Il secondo programma di installazione incrementa semplicemente un conteggio dei riferimenti sul componente. Il conteggio dei riferimenti garantisce che se uno dei pacchetti VSPackage viene disinstallato, il codice condiviso rimarrà per l'altro VSPackage. Se viene disinstallato anche il secondo pacchetto VSPackage, il codice condiviso verrà rimosso.  
  
## <a name="scenario-4-side-by-side-vspackage-update"></a>Scenario 4: aggiornamento di VSPackage affiancato  
 In questo scenario, il pacchetto VSPackage per [!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)] ha subito una vulnerabilità di sicurezza ed è necessario eseguire un aggiornamento. Come nello scenario 2, è possibile creare un nuovo file con estensione msi che aggiorna un'installazione esistente per includere la correzione per la sicurezza, nonché distribuire nuove installazioni con la correzione della sicurezza già in vigore.  
  
 In questo caso, il pacchetto VSPackage è un pacchetto VSPackage gestito installato nella Global Assembly Cache (GAC). Quando si ricompila la correzione per includere la correzione per la sicurezza, è necessario modificare la parte relativa al numero di revisione del numero di versione dell'assembly. Le informazioni di registrazione per il nuovo numero di versione dell'assembly sovrascrivono la versione precedente, causando [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] il caricamento dell'assembly fisso.  
  
 ![Rappresentazione grafica dell'aggiornamento del pacchetto di Visual Studio Side&#45;by&#45;](../../extensibility/internals/media/vs-sbys-packageupdate.gif "VS_SbyS_PackageUpdate")  
Programma di installazione dell'aggiornamento di VSPackage affiancato  
  
 **Nota** Per altre informazioni sulla distribuzione di assembly affiancati, vedere [semplificare la distribuzione e la risoluzione di dll Hello con la .NET Framework](https://msdn.microsoft.com/library/ms973843.aspx).  
  
## <a name="see-also"></a>Vedere anche  
 [Windows Installer](https://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [Supporto di più versioni di Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)
