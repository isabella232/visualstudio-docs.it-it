---
title: Alias dei comandi
description: Informazioni su come usare gli alias di comando per digitare un numero minore di caratteri quando si vuole eseguire un comando.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- aliases, Visual Studio commands
- Visual Studio, commands
- predefined command aliases
- commands, aliases
- Visual Studio commands
- pre-defined command aliases
- command aliases
ms.assetid: de8bb378-8c1c-4087-a9a5-537fa8314c19
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: e735a2a4d519cb785ca37f3cf57a55f2d901c4ee
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122116851"
---
# <a name="visual-studio-command-aliases"></a>Visual Studio Command Aliases

Gli alias di comandi consentono di digitare un numero inferiore di caratteri quando si esegue un comando. Immettere gli alias nella casella **Trova/Comando** o nella finestra di **comando**. Ad esempio, anziché immettere `>File.OpenFile` per visualizzare la finestra di dialogo **Apri file** è possibile usare l'alias predefinito `>of`.

Immettere `alias` nella finestra di **comando** per visualizzare un elenco degli alias correnti e le relative definizioni. Immettere `>cls` per cancellare il contenuto della finestra di **comando**. Per visualizzare un alias per un comando specifico, digitare `alias <command name>`.

È possibile creare facilmente un alias per uno dei comandi di Visual Studio (con o senza argomenti). La sintassi dell'alias `File.NewFile MyFile.txt` è ad esempio `alias MyAlias File.NewFile MyFile.txt`. È possibile eliminare uno degli alias con `alias <alias name> /delete`

Nella tabella seguente vengono elencati gli alias predefiniti dei comandi di Visual Studio. Ad alcuni nomi di comando è associato più di un alias predefinito. Fare clic sui collegamenti in corrispondenza dei nomi di comandi riportati di seguito per visualizzare argomenti dettagliati che illustrano la sintassi corretta, gli argomenti e le opzioni per tali comandi.

|Nome comando|Alias|Nome completo|
|------------------|-----------|-------------------|
|[Comando Stampa](../../ide/reference/print-command.md)|?|Debug.Print|
|[Comando Controllo rapido](../../ide/reference/quick-watch-command.md)|??|Debug.Quickwatch|
|Aggiungi nuovo progetto|AddProj|File.AddNewProject|
|[Comando Alias](../../ide/reference/alias-command.md)|Alias|Tools.Alias|
|Auto (finestra)|Auto|Debug.Autos|
|finestra Punti di interruzione|bl|Debug.Breakpoints|
|Imposta/Rimuovi punto di interruzione|bp|Debug.ToggleBreakPoint|
|Finestra Stack di chiamate|CallStack|Debug.CallStack|
|Cancella segnalibri|ClearBook|Edit.ClearBookmarks|
|Chiudi|Chiudi|File.Close|
|Chiudi tutti i documenti|CloseAll|Window.CloseAllDocuments|
|Cancella tutto|cls|Edit.ClearAll|
|Modalità di comando|cmd|View.CommandWindow|
|Visualizza codice|codice|View.ViewCode|
|[Comando Elenca memoria](../../ide/reference/list-memory-command.md)|d|Debug.ListMemory|
|[Comando Elenca memoria](../../ide/reference/list-memory-command.md) come ANSI|da|Debug.ListMemory /Ansi|
|[Comando Elenca memoria](../../ide/reference/list-memory-command.md) formato a byte singolo|db|Debug.ListMemory /Format:OneByte|
|[Comando Elenca memoria](../../ide/reference/list-memory-command.md) come ANSI con formato a quattro byte|dc|Debug.ListMemory /Format:FourBytes /Ansi|
|[Comando Elenca memoria](../../ide/reference/list-memory-command.md) formato a quattro byte|gg|Debug.ListMemory /Format:FourBytes|
|Elimina a inizio riga|DelBOL|Edit.DeleteToBOL|
|Elimina a fine riga|DelEOL|Edit.DeleteToEOL|
|Elimina spazio vuoto superfluo|DelHSp|Edit.DeleteHorizontalWhitespace|
|Progettazione viste|finestra di progettazione|View.ViewDesigner|
|[Comando Elenca memoria](../../ide/reference/list-memory-command.md) formato a virgola mobile|df|Debug.ListMemory/Format:Float|
|Disassembly (finestra)|disasm|Debug.Disassembly|
|[Comando Elenca memoria](../../ide/reference/list-memory-command.md) formato a otto byte|dq|Debug.ListMemory /Format:EightBytes|
|[Comando Elenca memoria](../../ide/reference/list-memory-command.md) come Unicode|du|Debug.ListMemory /Unicode|
|[Comando Evaluate Statement](../../ide/reference/evaluate-statement-command.md)|eval|Debug.EvaluateStatement|
|Esci|Esci|File.Exit|
|Formatta selezione|format|Edit.FormatSelection|
|Schermo intero|FullScreen|View.FullScreen|
|[Comando Start](../../ide/reference/start-command.md)|g|Debug.Start|
|[Comando Vai a](../../ide/reference/go-to-command.md)|GotoLn|Edit.GoTo|
|Vai a parentesi graffa|GotoBrace|Edit.GotoBrace|
|F1Help|Help|Help.F1Help|
|Modalità immediata|immed|Tools.ImmediateMode|
|Inserisci file come testo|InsertFile|Edit.InsertFileAsText|
|[Comando Elenca stack di chiamate](../../ide/reference/list-call-stack-command.md)|kb|Debug.ListCallStack|
|Minuscole|Lcase|Edit.MakeLowercase|
|Taglia la riga|LineCut|Edit.LineCut|
|Elimina riga|LineDel|Edit.LineDelete|
|Elenca membri|ListMembers|Edit.ListMembers|
|Finestra Variabili locali|Variabili locali|Debug.Locals|
|[Comando di output della finestra di comando log](../../ide/reference/log-command-window-output-command.md)|Log|Tools.LogCommandWindowOutput|
|Modalità indicatore nella finestra di comando|mark|Tools.CommandWindowMarkMode|
|Memoria (finestra)|Memory Memory1|Debug.Memory1|
|Finestra Memoria 2|Memory2|Debug.Memory2|
|Finestra Memoria 3|Memory3|Debug.Memory3|
|Finestra Memoria 4|Memory4|Debug.Memory4|
|[Comando Set Radix](../../ide/reference/set-radix-command.md)|n|Debug.SetRadix|
|[Comando ShowWebBrowser](../../ide/reference/showwebbrowser-command.md)|nav navigate|View.ShowWebBrowser|
|Segnalibro successivo|NextBook|Edit.NextBookmark|
|[Comando Nuovo file](../../ide/reference/new-file-command.md)|nf|File.NewFile|
|Nuovo progetto|np NewProj|File.NewProject|
|[Comando Apri file](../../ide/reference/open-file-command.md)|of Open|File.OpenFile|
|[Comando Apri Project](../../ide/reference/open-project-command.md)|op|File.OpenProject|
|Comprimi alle definizioni/Rimuovi struttura|OutlineDefs StopOutlining|Edit.CollapseToDefinitions|
|Esegui istruzione/routine|p|Debug.StepOver|
|Informazioni parametri|ParamInfo|Edit.ParameterInfo|
|Esci da istruzione/routine|pr|Debug.StepOut|
|Segnalibro precedente|PrevBook|Edit.PreviousBookmark|
|Stampa file|print|File.Print|
|Finestra Proprietà|props|View.PropertiesWindow|
|Interrompere|q|Debug.StopDebugging|
|Ripeti|rollforward|Edit.Redo|
|Registri (finestra)|registri|Debug.Registers|
|Esegui fino al cursore|rtc|Debug.RunToCursor|
|Salva elementi selezionati|Salva|File.SaveSelectedItems|
|Salva tutto|SaveAll|File.SaveAll|
|Save As|SaveAs|File.SaveSelectedItemsAs|
|[Comando shell](../../ide/reference/shell-command.md)|shell|Tools.Shell|
|Interrompi ricerca nei file|StopFind|Edit.FindInFiles /stop|
|Scambia punto di aggancio|SwapAnchor|Edit.SwapAnchor|
|Esegui istruzione|t|Debug.StepInto|
|Inserisci tabulazioni nella selezione|inserimento di tabulazioni|Edit.TabifySelection|
|Finestra dell'elenco attività|TaskList|View.TaskList|
|finestra Thread|Thread|Debug.Threads|
|Affianca orizzontalmente|TileH|Window.TileHorizontally|
|Affianca verticalmente|TileV|Window.TileVertically|
|Attiva/Disattiva segnalibro|ToggleBook|Edit.ToggleBookmark|
|Finestra della casella degli strumenti|casella degli strumenti|View.Toolbox|
|[Comando List Disassembly](../../ide/reference/list-disassembly-command.md)|u|Debug.ListDisassembly|
|Maiuscole|Ucase|Edit.MakeUppercase|
|Annulla|rollback|Edit.Undo|
|Rimuovi tabulazioni nella selezione|Untabify|Edit.UntabifySelection|
|Finestra Espressioni di controllo|Video|Debug.WatchN|
|Attiva/Disattiva a capo automatico|WordWrap|Edit.ToggleWordWrap|
|Elenca processi|&#124;|Debug.ListProcesses|
|[Comando Elenca thread](../../ide/reference/list-threads-command.md)|~ ~*k ~\*kb|Debug.ListThreads Debug.ListTheads /AllThreads|

## <a name="see-also"></a>Vedi anche

- [Visual Studio Comandi](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/Comando](../../ide/find-command-box.md)
