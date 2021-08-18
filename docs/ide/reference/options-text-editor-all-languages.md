---
title: Opzioni, Editor di testo, Tutti i linguaggi
description: Informazioni su come usare la pagina Generale nella sezione Tutti i linguaggi per modificare il comportamento predefinito dell'editor di codice all'interno Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.General
- VS.ToolsOptionsPages.Text_Editor.ResJSON.General
- VS.ToolsOptionsPages.Text_Editor.All_Languages.General
- VS.ToolsOptionsPages.Text_Editor.Basic.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.General
- VS.ToolsOptionsPages.Text_Editor.C/C++.General
- VS.ToolsOptionsPages.Text_Editor.CoffeeScript.General
- VS.ToolsOptionsPages.Text_Editor.CSS.General
- VS.ToolsOptionsPages.Text_Editor.Dockerfile.General
- VS.ToolsOptionsPages.Text_Editor.F#.General
- VS.ToolsOptionsPages.Text_Editor.Fsharp.General
- VS.ToolsOptionsPages.Text_Editor.HQL.General
- VS.ToolsOptionsPages.Text_Editor.HTML.General
- VS.ToolsOptionsPages.Text_Editor.HTML_(Web_Forms).General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.General
- VS.ToolsOptionsPages.Text_Editor.JSON.General
- VS.ToolsOptionsPages.Text_Editor.LESS.General
- VS.ToolsOptionsPages.Text_Editor.Plain_Text.General
- VS.ToolsOptionsPages.Text_Editor.SCSS.General
- VS.TOOLSOPTIONSPAGES.TEXT_EDITOR.SQL_SERVER_TOOLS.GENERAL
- VS.ToolsOptionsPages.Text_Editor.StreamAnalytics.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL90.General
- VS.ToolsOptionsPages.Text_Editor.U-SQL.General
- VS.ToolsOptionsPages.Text_Editor.XAML.General
- VS.ToolsOptionsPages.Text_Editor.XML.General
helpviewer_keywords:
- Text Editor Options dialog box
- statement completion
- word wrap
- General dialog box
- line numbers
- virtual space
ms.assetid: 49ee7306-9d46-4170-850f-a1716171752d
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: f581f48efb9fbba97aa65b9826f7114f7377e951
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122100998"
---
# <a name="options-dialog-box-text-editor--all-languages"></a>Finestra di dialogo Opzioni: Editor di testo \> Tutti i linguaggi

Questa finestra di dialogo consente di modificare il comportamento predefinito dell'editor del codice. Queste impostazioni si applicano anche agli altri editor basati sull'editor del codice, come ad esempio la visualizzazione dell'origine della finestra di progettazione HTML. Per aprire questa finestra di dialogo, selezionare **Opzioni** dal menu **Strumenti**. All'interno della cartella dell'**Editor di testo** espandere la sottocartella **All Languages** (Tutti i linguaggi), quindi scegliere **Generale**.

> [!CAUTION]
> Questa pagina consente di impostare le opzioni predefinite per tutti i linguaggi di sviluppo. Tenere presente che la reimpostazione di un'opzione in questa finestra di dialogo reimposterà le opzioni generali in tutti i linguaggi per qualunque scelta operata in questa fase. Per modificare le opzioni dell'editor di testo per un solo linguaggio, espandere la sottocartella per tale linguaggio e selezionare le pagine relative alle opzioni.

Quando nelle pagine di opzioni Generale è stata selezionata un'opzione per alcuni linguaggi di programmazione, ma non per altri, viene visualizzato un segno di spunta di colore grigio.

## <a name="statement-completion"></a>Completamento istruzioni

**Elenco automatico membri**

Quando questa opzione è selezionata, IntelliSense visualizzerà elenchi popup dei membri, delle proprietà, dei valori e dei metodi disponibili durante la digitazione nell'editor. Scegliere un elemento dall'elenco popup per inserirlo nel codice. Selezionando questa opzione viene attivata l'opzione **Nascondi membri avanzati**.

**Nascondi membri avanzati**

Se selezionata, gli elenchi popup di completamento delle istruzioni vengono ridotti e vengono visualizzati solo gli elementi di uso più comune. Gli altri elementi dell'elenco verranno filtrati.

**Informazioni sui parametri**

Quando questa opzione è selezionata, la sintassi completa della dichiarazione o della routine corrente viene visualizzata sotto il punto di inserimento nell'editor, con tutti i relativi parametri disponibili. Il parametro successivo che può essere assegnato è evidenziato in grassetto.

## <a name="settings"></a>Impostazioni

**Abilita spazio virtuale**

Quando questa opzione è selezionata e l'opzione **A capo automatico** è deselezionata, è possibile fare clic in qualsiasi punto oltre la fine della riga nell'editor di codice e digitare. È possibile utilizzare questa funzionalità per inserire commenti sempre nello stesso punto accanto al codice.

**Ritorno a capo automatico**

Se questa opzione è selezionata, la parte di una riga che si estende in senso orizzontale oltre la parte visibile dell'editor viene automaticamente visualizzata nella riga successiva. Se si seleziona questa opzione, l'opzione **Mostra icone per ritorno a capo automatico** viene attivata.

> [!NOTE]
> Mentre l'opzione **A capo automatico** è attivata, la funzionalità **Spazio virtuale** viene disattivata.

**Mostra icone per ritorno a capo automatico**

Quando questa opzione è selezionata, viene visualizzato un indicatore a forma di freccia rivolta indietro in caso di ritorno a capo automatico di una riga lunga su una seconda riga.

![Schermata LineBreakSymbol](../../ide/reference/media/linebreak.gif)

Deselezionare questa opzione per non visualizzare tali indicatori.

> [!NOTE]
> Tali frecce di promemoria non vengono aggiunte al codice né stampate, Si tratta esclusivamente di elementi di riferimento.

**Numeri di riga**

Quando questa opzione è selezionata, accanto a ciascuna riga di codice viene visualizzato un numero di riga.

> [!NOTE]
> Tali numeri di riga non vengono aggiunti al codice né stampati,  Si tratta esclusivamente di elementi di riferimento.

**Consenti navigazione URL con clic singolo**

Quando questa opzione è selezionata, il cursore del mouse assume la forma di una mano quando viene posizionato su un URL nell'editor. È possibile fare clic sull'URL per visualizzare la pagina indicata nel browser Web.

**Barra di navigazione**

Quando questa opzione è selezionata, nella parte superiore dell'editor di codice viene visualizzata la **barra di navigazione**,  i cui elenchi a discesa **Oggetti** e **Membri** consentono di scegliere un determinato oggetto nel codice, selezionarne i membri e passare alla dichiarazione del membro selezionato nell'editor di codice.

**Applica comandi Taglia o Copia a righe vuote in assenza di selezione**

Questa opzione consente di impostare il comportamento dell'editor quando si posiziona il punto di inserimento su una riga vuota, non si seleziona alcun elemento, quindi si utilizza il comando Copia o Taglia.

- Se questa opzione è selezionata, la riga vuota viene copiata o tagliata. Se successivamente si utilizza il comando Incolla, viene inserita una nuova riga vuota.

- Se questa opzione è deselezionata, il comando Taglia rimuove le righe vuote. Tuttavia, i dati negli Appunti vengono mantenuti. Quindi, se si utilizza il comando Incolla, viene inserito il contenuto copiato più di recente negli Appunti. Se non è stata eseguita alcuna operazione di copia, non viene incollato alcun elemento.

Questa impostazione non ha alcun effetto sul comando Copia o Taglia se una riga non è vuota. Se non è selezionato alcun elemento, viene copiata o tagliata la riga intera. Se quindi si applica il comando Incolla, viene inserito il testo dell'intera riga, incluso il carattere di fine riga.

> [!TIP]
> Per visualizzare gli indicatori per spazi, tabulazioni e fine riga e distinguere pertanto le righe rientrate da quelle completamente vuote, selezionare **Avanzate** dal menu **Modifica**, quindi scegliere **Mostra/Nascondi spazi**.

## <a name="see-also"></a>Vedi anche

- [Opzioni, Editor di testo, Tutti i linguaggi, Schede](../../ide/reference/options-text-editor-all-languages-tabs.md)
- [Generale, Ambiente, finestra di dialogo Opzioni](../../ide/reference/general-environment-options-dialog-box.md)
- [Uso di IntelliSense](../../ide/using-intellisense.md)
