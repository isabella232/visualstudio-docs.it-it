---
title: Attività comuni nella programmazione Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, getting started
- FAQs (frequently asked questions) [Office development in Visual Studio]
- Office development in Visual Studio, frequently asked questions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1b0856d3832d31dd7027b2f264dd0a9cd1d657ec
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63007327"
---
# <a name="common-tasks-in-office-programming"></a>Attività comuni nella programmazione Office
  Questo argomento descrive come usare Visual Studio per trovare le risposte alle seguenti categorie di domande frequenti relative alla programmazione delle soluzioni Office.

- [Installazione e attività generali](#projects).

- [Attività di personalizzazione dell'interfaccia utente](#ui).

- [Attività di automazione di Excel](#excel).

- [Attività di automazione di Word](#word).

- [Attività relative ai dati](#data).

- [Attività di gestione dei documenti sul lato server](#server).

- [Attività relative alla sicurezza](#security).

- [Attività di distribuzione](#deployment).

## <a name="projects"></a> Installazione e attività generali

- [Procedura: Creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

- [Procedura: Aggiornare soluzioni Office](https://msdn.microsoft.com/a269e539-b717-4680-a568-2152b070347e).

- [Procedura: Installare l'assembly di interoperabilità primari di Office](../vsto/how-to-install-office-primary-interop-assemblies.md).

- [Procedura: Sviluppare applicazioni di Office tramite assembly di interoperabilità primari](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md).

- [Procedura: Creare i gestori eventi nei progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

- [Procedura: Aprire soluzioni Office senza eseguire codice](../vsto/how-to-open-office-solutions-without-running-code.md).

- [Procedura: Impostare le informazioni di configurazione per una soluzione Office](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md).

- [Procedura: Visualizzare la scheda sviluppo nella barra multifunzione](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

- [Procedura: Mostra errori dell'interfaccia utente del componente aggiuntivo](../vsto/how-to-show-add-in-user-interface-errors.md).

## <a name="ui"></a> Attività di personalizzazione dell'interfaccia utente

### <a name="controls-on-documents-and-worksheets"></a>Controlli nei documenti e fogli di lavoro

- [Procedura: Aggiungere controlli Windows Form ai documenti di Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).

- [Procedura: Aggiungere controlli NamedRange a fogli di lavoro](../vsto/how-to-add-namedrange-controls-to-worksheets.md).

- [Procedura: Aggiungere controlli ListObject a fogli di lavoro](../vsto/how-to-add-listobject-controls-to-worksheets.md).

- [Procedura: Aggiungere controlli Windows Form ai documenti di Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).

- [Procedura: Aggiungere contenuto controlli ai documenti di Word](../vsto/how-to-add-content-controls-to-word-documents.md).

- [Procedura: Aggiungere controlli segnalibro ai documenti di Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md).

### <a name="task-panes-in-document-level-customizations"></a>Riquadri attività nelle personalizzazioni a livello di documento

- [Procedura: Aggiungere un riquadro azioni ai documenti di Word o le cartelle di lavoro di Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).

### <a name="task-panes-in-vsto-add-ins"></a>Riquadri attività nei componenti aggiuntivi VSTO

- [Procedura: Aggiungere un riquadro attività personalizzato a un'applicazione](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).

### <a name="ribbon-customizations"></a>Personalizzazioni della barra multifunzione

- [Procedura: Introduzione alla personalizzazione della barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md).

- [Procedura: Modificare la posizione di una scheda della barra multifunzione](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md).

- [Procedura: Personalizzare una scheda incorporata](../vsto/how-to-customize-a-built-in-tab.md).

- [Procedura: Aggiungere controlli alla visualizzazione Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md).

- [Procedura: Esportare una barra multifunzione dalla finestra di progettazione della barra multifunzione alla barra multifunzione XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md).

### <a name="outlook-form-regions"></a>Aree del modulo di Outlook

- [Procedura: Aggiungere un'area del modulo a un progetto di componente aggiuntivo di Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

- [Procedura: Impedire la visualizzazione di un'area del modulo di Outlook](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md).

### <a name="custom-menus"></a>Menu personalizzati

- [Procedura: Aggiungere comandi a menu di scelta rapida](../vsto/how-to-add-commands-to-shortcut-menus.md).

## <a name="excel"></a> Attività di automazione di Excel

- [Procedura: A livello di programmazione visualizzare una stringa in una cella di foglio di lavoro](../vsto/how-to-programmatically-display-a-string-in-a-worksheet-cell.md).

- [Procedura: A livello di codice crea nuove cartelle di lavoro](../vsto/how-to-programmatically-create-new-workbooks.md).

- [Procedura: A livello di codice aprire cartelle di lavoro](../vsto/how-to-programmatically-open-workbooks.md).

- [Procedura: A livello di programmazione salvare cartelle di lavoro](../vsto/how-to-programmatically-save-workbooks.md).

- [Procedura: A livello di programmazione chiudere cartelle di lavoro](../vsto/how-to-programmatically-close-workbooks.md).

- [Procedura: A livello di codice aggiungere nuovi fogli di lavoro alle cartelle di lavoro](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md).

- [Procedura: Nascondere i fogli di lavoro a livello di programmazione](../vsto/how-to-programmatically-hide-worksheets.md).

- [Procedura: A livello di programmazione spostare fogli di lavoro all'interno di cartelle di lavoro](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md).

- [Procedura: A livello di programmazione proteggere cartelle di lavoro](../vsto/how-to-programmatically-protect-workbooks.md).

- [Procedura: A livello di codice fare riferimento agli intervalli del foglio di lavoro nel codice](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md).

- [Procedura: A livello di programmazione applicare stili agli intervalli in cartelle di lavoro](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md).

- [Procedura: A livello di codice modificare la formattazione nelle righe del foglio di lavoro contenenti celle selezionate](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md).

- [Procedura: A livello di codice cercare testo negli intervalli del foglio di lavoro](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md).

- [Procedura: Stampa di fogli di lavoro](../vsto/how-to-programmatically-print-worksheets.md).

- [Procedura: Eseguire calcoli in Excel](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md).

- [Procedura: Ordinare i dati nei fogli di lavoro a livello di programmazione](../vsto/how-to-programmatically-sort-data-in-worksheets.md).

## <a name="word"></a> Attività di automazione di Word

- [Procedura: Creazione di nuovi documenti a livello di programmazione](../vsto/how-to-programmatically-create-new-documents.md).

- [Procedura: A livello di codice aprire documenti esistenti](../vsto/how-to-programmatically-open-existing-documents.md).

- [Procedura: Salvare i documenti a livello di programmazione](../vsto/how-to-programmatically-save-documents.md).

- [Procedura: Chiudere i documenti a livello di programmazione](../vsto/how-to-programmatically-close-documents.md).

- [Procedura: A livello di programmazione inserire testo nei documenti di Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md).

- [Procedura: Definire e selezionare intervalli nei documenti a livello di programmazione](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md).

- [Procedura: A livello di programmazione reimpostare gli intervalli nei documenti di Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md).

- [Procedura: Formattazione del testo nei documenti a livello di programmazione](../vsto/how-to-programmatically-format-text-in-documents.md).

- [Procedura: Aggiungere controlli XMLNode ai documenti Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md).

- [Procedura: A livello di codice aggiorna il testo di segnalibro](../vsto/how-to-programmatically-update-bookmark-text.md).

- [Procedura: Cercare e sostituire testo nei documenti a livello di programmazione](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md).

- [Procedura: A livello di programmazione stampare documenti](../vsto/how-to-programmatically-print-documents.md).

- [Procedura: A livello di codice, creare tabelle di Word](../vsto/how-to-programmatically-create-word-tables.md).

- [Procedura: A livello di codice aggiungere righe e colonne alle tabelle di Word](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md).

- [Procedura: Contare i caratteri nei documenti a livello di programmazione](../vsto/how-to-programmatically-count-characters-in-documents.md).

## <a name="data"></a> Attività di dati

### <a name="data-bound-controls"></a>Controlli con associazione a dati

- [Procedura: Popolare fogli di lavoro con i dati da un database](../vsto/how-to-populate-worksheets-with-data-from-a-database.md).

- [Procedura: Popolare documenti con dati da un database](../vsto/how-to-populate-documents-with-data-from-a-database.md).

- [Procedura: Popolare documenti con dati provenienti dai servizi](../vsto/how-to-populate-documents-with-data-from-services.md).

- [Procedura: Popolare documenti con dati da oggetti](../vsto/how-to-populate-documents-with-data-from-objects.md).

- [Procedura: Popolare documenti con dati da un database](../vsto/how-to-populate-documents-with-data-from-a-database.md).

- [Procedura: Popolare documenti con dati provenienti dai servizi](../vsto/how-to-populate-documents-with-data-from-services.md).

- [Procedura: Aggiornare un'origine dati con dati provenienti da un controllo host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).

### <a name="cached-data-in-document-level-solutions"></a>Dati memorizzati nella cache nelle soluzioni a livello di documento

- [Procedura: Memorizzare nella cache i dati per l'uso offline o in un server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).

- [Procedura: Memorizzare nella cache a livello di codice di un'origine dati in un documento di Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md).

- [Procedura: Memorizzare nella cache i dati in un documento protetto da password](../vsto/how-to-cache-data-in-a-password-protected-document.md).

### <a name="custom-xml-data"></a>Dati XML personalizzate

- [Procedura: Aggiungere parti XML personalizzate a personalizzazioni a livello di documento](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md).

- [Procedura: Aggiungere parti XML personalizzate a documenti usando componenti aggiuntivi VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md).

## <a name="server"></a> Attività di gestione di documenti sul lato server

- [Procedura: Rimuovere estensioni di codice gestito dai documenti](../vsto/how-to-remove-managed-code-extensions-from-documents.md).

- [Procedura: Associare estensioni di codice gestito a documenti](../vsto/how-to-attach-managed-code-extensions-to-documents.md).

## <a name="security"></a> Attività relative alla sicurezza

- [Procedura: Firmare soluzioni Office](../vsto/how-to-sign-office-solutions.md).

## <a name="deployment"></a> Attività di distribuzione

- [Procedura: Distribuire una soluzione Office usando ClickOnce](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8).

- [Procedura: Pubblicare una soluzione Office a livello di documento in un server SharePoint tramite ClickOnce](https://msdn.microsoft.com/2408e809-fb78-42a1-9152-00afa1522e58).

- [Procedura: Installare una soluzione ClickOnce Office](https://msdn.microsoft.com/14702f48-9161-4190-994c-78211fe18065).

- [Procedura: Installare i prerequisiti nei computer degli utenti finali per eseguire soluzioni Office](https://msdn.microsoft.com/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).

- [Procedura: Preparare IIS per la distribuzione di soluzioni Office](https://msdn.microsoft.com/f62bce70-81d4-4f8b-86e6-2f2afec5d9b4).

- [Procedura: Aggiornamento di soluzioni Office distribuite](https://msdn.microsoft.com/be96db53-b6ea-46ab-b8d9-b76b098b3b13).

- [Procedura: Modificare il percorso di installazione di una soluzione Office](https://msdn.microsoft.com/d0eaa07b-2d72-4902-899f-2f9fb165b8fd).

## <a name="see-also"></a>Vedere anche
- [Iniziare a usare &#40;sviluppo per Office in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Funzionalità disponibili in base al tipo di progetto e applicazioni di Office](../vsto/features-available-by-office-application-and-project-type.md)
- [Procedure dettagliate ed esempi di sviluppo office](../vsto/office-development-samples-and-walkthroughs.md)
