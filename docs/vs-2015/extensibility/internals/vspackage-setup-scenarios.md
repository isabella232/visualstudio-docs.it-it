---
title: Scenari di installazione di pacchetti VSPackage | Microsoft Docs
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
ms.openlocfilehash: 58b4350812900bc11e8aaa3222b3b0898db19e13
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440794"
---
# <a name="vspackage-setup-scenarios"></a>Scenari di installazione di pacchetti VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

È importante progettare il programma di installazione di VSPackage per la flessibilità. Ad esempio, potrebbe essere necessario rilasciare una patch di sicurezza in futuro oppure è possibile modificare una strategia di business che richiede il supporto del controllo delle versioni side-by-side completa.  
  
 Nelle [supporto di più versioni di Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md), è possibile leggere sui vantaggi e i problemi di supportare le installazioni side-by-side di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] le installazioni dei componenti condivisi o side-by-side di un VSPackage. In breve, i pacchetti VSPackage side-by-side offrono la massima flessibilità per supportare nuove funzionalità di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 Gli scenari descritti in questo argomento non sono le uniche scelte a disposizione, ma sono presentati come procedure consigliate.  
  
## <a name="components-privacy-and-sharing"></a>I componenti, Privacy e la condivisione  
  
##### <a name="make-your-components-independent"></a>Creazione di componenti indipendenti  
 Dopo avere identificato e compilare un componente, assegnare un `GUID`e distribuire il componente, non è possibile modificare la composizione. Se si modifica la composizione del componente, il componente risulta deve essere un nuovo componente con un nuovo `GUID`. La maggiore flessibilità nel versionamento dato questi fatti, si applicano apportando ogni unità indipendenti, radicato componente. Per altre informazioni sulle regole che controllano i componenti, vedere [modifica del codice del componente](http://msdn.microsoft.com/library/aa367849\(VS.85\).aspx) e [cosa accade se le regole di componente vengono interrotti?](http://msdn.microsoft.com/library/aa372795\(VS.85\).aspx).  
  
##### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>Non combinare risorse condivise e private in un componente  
 Il conteggio dei riferimenti si verifica a livello di componente. Di conseguenza, combinandole condivisi e privati in un singolo componente rende Impossibile aggiornare le risorse private, ad esempio un file eseguibile, senza sovrascrivere anche le risorse condivise. Questo scenario consente di creare problemi di compatibilità e limita la possibilità di creazione di funzionalità side-by-side.  
  
 I valori del Registro di sistema, ad esempio, consente di registrare il pacchetto VSPackage con il [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] deve essere mantenuto in un componente separato da quello utilizzato per registrare il pacchetto VSPackage con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. File condivisi o i valori del Registro di sistema passa in un altro componente.  
  
## <a name="scenario-1-shared-vspackage"></a>Scenario 1: Package VS condivisi  
 In questo scenario, un pacchetto VSPackage condiviso (un singolo file binario che supporta più versioni di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]) viene fornito in un pacchetto Windows Installer. La registrazione con ogni versione di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] è controllato dalle funzionalità selezionabili dall'utente. Significa anche che quando assegnato per separare le funzionalità, ogni componente possa essere selezionate singolarmente per l'installazione o la disinstallazione, inserisce l'utente controlla l'integrazione di VSPackage in versioni diverse di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. (Vedere [funzionalità di Windows Installer](http://msdn.microsoft.com/library/aa372840\(VS.85\).aspx) per altre informazioni sull'utilizzo delle funzionalità nei pacchetti di Windows Installer.)  
  
 ![Rappresentazione grafica di VSPackage condivisi VS](../../extensibility/internals/media/vs-sharedpackage.gif "VS_SharedPackage")  
Programma di installazione di VSPackage condiviso  
  
 Come illustrato nella figura, i componenti condivisi diventano parte della funzionalità Feat_Common, che viene sempre installata. Per rendere visibili le funzionalità Feat_VS2002 e Feat_VS2003, gli utenti possono scegliere in fase di installazione in quali versioni di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] desiderano il pacchetto VSPackage per l'integrazione. Gli utenti possono anche usare modalità di manutenzione di Windows Installer per aggiungere o rimuovere le funzionalità, che in questo caso aggiunge o rimuove le informazioni di registrazione di VSPackage da versioni diverse di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
> [!NOTE]
> Impostazione colonna da visualizzare una funzionalità su 0 per nasconderlo. Un valore di colonna di livello basso, ad esempio 1, garantisce che sarà sempre installata. Per altre informazioni, vedere [proprietà INSTALLLEVEL](http://msdn.microsoft.com/library/aa369536\(VS.85\).aspx) e [tabella delle funzionalità](http://msdn.microsoft.com/library/aa368585.aspx).  
  
## <a name="scenario-2-shared-vspackage-update"></a>Scenario 2: Update Package VS condivisi  
 In questo scenario, è disponibile una versione aggiornata del programma di installazione pacchetto VSPackage nello scenario 1. Ai fini di discussione, l'aggiornamento aggiunge il supporto per [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], ma potrebbe anche essere un semplice security patch o correzione di bug service pack. Le regole del programma di installazione di Windows per l'installazione dei componenti più recenti richiedono che i componenti invariati nel sistema è già non vengono ricopiati. In questo caso, un sistema con la versione 1.0 sono già presenti sovrascriverà il componente aggiornato Comp_MyVSPackage.dll e consentire agli utenti di scegliere di aggiungere la nuova funzionalità Feat_VS2005 al relativo componente Comp_VS2005_Reg.  
  
> [!CAUTION]
> Ogni volta che un pacchetto VSPackage è condiviso tra più versioni di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], è essenziale che le versioni successive del pacchetto VSPackage mantenere la compatibilità con le versioni precedenti di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Dove è possibile mantenere la compatibilità con le versioni precedenti, è necessario usare i pacchetti VSPackage side-by-side e privati. Per altre informazioni, vedere [supporto di più versioni di Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).  
  
 ![Immagine dell'aggiornamento pacchetto VS condivisi](../../extensibility/internals/media/vs-sharedpackageupdate.gif "VS_SharedPackageUpdate")  
Il programma di installazione di VSPackage aggiornamento condivisi  
  
 Questo scenario presenta un nuovo pacchetto VSPackage programma di installazione, sfruttando i vantaggi del supporto del programma di installazione di Windows per gli aggiornamenti secondari. Gli utenti installano la versione 1.1 e viene aggiornato alla versione 1.0. Non è tuttavia necessario avere la versione 1.0 nel sistema. Lo stesso di installazione installerà la versione 1.1 in un sistema senza versione 1.0. Il vantaggio di fornire gli aggiornamenti secondari in questo modo è che non è necessario passare attraverso il lavoro dello sviluppo di un programma di installazione aggiornamento e un programma di installazione completa del prodotto. Un programma di installazione esegue entrambi i processi. Una correzione di sicurezza o di un servizio di tipo pack potrebbe invece sfruttare le patch di Windows Installer. Per altre informazioni, vedere [applicazione di patch e aggiornamenti](http://msdn.microsoft.com/library/aa370579\(VS.85\).aspx).  
  
## <a name="scenario-3-side-by-side-vspackage"></a>Scenario 3: VSPackage side-by-Side  
 Questo scenario presenta due programmi di installazione del pacchetto VSPackage, ovvero uno per ogni versione di Visual Studio .NET 2003 e [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Ogni programma di installazione installa un side-by-side privati, VSPackage (uno in particolare compilato e installato per una particolare versione di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]). Ogni pacchetto VSPackage è nel proprio componente. Di conseguenza, ogni eseguire singolarmente la manutenzione con le patch o manutenzione rilascia. Poiché la DLL di VSPackage è ora specifici della versione, è consigliabile includere le informazioni di registrazione nel componente stesso come DLL.  
  
 ![Sul lato di Visual Studio&#45;da&#45;immagine di pacchetto di Visual Studio Side](../../extensibility/internals/media/vs-sbys-package.gif "VS_SbyS_Package")  
Programma di installazione di VSPackage side-by-side  
  
 Ogni programma di installazione include anche codice che verrà condivisi tra i due programmi di installazione. Se il codice condiviso viene installato in un percorso comune, entrambi i file con estensione msi di installazione installerà il codice condiviso una sola volta. Il programma di installazione secondo incrementa semplicemente un conteggio dei riferimenti del componente. Il conteggio dei riferimenti garantisce che se uno dei VSPackage viene disinstallato, il codice condiviso rimarrà per altri VSPackage. Se viene disinstallato anche il pacchetto VSPackage secondario, verrà rimosso il codice condiviso.  
  
## <a name="scenario-4-side-by-side-vspackage-update"></a>Scenario 4: Aggiornamento pacchetto VSPackage side-by-Side  
 In questo scenario, il pacchetto VSPackage per [!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)] subito dalla protezione di una vulnerabilità ed è necessario rilasciare un aggiornamento. Come nello scenario 2, è possibile creare un nuovo file con estensione msi che aggiorna un'installazione esistente per includere la correzione di sicurezza, nonché di distribuire le nuove installazioni con la correzione di sicurezza già presenti.  
  
 In questo caso, il pacchetto VSPackage è un pacchetto VSPackage gestito installato nella global assembly cache (GAC). Durante la ricompilazione per includere la correzione di sicurezza, è necessario modificare la parte del numero di revisione del numero di versione di assembly. Le informazioni di registrazione per il numero di versione nuova sovrascrive quella precedente, generando [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] per caricare l'assembly predefinito.  
  
 ![Sul lato di Visual Studio&#45;da&#45;immagine di aggiornamento del pacchetto di Visual Studio Side](../../extensibility/internals/media/vs-sbys-packageupdate.gif "VS_SbyS_PackageUpdate")  
Programma di installazione side-by-side package VS update  
  
 **Nota** per altre informazioni sulla distribuzione di assembly side-by-side, vedere [semplificando la distribuzione e la risoluzione di "DLL hell" con .NET Framework](http://msdn.microsoft.com/library/ms973843.aspx).  
  
## <a name="see-also"></a>Vedere anche  
 [Windows Installer](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [Supporto di più versioni di Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)
