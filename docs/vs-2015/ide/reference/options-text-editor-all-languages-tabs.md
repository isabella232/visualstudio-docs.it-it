---
title: Opzioni, Editor di testo, Tutti i linguaggi, Schede | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.ResJSON.Tabs
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Tabs
- VS.ToolsOptionsPages.Text_Editor.All_Languages.Tabs
helpviewer_keywords:
- indents, Code Editor
- Code Editor, default behavior
- tabs, setting in Code Editor
- All Languages Text Editor Options dialog box
- editors, Code Editor
- Code Editor, indenting
- Code Editor, tabs
ms.assetid: 7e208e1d-5e3a-4bf7-a27b-4417e3e049c7
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a4d94aa2f9445104ab6d645d057e68186e917d12
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2019
ms.locfileid: "59658240"
---
# <a name="options-text-editor-all-languages-tabs"></a>Opzioni, Editor di testo, Tutti i linguaggi, Schede
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Questa finestra di dialogo consente di modificare il comportamento predefinito dell'editor del codice. Queste impostazioni si applicano anche agli altri editor basati sull'editor del codice, come la visualizzazione dell'origine della finestra di progettazione HTML. Per visualizzare queste opzioni, selezionare **Opzioni** dal menu **Strumenti**. All'interno della cartella dell'**Editor di testo** espandere la sottocartella **All Languages** (Tutti i linguaggi), quindi scegliere **Schede**.  
  
> [!CAUTION]
>  Questa pagina consente di impostare le opzioni predefinite per tutti i linguaggi di sviluppo. Tenere presente che la reimpostazione di un'opzione in questa finestra di dialogo reimposterà le opzioni delle schede in tutti i linguaggi per qualunque scelta operata qui. Per modificare le opzioni dell'editor di testo per un solo linguaggio, espandere la sottocartella per tale linguaggio e selezionare le pagine relative alle opzioni.  
  
 Se vengono selezionate diverse impostazioni nelle pagine di opzioni delle schede per determinati linguaggi di programmazione, viene visualizzato il messaggio "Le impostazioni dei rientri per singoli formati di testo sono in conflitto" per diverse opzioni di **Rientri**; inoltre viene visualizzato il messaggio "Le impostazioni delle tabulazioni per singoli formati di testo sono in conflitto", per diverse opzioni della **Scheda**. Ad esempio, questo promemoria viene visualizzato se è stata selezionata l'opzione **Rientro automatico** per Visual Basic, mentre è stato selezionato **Block indenting** (Blocca rientro) per Visual C++.  
  
> [!NOTE]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="indenting"></a>Rientri  
 nessuno  
 Se l'opzione è selezionata, le nuove righe non vengono rientrate. Il punto di inserimento si trova nella prima colonna di una nuova riga.  
  
 Blocco  
 Se l'opzione è selezionata, le nuove righe vengono rientrate automaticamente. Il punto di inserimento si trova nello stesso punto iniziale della riga precedente.  
  
 Intelligenti  
 Se l'opzione è selezionata, le nuove righe vengono posizionate in modo da adattarsi al contesto del codice, in base ad altre impostazioni di formattazione del codice e alle convenzioni di IntelliSense per il linguaggio di sviluppo scelto. Questa opzione non è disponibile per tutti i linguaggi di sviluppo.  
  
 Ad esempio, le righe racchiuse tra una parentesi graffa di apertura ( { ) e una di chiusura ( } ), potrebbero essere rientrate automaticamente al successivo punto di tabulazione dalla posizione delle parentesi graffe allineate.  
  
## <a name="tabs"></a>Schede  
 Dimensione tabulazione  
 Viene impostato il numero di spazi tra due punti di tabulazione. Il valore predefinito è quattro spazi.  
  
 Dimensione rientro  
 Viene impostata la dimensione in spazi di un rientro automatico. Il valore predefinito è quattro spazi. Verranno inseriti i caratteri di tabulazione e di spazio, o entrambi, in modo da riempire la dimensione specificata.  
  
 Inserisci spazi  
 Se l'opzione è selezionata, tramite le operazioni di rientro vengono inseriti solo caratteri di spazio, non di tabulazione. Se **Dimensione rientro** è impostato su 5, ad esempio, vengono inseriti cinque caratteri di spazio ogni volta che viene premuto il tasto TAB o il pulsante **Aumenta rientro** nella barra degli strumenti **Formattazione**.  
  
 Mantieni tabulazioni  
 Se l'opzione è selezionata, tramite le operazioni di rientro vengono inseriti tutti i caratteri di tabulazione possibili. Tramite ogni carattere di tabulazione viene riempito il numero di spazi specificato in **Dimensione tabulazione**. Se **Dimensione rientro** non è un multiplo pari di **Dimensione tabulazione**, vengono aggiunti caratteri di spazio per colmare la differenza.  
  
## <a name="see-also"></a>Vedere anche  
 [Opzioni, Editor di testo, Tutti i linguaggi](../../ide/reference/options-text-editor-all-languages.md)   
 [Generale, Ambiente, finestra di dialogo Opzioni](../../ide/reference/general-environment-options-dialog-box.md)
