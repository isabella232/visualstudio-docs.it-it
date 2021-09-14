---
title: Opzioni di formattazione dell'editor U-SQL
description: Informazioni su come usare la pagina Opzioni di formattazione e le relative pagine secondarie per impostare le opzioni per la formattazione del codice nell'editor di codice durante la programmazione in U-SQL.
ms.custom: SEO-VS-2020
ms.date: 01/17/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting.General
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: e13ef80bae3e59901a8fb0ae67a837a2f344b551
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628650"
---
# <a name="options-text-editor-u-sql-formatting"></a>Opzioni, Editor di testo, U-SQL, Formattazione

Usare la pagina di opzioni **Formattazione** per impostare le opzioni di formattazione del codice nell'editor del codice. Per accedere a questa pagina delle opzioni, scegliere **Opzioni**  >  **strumenti**. Nella finestra di dialogo **Opzioni** scegliere **Editor di testo** > **U-SQL** > **Formattazione**.

## <a name="general-page"></a>Pagina Generale

### <a name="general-settings"></a>Impostazioni generali

Queste impostazioni influenzano *il momento in cui* l'editor del codice applica le opzioni di formattazione al codice.

- **Formatta automaticamente l'istruzione completata dopo l'immissione del punto e virgola**

   Se selezionata, le istruzioni vengono formattate dopo l'immissione del punto e virgola in base alle opzioni di formattazione selezionate per l'editor.

- **Formatta automaticamente dopo operazione Incolla**

   Quando questa opzione è selezionata, il testo incollato nell'editor viene formattato in base alle opzioni di formattazione selezionate per l'editor.

## <a name="preview-windows"></a>Finestre di anteprima

Ognuna delle pagine secondarie **Rientro**, **Nuove righe** e **Spaziatura** visualizza una finestra di anteprima nella parte inferiore. La finestra di anteprima illustra l'effetto di ogni opzione. Per usare la finestra di anteprima, selezionare un'opzione di formattazione. La finestra di anteprima illustra un esempio dell'opzione selezionata. Quando si modifica un'impostazione selezionando una casella di controllo, la finestra di anteprima viene aggiornata per mostrare l'effetto della nuova impostazione.

### <a name="indentation-remarks"></a>Osservazioni sul rientro

Le opzioni di rientro nelle pagine **Tabulazioni** per ogni linguaggio determinano solo dove l'editor di codice posiziona il cursore quando si preme **INVIO** alla fine di una riga. Le opzioni di rientro in **Formattazione** si applicano quando il codice viene formattato automaticamente, ad esempio:

- Quando si incolla codice nel file quando è selezionata l'opzione **Formatta automaticamente dopo operazione Incolla**
- Quando il blocco da formattare viene digitato manualmente

## <a name="see-also"></a>Vedi anche

- [Generale, Ambiente, finestra di dialogo Opzioni](../../ide/reference/general-environment-options-dialog-box.md)
