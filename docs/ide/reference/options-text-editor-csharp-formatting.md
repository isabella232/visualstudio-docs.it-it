---
title: Opzioni di formattazione dell'editor C#
description: Informazioni su come usare la pagina Opzioni di formattazione e le relative pagine secondarie per impostare le opzioni per la formattazione del codice nell'editor di codice durante la programmazione in C#.
ms.custom: SEO-VS-2020
ms.date: 08/14/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Wrapping
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.Formatting.General
helpviewer_keywords:
- formatting options [C#]
- Text editor Options dialog box, formatting
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- dotnet
ms.openlocfilehash: 13c8ca9dd8c71cf091868f1ddd00847209cf3bb1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122041139"
---
# <a name="options-dialog-box-text-editor--c--code-style--formatting"></a>Finestra di dialogo Opzioni: Formattazione dello \> stile del codice C# dell'editor \> di \> testo

Usare la pagina di opzioni **Formattazione** e le relative pagine secondarie ([**Rientro**](#indentation-page), **Nuove righe**, **Spaziatura** e **Ritorno a capo**) per impostare le opzioni di formattazione del codice nell'editor del codice.

Per accedere a questa pagina delle opzioni, scegliere  >  **Opzioni strumenti** dalla barra dei menu. Nella finestra di dialogo **Opzioni** scegliere **Editor di testo** > **C#** > **Stile codice** > **Formattazione**.

> [!TIP]
> Ognuna delle pagine secondarie **Rientro**, **Nuove righe**, **Spaziatura** e **Ritorno a capo** visualizza una finestra di anteprima nella parte inferiore che mostra l'effetto dell'applicazione di ogni opzione. Per usare la finestra di anteprima, selezionare un'opzione di formattazione. La finestra di anteprima illustra un esempio dell'opzione selezionata. Quando si modifica un'impostazione selezionando un pulsante di opzione o una casella di controllo, la finestra di anteprima viene aggiornata per mostrare l'effetto della nuova impostazione.

## <a name="formatting-general-page"></a>Pagina Formattazione (Generale)

### <a name="general-settings"></a>Impostazioni generali

Queste impostazioni influenzano *il momento in cui* l'editor del codice applica le opzioni di formattazione al codice.

|Etichetta|Descrizione|
|-----------|-----------------|
|**Formatta automaticamente durante la digitazione**|Quando questa opzione è deselezionata, le opzioni **Formatta automaticamente istruzione dopo :** e **Formatta automaticamente blocco dopo }** sono disabilitate.|
|**Formatta automaticamente istruzione dopo ;**|Quando questa opzione è selezionata, le istruzioni vengono formattate al completamento in base alle opzioni di formattazione selezionate per l'editor.|
|**Formatta automaticamente blocco dopo }**|Quando questa opzione è selezionata, i blocchi di codice vengono formattati in base alle opzioni di formattazione selezionate per l'editor subito dopo il completamento del blocco di codice.|
|**Formatta automaticamente dopo INVIO**|Quando questa opzione è selezionata, il testo viene formattato dopo la pressione di **INVIO**, in base alle opzioni di formattazione selezionate per l'editor.|
|**Formatta automaticamente dopo operazione Incolla**|Quando questa opzione è selezionata, il testo incollato nell'editor viene formattato in base alle opzioni di formattazione selezionate per l'editor.|

::: moniker range="vs-2019"

Se si è già utilizzato il comando **Formatta documento** per applicare impostazioni di stile al codice per i file C# in Visual Studio 2017, ora tale funzionalità disponibile con il nome [**Pulizia del codice**](../code-styles-and-code-cleanup.md#apply-code-styles).

::: moniker-end

::: moniker range="vs-2017"

### <a name="format-document-settings"></a>Impostazioni di Formatta documento

Queste impostazioni configurano il comando **Formatta documento** per eseguire una pulizia del codice aggiuntiva in un file. Per altre informazioni su come applicare queste impostazioni, vedere [Format Document command](../code-styles-and-code-cleanup.md#apply-code-styles) (Comando Formatta documento).

|Etichetta|Descrizione|Regole di EditorConfig e Strumenti > Opzioni corrispondenti|
|-----------|-----------------|-----------------|-----------------|
|**Applica tutte le regole di formattazione di C# (rientro, ritorno a capo, spaziatura)**|Il comando **Formatta documento** corregge sempre i problemi di formattazione. Questa impostazione non può essere modificata.| [Opzioni di base di EditorConfig](../../ide/create-portable-custom-editor-options.md)<br/>[Opzioni di formattazione di EditorConfig .NET](/dotnet/fundamentals/code-analysis/style-rules/formatting-rules)<br/><br/>**Strumenti**  >  **Opzioni**  >  **Editor di testo**  >  **C#**  >  **Formattazione** > [**rientro** o **nuove righe** o **spaziatura** o **ritorno a capo**]|
|**Esegui la pulizia aggiuntiva del codice durante la formattazione**|Se selezionata, applica le correzioni alle regole specificate di seguito nel comando **Edit.FormatDocument**.| N/A |
|**Rimuovere gli utilizzi non necessari**|Se selezionata, consente di rimuovere le direttive `using` inutili quando **Edit.FormatDocument** viene attivato.| N/A |
|**Usare l'ordinamento**|Se selezionata, consente di ordinare le direttive `using` quando **Edit.FormatDocument** viene attivato.| dotnet_sort_system_directives_first<br/><br/>**Strumenti**  >  **Opzioni**  >  **Editor di testo**  >  **C#**  >  **Avanzate**  >  **Inserire prima le direttive 'System' quando si esegue l'ordinamento tramite** |
|**Aggiungi/rimuovi le parentesi graffe per le istruzioni di controllo a riga singola**|Se selezionata, aggiunge o rimuove le parentesi graffe da istruzioni di controllo a riga singola quando **Edit.FormatDocument** viene attivato.| csharp_prefer_braces<br/><br/>**Strumenti**  >  **Opzioni**  >  **Editor di testo**  >  **C#**  >  **Stile codice**  >  **Preferenze del blocco di codice**  >  **Preferire le parentesi graffe** |
|**Aggiungi i modificatori di accessibilità**|Se selezionata, aggiunge i modificatori di accessibilità mancanti quando **Edit.FormatDocument** viene attivato.| dotnet_style_require_accessibility_modifiers |
|**Ordina i modificatori di accessibilità**|Se selezionata, ordina i modificatori di accessibilità quando **Edit.FormatDocument** viene attivato.| csharp_preferred_modifier_order<br/>visual_basic_preferred_modifier_order |
|**Applica le preferenze relative al corpo di espressioni/blocchi**|Se selezionata, converte i membri con corpo di espressione per bloccare i corpi, o viceversa, quando **Edit.FormatDocument** viene attivato.| [Opzioni di EditorConfig per il membro con corpo di espressione](/dotnet/fundamentals/code-analysis/style-rules/language-rules#expression-bodied-members)<br/><br/>**Strumenti**  >  **Opzioni**  >  **Editor di testo**  >  **C#**  >  **Stile del codice**  >  **Preferenze delle espressioni**  >  **Usare il corpo dell'espressione per metodi, costruttori e così via.** |
|**Applica le preferenze relative al tipo implicito/esplicito**|Se selezionata, consente di convertire `var` al tipo esplicito, o viceversa, quando **Edit.FormatDocument** viene attivato.| [Opzioni di base di EditorConfig per il tipo esplicito](/dotnet/fundamentals/code-analysis/style-rules/language-rules#implicit-and-explicit-types)<br/><br/>**Strumenti**  >  **Opzioni**  >  **Editor di testo**  >  **C#**  >  **Stile codice**  >  **Preferenze di 'var'** |
|**Applica le preferenze relative alle variabili 'out' inline**|Se selezionata, ordina inline le variabili `out` dove possibile quando **Edit.FormatDocument** viene attivato.| csharp_style_inlined_variable_declaration<br/><br/>**Strumenti**  >  **Opzioni**  >  **Editor di testo**  >  **C#**  >  **Stile codice**  >  **Preferenze delle variabili**  >  **Preferire la dichiarazione di variabile inline** |
|**Applica le preferenze relative al tipo di linguaggio/framework**|Se selezionata, consente di convertire i tipi di linguaggio ai tipi framework, o viceversa, quando **Edit.FormatDocument** viene attivato.| dotnet_style_predefined_type_for_locals_parameters_members<br/>dotnet_style_predefined_type_for_member_access<br/><br/>**Strumenti**  >  **Opzioni**  >  **Editor di testo**  >  **C#**  >  **Stile codice**  >  **preferenze di tipo predefinite** |
|**Applica le preferenze di inizializzazione di oggetti/raccolte**|Se selezionata, usa inizializzatori di insieme e oggetto laddove possibile quando **Edit.FormatDocument** viene attivato.| dotnet_style_object_initializer<br/>dotnet_style_collection_initializer<br/><br/>**Strumenti**  >  **Opzioni**  >  **Editor di testo**  >  **C#**  >  **Stile del codice**  >  **Preferenze delle espressioni**  >  **Preferire l'inizializzatore di oggetto** **o preferire l'inizializzatore di raccolta** |
|**Applica le preferenze relative alla qualificazione 'this.'**|Se selezionata, consente di applicare le preferenze `this.` quando **Edit.FormatDocument** viene attivato.| [Opzioni di EditorConfig per la qualificazione this.](/dotnet/fundamentals/code-analysis/style-rules/language-rules#this-and-me)<br/><br/>**Strumenti**  >  **Opzioni**  >  **Editor di testo**  >  **C#**  >  **Stile del codice**  >  **Preferenze di "this".** |
|**Imposta i campi privati come di sola lettura quando possibile**|Se selezionata, rende privati i campi `readonly` dove possibile quando **Edit.FormatDocument** viene attivato.| dotnet_style_readonly_field<br/><br/>**Strumenti**  >  **Opzioni**  >  **Editor di testo**  >  **C#**  >  **Stile codice**  >  **Preferenze dei campi**  >  **Preferire readonly** |
|**Rimuovi cast non necessari**|Se selezionata, consente di rimuovere i cast inutili quando **Edit.FormatDocument** viene attivato.| N/A |
|**Rimuovere le variabili non utilizzate**|Se selezionata, consente di rimuovere le variabili non usate quando **Edit.FormatDocument** viene attivato.| N/A |

![Impostazioni di pulizia del codice per C# in Visual Studio](media/format-document-settings.png)

::: moniker-end

## <a name="indentation-page"></a>Pagina Rientro

Le opzioni di rientro di questa pagina sono applicate quando il codice viene formattato automaticamente. Un esempio di formattazione automatica del codice è quando si incolla codice nel file con l'opzione **Formatta automaticamente dopo operazione Incolla** selezionata. (L'opzione **Formatta automaticamente dopo operazione Incolla** si trova in **Formattazione** > **Generale**.)

![Opzioni di rientro dell'editor di testo C# in Visual Studio](media/csharp-indentation-options.png)

> [!TIP]
> Sono disponibili anche opzioni di rientro nella pagina delle opzioni Tabulazioni C# **dell'editor**  >    >   di testo. Le opzioni determinano solo il punto in cui l'editor del codice posiziona il cursore quando si preme **INVIO** alla fine di una riga.
>
> ![Opzioni di tabulazione dell'editor di testo C# in Visual Studio](media/csharp-tabs-options.png)

## <a name="see-also"></a>Vedi anche

- [Generale, Ambiente, finestra di dialogo Opzioni](../../ide/reference/general-environment-options-dialog-box.md)
