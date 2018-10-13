---
title: Finestra di dialogo Prerequisiti | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Microsoft.VisualStudio.Publish.BaseProvider.Dialog.Bootstrapper
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Prerequisites dialog box
ms.assetid: 53ac863c-77a0-409b-91e5-7a4bd8b8474e
caps.latest.revision: 79
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6aff33e7129123e2f910116a5d9352944e1c064a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49183950"
---
# <a name="prerequisites-dialog-box"></a>Prerequisiti (finestra di dialogo)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
In questa finestra di dialogo vengono indicati i componenti dei prerequisiti installati, la modalità di installazione e l'ordine di installazione dei pacchetti.  
  
 Per accedere a questa finestra di dialogo, selezionare un nodo di progetto in **Esplora soluzioni**, quindi scegliere **Proprietà** dal menu **Progetto**. In **Progettazione progetti** fare clic sulla scheda **Pubblica** . Nella pagina **Pubblica** fare clic su **Prerequisiti**. Per i progetti di installazione, scegliere **Proprietà** dal menu **Progetto**. Quando viene visualizzata la finestra di dialogo **Pagine delle proprietà** fare clic su **Prerequisiti**.  
  
## <a name="uielement-list"></a>Elenco UIElement  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|**Crea programma di installazione per installare componenti dei prerequisiti**|Nel programma di installazione dell'applicazione (Setup.exe) include i componenti dei prerequisiti che verranno installati prima dell'applicazione, in ordine di dipendenza. Questa opzione è selezionata per impostazione predefinita. Se l'opzione non è selezionata, non viene creato alcun programma Setup.exe.|  
|**Scegliere i prerequisiti da installare**|Specifica se installare i componenti come [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], Crystal Reports e così via.<br /><br /> Ad esempio, selezionando la casella di controllo accanto a **SQL Server 2005 Express Edition SP2**, si specifica che il programma di installazione deve verificare se tale componente è già installato nel computer di destinazione e, in caso contrario, installarlo.<br /><br /> Per informazioni dettagliate su ciascun pacchetto di prerequisiti, vedere la tabella Informazioni sui prerequisiti più avanti in questo argomento.|  
|**Controlla il sito Microsoft Update per altri componenti ridistribuibili**|Se si fa clic su questo collegamento, si viene indirizzati al sito Web [Pacchetti del programma di avvio automatico per ridistribuire i componenti](http://go.microsoft.com/fwlink/?LinkId=208835) per controllare la disponibilità di aggiornamenti.|  
|**Scarica prerequisiti dal sito Web del fornitore del componente**|Specifica che i componenti dei prerequisiti devono essere installati dal sito Web del fornitore. Questa è l'opzione predefinita.|  
|**Scarica prerequisiti dallo stesso percorso dell'applicazione**|Specifica che i componenti dei prerequisiti devono essere installati dallo stesso percorso dell'applicazione. In questo modo vengono copiati tutti i pacchetti di prerequisiti nel percorso di pubblicazione. Per il corretto funzionamento di questa opzione, i pacchetti di prerequisiti devono essere presenti nel computer di sviluppo.|  
|**Scarica prerequisiti dal seguente percorso**|Specifica che i componenti dei prerequisiti devono essere installati dal percorso selezionato. Per selezionare un percorso usare il pulsante **Sfoglia**.|  
  
## <a name="prerequisites-information"></a>Informazioni sui prerequisiti  
 I componenti dei prerequisiti che sono visualizzati nella finestra di dialogo **Prerequisiti** potrebbero differire da quelli presenti nell'elenco seguente. I pacchetti dei prerequisiti elencati nella **finestra di dialogo Prerequisiti** vengono impostati automaticamente alla prima apertura della finestra di dialogo. In caso di modifiche successive al framework di destinazione del progetto, sarà necessario selezionare manualmente i prerequisiti in modo che vi sia corrispondenza.  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|**.NET Framework 3.5 SP1**|Con questo pacchetto vengono installati gli elementi seguenti:<br /><br /> -   .NET Framework versioni 2.0, 3.0 e 3.5.<br />-   Supporto per tutte le versioni di .NET Framework nei sistemi operativi a 32 bit (x86) e a 64 bit (x64).<br />-   Language Pack per ciascuna versione di .NET Framework installata con il pacchetto.<br />-   Service Pack per .NET Framework 2.0 e 3.0.<br /><br /> .NET Framework 3.0 viene fornito con Windows Vista e .NET Framework 3.5 viene fornito con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. .NET Framework 3.5 è necessario per tutti i progetti Visual Basic e Visual C# che vengono compilati per i sistemi operativi a 32 bit e per i quali il framework di destinazione è impostato su **.NET Framework 3.5**, oltre che per i progetti Visual Basic e Visual C# compilati per i sistemi operativi a 64 bit. IA64 non è supportato. Si noti che i progetti Visual Basic e Visual C# vengono compilati per qualsiasi architettura della CPU per impostazione predefinita. Per altre informazioni, vedere [Panoramica del multitargeting di Visual Studio](../../ide/visual-studio-multi-targeting-overview.md), [Ridistribuzione di .NET Framework](http://msdn.microsoft.com/en-us/a18d0456-fd89-493e-97f4-756505bfe287) e [Prerequisiti per la distribuzione di applicazioni a 64 bit](../../deployment/deploying-prerequisites-for-64-bit-applications.md).<br /><br /> Questo elemento è selezionato per impostazione predefinita.|  
|**.NET Framework 3.5 SP1 Client Profile**|.NET Framework Client Profile è un sottoinsieme della versione completa di .NET Framework 3.5 SP1 destinata alle applicazioni client. Fornisce un sottoinsieme semplificato delle funzionalità di Windows Presentation Foundation (WPF), Windows Form, Windows Communication Foundation (WCF) e ClickOnce. In questo modo, è possibile rendere disponibili scenari di distribuzione rapidi per WPF, Windows Form, WCF e applicazioni console destinate a .NET Framework Client Profile. Per altre informazioni, vedere [.NET Framework Client Profile](http://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1).|  
|**Microsoft .NET Framework 4 (x86 e x64)**|Con questo pacchetto viene installato .NET Framework 4 per piattaforme x86 e x64.<br /><br /> Per altre informazioni, vedere [Panoramica del multitargeting di Visual Studio](../../ide/visual-studio-multi-targeting-overview.md), [Ridistribuzione di .NET Framework](http://msdn.microsoft.com/en-us/a18d0456-fd89-493e-97f4-756505bfe287) e [Prerequisiti per la distribuzione di applicazioni a 64 bit](../../deployment/deploying-prerequisites-for-64-bit-applications.md).<br /><br /> Questo elemento è selezionato per impostazione predefinita.|  
|**Microsoft .NET Framework 4 Client Profile (x86 e x64)**|.NET Framework 4 Client Profile è un sottoinsieme della versione completa di .NET Framework 4 destinata alle applicazioni client. Fornisce un sottoinsieme semplificato delle funzionalità di Windows Presentation Foundation (WPF), Windows Form, Windows Communication Foundation (WCF) e ClickOnce. In questo modo, è possibile rendere disponibili scenari di distribuzione rapidi per WPF, Windows Form e applicazioni console destinate a .NET Framework 4 Client Profile. Per altre informazioni, vedere [.NET Framework Client Profile](http://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1).|  
|**Assembly di interoperabilità primari di Microsoft Office 2007**|Con questo pacchetto vengono installati gli assembly di interoperabilità primari per prodotti Microsoft Office 2007. Gli assembly di interoperabilità primari consentono l'interazione tra il codice gestito e il modello a oggetti basati su COM di un'applicazione di Microsoft Office. Per altre informazioni, vedere [Assembly di interoperabilità primari di Office](http://msdn.microsoft.com/library/aa29d12c-185f-4558-a7cd-3d85f924203d).|  
|**Microsoft Visual Basic PowerPacks versione 10.0**|I Power Pack sono componenti aggiuntivi, controlli, componenti e strumenti utili allo sviluppo di applicazioni Visual Basic. In questa versione è incluso il componente <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>, che consente di stampare il contenuto di un Windows Form, e la Printer Compatibility Library, che consente di eseguire il codice Printer di Visual Basic 6.0 senza modifiche.|  
|**Microsoft Visual F# Runtime per .NET 2.0**|Con questo pacchetto vengono installate librerie di runtime di Visual F# per sistemi operativi x86 e x64 che forniscono supporto sia per la programmazione funzionale che per la programmazione orientata a oggetti e imperativa (procedurale) tradizionale. È necessario installare questo pacchetto se l'applicazione o i relativi componenti vengono creati in Visual F# e .NET Framework 2.0, .NET Framework 3.0 o .NET Framework 3.5.<br /><br /> Per altre informazioni, vedere [Riferimenti per il linguaggio F#](http://msdn.microsoft.com/library/16b706f8-b5f2-4ff7-b2c1-64df33cd6adf).|  
|**Microsoft Visual F# Runtime per .NET 4.0**|Con questo pacchetto vengono installate librerie di runtime di Visual F# per sistemi operativi x86 e x64 che forniscono supporto sia per la programmazione funzionale che per la programmazione orientata a oggetti e imperativa (procedurale) tradizionale. È necessario installare questo pacchetto se l'applicazione o i relativi componenti vengono creati in Visual F# e .NET Framework 4.<br /><br /> Per altre informazioni, vedere [Riferimenti per il linguaggio F#](http://msdn.microsoft.com/library/16b706f8-b5f2-4ff7-b2c1-64df33cd6adf).|  
|**Microsoft Visual Studio 2010 Report Viewer**|Con questo pacchetto vengono installati nuovi controlli del visualizzatore rapporti che consentono di aggiungere funzionalità avanzate per i report di dati alle applicazioni Windows Form e ASP.NET.|  
|**Microsoft Visual Studio 2010 per Office Runtime (x86 e x64)**|Gli strumenti di sviluppo di Office in Visual Studio offrono strumenti integrati e facili da utilizzare per la creazione di soluzioni aziendali personalizzate con Microsoft Office. È possibile creare soluzioni Smart Client gestite nelle quali le applicazioni Office vengono utilizzate come interfaccia utente. Gli strumenti consentono agli sviluppatori di creare soluzioni protette, facili da distribuire e gestire.<br /><br /> Per altre informazioni, vedere [Procedura: Distribuire una soluzione Office usando ClickOnce](http://msdn.microsoft.com/en-us/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8).|  
|**SQL Server 2005 Express Edition SP2 (x86)**|Questo pacchetto consente di installare Microsoft SQL Server 2005 Express Edition SP2, un'applicazione di database basata su [!INCLUDE[sqprsqext](../../includes/sqprsqext-md.md)]. SQL Server Express sostituisce Microsoft SQL Server Desktop Engine (MSDE). SQL Server Express è gratuito e può essere ridistribuito (secondo contratto). Funziona sia come un database client sia come un database server di base. Equivale a SQL Server 2005, a eccezione di quanto segue:<br /><br /> -   Nessun supporto per funzionalità aziendali.<br />-   Limitato a una CPU.<br />-   La memoria è limitata a 1 GB per il pool di buffer.<br />-   La dimensione massima per i database è limitata a 4 GB.|  
|**SQL Server 2008 Express**|Con questo pacchetto viene installato Microsoft SQL Server 2008 Express, un'edizione gratuita di Microsoft SQL Server 2008, un database ideale per piccole applicazioni Web, server o desktop. Può essere utilizzato gratuitamente per lo sviluppo e la produzione. Per distribuire SQL Server 2008 Express con l'applicazione è necessaria una [registrazione](http://go.microsoft.com/fwlink/?LinkId=130380) gratuita.<br /><br /> Di seguito viene descritto il comportamento del programma di avvio automatico:<br /><br /> -   Se il computer dispone già di SQL Server 2008 Express o versioni successive, rimarrà con SQL Server 2008 Express o versioni successive.<br />-   Se il computer non dispone di SQL Server 2008 Express né delle versioni successive, con il pacchetto viene installata la versione più recente di SQL Server 2008 Express SP1.<br /><br /> Per altre informazioni su SQL Server 2008 Express, visitare [ http://go.microsoft.com/fwlink/?LinkId=183586 ](http://go.microsoft.com/fwlink/?LinkId=183586).|  
|**Librerie di runtime di Visual C++ 2010 (IA64)**|Con questo pacchetto vengono installate le librerie di runtime di Visual C++ per l'architettura Itanium che forniscono routine di programmazione per il sistema operativo Microsoft Windows. Queste routine consentono di automatizzare molte attività di programmazione comuni non fornite dai linguaggi C e C++.<br /><br /> Per altyre informazioni, vedere [Riferimenti alla libreria di runtime C](http://msdn.microsoft.com/library/a503e11c-8dca-4846-84fb-025a826c32b8).|  
|**Librerie di runtime di Visual C++ 2010 (x64)**|Con questo pacchetto vengono installate le librerie di runtime di Visual C++ per i sistemi operativi x64 che forniscono routine di programmazione per il sistema operativo Microsoft Windows. Queste routine consentono di automatizzare molte attività di programmazione comuni non fornite dai linguaggi C e C++.<br /><br /> Per altyre informazioni, vedere [Riferimenti alla libreria di runtime C](http://msdn.microsoft.com/library/a503e11c-8dca-4846-84fb-025a826c32b8).|  
|**Librerie di runtime di Visual C++ 2010 (x86)**|Con questo pacchetto vengono installate le librerie di runtime di Visual C++ per i sistemi operativi x86 che forniscono routine di programmazione per il sistema operativo Microsoft Windows. Queste routine consentono di automatizzare molte attività di programmazione comuni non fornite dai linguaggi C e C++.<br /><br /> Per altyre informazioni, vedere [Riferimenti alla libreria di runtime C](http://msdn.microsoft.com/library/a503e11c-8dca-4846-84fb-025a826c32b8).|  
|**Windows Installer 3.1**|Con questo pacchetto viene installato Microsoft Windows Installer Redistributable versione 3.1 che consente l'installazione di progetti di installazione di Windows Installer. È preinstallato in Windows Server 2003 con SP1 e versioni successive.<br /><br /> Questo elemento è selezionato per impostazione predefinita.|  
|**Windows Installer 4.5**|Con questo pacchetto viene installato Microsoft Windows Installer Redistributable versione 4.5 che consente l'installazione di progetti di installazione di Windows Installer.|  
  
## <a name="see-also"></a>Vedere anche  
 [Pagina Pubblica, Creazione progetti](../../ide/reference/publish-page-project-designer.md)   
 [Prerequisiti per la distribuzione dell'applicazione](../../deployment/application-deployment-prerequisites.md)   
 [Ridistribuzione di .NET Framework](http://msdn.microsoft.com/en-us/a18d0456-fd89-493e-97f4-756505bfe287)   
 [Prerequisiti per la distribuzione di applicazioni a 64 bit](../../deployment/deploying-prerequisites-for-64-bit-applications.md)   
 [Panoramica del multitargeting di Visual Studio](../../ide/visual-studio-multi-targeting-overview.md)



