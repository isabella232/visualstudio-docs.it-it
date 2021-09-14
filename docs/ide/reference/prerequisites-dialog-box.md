---
title: Prerequisiti (finestra di dialogo)
description: La finestra di dialogo Prerequisiti specifica i componenti dei prerequisiti installati, la modalità di installazione e l'ordine di installazione dei pacchetti.
ms.custom: SEO-VS-2020
ms.date: 06/29/2018
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- Microsoft.VisualStudio.Publish.BaseProvider.Dialog.Bootstrapper
helpviewer_keywords:
- Prerequisites dialog box
author: Mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 78d5f4f00a81fccf573e69797b9d528ee61ffdc5
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628583"
---
# <a name="prerequisites-dialog-box"></a>Prerequisiti (finestra di dialogo)

La finestra di dialogo **Prerequisiti** specifica i componenti dei prerequisiti installati, la modalità di installazione e l'ordine di installazione dei pacchetti.

![Finestra di dialogo Prerequisiti in Visual Studio 2017](media/prerequisites-dialog-box.png)

Per accedere a questa finestra di dialogo, selezionare un nodo di progetto in **Esplora soluzioni**, quindi scegliere **Progetto** > **Proprietà**. Quando viene visualizzata **Creazione progetti**, selezionare la scheda **Pubblica** e quindi selezionare **Prerequisiti**. Per i progetti di installazione, scegliere **Proprietà** dal menu **Progetto**. Quando viene visualizzata la finestra di dialogo **Pagine delle proprietà** fare clic su **Prerequisiti**.

## <a name="uielement-list"></a>Elenco degli elementi di interfaccia

|Elemento|Descrizione|
|-------------|-----------------|
|**Crea programma di installazione per installare componenti dei prerequisiti**|Include i componenti dei prerequisiti nel programma di installazione dell'applicazione (*Setup.exe*) in modo che vengano installati prima dell'applicazione in ordine di dipendenza. Questa opzione è selezionata per impostazione predefinita. Se l'opzione non è selezionata, non viene creato alcun programma *Setup.exe*.|
|**Scegliere i prerequisiti da installare**|Specifica se installare i componenti, ad esempio librerie di runtime di .NET Framework e C++.<br /><br />Ad esempio, selezionando la casella di controllo accanto a **SQL Server 2012 Express**, si specifica che il programma di installazione deve verificare se il componente è già installato nel computer di destinazione e, in caso contrario, installarlo.<br /><br />Per informazioni dettagliate su ogni pacchetto di prerequisiti, vedere [Informazioni sui prerequisiti](#prerequisites-information).|
|**Scarica prerequisiti dal sito Web del fornitore del componente**|Specifica che i componenti dei prerequisiti devono essere installati dal sito Web del fornitore. Questa è l'opzione predefinita.|
|**Scarica prerequisiti dallo stesso percorso dell'applicazione**|Specifica che i componenti dei prerequisiti devono essere installati dallo stesso percorso dell'applicazione. In questo modo vengono copiati tutti i pacchetti di prerequisiti nel percorso di pubblicazione. Per il corretto funzionamento di questa opzione, i pacchetti di prerequisiti devono essere presenti nel computer di sviluppo.|
|**Scarica prerequisiti dal seguente percorso**|Specifica che i componenti dei prerequisiti devono essere installati dal percorso specificato. Per selezionare un percorso usare il pulsante **Sfoglia**.|

> [!NOTE]
> Per informazioni su dove inserire i prerequisiti, vedere [Creare pacchetti del programma di avvio automatico](../../deployment/creating-bootstrapper-packages.md#create-custom-bootstrapper-packages).

## <a name="prerequisites-information"></a>Informazioni sui prerequisiti

I componenti dei prerequisiti che sono visualizzati nella finestra di dialogo **Prerequisiti** potrebbero differire da quelli presenti nell'elenco seguente. I pacchetti dei prerequisiti elencati nella **finestra di dialogo Prerequisiti** vengono impostati automaticamente alla prima apertura della finestra di dialogo. In caso di modifiche successive al framework di destinazione del progetto, è necessario selezionare manualmente i prerequisiti in modo che vi sia corrispondenza.

|Elemento|Descrizione|
|-------------|-----------------|
|**.NET Framework 3.5 SP1**|Con questo pacchetto vengono installati gli elementi seguenti:<br /><br /> -   .NET Framework versioni 2.0, 3.0 e 3.5.<br />-   Supporto per tutte le versioni di .NET Framework nei sistemi operativi a 32 bit (x86) e a 64 bit (x64).<br />-   Language Pack per ciascuna versione di .NET Framework installata con il pacchetto.<br />-   Service Pack per .NET Framework 2.0 e 3.0.<br /><br /> .NET Framework 3.0 è incluso in Windows Vista e .NET Framework 3.5 è incluso in Visual Studio. .NET Framework 3.5 è necessario per tutti i progetti Visual Basic e C# che vengono compilati per i sistemi operativi a 32 bit e per i quali il framework di destinazione è impostato su **.NET Framework 3.5**, oltre che per i progetti Visual Basic e C# compilati per i sistemi operativi a 64 bit. IA64 non è supportato. Si noti che Visual Basic progetti C# vengono compilati per qualsiasi architettura della CPU per impostazione predefinita. Per altre informazioni, vedere [Panoramica sull'impostazione dei framework di destinazione](../../ide/visual-studio-multi-targeting-overview.md) e [Distribuire i prerequisiti per le applicazioni a 64 bit](../../deployment/deploying-prerequisites-for-64-bit-applications.md).|
|**Microsoft .NET Framework 4.x**|Con questo pacchetto viene installato .NET Framework 4.x per le piattaforme x86 e x64.|
|**Microsoft System CLR Types per SQL Server 2014 (x64 e x86)**|Questo pacchetto installa Microsoft System CLR Types per SQL Server 2014 per la piattaforma x64 o x86.|
|**SQL Server 2008 R2 Express**|Questo pacchetto installa Microsoft SQL Server 2008 R2 Express, un'edizione gratuita di Microsoft SQL Server 2008 R2, che è un database ideale per piccole applicazioni Web, server o desktop. Può essere utilizzato gratuitamente per lo sviluppo e la produzione.|
|**SQL Server 2012 Express**|Questo pacchetto installa Microsoft SQL Server 2012 Express.|
|**SQL Server 2012 Express LocalDB**|Questo pacchetto installa Microsoft SQL Server 2012 Express LocalDB.|
|**Librerie di runtime di Visual C++ "14" (ARM)**|Con questo pacchetto vengono installate le librerie di runtime di Visual C++ per l'architettura Itanium che forniscono routine di programmazione per il sistema operativo Microsoft Windows. Queste routine automatizzano molte attività di programmazione comuni non fornite dai linguaggi C e C++.<br /><br /> Per altyre informazioni, vedere [Riferimenti alla libreria di runtime C](/cpp/c-runtime-library/c-run-time-library-reference).|
|**Librerie di runtime di Visual C++ "14" (x64)**|Con questo pacchetto vengono installate le librerie di runtime di Visual C++ per i sistemi operativi x64 che forniscono routine di programmazione per il sistema operativo Microsoft Windows. Queste routine automatizzano molte attività di programmazione comuni non fornite dai linguaggi C e C++.<br /><br /> Per altyre informazioni, vedere [Riferimenti alla libreria di runtime C](/cpp/c-runtime-library/c-run-time-library-reference).|
|**Librerie di runtime di Visual C++ "14" (x86)**|Con questo pacchetto vengono installate le librerie di runtime di Visual C++ per i sistemi operativi x86 che forniscono routine di programmazione per il sistema operativo Microsoft Windows. Queste routine automatizzano molte attività di programmazione comuni non fornite dai linguaggi C e C++.<br /><br /> Per altyre informazioni, vedere [Riferimenti alla libreria di runtime C](/cpp/c-runtime-library/c-run-time-library-reference).|

## <a name="see-also"></a>Vedi anche

- [Pagina Pubblica, Progettazione progetti](../../ide/reference/publish-page-project-designer.md)
- [Prerequisiti per la distribuzione di applicazioni](../../deployment/application-deployment-prerequisites.md)
- [Prerequisiti per la distribuzione di applicazioni a 64 bit](../../deployment/deploying-prerequisites-for-64-bit-applications.md)
- [Panoramica sull'impostazione dei framework di destinazione](../../ide/visual-studio-multi-targeting-overview.md)
