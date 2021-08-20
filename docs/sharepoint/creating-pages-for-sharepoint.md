---
title: Creazione di pagine per SharePoint | Microsoft Docs
description: Creare pagine dell'applicazione SharePoint usando un modello in Visual Studio. Creare pagine del sito, pagine master e layout di pagina usando SharePoint Designer.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: ea354e391be2f94e2d80c3c549219c3d9e1b0787
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122149533"
---
# <a name="create-pages-for-sharepoint"></a>Creare pagine per SharePoint
  È possibile creare pagine dell'applicazione, pagine del sito, pagine master e layout di pagina per un SharePoint sito.

 È possibile creare pagine dell'applicazione usando un modello in Visual Studio. Creare pagine del sito, pagine master e layout di pagina usando SharePoint Designer. È quindi possibile importare queste pagine in Visual Studio usarle in un SharePoint progetto.

 È anche possibile modificare l'aspetto e il comportamento delle pagine usando fogli di stile CSS, ECMAScript e temi.

## <a name="types-of-sharepoint-pages"></a>Tipi di SharePoint pagine
 La tabella seguente descrive i quattro tipi principali di pagine contenute in SharePoint sito.

|Tipo di pagina|Descrizione|
|---------------|-----------------|
|Pagine dell'applicazione|Creare una pagina dell'applicazione se si vuole che la pagina contenga codice personalizzato o che la pagina sia condivisa tra più siti. In caso contrario, una pagina del sito potrebbe essere la scelta migliore.|
|Pagine del sito|Creare una pagina del sito se si vuole eseguire una delle attività seguenti:<br /><br /> - Aggiungere la pagina a una SharePoint libreria.<br />- Abilitare la pagina per ospitare funzionalità quali l'Web part dinamica e le zone web part.<br />- Abilitare gli utenti per personalizzare la pagina usando SharePoint Designer.<br /><br /> Non creare una pagina del sito se si vuole che la pagina contenga codice personalizzato. Anche se è possibile aggiungere codice personalizzato a una pagina del sito, l'esecuzione del codice viene interrotta quando l'utente personalizza la pagina usando SharePoint Designer.|
|Pagine master|Creare una pagina master se si vuole definire una struttura comune per le pagine del sito e le pagine dell'applicazione.|
|Layout di pagina|I layout di pagina sono specifici di e consentono di definire ulteriormente una struttura comune per [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] le pagine del sito e le pagine dell'applicazione.|

 Per una panoramica di ogni tipo di pagina, vedere [Blocco predefinito:](/previous-versions/office/developer/sharepoint-2010/ee539040(v=office.14))pagine e Interfaccia utente e [Layout di pagina e Pagine master](/previous-versions/office/developer/sharepoint-2010/ms543497(v=office.14)).

## <a name="create-application-pages"></a>Creare pagine dell'applicazione
 È possibile creare pagine dell'applicazione in Visual Studio aggiungendo un **elemento Pagina applicazione** a un SharePoint progetto. È possibile aggiungere controlli alla pagina e quindi gestire gli eventi del controllo aggiungendo codice.

 È possibile impostare punti di interruzione nel file di codice della pagina, avviare il debugger e testare la pagina in un sito SharePoint locale senza eseguire passaggi di configurazione aggiuntivi. Per altre informazioni, vedere [Creazione di pagine applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

## <a name="create-site-pages-master-pages-and-page-layouts"></a>Creare pagine del sito, pagine master e layout di pagina
 È possibile creare pagine del sito, pagine master e layout di pagina usando SharePoint Designer. È quindi possibile importare queste pagine in Visual Studio. Importare le pagine se si vuole sfruttare le funzionalità di distribuzione o controllo del codice sorgente disponibili in Visual Studio. Per altre informazioni, vedere [Importazione di elementi da un sito SharePoint esistente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

 Poiché è difficile modificare queste pagine dopo averle importate, è consigliabile progettarle prima di importarle.

## <a name="create-cascading-style-sheets-ecmascript-and-themes"></a>Creare fogli di stile CSS, ECMAScript e temi
 Visual Studio non fornisce modelli per lo sviluppo di Cascading Style Sheets (CSS), ECMAScript (JavaScript, JScript) o file di tema per SharePoint siti. È possibile creare questi file usando le indicazioni disponibili in SharePoint SDK o usando strumenti come SharePoint Designer.

 È possibile aggiungere questi file direttamente alla soluzione oppure importarli. In entrambi i casi, è necessario creare le cartelle mappate appropriate per ogni elemento aggiunto. Per altre informazioni su come creare una cartella mappata, vedere [Procedura: aggiungere e rimuovere cartelle mappate](../sharepoint/how-to-add-and-remove-mapped-folders.md).

 Per altre informazioni sulla creazione di Cascading Style Sheets, vedere Cascading Style Sheets [Class Usage in SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ms438349(v=office.14)). Per altre informazioni sulla creazione di file JavaScript e JScript per una soluzione SharePoint, vedere Impostazione di una pagina ASPX di base [per ECMAScript](/previous-versions/office/developer/sharepoint-2010/ee535709(v=office.14)). Per altre informazioni sui temi, vedere [Blocco predefinito: pagine e](/previous-versions/office/developer/sharepoint-2010/ee539040(v=office.14))Interfaccia utente .

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Creare pagine dell'applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)|Viene descritto come aggiungere pagine di applicazioni: contenuto *aspx* unito a una SharePoint master.|
|[Procedura: Creare una pagina dell'applicazione](../sharepoint/how-to-create-an-application-page.md)|Illustra come creare pagine ASP.NET in esecuzione in un SharePoint sito.|
|[Procedura dettagliata: Creare una pagina SharePoint'applicazione](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)|Illustra come progettare ed eseguire il debug di una ASP.NET Web per un SharePoint sito.|
