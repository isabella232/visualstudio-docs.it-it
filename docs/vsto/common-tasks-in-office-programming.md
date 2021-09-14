---
title: Attività comuni nella programmazione Office
description: Informazioni su come programmare in base ai dati in una personalizzazione a livello di documento senza dover usare il modello a oggetti di Microsoft Office Word o Office Excel.
ms.custom: SEO-VS-2020SS
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 152af5d3be5385e6f5c91fb510d62ea7bc336218
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710105"
---
# <a name="common-tasks-in-office-programming"></a>Attività comuni nella programmazione Office
  Questo argomento descrive come usare Visual Studio per trovare le risposte alle seguenti categorie di domande frequenti relative alla programmazione delle soluzioni Office.

- [Configurazione e attività generali](#projects).

- [Attività di personalizzazione dell'interfaccia utente](#ui).

- [Excel attività di automazione di](#excel).

- [Attività di automazione di Word](#word).

- [Attività relative ai dati](#data).

- [Attività di gestione dei documenti sul lato server](#server).

- [Attività di sicurezza](#security).

- [Attività di distribuzione](#deployment).

## <a name="setup-and-general-tasks"></a><a name="projects"></a> Configurazione e attività generali

- [Procedura: Creare progetti Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

- [Procedura: Aggiornare Office soluzioni](/previous-versions/4bez6837(v=vs.140)).

- [Procedura: Installare Office assembly di interoperabilità primari.](../vsto/how-to-install-office-primary-interop-assemblies.md)

- [Procedura: Impostare come destinazione Office applicazioni tramite assembly di interoperabilità primari.](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)

- [Procedura: Creare gestori eventi in Office progetti](../vsto/how-to-create-event-handlers-in-office-projects.md).

- [Procedura: Aprire soluzioni Office senza eseguire codice](../vsto/how-to-open-office-solutions-without-running-code.md).

- [Procedura: Configurare le informazioni di configurazione per una Office soluzione](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md).

- [Procedura: Visualizzare la scheda Sviluppatore nella barra multifunzione.](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)

- [Procedura: Visualizzare gli errori dell'interfaccia utente del componente aggiuntivo](../vsto/how-to-show-add-in-user-interface-errors.md).

## <a name="user-interface-customization-tasks"></a><a name="ui"></a> Attività di personalizzazione dell'interfaccia utente

### <a name="controls-on-documents-and-worksheets"></a>Controlli su documenti e fogli di lavoro

- [Procedura: Aggiungere controlli form Windows ai Office documenti](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).

- [Procedura: Aggiungere controlli NamedRange ai fogli di lavoro](../vsto/how-to-add-namedrange-controls-to-worksheets.md).

- [Procedura: Aggiungere controlli ListObject ai fogli di lavoro](../vsto/how-to-add-listobject-controls-to-worksheets.md).

- [Procedura: Aggiungere controlli form Windows ai Office documenti](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).

- [Procedura: Aggiungere controlli contenuto ai documenti di Word.](../vsto/how-to-add-content-controls-to-word-documents.md)

- [Procedura: Aggiungere controlli Bookmark ai documenti di Word.](../vsto/how-to-add-bookmark-controls-to-word-documents.md)

### <a name="task-panes-in-document-level-customizations"></a>Riquadri attività nelle personalizzazioni a livello di documento

- [Procedura: Aggiungere un riquadro azioni a documenti di Word o Excel cartelle di lavoro](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)di .

### <a name="task-panes-in-vsto-add-ins"></a>Riquadri attività VSTO componenti aggiuntivi

- [Procedura: Aggiungere un riquadro attività personalizzato a un'applicazione](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).

### <a name="ribbon-customizations"></a>Personalizzazioni della barra multifunzione

- [Procedura: Iniziare a personalizzare la barra multifunzione.](../vsto/how-to-get-started-customizing-the-ribbon.md)

- [Procedura: Modificare la posizione di una scheda nella barra multifunzione.](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)

- [Procedura: Personalizzare una scheda incorporata.](../vsto/how-to-customize-a-built-in-tab.md)

- [Procedura: Aggiungere controlli alla visualizzazione Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md).

- [Procedura: Esportare una barra multifunzione dalla finestra di progettazione in un XML della barra multifunzione](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md).

### <a name="outlook-form-regions"></a>Aree del modulo di Outlook

- [Procedura: Aggiungere un'area del modulo a Outlook progetto di componente aggiuntivo](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

- [Procedura: Impedire Outlook visualizzare un'area del modulo](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md).

### <a name="custom-menus"></a>Menu personalizzati

- [Procedura: Aggiungere comandi ai menu di scelta rapida](../vsto/how-to-add-commands-to-shortcut-menus.md).

## <a name="excel-automation-tasks"></a><a name="excel"></a>Excel di automazione

- [Procedura: Visualizzare una stringa in una cella del foglio](../vsto/how-to-programmatically-display-a-string-in-a-worksheet-cell.md)di lavoro a livello di codice.

- [Procedura: Creare nuove cartelle di lavoro a livello di codice.](../vsto/how-to-programmatically-create-new-workbooks.md)

- [Procedura: Aprire cartelle di lavoro a livello di codice.](../vsto/how-to-programmatically-open-workbooks.md)

- [Procedura: Salvare cartelle di lavoro a livello di codice.](../vsto/how-to-programmatically-save-workbooks.md)

- [Procedura: Chiudere cartelle di lavoro a livello di codice.](../vsto/how-to-programmatically-close-workbooks.md)

- [Procedura: Aggiungere nuovi fogli di lavoro alle cartelle di lavoro](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)a livello di codice.

- [Procedura: Nascondere i fogli di lavoro a livello di codice.](../vsto/how-to-programmatically-hide-worksheets.md)

- [Procedura: Spostare fogli di lavoro all'interno di cartelle di lavoro a livello di codice.](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)

- [Procedura: Proteggere le cartelle di lavoro a livello di codice.](../vsto/how-to-programmatically-protect-workbooks.md)

- [Procedura: Fare riferimento a intervalli di fogli di lavoro nel codice a livello di codice.](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)

- [Procedura: Applicare stili agli intervalli nelle cartelle di](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)lavoro a livello di codice.

- [Procedura: Modificare la formattazione a livello di codice nelle righe del foglio di lavoro contenenti celle selezionate.](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md)

- [Procedura: Cercare testo negli intervalli dei fogli](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)di lavoro a livello di codice.

- [Procedura: Stampare fogli di lavoro a livello di codice.](../vsto/how-to-programmatically-print-worksheets.md)

- [Procedura: Eseguire calcoli di Excel a livello di codice.](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)

- [Procedura: Ordinare i dati nei fogli di lavoro a livello di codice.](../vsto/how-to-programmatically-sort-data-in-worksheets.md)

## <a name="word-automation-tasks"></a><a name="word"></a> Attività di automazione di Word

- [Procedura: Creare nuovi documenti a livello di codice.](../vsto/how-to-programmatically-create-new-documents.md)

- [Procedura: Aprire documenti esistenti a livello di codice.](../vsto/how-to-programmatically-open-existing-documents.md)

- [Procedura: Salvare documenti a livello di codice.](../vsto/how-to-programmatically-save-documents.md)

- [Procedura: Chiudere documenti a livello di codice.](../vsto/how-to-programmatically-close-documents.md)

- [Procedura: Inserire testo nei documenti di Word a livello di codice.](../vsto/how-to-programmatically-insert-text-into-word-documents.md)

- [Procedura: Definire e selezionare intervalli nei documenti](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)a livello di codice.

- [Procedura: Reimpostare gli intervalli nei documenti di Word a livello di codice.](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)

- [Procedura: Formattare il testo nei documenti a livello di codice.](../vsto/how-to-programmatically-format-text-in-documents.md)

- [Procedura: Aggiungere controlli XMLNode ai documenti di Word.](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)

- [Procedura: Aggiornare il testo del segnalibro a livello di codice.](../vsto/how-to-programmatically-update-bookmark-text.md)

- [Procedura: Cercare e sostituire testo nei documenti a livello di codice.](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)

- [Procedura: Stampare documenti a livello di codice.](../vsto/how-to-programmatically-print-documents.md)

- [Procedura: Creare tabelle di Word a livello di codice.](../vsto/how-to-programmatically-create-word-tables.md)

- [Procedura: Aggiungere righe e colonne alle tabelle di Word a livello di codice.](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)

- [Procedura: Contare i caratteri nei documenti a livello di codice.](../vsto/how-to-programmatically-count-characters-in-documents.md)

## <a name="data-tasks"></a><a name="data"></a> Attività relative ai dati

### <a name="data-bound-controls"></a>Controlli associati a dati

- [Procedura: Popolare i fogli di lavoro con i dati di un database](../vsto/how-to-populate-worksheets-with-data-from-a-database.md).

- [Procedura: Popolare documenti con dati da un database](../vsto/how-to-populate-documents-with-data-from-a-database.md).

- [Procedura: Popolare i documenti con i dati dei servizi](../vsto/how-to-populate-documents-with-data-from-services.md).

- [Procedura: Popolare documenti con dati da oggetti](../vsto/how-to-populate-documents-with-data-from-objects.md).

- [Procedura: Popolare documenti con dati da un database](../vsto/how-to-populate-documents-with-data-from-a-database.md).

- [Procedura: Popolare i documenti con i dati dei servizi](../vsto/how-to-populate-documents-with-data-from-services.md).

- [Procedura: Aggiornare un'origine dati con i dati di un controllo host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).

### <a name="cached-data-in-document-level-solutions"></a>Dati memorizzati nella cache nelle soluzioni a livello di documento

- [Procedura: Memorizzare nella cache i dati da usare offline o in un server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).

- [Procedura: Memorizzare nella cache a livello di codice un'origine dati in Office documento](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md).

- [Procedura: Memorizzare nella cache i dati in un documento protetto da password.](../vsto/how-to-cache-data-in-a-password-protected-document.md)

### <a name="custom-xml-data"></a>Dati XML personalizzati

- [Procedura: Aggiungere parti XML personalizzate alle personalizzazioni a livello di documento.](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)

- [Procedura: Aggiungere parti XML personalizzate ai documenti usando VSTO componenti aggiuntivi](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md).

## <a name="server-side-document-management-tasks"></a><a name="server"></a> Attività di gestione dei documenti lato server

- [Procedura: Rimuovere estensioni di codice gestito dai documenti](../vsto/how-to-remove-managed-code-extensions-from-documents.md).

- [Procedura: Associare estensioni di codice gestito a documenti](../vsto/how-to-attach-managed-code-extensions-to-documents.md).

## <a name="security-tasks"></a><a name="security"></a> Attività di sicurezza

- [Procedura: Firmare Office soluzioni](../vsto/how-to-sign-office-solutions.md).

## <a name="deployment-tasks"></a><a name="deployment"></a> Attività di distribuzione

- [Procedura: Pubblicare una soluzione Office usando ClickOnce](/previous-versions/bb386095(v=vs.110)).

- [Procedura: Pubblicare una soluzione Office a](/previous-versions/bb608595(v=vs.110))livello di documento in un server SharePoint usando ClickOnce .

- [Procedura: Installare una soluzione ClickOnce Office.](/previous-versions/bb608592(v=vs.110))

- [Procedura: Installare i prerequisiti nei computer degli utenti finali per eseguire Office soluzioni](/previous-versions/bb608608(v=vs.110)).

- [Procedura: Preparare IIS per la distribuzione di Office soluzioni](/previous-versions/bb608629(v=vs.110)).

- [Procedura: Aggiornare soluzioni Office distribuite.](/previous-versions/bb157871(v=vs.110))

- [Procedura: Modificare il percorso di installazione di una Office soluzione](/previous-versions/bb608626(v=vs.110)).

## <a name="see-also"></a>Vedi anche
- [Introduzione allo &#40;Office sviluppo in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Funzionalità disponibili in base Office'applicazione e al tipo di progetto](../vsto/features-available-by-office-application-and-project-type.md)
- [Office e procedure dettagliate per lo sviluppo di applicazioni](../vsto/office-development-samples-and-walkthroughs.md)