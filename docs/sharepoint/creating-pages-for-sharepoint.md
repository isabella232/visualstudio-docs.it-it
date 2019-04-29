---
title: Creazione di pagine per SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, master pages
- SharePoint development in Visual Studio, page layouts
- SharePoint development in Visual Studio, content pages
- master pages[SharePoint development in Visual Studio], designing
- content pages[SharePoint development in Visual Studio], designing
- page layouts[SharePoint development in Visual Studio], designing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f58af55b18d7cd6341b779d71da2994875c98a62
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62419885"
---
# <a name="create-pages-for-sharepoint"></a>Creazione di pagine per SharePoint
  È possibile creare le pagine dell'applicazione, le pagine del sito, le pagine master e layout di pagina per un sito di SharePoint.

 È possibile creare le pagine dell'applicazione usando un modello in Visual Studio. Creare layout di pagina, le pagine del sito e le pagine master utilizzando SharePoint Designer. Quindi, è possibile importare queste pagine in Visual Studio per usarli in un progetto SharePoint.

 È anche possibile modificare l'aspetto e il comportamento delle pagine usando i fogli di stile, ECMAScript e temi.

## <a name="types-of-sharepoint-pages"></a>Tipi di pagine di SharePoint
 La tabella seguente descrive i quattro tipi principali di pagine che contiene un sito di SharePoint.

|Tipo di pagina|Descrizione|
|---------------|-----------------|
|Pagine dell'applicazione|Se si desidera che la pagina contiene codice personalizzato o si desidera che la pagina per essere condivisi tra più siti, creare una pagina dell'applicazione. In caso contrario, una pagina del sito potrebbe essere la scelta migliore.|
|Pagine del sito|Creare una pagina del sito se si desidera eseguire una qualsiasi delle attività seguenti:<br /><br /> -Aggiungere la pagina in una raccolta di SharePoint.<br />-Abilitare la pagina di funzionalità host, ad esempio dynamic Web part e le aree Web Part.<br />-Consentire agli utenti di personalizzare la pagina utilizzando SharePoint Designer.<br /><br /> Non creare una pagina del sito se si desidera che la pagina contiene codice personalizzato. Sebbene sia possibile aggiungere codice personalizzato a una pagina del sito, il codice si interrompe quando l'utente Personalizza la pagina utilizzando SharePoint Designer.|
|Pagine master|Creare una pagina master se si vuole definire una struttura comune per le pagine del sito e le pagine dell'applicazione.|
|Layout di pagina|Layout di pagina sono specifiche di [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] e consentono di definire una struttura comune per le pagine del sito e le pagine dell'applicazione.|

 Per una panoramica di ogni tipo di pagina, vedere [blocco predefinito: Le pagine e l'interfaccia utente](http://go.microsoft.com/fwlink/?LinkID=182095), e [pagina layout e pagine Master](http://go.microsoft.com/fwlink/?LinkID=182096).

## <a name="create-application-pages"></a>Creare le pagine dell'applicazione
 È possibile creare le pagine dell'applicazione in Visual Studio mediante l'aggiunta di un **pagina dell'applicazione** elemento a un progetto SharePoint. È possibile aggiungere controlli alla pagina e quindi gestire gli eventi di controllo aggiungendo il codice.

 È possibile impostare punti di interruzione nel file di codice della pagina, avviare il debugger e testare la pagina in un sito di SharePoint locale senza eseguire altri passaggi di configurazione. Per altre informazioni, vedere [creazione di pagine dell'applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

## <a name="create-site-pages-master-pages-and-page-layouts"></a>Creare le pagine del sito, le pagine master e layout di pagina
 È possibile creare le pagine del sito, le pagine master e layout di pagina utilizzando SharePoint Designer. Quindi, è possibile importare queste pagine in Visual Studio. Se si desidera sfruttare la distribuzione o la funzionalità di controllo codice sorgente che sono disponibili in Visual Studio, importare le pagine. Per altre informazioni, vedere [importazione di elementi da un sito di SharePoint esistente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

 Poiché è difficile da modificare queste pagine dopo che è possibile importarli, è consigliabile progettare queste pagine prima di importarli.

## <a name="create-cascading-style-sheets-ecmascript-and-themes"></a>Creare fogli di stile CSS, ECMAScript e temi
 Visual Studio non fornisce modelli per lo sviluppo fogli CSS (Cascading Style), ECMAScript (JavaScript, JScript) o file di temi per i siti di SharePoint. È possibile creare questi file usando le istruzioni disponibili nel SDK di SharePoint o tramite gli strumenti, ad esempio SharePoint Designer.

 È possibile aggiungere questi file alla soluzione direttamente oppure è possibile importarli. In entrambi i casi, è necessario creare le cartelle mappate appropriate per ogni elemento che si aggiunge. Per altre informazioni su come creare una cartella mappata, vedere [procedura: aggiungere e rimuovere cartelle mappate](../sharepoint/how-to-add-and-remove-mapped-folders.md).

 Per altre informazioni sulla creazione di fogli di stile CSS, vedere [utilizzo della classe fogli di stile CSS in SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkID=182098). Per altre informazioni sulla creazione di file JavaScript e JScript per una soluzione di SharePoint, vedere [impostazione di una pagina ASPX di base per ECMAScript](http://go.microsoft.com/fwlink/?LinkID=182099). Per altre informazioni sui temi, vedere [blocco predefinito: Le pagine e l'interfaccia utente](http://go.microsoft.com/fwlink/?LinkID=182095).

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Creare le pagine dell'applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)|Viene descritto come aggiungere le pagine di applicazioni: *aspx* contenuto che viene unito a una pagina master di SharePoint.|
|[Procedura: Creare una pagina applicazione](../sharepoint/how-to-create-an-application-page.md)|Illustra come creare pagine ASP.NET eseguite in un sito di SharePoint.|
|[Procedura dettagliata: Creare una pagina dell'applicazione SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)|Illustra come progettare ed eseguire il debug di una pagina Web ASP.NET per un sito di SharePoint.|
