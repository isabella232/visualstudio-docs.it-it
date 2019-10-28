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
ms.openlocfilehash: 297ebf0e7c2ed1273dd5a8ac973ce497c4c64781
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986347"
---
# <a name="create-pages-for-sharepoint"></a>Creazione di pagine per SharePoint
  È possibile creare pagine dell'applicazione, pagine del sito, pagine master e layout di pagina per un sito di SharePoint.

 È possibile creare pagine dell'applicazione usando un modello in Visual Studio. Creazione di pagine del sito, pagine master e layout di pagina mediante SharePoint Designer. Quindi, è possibile importare queste pagine in Visual Studio per utilizzarle in un progetto SharePoint.

 È anche possibile modificare l'aspetto e il comportamento delle pagine usando fogli di stile CSS, ECMAScript e temi.

## <a name="types-of-sharepoint-pages"></a>Tipi di pagine di SharePoint
 Nella tabella seguente vengono descritti i quattro tipi principali di pagine contenute in un sito di SharePoint.

|Tipo di pagina|Descrizione|
|---------------|-----------------|
|Pagine applicazione|Creare una pagina dell'applicazione se si desidera che la pagina contenga codice personalizzato o si desideri che la pagina venga condivisa tra più siti. In caso contrario, una pagina del sito potrebbe essere la scelta migliore.|
|Pagine del sito|Creare una pagina del sito se si desidera eseguire una delle attività seguenti:<br /><br /> -Aggiungere la pagina a una raccolta di SharePoint.<br />-Abilitare la pagina per ospitare funzionalità come la Web part dinamica e le zone Web part.<br />-Consente agli utenti di personalizzare la pagina utilizzando SharePoint Designer.<br /><br /> Non creare una pagina del sito se si desidera che la pagina contenga codice personalizzato. Sebbene sia possibile aggiungere codice personalizzato a una pagina del sito, l'esecuzione del codice viene arrestata quando l'utente personalizza la pagina utilizzando SharePoint Designer.|
|Pagine master|Creare una pagina master se si desidera definire una struttura comune per le pagine del sito e le pagine dell'applicazione.|
|Layout di pagina|I layout di pagina sono specifici per [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] e consentono di definire ulteriormente una struttura comune per le pagine del sito e le pagine dell'applicazione.|

 Per una panoramica di ogni tipo di pagina, vedere [blocco predefinito: pagine e interfaccia utente](/previous-versions/office/developer/sharepoint-2010/ee539040(v=office.14))e layout di [pagina e pagine master](/previous-versions/office/developer/sharepoint-2010/ms543497(v=office.14)).

## <a name="create-application-pages"></a>Crea pagine applicazione
 Per creare pagine dell'applicazione in Visual Studio, è possibile aggiungere un elemento della **pagina dell'applicazione** a un progetto SharePoint. È possibile aggiungere controlli alla pagina, quindi gestire gli eventi di controllo aggiungendo codice.

 È possibile impostare punti di interruzione nel file di codice della pagina, avviare il debugger e testare la pagina in un sito di SharePoint locale senza eseguire altri passaggi di configurazione. Per ulteriori informazioni, vedere [creazione di pagine dell'applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

## <a name="create-site-pages-master-pages-and-page-layouts"></a>Creazione di pagine del sito, pagine master e layout di pagina
 È possibile creare pagine del sito, pagine master e layout di pagina utilizzando SharePoint Designer. Quindi, è possibile importare queste pagine in Visual Studio. Importare le pagine se si desidera sfruttare le funzionalità di distribuzione o controllo del codice sorgente disponibili in Visual Studio. Per ulteriori informazioni, vedere [importazione di elementi da un sito di SharePoint esistente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

 Poiché è difficile modificare queste pagine dopo l'importazione, è necessario progettare queste pagine prima di importarle.

## <a name="create-cascading-style-sheets-ecmascript-and-themes"></a>Creare fogli di stile CSS, ECMAScript e temi
 Visual Studio non fornisce modelli per lo sviluppo di Cascading Style Sheets (CSS), ECMAScript (JavaScript, JScript) o file di tema per i siti di SharePoint. È possibile creare questi file utilizzando le linee guida disponibili in SharePoint SDK o utilizzando strumenti come SharePoint Designer.

 Questi file possono essere aggiunti direttamente alla soluzione oppure possono essere importati. In entrambi i casi, è necessario creare le cartelle mappate appropriate per ogni elemento aggiunto. Per altre informazioni su come creare una cartella mappata, vedere [procedura: aggiungere e rimuovere cartelle mappate](../sharepoint/how-to-add-and-remove-mapped-folders.md).

 Per ulteriori informazioni sulla creazione di Cascading Style Sheets, vedere [utilizzo delle classi Cascading Style Sheets in SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ms438349(v=office.14)). Per ulteriori informazioni sulla creazione di file JavaScript e JScript per una soluzione SharePoint, vedere [la pagina relativa alla configurazione di una pagina aspx di base per ECMAScript](/previous-versions/office/developer/sharepoint-2010/ee535709(v=office.14)). Per ulteriori informazioni sui temi, vedere [blocco predefinito: pagine e interfaccia utente](/previous-versions/office/developer/sharepoint-2010/ee539040(v=office.14)).

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Creazione di pagine applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)|Viene descritto come aggiungere pagine di applicazioni: contenuto con *estensione aspx* Unito a una pagina master di SharePoint.|
|[Procedura: creare una pagina dell'applicazione](../sharepoint/how-to-create-an-application-page.md)|Viene illustrato come creare pagine ASP.NET che vengono eseguite in un sito di SharePoint.|
|[Procedura dettagliata: creare una pagina dell'applicazione SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)|Viene illustrato come progettare ed eseguire il debug di una pagina Web ASP.NET per un sito di SharePoint.|
