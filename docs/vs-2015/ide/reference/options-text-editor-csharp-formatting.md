---
title: Opzioni, Editor di testo, C#, Formattazione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Wrapping
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Wrapping
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting
helpviewer_keywords:
- formatting [C#]
- formatting [J#]
- Text Editor Options dialog box, formatting
ms.assetid: 5a7bb668-1d0c-4ffe-9508-24592813162e
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5371b7180aed462910a57daeb9bf5d43f2ecfedb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662278"
---
# <a name="options-text-editor-c-formatting"></a>Opzioni, Editor di testo, C#, Formattazione
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Usare la pagina delle proprietà **Formattazione** per impostare le opzioni di formattazione del codice nell'editor del codice. Per accedere a questa finestra di dialogo, scegliere **Opzioni** dal menu **Strumenti**, espandere **Editor di testo**, espandere **C#** e quindi fare clic su **Formattazione**.

> [!NOTE]
> È possibile che le finestre di dialogo e i comandi di menu visualizzati varino da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [personalizzazione delle impostazioni di sviluppo in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="general-settings"></a>Impostazioni generali
 Le impostazioni generali hanno effetto sulla modalità con la quale l'editor del codice applica le opzioni di formattazione al codice.

## <a name="uielement-list"></a>Elenco degli elementi di interfaccia

|Etichetta|Descrizione|
|-----------|-----------------|
|**Formatta automaticamente istruzione completata dopo l'immissione di ;**|Quando questa opzione è selezionata, vengono formattate le istruzioni al completamento in base alle opzioni di formattazione selezionate per l'editor del codice. Deselezionare questa opzione se non si vuole modificare le istruzioni con l'editor di codice.|
|**Formatta automaticamente blocco completato dopo l'immissione di }**|Quando l'opzione è selezionata, i blocchi di codice vengono formattati in base alle opzioni di formattazione selezionate per l'editor di codice subito dopo il completamento del blocco. Deselezionare questa opzione se non si vuole modificare i blocchi con l'editor di codice.|
|**Modifica rientro dopo operazione Incolla**|Quando l'opzione è selezionata, il testo inserito nell'editor di codice viene formattato in base alle opzioni di formattazione selezionate per l'editor di codice. Deselezionare questa opzione se non si vuole modificare il testo inserito.|

## <a name="preview-window"></a>Finestra di anteprima
 I riquadri delle opzioni **Rientro**, **Nuove righe**, **Spaziatura** e **Ritorno a capo** visualizzano una finestra di anteprima. La finestra di anteprima illustra l'effetto di ogni opzione. Per usare la finestra di anteprima, selezionare un'opzione di formattazione. La finestra di anteprima illustra un esempio dell'opzione selezionata. Se si modifica questa impostazione, ad esempio si seleziona o deseleziona una casella di controllo, la finestra di anteprima viene aggiornata per visualizzare l'effetto della nuova impostazione.

## <a name="remarks"></a>Osservazioni
 Le opzioni di rientro nelle pagine **Tabulazioni** per ogni lingua solo determinano solo il punto in cui l'editor del codice posiziona il cursore quando si preme INVIO alla fine di una riga. Le opzioni di rientro in **Formattazione** si applicano quando il codice viene formattato automaticamente, ad esempio quando si inserisce codice nel file ed è selezionata l'opzione **Modifica rientro dopo operazione Incolla** o quando il blocco da formattare viene digitato manualmente.

## <a name="see-also"></a>Vedere anche
 [Generale, ambiente, finestra di dialogo Opzioni](../../ide/reference/general-environment-options-dialog-box.md)
