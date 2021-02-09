---
title: Attività comuni nella programmazione di Office
description: Informazioni su come è possibile programmare i dati in una personalizzazione a livello di documento senza dover usare il modello a oggetti di Microsoft Office Word o Office Excel.
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
ms.workload:
- office
ms.openlocfilehash: 67b09d3881dcde1d404b7ff0c1096ced1ecb50ea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910607"
---
# <a name="common-tasks-in-office-programming"></a>Attività comuni nella programmazione di Office
  Questo argomento descrive come usare Visual Studio per trovare le risposte alle seguenti categorie di domande frequenti relative alla programmazione delle soluzioni Office.

- [Installazione e attività generali](#projects).

- [Attività di personalizzazione dell'interfaccia utente](#ui).

- [Attività di automazione di Excel](#excel).

- [Attività di automazione di Word](#word).

- [Attività relative ai dati](#data).

- [Attività di gestione dei documenti sul lato server](#server).

- [Attività di sicurezza](#security).

- [Attività di distribuzione](#deployment).

## <a name="setup-and-general-tasks"></a><a name="projects"></a> Installazione e attività generali

- [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

- [Procedura: aggiornare le soluzioni Office](/previous-versions/4bez6837(v=vs.140)).

- [Procedura: installare gli assembly di interoperabilità primari di Office](../vsto/how-to-install-office-primary-interop-assemblies.md).

- [Procedura: destinare applicazioni di Office tramite assembly di interoperabilità primari](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md).

- [Procedura: creare gestori eventi nei progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

- [Procedura: aprire soluzioni Office senza eseguire codice](../vsto/how-to-open-office-solutions-without-running-code.md).

- [Procedura: impostare le informazioni di configurazione per una soluzione Office](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md).

- [Procedura: visualizzare la scheda Developer sulla barra multifunzione](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

- [Procedura: visualizzare gli errori dell'interfaccia utente del componente aggiuntivo](../vsto/how-to-show-add-in-user-interface-errors.md).

## <a name="user-interface-customization-tasks"></a><a name="ui"></a> Attività di personalizzazione dell'interfaccia utente

### <a name="controls-on-documents-and-worksheets"></a>Controlli su documenti e fogli di foglio

- [Procedura: aggiungere controlli Windows Form ai documenti di Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).

- [Procedura: aggiungere controlli NamedRange ai fogli di foglio](../vsto/how-to-add-namedrange-controls-to-worksheets.md).

- [Procedura: aggiungere controlli ListObject a fogli di controllo](../vsto/how-to-add-listobject-controls-to-worksheets.md).

- [Procedura: aggiungere controlli Windows Form ai documenti di Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).

- [Procedura: aggiungere controlli contenuto a documenti di Word](../vsto/how-to-add-content-controls-to-word-documents.md).

- [Procedura: aggiungere controlli Bookmark ai documenti di Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md).

### <a name="task-panes-in-document-level-customizations"></a>Riquadri attività nelle personalizzazioni a livello di documento

- [Procedura: aggiungere un riquadro azioni ai documenti di Word o alle cartelle di lavoro di Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).

### <a name="task-panes-in-vsto-add-ins"></a>Riquadri attività nei componenti aggiuntivi VSTO

- [Procedura: aggiungere un riquadro attività personalizzato a un'applicazione](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).

### <a name="ribbon-customizations"></a>Personalizzazioni della barra multifunzione

- [Procedura: iniziare a personalizzare la barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md).

- [Procedura: modificare la posizione di una scheda nella barra multifunzione](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md).

- [Procedura: personalizzare una scheda incorporata](../vsto/how-to-customize-a-built-in-tab.md).

- [Procedura: aggiungere controlli alla visualizzazione Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md).

- [Procedura: Esportare una barra multifunzione dalla finestra di progettazione in un XML della barra multifunzione](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md).

### <a name="outlook-form-regions"></a>Aree del modulo di Outlook

- [Procedura: aggiungere un'area del modulo a un progetto di componente aggiuntivo di Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

- [Procedura: impedire la visualizzazione di un'area del modulo in Outlook](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md).

### <a name="custom-menus"></a>Menu personalizzati

- [Procedura: aggiungere comandi a menu di scelta rapida](../vsto/how-to-add-commands-to-shortcut-menus.md).

## <a name="excel-automation-tasks"></a><a name="excel"></a> Attività di automazione di Excel

- [Procedura: visualizzare una stringa in una cella del foglio di codice a livello di codice](../vsto/how-to-programmatically-display-a-string-in-a-worksheet-cell.md).

- [Procedura: creare nuove cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-create-new-workbooks.md).

- [Procedura: aprire cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-open-workbooks.md).

- [Procedura: salvare cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-save-workbooks.md).

- [Procedura: chiudere cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-close-workbooks.md).

- [Procedura: aggiungere nuovi fogli di lavoro alle cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md).

- [Procedura: nascondere i fogli di programmazione a livello di codice](../vsto/how-to-programmatically-hide-worksheets.md).

- [Procedura: spostare fogli di lavoro all'interno di cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md).

- [Procedura: proteggere le cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-protect-workbooks.md).

- [Procedura: fare riferimento a intervalli di fogli di tabella nel codice a livello di codice](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md).

- [Procedura: applicare stili agli intervalli nelle cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md).

- [Procedura: modificare la formattazione nelle righe di un foglio di un foglio di codice contenente celle selezionate a livello di codice](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md)

- [Procedura: eseguire la ricerca di testo negli intervalli dei fogli di testo a livello di codice](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md).

- [Procedura: stampa di fogli di fogli di codice a livello di codice](../vsto/how-to-programmatically-print-worksheets.md).

- [Procedura: eseguire calcoli di Excel a livello di codice](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md).

- [Procedura: ordinare i dati nei fogli di dati a livello di codice](../vsto/how-to-programmatically-sort-data-in-worksheets.md).

## <a name="word-automation-tasks"></a><a name="word"></a> Attività di automazione di Word

- [Procedura: creare nuovi documenti a livello di codice](../vsto/how-to-programmatically-create-new-documents.md).

- [Procedura: aprire documenti esistenti a livello di codice](../vsto/how-to-programmatically-open-existing-documents.md).

- [Procedura: salvare documenti a livello di codice](../vsto/how-to-programmatically-save-documents.md).

- [Procedura: chiudere documenti a livello di codice](../vsto/how-to-programmatically-close-documents.md).

- [Procedura: inserire testo in documenti di Word a livello di codice](../vsto/how-to-programmatically-insert-text-into-word-documents.md).

- [Procedura: definire e selezionare intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md).

- [Procedura: reimpostare gli intervalli nei documenti di Word a livello di codice](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md).

- [Procedura: formattare il testo nei documenti a livello di codice](../vsto/how-to-programmatically-format-text-in-documents.md).

- [Procedura: aggiungere controlli XMLNode ai documenti di Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md).

- [Procedura: aggiornare il testo del segnalibro a livello di codice](../vsto/how-to-programmatically-update-bookmark-text.md).

- [Procedura: cercare e sostituire testo nei documenti a livello di codice](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md).

- [Procedura: stampare documenti a livello di codice](../vsto/how-to-programmatically-print-documents.md).

- [Procedura: creare tabelle di Word a livello di codice](../vsto/how-to-programmatically-create-word-tables.md).

- [Procedura: aggiungere righe e colonne alle tabelle di Word a livello di codice](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md).

- [Procedura: contare i caratteri nei documenti a livello di codice](../vsto/how-to-programmatically-count-characters-in-documents.md).

## <a name="data-tasks"></a><a name="data"></a> Attività dati

### <a name="data-bound-controls"></a>Controlli con associazione a dati

- [Procedura: popolare fogli di dati da un database](../vsto/how-to-populate-worksheets-with-data-from-a-database.md).

- [Procedura: popolare documenti con dati da un database](../vsto/how-to-populate-documents-with-data-from-a-database.md).

- [Procedura: popolare documenti con dati dei servizi](../vsto/how-to-populate-documents-with-data-from-services.md).

- [Procedura: popolare documenti con dati da oggetti](../vsto/how-to-populate-documents-with-data-from-objects.md).

- [Procedura: popolare documenti con dati da un database](../vsto/how-to-populate-documents-with-data-from-a-database.md).

- [Procedura: popolare documenti con dati dei servizi](../vsto/how-to-populate-documents-with-data-from-services.md).

- [Procedura: aggiornare un'origine dati con i dati di un controllo host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).

### <a name="cached-data-in-document-level-solutions"></a>Dati memorizzati nella cache nelle soluzioni a livello di documento

- [Procedura: memorizzare nella cache i dati per l'uso offline o su un server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).

- [Procedura: memorizzare nella cache a livello di codice un'origine dati in un documento di Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md).

- [Procedura: memorizzare nella cache i dati in un documento protetto da password](../vsto/how-to-cache-data-in-a-password-protected-document.md).

### <a name="custom-xml-data"></a>Dati XML personalizzati

- [Procedura: aggiungere parti XML personalizzate a personalizzazioni a livello di documento](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md).

- [Procedura: aggiungere parti XML personalizzate ai documenti usando i componenti aggiuntivi VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md).

## <a name="server-side-document-management-tasks"></a><a name="server"></a> Attività di gestione dei documenti sul lato server

- [Procedura: rimuovere estensioni di codice gestito da documenti](../vsto/how-to-remove-managed-code-extensions-from-documents.md).

- [Procedura: aggiungere estensioni di codice gestito ai documenti](../vsto/how-to-attach-managed-code-extensions-to-documents.md).

## <a name="security-tasks"></a><a name="security"></a> Attività di sicurezza

- [Procedura: firmare soluzioni Office](../vsto/how-to-sign-office-solutions.md).

## <a name="deployment-tasks"></a><a name="deployment"></a> Attività di distribuzione

- [Procedura: pubblicare una soluzione Office tramite ClickOnce](/previous-versions/bb386095(v=vs.110)).

- [Procedura: pubblicare una soluzione Office a livello di documento in un server SharePoint tramite ClickOnce](/previous-versions/bb608595(v=vs.110)).

- [Procedura: installare una soluzione Office ClickOnce](/previous-versions/bb608592(v=vs.110)).

- [Procedura: installare i prerequisiti nei computer degli utenti finali per eseguire soluzioni Office](/previous-versions/bb608608(v=vs.110)).

- [Procedura: preparare IIS per la distribuzione di soluzioni Office](/previous-versions/bb608629(v=vs.110)).

- [Procedura: aggiornare le soluzioni Office distribuite](/previous-versions/bb157871(v=vs.110)).

- [Procedura: modificare il percorso di installazione di una soluzione Office](/previous-versions/bb608626(v=vs.110)).

## <a name="see-also"></a>Vedi anche
- [Introduzione &#40;sviluppo per Office in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Funzionalità disponibili in base ai tipi di progetto e applicazioni di Office](../vsto/features-available-by-office-application-and-project-type.md)
- [Procedure dettagliate e esempi di sviluppo per Office](../vsto/office-development-samples-and-walkthroughs.md)