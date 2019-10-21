---
title: Opzioni, Editor di testo, Tutti i linguaggi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.General
- VS.ToolsOptionsPages.Text_Editor.ResJSON.General
- vs.toolsoptionspages.text_editor.all_languages.scrollbars
helpviewer_keywords:
- Text Editor Options dialog box
- statement completion
- word wrap
- General dialog box
- line numbers
- virtual space
ms.assetid: 49ee7306-9d46-4170-850f-a1716171752d
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ebe2da1dec9917a792f3e4e02516a79cff605c80
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662406"
---
# <a name="options-text-editor-all-languages"></a>Opzioni, Editor di testo, Tutti i linguaggi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Questa finestra di dialogo consente di modificare il comportamento predefinito dell'editor del codice. Queste impostazioni si applicano anche agli altri editor basati sull'editor del codice, come ad esempio la visualizzazione dell'origine della finestra di progettazione HTML. Per aprire questa finestra di dialogo, selezionare **Opzioni** dal menu **Strumenti**. All'interno della cartella dell'**Editor di testo** espandere la sottocartella **All Languages** (Tutti i linguaggi), quindi scegliere **Generale**.

> [!CAUTION]
> Questa pagina consente di impostare le opzioni predefinite per tutti i linguaggi di sviluppo. Tenere presente che la reimpostazione di un'opzione in questa finestra di dialogo reimposterà le opzioni generali in tutti i linguaggi per qualunque scelta operata in questa fase. Per modificare le opzioni dell'editor di testo per un solo linguaggio, espandere la sottocartella per tale linguaggio e selezionare le pagine relative alle opzioni.

 Quando nelle pagine di opzioni Generale è stata selezionata un'opzione per alcuni linguaggi di programmazione, ma non per altri, viene visualizzato un segno di spunta di colore grigio.

> [!NOTE]
> Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="statement-completion"></a>Completamento istruzioni
 Elenca automaticamente i membri quando vengono selezionati, gli elenchi popup di membri, proprietà, valori o metodi disponibili vengono visualizzati da IntelliSense durante la digitazione nell'editor. Scegliere qualsiasi elemento dall'elenco popup per inserirlo nel codice. Selezionando questa opzione viene attivata l'opzione **Nascondi membri avanzati**.

 Nascondi membri avanzati se selezionato, abbrevia gli elenchi popup di completamento delle istruzioni visualizzando solo gli elementi utilizzati più di frequente. Agli altri elementi viene applicato un filtro che non ne consente la visualizzazione nell'elenco.

 Informazioni sui parametri quando questa opzione è selezionata, la sintassi completa della dichiarazione o della routine corrente viene visualizzata sotto il punto di inserimento nell'editor, con tutti i relativi parametri disponibili. Il parametro successivo che è possibile assegnare viene visualizzato in grassetto.

## <a name="settings"></a>Impostazioni
 Abilita spazio virtuale quando questa opzione è selezionata e il **ritorno a capo automatico** è deselezionato, è possibile fare clic in un punto qualsiasi oltre la fine di una riga nell'editor di codice e digitare. È possibile utilizzare questa funzionalità per inserire commenti sempre nello stesso punto accanto al codice.

 Ritorno a capo automatico quando selezionato, qualsiasi parte di una riga che si estende orizzontalmente oltre l'area visibile dell'editor viene automaticamente visualizzata nella riga successiva. Se si seleziona questa opzione, l'opzione **Mostra icone per ritorno a capo automatico** viene attivata.

> [!NOTE]
> Mentre l'opzione **A capo automatico** è attivata, la funzionalità **Spazio virtuale** viene disattivata.

 Mostra glifi visivi per il ritorno a capo automatico quando è selezionato, viene visualizzato un indicatore di ritorno a capo quando una riga lunga si trova su una seconda riga.

 ![Screenshot LineBreakSymbol](../../ide/reference/media/linebreak.gif "linebreak")

 Deselezionare questa opzione per non visualizzare tali indicatori.

> [!NOTE]
> Tali frecce di promemoria non vengono aggiunte al codice né stampate, ma vengono visualizzati solo a scopo di riferimento.

 Applica comandi Taglia o copia a righe vuote in assenza di selezione questa opzione consente di impostare il comportamento dell'editor quando si posiziona il punto di inserimento su una riga vuota, non selezionare nulla, quindi copiare o tagliare.

- Se questa opzione è selezionata, la riga vuota viene copiata o tagliata. Se successivamente si utilizza il comando Incolla, viene inserita una nuova riga vuota.

- Se questa opzione è deselezionata, il comando Taglia rimuove le righe vuote. Tuttavia, i dati negli Appunti vengono mantenuti. Quindi, se si utilizza il comando Incolla, viene inserito il contenuto copiato più di recente negli Appunti. Se non è stata effettuata alcuna copia precedente, non viene incollato nulla.

  Questa impostazione non ha alcun effetto sul comando Copia o Taglia se una riga non è vuota. Se non si seleziona alcun elemento, viene copiata o tagliata l'intera riga. Se quindi si applica il comando Incolla, viene inserito il testo dell'intera riga, incluso il carattere di fine riga.

> [!TIP]
> Per visualizzare gli indicatori per spazi, tabulazioni e fine riga e distinguere pertanto le righe rientrate da quelle completamente vuote, selezionare **Avanzate** dal menu **Modifica**, quindi scegliere **Mostra/Nascondi spazi**.

## <a name="display"></a>Visualizzazione
 Numeri di riga quando questa opzione è selezionata, accanto a ogni riga di codice viene visualizzato un numero di riga.

> [!NOTE]
> Tali numeri di riga non vengono aggiunti al codice né stampati, ma vengono visualizzati solo a scopo di riferimento.

 Consenti navigazione URL con clic singolo quando selezionata, il cursore del mouse assume la forma di un puntatore mentre passa su un URL nell'editor. È possibile fare clic sull'URL per visualizzare la pagina indicata nel browser Web.

 Barra di spostamento quando selezionata, Visualizza la **barra di spostamento** nella parte superiore dell'editor di codice. i cui elenchi a discesa **Oggetti** e **Membri** consentono di scegliere un determinato oggetto nel codice, selezionarne i membri e passare alla dichiarazione del membro selezionato nell'editor di codice.

## <a name="see-also"></a>Vedere anche
 [Opzioni, editor di testo, tutti i linguaggi, schede](../../ide/reference/options-text-editor-all-languages-tabs.md) [generale, ambiente, finestra di dialogo Opzioni](../../ide/reference/general-environment-options-dialog-box.md) [con IntelliSense](../../ide/using-intellisense.md)
