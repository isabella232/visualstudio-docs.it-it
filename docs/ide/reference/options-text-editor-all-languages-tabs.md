---
title: Opzioni, Editor di testo, Tutti i linguaggi, Schede
description: Informazioni su come usare la pagina Tabulazioni nella sezione Tutti i linguaggi per modificare il comportamento predefinito delle schede dell'editor di codice all'interno Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.All_Languages.Tabs
- VS.ToolsOptionsPages.Text_Editor.Basic.Tabs
- VS.ToolsOptionsPages.Text_Editor.CSharp.Tabs
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Tabs
- VS.ToolsOptionsPages.Text_Editor.CoffeeScript.Tabs
- VS.ToolsOptionsPages.Text_Editor.CSS.Tabs
- VS.ToolsOptionsPages.Text_Editor.Dockerfile.Tabs
- VS.ToolsOptionsPages.Text_Editor.F%2523.Tabs
- VS.ToolsOptionsPages.Text_Editor.HQL.Tabs
- VS.ToolsOptionsPages.Text_Editor.HTML.Tabs
- VS.ToolsOptionsPages.Text_Editor.HTMLX.Tabs
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Tabs
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Tabs
- VS.ToolsOptionsPages.Text_Editor.JSON.Tabs
- VS.ToolsOptionsPages.Text_Editor.LESS.Tabs
- VS.ToolsOptionsPages.Text_Editor.Plain_Text.Tabs
- VS.ToolsOptionsPages.Text_Editor.ResJSON.Tabs
- VS.ToolsOptionsPages.Text_Editor.SCSS.Tabs
- VS.ToolsOptionsPages.Text_Editor.SQL_Server_Tools.Tabs
- VS.ToolsOptionsPages.Text_Editor.StreamAnalytics.Tabs
- VS.ToolsOptionsPages.Text_Editor.T-SQL90.Tabs
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Tabs
- VS.ToolsOptionsPages.Text_Editor.XAML.Tabs
- VS.ToolsOptionsPages.Text_Editor.XML.Tabs
helpviewer_keywords:
- indents, Code Editor
- Code Editor, default behavior
- tabs, setting in Code Editor
- All Languages Text Editor Options dialog box
- editors, Code Editor
- Code Editor, indenting
- Code Editor, tabs
ms.assetid: 7e208e1d-5e3a-4bf7-a27b-4417e3e049c7
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: c8a37f493f90ee8bbc6d36e9a5d4eb9de5d57ab3
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627197"
---
# <a name="options-text-editor-all-languages-tabs"></a>Opzioni, Editor di testo, Tutti i linguaggi, Schede

Questa finestra di dialogo consente di modificare il comportamento predefinito dell'editor del codice. Queste impostazioni si applicano anche agli altri editor basati sull'editor del codice, come ad esempio la visualizzazione dell'origine della finestra di progettazione HTML. Per visualizzare queste opzioni, selezionare **Opzioni** dal menu **Strumenti**. All'interno della cartella dell'**Editor di testo** espandere la sottocartella **All Languages** (Tutti i linguaggi), quindi scegliere **Schede**.

> [!CAUTION]
> Questa pagina consente di impostare le opzioni predefinite per tutti i linguaggi di sviluppo. Tenere presente che la reimpostazione di un'opzione in questa finestra di dialogo reimposterà le opzioni delle schede in tutti i linguaggi per qualunque scelta operata qui. Per modificare le opzioni dell'editor di testo per un solo linguaggio, espandere la sottocartella per tale linguaggio e selezionare le pagine relative alle opzioni.

Se vengono selezionate diverse impostazioni nelle pagine di opzioni delle schede per determinati linguaggi di programmazione, viene visualizzato il messaggio "Le impostazioni dei rientri per singoli formati di testo sono in conflitto" per diverse opzioni di **Rientri**; inoltre viene visualizzato il messaggio "Le impostazioni delle tabulazioni per singoli formati di testo sono in conflitto", per diverse opzioni della **Scheda**. Ad esempio, questo promemoria viene visualizzato se è stata selezionata l'opzione **Rientro automatico** per Visual Basic, mentre è stato selezionato **Block indenting** (Blocca rientro) per Visual C++.

## <a name="indenting"></a>Stili rientri

Nessuno

Se l'opzione è selezionata, le nuove righe non vengono rientrate. Il punto di inserimento si trova nella prima colonna di una nuova riga.

Blocca

Se l'opzione è selezionata, le nuove righe vengono rientrate automaticamente. Il punto di inserimento si trova nello stesso punto iniziale della riga precedente.

Intelligenti

Se l'opzione è selezionata, le nuove righe vengono posizionate in modo da adattarsi al contesto del codice, in base ad altre impostazioni di formattazione del codice e alle convenzioni di IntelliSense per il linguaggio di sviluppo scelto. Questa opzione non è disponibile per tutti i linguaggi di sviluppo.

Ad esempio, le righe racchiuse tra una parentesi graffa di apertura ( { ) e una di chiusura ( } ), potrebbero essere rientrate automaticamente al successivo punto di tabulazione dalla posizione delle parentesi graffe allineate.

## <a name="tabs"></a>Schede

Dimensione tabulazione

Consente di impostare la distanza in spazi tra le tabulazioni. Il valore predefinito è quattro spazi.

Dimensione rientro

Consente di impostare la dimensione in spazi di un rientro automatico. Il valore predefinito è quattro spazi. Per riempire la dimensione specificata verranno inseriti caratteri di tabulazione, caratteri spazio o entrambi i caratteri.

Inserisci spazi

Se l'opzione è selezionata, tramite le operazioni di rientro vengono inseriti solo caratteri di spazio, non di tabulazione. Se **Dimensione rientro** è impostato su 5, ad esempio, vengono inseriti cinque caratteri di spazio ogni volta che viene premuto il tasto TAB o il pulsante **Aumenta rientro** nella barra degli strumenti **Formattazione**.

Mantieni tabulazioni

Se l'opzione è selezionata, tramite le operazioni di rientro vengono inseriti tutti i caratteri di tabulazione possibili. Ogni carattere TAB riempie il numero di spazi specificato in **Dimensioni tabulazione**. Se **Dimensione rientro** non è un multiplo pari di **Dimensione tabulazione**, vengono aggiunti caratteri di spazio per colmare la differenza.

## <a name="see-also"></a>Vedi anche

- [Opzioni, Editor di testo, Tutti i linguaggi](../../ide/reference/options-text-editor-all-languages.md)
- [Generale, Ambiente, finestra di dialogo Opzioni](../../ide/reference/general-environment-options-dialog-box.md)
