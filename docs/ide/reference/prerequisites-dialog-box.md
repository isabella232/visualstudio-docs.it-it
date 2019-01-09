---
title: Prerequisiti (finestra di dialogo)
ms.date: 06/29/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- Microsoft.VisualStudio.Publish.BaseProvider.Dialog.Bootstrapper
helpviewer_keywords:
- Prerequisites dialog box
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e3425573d1ee60ce5a4f96d5762b353afa18dc9b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53827101"
---
# <a name="prerequisites-dialog-box"></a>Prerequisiti (finestra di dialogo)

La finestra di dialogo **Prerequisiti** specifica i componenti dei prerequisiti installati, la modalità di installazione e l'ordine di installazione dei pacchetti.

![Finestra di dialogo Prerequisiti in Visual Studio 2017](media/prerequisites-dialog-box.png)

Per accedere a questa finestra di dialogo, selezionare un nodo di progetto in **Esplora soluzioni**, quindi scegliere **Progetto** > **Proprietà**. Quando viene visualizzata **Creazione progetti**, selezionare la scheda **Pubblica** e quindi selezionare **Prerequisiti**. Per i progetti di installazione, scegliere **Proprietà** dal menu **Progetto**. Quando viene visualizzata la finestra di dialogo **Pagine delle proprietà** fare clic su **Prerequisiti**.

## <a name="uielement-list"></a>Elenco UIElement

|Elemento|Description|
|-------------|-----------------|
|**Crea programma di installazione per installare componenti dei prerequisiti**|Include i componenti dei prerequisiti nel programma di installazione dell'applicazione (*Setup.exe*) in modo che vengano installati prima dell'applicazione in ordine di dipendenza. Questa opzione è selezionata per impostazione predefinita. Se l'opzione non è selezionata, non viene creato alcun programma *Setup.exe*.|
|**Scegliere i prerequisiti da installare**|Specifica se installare i componenti, ad esempio librerie di runtime di .NET Framework e C++.<br /><br />Ad esempio, selezionando la casella di controllo accanto a **SQL Server 2012 Express**, si specifica che il programma di installazione deve verificare se il componente è già installato nel computer di destinazione e, in caso contrario, installarlo.<br /><br />Per informazioni dettagliate su ogni pacchetto di prerequisiti, vedere [Informazioni sui prerequisiti](#prerequisites-information).|
|**Scarica prerequisiti dal sito Web del fornitore del componente**|Specifica che i componenti dei prerequisiti devono essere installati dal sito Web del fornitore. Questa è l'opzione predefinita.|
|**Scarica prerequisiti dallo stesso percorso dell'applicazione**|Specifica che i componenti dei prerequisiti devono essere installati dallo stesso percorso dell'applicazione. In questo modo vengono copiati tutti i pacchetti di prerequisiti nel percorso di pubblicazione. Per il corretto funzionamento di questa opzione, i pacchetti di prerequisiti devono essere presenti nel computer di sviluppo.|
|**Scarica prerequisiti dal seguente percorso**|Specifica che i componenti dei prerequisiti devono essere installati dal percorso specificato. Per selezionare un percorso usare il pulsante **Sfoglia**.|

## <a name="prerequisites-information"></a>Informazioni sui prerequisiti

I componenti dei prerequisiti che sono visualizzati nella finestra di dialogo **Prerequisiti** potrebbero differire da quelli presenti nell'elenco seguente. I pacchetti dei prerequisiti elencati nella **finestra di dialogo Prerequisiti** vengono impostati automaticamente alla prima apertura della finestra di dialogo. In caso di modifiche successive al framework di destinazione del progetto, è necessario selezionare manualmente i prerequisiti in modo che vi sia corrispondenza.

|Elemento|Description|
|-------------|-----------------|
|**.NET Framework 3.5 SP1**|Con questo pacchetto vengono installati gli elementi seguenti:<br /><br /> -   .NET Framework versioni 2.0, 3.0 e 3.5.<br />-   Supporto per tutte le versioni di .NET Framework nei sistemi operativi a 32 bit (x86) e a 64 bit (x64).<br />-   Language Pack per ciascuna versione di .NET Framework installata con il pacchetto.<br />-   Service Pack per .NET Framework 2.0 e 3.0.<br /><br /> .NET Framework 3.0 è incluso in Windows Vista e .NET Framework 3.5 è incluso in Visual Studio. .NET Framework 3.5 è necessario per tutti i progetti Visual Basic e C# che vengono compilati per i sistemi operativi a 32 bit e per i quali il framework di destinazione è impostato su **.NET Framework 3.5**, oltre che per i progetti Visual Basic e C# compilati per i sistemi operativi a 64 bit. IA64 non è supportato. Si noti che i progetti Visual Basic e C# vengono compilati per qualsiasi architettura della CPU per impostazione predefinita. Per altre informazioni, vedere [Panoramica del multitargeting di Visual Studio](../../ide/visual-studio-multi-targeting-overview.md) e [Distribuire i prerequisiti per le applicazioni a 64 bit](../../deployment/deploying-prerequisites-for-64-bit-applications.md).|
|**Microsoft .NET Framework 4.x**|Con questo pacchetto viene installato .NET Framework 4.x per le piattaforme x86 e x64.|
|**Microsoft System CLR Types per SQL Server 2014 (x64 e x86)**|Questo pacchetto installa Microsoft System CLR Types per SQL Server 2014 per la piattaforma x64 o x86.|
|**SQL Server 2008 R2 Express**|Con questo pacchetto viene installato Microsoft SQL Server 2008 R2 Express, un'edizione gratuita di Microsoft SQL Server 2008 R2, un database ideale per piccole applicazioni Web, server o desktop. Può essere utilizzato gratuitamente per lo sviluppo e la produzione.|
|**SQL Server 2012 Express**|Questo pacchetto installa Microsoft SQL Server 2012 Express.|
|**SQL Server 2012 Express LocalDB**|Questo pacchetto installa Microsoft SQL Server 2012 Express LocalDB.|
|**Librerie di runtime di Visual C++ "14" (ARM)**|Con questo pacchetto vengono installate le librerie di runtime di Visual C++ per l'architettura Itanium che forniscono routine di programmazione per il sistema operativo Microsoft Windows. Queste routine consentono di automatizzare molte attività di programmazione comuni non fornite dai linguaggi C e C++.<br /><br /> Per altyre informazioni, vedere [Riferimenti alla libreria di runtime C](/cpp/c-runtime-library/c-run-time-library-reference).|
|**Librerie di runtime di Visual C++ "14" (x64)**|Con questo pacchetto vengono installate le librerie di runtime di Visual C++ per i sistemi operativi x64 che forniscono routine di programmazione per il sistema operativo Microsoft Windows. Queste routine consentono di automatizzare molte attività di programmazione comuni non fornite dai linguaggi C e C++.<br /><br /> Per altyre informazioni, vedere [Riferimenti alla libreria di runtime C](/cpp/c-runtime-library/c-run-time-library-reference).|
|**Librerie di runtime di Visual C++ "14" (x86)**|Con questo pacchetto vengono installate le librerie di runtime di Visual C++ per i sistemi operativi x86 che forniscono routine di programmazione per il sistema operativo Microsoft Windows. Queste routine consentono di automatizzare molte attività di programmazione comuni non fornite dai linguaggi C e C++.<br /><br /> Per altyre informazioni, vedere [Riferimenti alla libreria di runtime C](/cpp/c-runtime-library/c-run-time-library-reference).|

## <a name="see-also"></a>Vedere anche

- [Pagina Pubblica, Creazione progetti](../../ide/reference/publish-page-project-designer.md)
- [Prerequisiti per la distribuzione dell'applicazione](../../deployment/application-deployment-prerequisites.md)
- [Prerequisiti per la distribuzione di applicazioni a 64 bit](../../deployment/deploying-prerequisites-for-64-bit-applications.md)
- [Panoramica del multitargeting di Visual Studio](../../ide/visual-studio-multi-targeting-overview.md)