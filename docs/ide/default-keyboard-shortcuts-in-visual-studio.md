---
title: Tasti di scelta rapida
description: Informazioni sui tasti di scelta rapida predefiniti in Visual Studio che consentono di accedere a un'ampia gamma di comandi e finestre.
ms.custom: SEO-VS-2020
ms.date: 09/23/2021
ms.topic: reference
helpviewer_keywords:
- shortcut keys [Visual Studio], keyboard binding schemes
- keyboard binding schemes [Visual Studio]
- Help [Visual Studio], shortcut keys
- keyboard shortcuts [Visual Studio], keyboard binding schemes
- keyboard shortcuts
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 75c7ddb84d561c123a7bb7bc1bc4a41df2a711b8
ms.sourcegitcommit: 65a1b6aae8387735f05a83b45e1a6865e9805e1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2021
ms.locfileid: "129339629"
---
# <a name="keyboard-shortcuts-in-visual-studio"></a>Tasti di scelta rapida in Visual Studio

Per accedere a vari [comandi](reference/visual-studio-commands.md) e finestre in Visual Studio, è possibile scegliere il tasto di scelta rapida appropriato. In questa pagina vengono elencati i tasti di scelta rapida predefiniti per i comandi per il profilo **Generale**, che potrebbe essere stato scelto durante l'installazione di Visual Studio. Indipendentemente dal profilo scelto, è possibile [identificare il tasto di scelta rapida](identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md) per un comando aprendo la finestra di dialogo **Opzioni**, espandendo il nodo **Ambiente** e scegliendo **Tastiera**. È anche possibile personalizzare i tasti di scelta rapida assegnandone uno diverso per ciascun comando.

Per un elenco di tasti di scelta rapida comuni e altre informazioni sulla produttività, vedere:

- [Suggerimenti relativi alla tastiera](../ide/productivity-shortcuts.md)
- [Suggerimenti per la produttività](../ide/productivity-features.md)

Per altre informazioni sull'accessibilità in [](../ide/reference/accessibility-tips-and-tricks.md) Visual Studio, vedere Suggerimenti e consigli sull'accessibilità e [Procedura: Usare la tastiera in modo esclusivo.](../ide/reference/how-to-use-the-keyboard-exclusively.md)

## <a name="printable-shortcut-cheatsheet"></a>Foglio di controllo dei collegamenti stampabile

Fare clic per ottenere il foglio di controllo dei tasti di scelta rapida [stampabile per Visual Studio](https://visualstudio.microsoft.com/keyboard-shortcuts.pdf).

[:::image type="content" source="media/default-keyboard-shortcuts-in-visual-studio/visual-studio-keyboard-shortcut-cheatsheet.png" alt-text="Foglio di controllo stampabile per i tasti di scelta rapida.":::](https://visualstudio.microsoft.com/keyboard-shortcuts.pdf)

<a name="popular"></a>
## <a name="popular-keyboard-shortcuts-for-visual-studio"></a>Tasti di scelta rapida più comuni per Visual Studio

Tutti i tasti di scelta rapida in questa sezione si applicano a livello globale, se non diversamente specificato. Il contesto *Globale* indica che il tasto di scelta rapida è applicabile in qualsiasi finestra degli strumenti in Visual Studio.

> [!NOTE]
> È possibile [cercare il tasto di scelta rapida](identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md) per qualsiasi comando aprendo la finestra di dialogo **Opzioni**, espandendo il nodo **Ambiente** e quindi scegliendo **Tastiera**.

- [Compila](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_build-popular-shortcuts)
- [Eseguire il debug](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_debug-popular-shortcuts)
- [Modifica](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_edit-popular-shortcuts)
- [File](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_file-popular-shortcuts)
- [Progetto](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_project-popular-shortcuts)
- [Refactoring](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_refactor-popular-shortcuts)
- [Strumenti](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_tools-popular-shortcuts)
- [Visualizzazione](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_view-popular-shortcuts)
- [Window](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_window-popular-shortcuts)

#### <a name="build-popular-shortcuts"></a><a name="bkmk_build-popular-shortcuts"></a> Compilazione: scelte rapide comuni

|Comandi|Tasti di scelta rapida |ID comando|
|-|-|-|
|Compila soluzione|**CTRL+MAIUSC+B** | Build.BuildSolution |
|Annulla|**CTRL+INTERR** | Build.Cancel |
|Compilazione|**Ctrl+F7** | Build.Compile |
|Eseguire l'analisi del codice nella soluzione|**ALT+F11**| Build.RunCodeAnalysisonSolution |

#### <a name="debug-popular-shortcuts"></a><a name="bkmk_debug-popular-shortcuts"></a> Debug: tasti di scelta rapida comuni

|Comandi|Tasti di scelta rapida [contesti speciali]|ID comando|
|-|-|-|
|Interrompere l'operazione a una funzione|**CTRL+B**| Debug.BreakatFunction |
|Interrompere tutto|**CTRL+ALT+INTERR**| Debug.BreakAll |
|Eliminare tutti i punti di interruzione|**CTRL+MAIUSC+F9**| Debug.DeleteAllBreakpoints |
|Eccezioni|**CTRL+ALT+E**| Debug.Exceptions |
|Controllo rapido|**CTRL+ALT+Q**<br /><br />o **MAIUSC+F9**| Debug.QuickWatch |
|Riavvia|**Ctrl+Maiusc+F5**| Debug.Restart |
|Esecuzione fino al cursore|**CTRL+F10**| Debug.RunToCursor |
|Impostare l'istruzione successiva|**Ctrl+Maiusc+F10**| Debug.SetNextStatement |
|Avvio|**F5**| Debug.Start |
|Avviare senza eseguire il debug|**CTRL+F5**| Debug.StartWithoutDebugging |
|Eseguire l'istruzione|**F11**| Debug.StepInto |
|Uscire dall'istruzione/routine|**MAIUSC+F11**| Debug.StepOut |
|Eseguire l'istruzione/routine|**F10**| Debug.StepOver |
|Arrestare l'esecuzione del debug|**MAIUSC+F5**| Debug.StopDebugging |
|Impostare/rimuovere un punto di interruzione|**F9**| Debug.ToggleBreakpoint |

#### <a name="edit-popular-shortcuts"></a><a name="bkmk_edit-popular-shortcuts"></a> Modifica: scelte rapide comuni

|Comandi|Tasti di scelta rapida [contesti speciali]|ID comando|
|-|-|-|
|Riga di interruzione|**Immettere** [Editor di testo, Progettazione report, Windows Form Designer]<br /><br />o **MAIUSC+INVIO** [Editor di testo]| Edit.BreakLine |
|Comprimi in definizioni|**CTRL+M,** **CTRL+O** [Editor di testo]| Edit.CollapseToDefinitions |
|Selezione dei commenti|**CTRL+K,** **CTRL+C** [Editor di testo]| Edit.CommentSelection |
|Completare una parola|**ALT+Freccia DESTRA** [Editor di testo, Progettazione flussi di lavoro]<br /><br />o **CTRL+BARRA SPAZIATRICE** [Editor di testo, Progettazione flussi di lavoro]<br /><br />o **CTRL+K**, **W** [Progettazione flussi di lavoro]<br /><br />o **CTRL+K, CTRL+W** [Progettazione flussi di lavoro]| Edit.CompleteWord |
|Copia|**CTRL+C**<br /><br />o **CTRL+INS**| Edit.Copy |
|Taglia|**CTRL+X**<br /><br />o **MAIUSC+CANC**| Edit.Cut |
|Elimina|**Delete** [Team Explorer]<br /><br />o **MAIUSC+CANC** [diagramma sequenza, diagramma attività UML, diagramma livello]<br /><br />o **CTRL+CANC** [Diagramma classi]| Edit.Delete |
|Find|**CTRL+F**| Edit.Find |
|Trova tutti i riferimenti|**MAIUSC+F12**| Edit.FindAllReferences |
|Cercare nei file|**CTRL+MAIUSC+F**| Edit.FindinFiles |
|Trova successivo|**F3**| Edit.FindNext |
|Trova successivo selezionato|**CTRL+F3**| Edit.FindNextSelected |
|Formatta documento|**CTRL+K, CTRL+D** [Editor di testo]| Edit.FormatDocument |
|Selezione di Formatta|**CTRL+K, CTRL+F** [Editor di testo]| Edit.FormatSelection |
|Passare a|**CTRL+G**| Edit.GoTo |
|Vai alla dichiarazione|**Ctrl+F12**| Edit.GoToDeclaration |
|Vai alla definizione|**F12**| Edit.GoToDefinition |
|Vai alla casella combinata Trova|**CTRL+D**| Edit.GoToFindCombo |
|Passare alla posizione successiva|**F8**| Edit.GoToNextLocation |
|Inserire un frammento di codice|**CTRL+K,** **CTRL+X**| Edit.InsertSnippet |
|Scheda Inserisci|**Tab** [Progettazione report, Windows Forms Designer, Text Editor]| Edit.InsertTab |
|Taglio di linea|**CTRL+L** [Editor di testo]| Edit.LineCut |
|Estendere la colonna verso il basso|**MAIUSC+ALT+Freccia GIÙ** [Editor di testo]| Edit.LineDownExtendColumn |
|Riga aperta sopra|**CTRL+INVIO** [Editor di testo]| Edit.LineOpenAbove |
|Elencare i membri|**CTRL+J** [Editor di testo, Progettazione flussi di lavoro]<br /><br />o **CTRL+K, CTRL+L** [Progettazione flussi di lavoro]<br /><br />o **CTRL+K, L** [Progettazione flussi di lavoro]| Edit.ListMembers |
|Passa a|**CTRL+,**| Edit.NavigateTo |
|Aprire il file|**CTRL+MAIUSC+G**| Edit.OpenFile |
|Modalità sovrascritta|**Insert** [Editor di testo]| Edit.OvertypeMode |
|Informazioni sui parametri|**CTRL+MAIUSC+BARRA SPAZIATRICE** [Editor di testo, Progettazione flussi di lavoro]<br /><br />o **CTRL+K, CTRL+P** [Progettazione flussi di lavoro]<br /><br />o **CTRL+K, P** [Progettazione flussi di lavoro]| Edit.ParameterInfo |
|Incolla|**CTRL+V**<br /><br />o **MAIUSC+INS**| Edit.Paste |
|Visualizzare la definizione|**ALT+F12** [Editor di testo]| Edit.PeekDefinition |
|Ripeti|**CTRL+Y**<br /><br />o **MAIUSC+ALT+BACKSPACE**<br /><br />o **CTRL+MAIUSC+Z**| Edit.Redo |
|Sostituisci|**CTRL+H**| Edit.Replace |
|Seleziona tutto|**CTRL+A**| Edit.SelectAll |
|Selezionare la parola corrente|**CTRL+W** [Editor di testo]| Edit.SelectCurrentWord |
|Annullamento della selezione|**Esc** [Editor di testo, Progettazione report, Impostazioni, progettazione Windows Form, Editor risorse gestite]| Edit.SelectionCancel |
|Racchiudere con|**Ctrl+K, Ctrl+S**| Edit.SurroundWith |
|Tab a sinistra|**MAIUSC+TAB** [Editor di testo, Progettazione report, Windows Forms Editor]| Edit.TabLeft |
|Attiva/Disattiva tutte le struttura|**CTRL+M, CTRL+L** [Editor di testo]| Edit.ToggleAllOutlining |
|Attiva/disattiva il segnalibro|**CTRL+K, CTRL+K** [Editor di testo]| Edit.ToggleBookmark |
|Attivare/disattivare la modalità di completamento|**CTRL+ALT+BARRA SPAZIATRICE** [Editor di testo]| Edit.ToggleCompletionMode |
|Attivare/disattivare l'espansione della struttura|**CTRL+M, CTRL+M** [Editor di testo]| Edit.ToggleOutliningExpansion |
|Rimuovere il commento dalla selezione|**CTRL+K, CTRL+U** [Editor di testo]| Edit.UncommentSelection |
|Annulla|**CTRL+Z**<br /><br />o **ALT+BACKSPACE**| Edit.Undo |
|Eliminazione di word fino alla fine|**CTRL+CANC** [Editor di testo]| Edit.WordDeleteToEnd |
|Eliminazione di word per iniziare|**CTRL+BACKSPACE** [Editor di testo]| Edit.WordDeleteToStart |

#### <a name="file-popular-shortcuts"></a><a name="bkmk_file-popular-shortcuts"></a> File: scelte rapide più comuni

|Comandi|Tasti di scelta rapida [contesti speciali]|ID comando|
|-|-|-|
|Esci|**ALT+F4**| File.Exit |
|Nuovo file|**CTRL+N**| File.NewFile |
|Nuovo progetto|**CTRL+MAIUSC+N**| File.NewProject |
|Nuovo sito Web|**MAIUSC+ALT+N**| File.NewWebSite |
|Aprire il file|**CTRL+O**| File.OpenFile |
|Aprire il progetto|**CTRL+MAIUSC+O**| File.OpenProject |
|Aprire il sito Web|**MAIUSC+ALT+O**| File.OpenWebSite |
|Rinominare|**F2** [Team Explorer]| File.Rename |
|Salvare tutto|**CTRL+MAIUSC+S**| File.SaveAll |
|Salvare gli elementi selezionati|**CTRL+S**| File.SaveSelectedItems |
|Visualizzare nel browser|**CTRL+MAIUSC+W**| File.ViewinBrowser |

#### <a name="project-popular-shortcuts"></a><a name="bkmk_project-popular-shortcuts"></a>Project: scelte rapide più comuni

|Comandi|Tasti di scelta rapida [contesti speciali]|ID comando|
|-|-|-|
|Aggiungere un elemento esistente|**MAIUSC+ALT+A**| Project.AddExistingItem |
|Aggiungere un nuovo elemento|**CTRL+MAIUSC+A**| Project.AddNewItem |

#### <a name="refactor-popular-shortcuts"></a><a name="bkmk_refactor-popular-shortcuts"></a> Refactoring: scelte rapide comuni

|Comando|Scelta rapida da tastiera [Contesti speciali]|ID comando|
|-|-|-|
|Estrai metodo|**CTRL+R, CTRL+M**| Refactor.ExtractMethod |

#### <a name="tools-popular-shortcuts"></a><a name="bkmk_tools-popular-shortcuts"></a> Strumenti: scelte rapide comuni

|Comando|Scelta rapida da tastiera [Contesti speciali]|ID comando|
|-|-|-|
|Associa a processo|**CTRL+ALT+P**| Tools.AttachtoProcess |

#### <a name="view-popular-shortcuts"></a><a name="bkmk_view-popular-shortcuts"></a> Visualizza: scelte rapide comuni

|Comandi|Tasti di scelta rapida [contesti speciali]|ID comando|
|-|-|-|
|Visualizzazione classi|**CTRL+MAIUSC+C**| View.ClassView |
|Modificare l'etichetta|**F2**| View.EditLabel |
|Elenco errori|**\\CTRL+, CTRL+E**<br /><br />o **\\ CTRL+, E**| View.ErrorList |
|Spostarsi all'indietro|**CTRL+-**| View.NavigateBackward |
|Spostarsi in avanti|**CTRL+MAIUSC+-**| View.NavigateForward |
|Visualizzatore oggetti|**CTRL+ALT+J**| View.ObjectBrowser |
|Output|**CTRL+ALT+O**| View.Output |
|Finestra Proprietà|**F4**| View.PropertiesWindow |
|Aggiorna|**F5** [Team Explorer]| View.Refresh |
|Esplora server|**CTRL + ALT + S**| View.ServerExplorer |
|Mostra smart tag|**CTRL+.**<br /><br />o **MAIUSC+ALT+F10** [visualizzazione Progettazione editor HTML]| View.ShowSmartTag |
|Esplora soluzioni|**CTRL+ALT+L**| View.SolutionExplorer |
|Team Explorer di TFS|**\\CTRL+, CTRL+M**| View.TfsTeamExplorer |
|Casella degli strumenti|**CTRL+ALT+X**| View.Toolbox |
|Visualizzare il codice|**Immettere** [Diagramma classi]<br /><br />o **F7** [Impostazioni Designer]| View.ViewCode |
|Progettazione vista|**MAIUSC+F7** [Visualizzazione origine editor HTML]| View.ViewDesigner |

#### <a name="window-popular-shortcuts"></a><a name="bkmk_window-popular-shortcuts"></a> Finestra: scelte rapide comuni

|Comandi|Tasti di scelta rapida [contesti speciali]|ID comando|
|-|-|-|
|Attivare la finestra del documento|**ESC**| Window.ActivateDocumentWindow |
|Chiudere la finestra del documento|**CTRL+F4**| Window.CloseDocumentWindow |
|Finestra del documento successiva|**CTRL+F6**| Window.NextDocumentWindow |
|Spostamento successivo della finestra del documento|**CTRL+TAB**| Window.NextDocumentWindowNav |
|Riquadro di divisione successivo|**F6**| Window.NextSplitPane |


## <a name="global-shortcuts"></a>Tasti di scelta rapida globali

Questi tasti di scelta rapida sono *globali*, ovvero possono essere usati quando lo stato attivo si trova in qualsiasi finestra di Visual Studio.

- [Analizzare](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_analyze-global-shortcuts)
- [Architettura](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_architecture-global-shortcuts)
- [Azure](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_windowsazure-global-shortcuts)
- [Compila](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_build-global-shortcuts)
- [Menu di scelta rapida per Visualizzazione classi](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_classview-global-shortcuts)
- [Eseguire il debug](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_debug-global-shortcuts)
- [Menu di scelta rapida di debug](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_debugger-global-shortcuts)
- [Hub di diagnostica](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_diagnostics-global-shortcuts)
- [Modifica](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_edit-global-shortcuts)
- [Menu di scelta rapida dell'editor](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_editorContext-global-shortcuts)
- [File](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_file-global-shortcuts)
- [?](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_help-global-shortcuts)
- [Test di carico](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_loadtest-global-shortcuts)
- [Altri menu di scelta rapida](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_otherContext-global-shortcuts)
- [Progetto](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_project-global-shortcuts)
- [Menu di scelta rapida per progetti e soluzioni](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_projectContext-global-shortcuts)
- [Refactoring](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_refactor-global-shortcuts)
- [Esplora soluzioni](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_solutionexplorerGLOBAL)
- [Team](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_team-global-shortcuts)
- [Menu di scelta rapida per Team Foundation](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_TFcontext-global-shortcuts)
- [Test](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_test-global-shortcuts)
- [Esplora test](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_testexplorerGLOBAL)
- [Strumenti](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_tools-global-shortcuts)
- [Visualizzazione](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_view-global-shortcuts)
- [Window](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_window-global-shortcuts)

### <a name="analyze-global-shortcuts"></a><a name="bkmk_analyze-global-shortcuts"></a> Analizza: scelte rapide globali

|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Spostarsi all'indietro|**MAIUSC+ALT+3**| Analyze.NavigateBackward |
|Spostarsi in avanti|**MAIUSC+ALT+4**| Analyze.NavigateForward |

### <a name="architecture-global-shortcuts"></a><a name="bkmk_architecture-global-shortcuts"></a> Architettura: scelte rapide globali

|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Nuovo diagramma|**\\CTRL+, CTRL+N**| Architecture.NewDiagram |

### <a name="azure-global-shortcuts"></a><a name="bkmk_windowsazure-global-shortcuts"></a> Azure: scelte rapide globali

|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Ripetere l'operazione di script del servizio mobile|**CTRL+NUM, \* CTRL+R**| WindowsAzure.RetryMobileServiceScriptOperation |
|Visualizzare i dettagli dell'errore dello script del servizio mobile|**CTRL+NUM, \* CTRL+D**| WindowsAzure.ShowMobileServiceScriptErrorDetails |

### <a name="build-global-shortcuts"></a><a name="bkmk_build-global-shortcuts"></a> Compilazione: scelte rapide globali

|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Compila selezione|**CTRL+B** (Visual Studio 2019)| Build.BuildSelection |
|Compila soluzione|**CTRL+MAIUSC+B**| Build.BuildSolution |
|Annulla|**CTRL+INTERR**| Build.Cancel |
|Compilazione|**Ctrl+F7**| Build.Compile |
|Eseguire l'analisi del codice nella soluzione|**ALT+F11**| Build.RunCodeAnalysisonSolution |

### <a name="class-view-context-menus-global-shortcuts"></a><a name="bkmk_classview-global-shortcuts"></a> Visualizzazione classi di scelta rapida: scelte rapide globali

|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Proprietà|**ALT+INVIO**| ClassViewContextMenus.ClassViewMultiselectProjectreferencesItems.Properties |

### <a name="debug-global-shortcuts"></a><a name="bkmk_debug-global-shortcuts"></a> Debug: scelte rapide globali

|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Applicare modifiche al codice|**ALT+F10**| Debug.ApplyCodeChanges |
|Connettersi a un processo|**CTRL+ALT+P**| Debug.AttachtoProcess |
|Auto|**Ctrl+Alt+V, A**| Debug.Autos |
|Interrompere tutto|**CTRL+ALT+INTERR**| Debug.BreakAll |
|Punti di interruzione|**CTRL+ALT+B**| Debug.Breakpoints |
|Stack di chiamate|**CTRL+ALT+C**| Debug.CallStack |
|Eliminare tutti i punti di interruzione|**CTRL+MAIUSC+F9**| Debug.DeleteAllBreakpoints |
|Launch|**ALT+F2**| Debug.DiagnosticsHub.Launch |
|Disassembly|**CTRL+ALT+D**| Debug.Disassembly |
|Dom Explorer|**Ctrl+Alt+V, D**| Debug.DOMExplorer |
|Abilitare un punto di interruzione|**CTRL+F9**| Debug.EnableBreakpoint |
|Eccezioni|**CTRL+ALT+E**| Debug.Exceptions |
|Punto di interruzione della funzione|**CTRL+K, B** (Visual Studio 2019)<br />**CTRL+FRECCIA DESTRA** + **B** (Visual Studio 2017)| Debug.FunctionBreakpoint |
|Passare alla chiamata precedente o all'evento IntelliTrace|**Ctrl+Maiusc+F11**| Debug.GoToPreviousCallorIntelliTraceEvent |
|Avviare la diagnostica|**ALT+F5**| Debug.Graphics.StartDiagnostics |
|Immediato|**CTRL+ALT+I**| Debug.Immediate |
|Chiamate di IntelliTrace|**CTRL+ALT+Y, T**| Debug.IntelliTraceCalls |
|Eventi IntelliTrace|**CTRL+ALT+Y, F**| Debug.IntelliTraceEvents |
|Console JavaScript|**Ctrl+Alt+V, C**| Debug.JavaScriptConsole |
|Variabili locali|**Ctrl+Alt+V, L**| Debug.Locals |
|Combinazione di processi|**CTRL+5**| Debug.LocationToolbar.ProcessCombo |
|Combinazione di stack frame|**CTRL+7**| Debug.LocationToolbar.StackFrameCombo |
|Combinazione di thread|**CTRL+6**| Debug.LocationToolbar.ThreadCombo |
|Attiva/disattiva lo stato contrassegnato del thread corrente|**CTRL+8**| Debug.LocationToolbar.ToggleCurrentThreadFlaggedState |
|Attivare/disattivare i thread contrassegnati|**CTRL+9**| Debug.LocationToolbar.ToggleFlaggedThreads |
|Memoria 1|**CTRL+ALT+M, 1**| Debug.Memory1 |
|Memoria 2|**CTRL+ALT+M, 2**| Debug.Memory2 |
|Memoria 3|**CTRL+ALT+M, 3**| Debug.Memory3 |
|Memoria 4|**CTRL+ALT+M, 4**| Debug.Memory4 |
|Moduli|**CTRL+ALT+U**| Debug.Modules |
|Stack paralleli|**CTRL+MAIUSC+D, S**| Debug.ParallelStacks |
|Orologio parallelo 1|**CTRL+MAIUSC+D, 1**| Debug.ParallelWatch1 |
|Orologio parallelo 2|**CTRL+MAIUSC+D, 2**| Debug.ParallelWatch2 |
|Orologio parallelo 3|**CTRL+MAIUSC+D, 3**| Debug.ParallelWatch3 |
|Orologio parallelo 4|**CTRL+MAIUSC+D, 4**| Debug.ParallelWatch4 |
|Processi|**CTRL + ALT + Z**| Debug.Processes |
|Controllo rapido|**MAIUSC+F9** o **CTRL+ALT+Q**| Debug.QuickWatch |
|Riconllegare al processo|**MAIUSC+ALT+P**| Debug.ReattachtoProcess |
|Aggiornare windowsapp|**CTRL+MAIUSC+R**| Debug.RefreshWindowsapp |
|Registri|**CTRL+ALT+G**| Debug.Registers |
|Riavvia|**Ctrl+Maiusc+F5**| Debug.Restart |
|Esecuzione fino al cursore|**CTRL+F10**| Debug.RunToCursor |
|Impostare l'istruzione successiva|**Ctrl+Maiusc+F10**| Debug.SetNextStatement |
|Visualizzare lo stack di chiamate sulla mappa codice|**CTRL+MAIUSC+'**| Debug.ShowCallStackonCodeMap |
|Mostrare l'istruzione successiva|**ALT+NUM** *| Debug.ShowNextStatement |
|Avvio|**F5**| Debug.Start |
|Avviare l'analisi dell'applicazione Windows Phone|**ALT+F1**| Debug.StartWindowsPhoneApplicationAnalysis |
|Avviare senza eseguire il debug|**CTRL+F5**| Debug.StartWithoutDebugging |
|Eseguire l'istruzione|**F11**| Debug.StepInto |
|Eseguire un'istruzione nel processo corrente|**Ctrl+Alt+F11**| Debug.StepIntoCurrentProcess |
|Eseguire un'istruzione specifica|**MAIUSC+ALT+F11**| Debug.StepIntoSpecific |
|Uscire dall'istruzione/routine|**MAIUSC+F11**| Debug.StepOut |
|Uscire dal processo corrente|**CTRL+MAIUSC+ALT+F11**| Debug.StepOutCurrentProcess |
|Eseguire l'istruzione/routine|**F10** (durante il debug: esegue un'azione di passaggio)| Debug.StepOver |
|Eseguire l'istruzione/routine|**F10** (Quando non si esegue il debug: avvia il debug e si arresta nella prima riga di codice utente)| Debug.StepOver |
|Eseguire il passaggio del processo corrente|**Ctrl+Alt+F10**| Debug.SetpOverCurrentProcess |
|Arrestare l'esecuzione del debug|**MAIUSC+F5**| Debug.StopDebugging |
|Arrestare l'analisi delle prestazioni|**MAIUSC+ALT+F2**| Debug.StopPerformanceAnalysis |
|Attività|**CTRL+MAIUSC+D, K**| Debug.Tasks |
|Thread|**CTRL+ALT+H**| Debug.Threads |
|Impostare/rimuovere un punto di interruzione|**F9**| Debug.ToggleBreakpoint |
|Attivare/disattivare il disassembly|**CTRL+F11**| Debug.ToggleDisassembly |
|Espressione di controllo 1|**CTRL+ALT+W, 1**| Debug.Watch1 |
|Orologio 2|**CTRL+ALT+W, 2**| Debug.Watch2 |
|Orologio 3|**CTRL+ALT+W, 3**| Debug.Watch3 |
|Orologio 4|**CTRL+ALT+W, 4**| Debug.Watch4 |

### <a name="debugger-context-menus-global-shortcuts"></a><a name="bkmk_debugger-global-shortcuts"></a> Menu di scelta rapida del debugger: tasti di scelta rapida globali

|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Elimina|**Alt+F9, D**| DebuggerContextMenus.BreakpointsWindow.Delete |
|Passare a disassembly|**ALT+F9, A**| DebuggerContextMenus.BreakpointsWindow.GoToDisassembly |
|Passare al codice sorgente|**ALT+F9, S**| DebuggerContextMenus.BreakpointsWindow.GoToSourceCode |

### <a name="diagnostics-hub-global-shortcuts"></a><a name="bkmk_diagnostics-global-shortcuts"></a> Hub di diagnostica: tasti di scelta rapida globali

|Comando|Tasto di scelta rapida|ID comando|
|-|-|-|
|Arresta raccolta|**CTRL+ALT+F2**| DiagnosticsHub.StopCollection |

### <a name="edit-global-shortcuts"></a><a name="bkmk_edit-global-shortcuts"></a> Modifica: scelte rapide globali

|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Copia|**CTRL+C**<br /><br /> oppure<br /><br /> **CTRL+INS**| Edit.Copy |
|Taglia|**CTRL+X**<br /><br /> oppure<br /><br /> **MAIUSC+CANC**| Edit.Cut |
|Ciclo dell'anello degli Appunti|**CTRL+MAIUSC+V**<br /><br /> oppure<br /><br /> **CTRL+ MAIUSC+INS**| Edit.CycleClipboardRing |
|Elimina|**Elimina**| Edit.Delete |
|Duplicare|**CTRL+D**| Edit.Duplicate |
|Find|**CTRL+F**| Edit.Find |
|Trova tutti i riferimenti|**MAIUSC+F12**| Edit.FindAllReferences |
|Cercare nei file|**CTRL+MAIUSC+F**| Edit.FindinFiles |
|Trova successivo|**F3**| Edit.FindNext |
|Trova successivo selezionato|**CTRL+F3**| Edit.FindNextSelected |
|Trova precedente|**MAIUSC+F3**| Edit.FindPrevious |
|Trova i precedenti selezionati|**CTRL+MAIUSC+F3**| Edit.FindPreviousSelected |
|Generare un metodo|**CTRL+K, CTRL+M**| Edit.GenerateMethod |
|Passare a|**CTRL+G**| Edit.GoTo |
|Vai a tutti|**CTRL+,** o **CTRL+T**| Edit.GoToAll |
|Vai alla dichiarazione|**Ctrl+F12**| Edit.GoToDeclaration |
|Vai alla definizione|**F12**| Edit.GoToDefinition |
|Vai al membro|**CTRL+1, CTRL+M** o **CTRL+1, M** o **ALT+\\**| Edit.GoToMember |
|Passare al percorso successivo|**F8** (errore successivo nella finestra Elenco errori o Output)| Edit.GoToNextLocation |
|Passare alla posizione precedente|**MAIUSC+F8** (errore precedente nella finestra Elenco errori o Output)| Edit.GoToPrevLocation |
|Inserire un frammento di codice|**Ctrl+K, Ctrl+X**| Edit.InsertSnippet |
|Spostare il controllo verso il basso|**CTRL+FRECCIA GIÙ**| Edit.MoveControlDown |
|Spostare il controllo nella griglia verso il basso|**Freccia GIÙ**| Edit.MoveControlDownGrid |
|Spostare il controllo a sinistra|**CTRL+FRECCIA SINISTRA**| Edit.MoveControlLeft |
|Spostare il controllo a sinistra della griglia|**Freccia SINISTRA**| Edit.MoveControlLeftGrid |
|Spostare il controllo a destra|**CTRL+FRECCIA DESTRA**| Edit.MoveControlRight |
|Spostare la griglia a destra del controllo|**Freccia DESTRA**| Edit.MoveControlRightGrid |
|Spostare il controllo verso l'alto|**CTRL+FRECCIA SU**| Edit.MoveControlUp |
|Spostare il controllo verso l'alto nella griglia|**Freccia SU**| Edit.MoveControlUpGrid |
|Segnalibro successivo|**Ctrl+K, Ctrl+N**| Edit.NextBookmark |
|Segnalibro successivo nella cartella|**CTRL+MAIUSC+K, CTRL+MAIUSC+N**| Edit.NextBookmarkInFolder |
|Aprire il file|**CTRL+MAIUSC+G** (apre il nome di file in corrispondenza del cursore)| Edit.OpenFile |
|Incolla|**CTRL+V**<br /><br /> oppure<br /><br /> **MAIUSC+INS**| Edit.Paste |
|Segnalibro precedente|**Ctrl+K, Ctrl+P**| Edit.PreviousBookmark |
|Segnalibro precedente nella cartella|**CTRL+MAIUSC+K, CTRL+MAIUSC+P**| Edit.PreviousBookmarkInFolder |
|Simbolo di ricerca rapida|**MAIUSC+ALT+F12**| Edit.QuickFindSymbol |
|Ripeti|**CTRL+Y**<br /><br /> oppure<br /><br /> **CTRL+MAIUSC+Z**<br /><br /> oppure<br /><br /> **MAIUSC+ALT+BACKSPACE**| Edit.Redo |
|Aggiornare i riferimenti remoti|**CTRL+MAIUSC+J**| Edit.RefreshRemoteReferences |
|Sostituisci|**CTRL+H**| Edit.Replace |
|Sostituisci nei file|**CTRL+MAIUSC+H**| Edit.ReplaceinFiles |
|Seleziona tutto|**CTRL+A**| Edit.SelectAll |
|Selezionare il controllo successivo|**TAB**| Edit.SelectNextControl |
|Selezionare il controllo precedente|**MAIUSC+TAB**| Edit.SelectPreviousControl |
|Mostra griglia riquadri|**INVIO**| Edit.ShowTileGrid |
|Controllo delle dimensioni in basso|**CTRL+MAIUSC+Freccia GIÙ**| Edit.SizeControlDown |
|Controllo delle dimensioni nella griglia verso il basso|**MAIUSC+Freccia GIÙ**| Edit.SizeControlDownGrid |
|Controllo delle dimensioni a sinistra|**CTRL+MAIUSC+Freccia SINISTRA**| Edit.SizeControlLeft |
|Controllo dimensioni griglia sinistra|**MAIUSC+Freccia SINISTRA**| Edit.SizeControlLeftGrid |
|Controllo delle dimensioni a destra|**CTRL+MAIUSC+Freccia DESTRA**| Edit.SizeControlRight |
|Griglia destra del controllo Dimensioni|**MAIUSC+Freccia DESTRA**| Edit.SizeControlRightGrid |
|Controllo delle dimensioni in alto|**CTRL+MAIUSC+freccia SU**| Edit.SizeControlUp |
|Controllo delle dimensioni nella griglia in alto|**MAIUSC+Freccia SU**| Edit.SizeControlUpGrid |
|Arrestare la ricerca|**Alt+F3, S**| Edit.StopSearch |
|Racchiudere tra|**Ctrl+K, Ctrl+S**| Edit.SurroundWith |
|Annulla|**CTRL+Z**<br /><br /> oppure<br /><br /> **ALT+BACKSPACE**| Edit.Undo |

### <a name="editor-context-menus-global-shortcuts"></a><a name="bkmk_editorContext-global-shortcuts"></a> Menu di scelta rapida dell'editor: scelte rapide globali

|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Condizioni punto di interruzione|**Alt+F9, C**| EditorContextMenus.CodeWindow.Breakpoint.BreakpointConditions |
|Modificare le etichette dei punti di interruzione|**Alt+F9, L**| EditorContextMenus.CodeWindow.Breakpoint.BreakpointEditlabels |
|Inserire un punto di interruzione temporaneo|**MAIUSC+ALT+F9, T**| EditorContextMenus.CodeWindow.Breakpoint.InsertTemporaryBreakpoint |
|Mostra elemento|**CTRL+'**| EditorContextMenus.CodeWindow.CodeMap.ShowItem |
|Execute|**CTRL+Alt+F5**| EditorContextMenus.CodeWindow.Execute |
|Vai alla visualizzazione|**CTRL+M, CTRL+G**| EditorContextMenus.CodeWindow.GoToView |
|Attivare/disattivare il file di codice di intestazione|**CTRL+K, CTRL+O** (lettera "O")| EditorContextMenus.CodeWindow.ToggleHeaderCodeFile |
|Visualizzare la gerarchia di chiamata|**CTRL+K, CTRL+T**<br /><br /> oppure<br /><br /> **CTRL+K, S**| EditorContextMenus.CodeWindow.ViewCallHierarchy |

### <a name="file-global-shortcuts"></a><a name="bkmk_file-global-shortcuts"></a> File: collegamenti globali

|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Esci|**ALT+F4**| File.Exit |
|Nuovo file|**CTRL+N**| File.NewFile |
|Nuovo progetto|**CTRL+MAIUSC+N**| File.NewProject |
|Nuovo sito Web|**MAIUSC+ALT+N**| File.NewWebSite |
|Aprire il file|**CTRL+O** (lettera "O")| File.OpenFile |
|Aprire il progetto|**CTRL+MAIUSC+O** (lettera "O")| File.OpenProject |
|Aprire il sito Web|**MAIUSC+ALT+O** (lettera "O")| File.OpenWebSite |
|Stampa|**CTRL+P**| File.Print |
|Salvare tutto|**CTRL+MAIUSC+S**| File.SaveAll |
|Salvare gli elementi selezionati|**CTRL+S**| File.SaveSelectedItems |
|Visualizzare nel browser|**CTRL+MAIUSC+W**| File.ViewinBrowser |

### <a name="help-global-shortcuts"></a><a name="bkmk_help-global-shortcuts"></a> Guida: scelte rapide globali

|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Aggiungere e rimuovere il contenuto della Guida|**CTRL+ALT+F1**| Help.AddandRemoveHelpContent |
|Guida sensibile al contesto|**F1**| Help.F1Help |
|Visualizzare la Guida|**CTRL+F1**| Help.ViewHelp |
|Guida di Windows|**MAIUSC+F1**| Help.WindowHelp |

### <a name="load-test-global-shortcuts"></a><a name="bkmk_loadtest-global-shortcuts"></a> Test di carico: tasti di scelta rapida globali

|Comando|Tasto di scelta rapida|ID comando|
|-|-|-|
|Passare al riquadro contatore|**CTRL+R, Q**| LoadTest.JumpToCounterPane |

### <a name="other-context-menus-global-shortcuts"></a><a name="bkmk_otherContext-global-shortcuts"></a> Altri menu di scelta rapida: tasti di scelta rapida globali

|Comando|Tasto di scelta rapida|ID comando|
|-|-|-|
|Aggiungere un nuovo diagramma|**Inserimento**| OtherContextMenus.MicrosoftDataEntityDesignContext.AddNewDiagram |

### <a name="project-global-shortcuts"></a><a name="bkmk_project-global-shortcuts"></a>Project: scelte rapide globali

|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Aggiungere un elemento esistente|**MAIUSC+ALT+A**| Project.AddExistingItem |
|Aggiungere un nuovo elemento|**CTRL+MAIUSC+A**| Project.AddNewItem |
|Creazione guidata classe|**CTRL+ MAIUSC+X**| Project.ClassWizard |
|Sostituisci|**CTRL+ALT+INS**| Project.Override |
|Anteprima modifiche|**ALT+;** quindi **ALT+C**| Project.Previewchanges |
|Pubblicare i file selezionati|**ALT+;** quindi **ALT+P**| Project.Publishselectedfiles |
|Sostituire i file selezionati dal server|**ALT+;** quindi **ALT+R**| Project.Replaceselectedfilesfromserver |

### <a name="project-and-solution-context-menus-global-shortcuts"></a><a name="bkmk_projectContext-global-shortcuts"></a>Project menu di scelta rapida e soluzione: tasti di scelta rapida globali

|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Sposta giù|**ALT+freccia GIÙ**| ProjectandSolutionContextMenus.Item.MoveDown |
|Sposta su|**ALT+freccia SU**| ProjectandSolutionContextMenus.Item.MoveUp |

### <a name="refactor-global-shortcuts"></a><a name="bkmk_refactor-global-shortcuts"></a> Refactoring: scelte rapide globali

|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Incapsula campo|**CTRL+R, CTRL+E**| Refactor.EncapsulateField |
|Estrarre l'interfaccia|**CTRL+R, CTRL+I**| Refactor.ExtractInterface |
|Estrai metodo|**CTRL+R, CTRL+M**| Refactor.ExtractMethod |
|Rimuovere i parametri|**CTRL+R, CTRL+V**| Refactor.RemoveParameters |
|Rinominare|**CTRL+R, CTRL+R**| Refactor.Rename |
|Riordinare i parametri|**CTRL+R, CTRL+O** (lettera "O")| Refactor.ReorderParameters |

### <a name="solution-explorer-global-shortcuts"></a><a name="bkmk_solutionexplorerGLOBAL"></a> Esplora soluzioni: scelte rapide globali

|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Filtro apri file|**CTRL+[**, **O** (lettera "O")<br /><br /> oppure<br /><br /> **CTRL+[**, **CTRL+O** (lettera "O")| SolutionExplorer.OpenFilesFilter |
|Filtro modifiche in sospeso|**CTRL+[**, **P**<br /><br /> oppure<br /><br /> **CTRL+[**, **CTRL+P**| SolutionExplorer.PendingChangesFilter |
|Sincronizzare con il documento attivo|**CTRL+[**, **S**<br /><br /> oppure<br /><br /> **CTRL+[**, **CTRL+S**| SolutionExplorer.SyncWithActiveDocument |

### <a name="team-global-shortcuts"></a><a name="bkmk_team-global-shortcuts"></a> Team: scelte rapide globali

|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Passare ai rami Git|**CTRL+0** (zero), **CTRL+N**<br /><br /> oppure<br /><br /> **CTRL+0, N**| Team.Git.GoToGitBranches |
|Passare alle modifiche di Git|**CTRL+0** (zero), **CTRL+G**<br /><br /> oppure<br /><br /> **CTRL+0, G**| Team.Git.GoToGitChanges |
|Passare ai commit Git|**CTRL+0**, **CTRL+O** (lettera "O")<br /><br /> oppure<br /><br /> **Ctrl+0, O**| Team.Git.GoToGitCommits |
|Ricerca in Team Explorer|**CTRL+'**| Team.TeamExplorerSearch |

### <a name="team-foundation-context-menus-global-shortcuts"></a><a name="bkmk_TFcontext-global-shortcuts"></a> Menu di scelta rapida di Team Foundation: scelte rapide globali

|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Passare alle compilazioni|**CTRL+0** (zero), **CTRL+B**<br /><br /> oppure<br /><br /> **Ctrl+0, B**| TeamFoundationContextMenus.Commands.GoToBuilds |
|Passare alla connessione|**CTRL+0** (zero), **CTRL+C**<br /><br /> oppure<br /><br /> **CTRL+0, C**| TeamFoundationContextMenus.Commands.GoToConnect |
|Passare ai documenti|**CTRL+0** (zero), **CTRL+D**<br /><br /> oppure<br /><br /> **CTRL+0, D**| TeamFoundationContextMenus.Commands.GoToDocuments |
|Vai a home page|**CTRL+0** (zero), **CTRL+H**<br /><br /> oppure<br /><br /> **CTRL+0, H**| TeamFoundationContextMenus.Commands.GoToHome |
|Vai al mio lavoro|**CTRL+0** (zero), **CTRL+M**<br /><br /> oppure<br /><br /> **CTRL+0, M**| TeamFoundationContextMenus.Commands.GoToMyWork |
|Passare alle modifiche in sospeso|**CTRL+0** (zero), **CTRL+P**<br /><br /> oppure<br /><br /> **Ctrl+0, P**| TeamFoundationContextMenus.Commands.GoToPendingChanges |
|Passare ai report|**CTRL+0** (zero), **CTRL+R**<br /><br /> oppure<br /><br /> **CTRL+0, R**| TeamFoundationContextMenus.Commands.GoToReports |
|Passare alle impostazioni|**CTRL+0** (zero), **CTRL+S**<br /><br /> oppure<br /><br /> **CTRL+0, S**| TeamFoundationContextMenus.Commands.GoToSettings |
|Passare all'accesso Web|**CTRL+0** (zero), **CTRL+A**<br /><br /> oppure<br /><br /> **CTRL+0, A**| TeamFoundationContextMenus.Commands.GoToWebAccess |
|Passare agli elementi di lavoro|**CTRL+0** (zero), **CTRL+W**<br /><br /> oppure<br /><br /> **CTRL+0, W**| TeamFoundationContextMenus.Commands.GoToWorkItems |

### <a name="test-global-shortcuts"></a><a name="bkmk_test-global-shortcuts"></a> Test: scelte rapide globali

|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Usare il generatore di test codificati dell'interfaccia utente|**\\CTRL+, CTRL+C**| Test.UseCodedUITestBuilder |
|Usare la registrazione delle azioni esistente|**\\CTRL+, CTRL+A**| Test.UseExistingActionRecording |

### <a name="test-explorer-global-shortcuts"></a><a name="bkmk_testexplorerGLOBAL"></a> Esplora test: tasti di scelta rapida globali

|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Eseguire il debug di tutti i test|**CTRL+R, CTRL+A**| TestExplorer.DebugAllTests |
|Eseguire il debug di tutti i test nel contesto|**Ctrl+R, Ctrl+T**| TestExplorer.DebugAllTestsInContext |
|Eseguire il debug dell'ultima esecuzione|**Ctrl+R, D**| TestExplorer.DebugLastRun |
|Ripetere l'ultima esecuzione|**Ctrl+R, L**| TestExplorer.RepeatLastRun |
|Eseguire tutti i test|**Ctrl+R, A**| TestExplorer.RunAllTests |
|Eseguire tutti i test nel contesto|**Ctrl+R, T**| TestExplorer.RunAllTestsInContext |
|Mostra Esplora test|**Ctrl+E, T**| TestExplorer.ShowTestExplorer |
|Scheda Apri|**Ctrl+E, L**| LiveUnitTesting.OpenTab |
|Risultati Code coverage|**CTRL+E, C**| Test.CodeCoverageResults |

### <a name="tools-global-shortcuts"></a><a name="bkmk_tools-global-shortcuts"></a> Strumenti: scelte rapide globali

|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Associa a processo|**CTRL+ALT+P**| Tools.AttachtoProcess |
|Gestione frammenti di codice|**Ctrl+K, Ctrl+B**| Tools.CodeSnippetsManager |
|Forza gc|**CTRL+MAIUSC+ALT+F12, CTRL+MAIUSC+ALT+F12**| Tools.ForceGC |

### <a name="view-global-shortcuts"></a><a name="bkmk_view-global-shortcuts"></a> Visualizza: scelte rapide globali

|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Tutte le finestre|**MAIUSC+ALT+M**| View.AllWindows |
|Esplora architettura|**\\CTRL+, CTRL+R**| View.ArchitectureExplorer |
|indietro|**ALT+freccia SINISTRA** (funziona in modo diverso da View.NavigateBackward nell'Editor di testo)| View.Backward |
|Finestra Segnalibro|**Ctrl+K, Ctrl+W**| View.BookmarkWindow |
|Sfoglia successivo|**CTRL+MAIUSC+1**| View.BrowseNext |
|Sfoglia precedente|**CTRL+MAIUSC+2**| View.BrowsePrevious |
|Gerarchia di chiamata|**CTRL+ALT+K**| View.CallHierarchy |
|Visualizzazione classi|**CTRL+MAIUSC+C**| View.ClassView |
|Visualizzazione classi vai alla casella combinata di ricerca|**CTRL+K, CTRL+V**| View.ClassViewGoToSearchCombo |
|Finestra di definizione del codice|**Ctrl+ \\ , D**<br /><br /> oppure<br /><br /> **\\CTRL+, CTRL+D**| View.CodeDefinitionWindow |
|Finestra di comando|**CTRL+ALT+A**| View.CommandWindow |
|Origini dati|**MAIUSC+ALT+D**| View.DataSources |
|Struttura del documento|**CTRL+ALT+T**| View.DocumentOutline |
|Modificare l'etichetta|**F2**| View.EditLabel |
|Elenco errori|**Ctrl+ \\ , E**<br /><br /> oppure<br /><br /> **\\CTRL+, CTRL+E**| View.ErrorList |
|F# Interactive|**CTRL+ALT+F**| View.F#Interactive |
|Trovare i risultati dei simboli|**Ctrl+Alt+F12**| View.FindSymbolResults |
|Inoltra|**ALT + freccia destra** (funzioni in modo diverso dai View.NavigateForward nell'Editor di testo)| View.Forward |
|Torna a definizione|**CTRL+MAIUSC+7**| View.ForwardBrowseContext |
|Schermo intero|**MAIUSC+ALT+INVIO**| View.FullScreen |
|Spostarsi all'indietro|**CTRL+-**| View.NavigateBackward |
|Spostarsi in avanti|**CTRL+MAIUSC+-**| View.NavigateForward |
|Errore successivo|**CTRL+MAIUSC+F12**| View.NextError |
|Notifiche|**CTRL+W, N**<br /><br /> oppure<br /><br /> **CTRL+W, CTRL+N**| View.Notifications |
|Visualizzatore oggetti|**CTRL+ALT+J**| View.ObjectBrowser |
|Visualizzatore oggetti vai alla casella combinata di ricerca|**CTRL+K, CTRL+R**| View.ObjectBrowserGoToSearchCombo |
|Output|**CTRL+ALT+O** (lettera "O")| View.Output |
|Contesto di esplorazione popup|**CTRL+MAIUSC+8** (solo C++)| View.PopBrowseContext |
|Finestra Proprietà|**F4**| View.PropertiesWindow |
|pagine delle proprietà|**MAIUSC+F4**| View.PropertyPages |
|Visualizzazione delle risorse|**CTRL+MAIUSC+E**| View.ResourceView |
|Esplora server|**CTRL + ALT + S**| View.ServerExplorer |
|Mostra smart tag|**MAIUSC+ALT+F10**<br /><br /> oppure<br /><br /> **CTRL+.**| View.ShowSmartTag |
|Esplora soluzioni|**CTRL+ALT+L**| View.SolutionExplorer |
|SQL esplora oggetti server|**\\CTRL+, CTRL+S**| View.SQLServerObjectExplorer |
|Elenco attività|**Ctrl+ \\ , T**<br /><br /> oppure<br /><br /> **\\CTRL+, CTRL+T**| View.TaskList |
|Team Explorer di TFS|**\\CTRL+, CTRL+M**| View.TfsTeamExplorer |
|Casella degli strumenti|**CTRL+ALT+X**| View.Toolbox |
|Esplora modelli UML|**\\CTRL+, CTRL+U**| View.UMLModelExplorer |
|Visualizzare il codice|**F7**| View.ViewCode |
|Progettazione vista|**MAIUSC+F7**| View.ViewDesigner |
|Web browser|**CTRL+ALT+R**| View.WebBrowser |
|Zoom avanti|**CTRL+MAIUSC+.**| View.ZoomIn |
|Zoom indietro|**CTRL+MAIUSC+,**| View.ZoomOut |
|Mostra Esplora test|**Ctrl+E, T**| TestExplorer.ShowTestExplorer |

### <a name="window-global-shortcuts"></a><a name="bkmk_window-global-shortcuts"></a> Finestra: scelte rapide globali

|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Attivare la finestra del documento|**ESC**| Window.ActivateDocumentWindow |
|Aggiungi scheda alla selezione|**CTRL+MAIUSC+ALT+BARRA SPAZIATRICE**| Window.AddTabtoSelection |
|Chiudere la finestra del documento|**CTRL+F4**| Window.CloseDocumentWindow |
|Chiudere la finestra degli strumenti|**MAIUSC+ESC**| Window.CloseToolWindow |
|Mantenere aperta la scheda|**CTRL+ALT+HOME**| Window.KeepTabOpen |
|Passare alla barra di spostamento|**CTRL+F2**| Window.MovetoNavigationBar |
|Finestra del documento successiva|**CTRL+F6**| Window.NextDocumentWindow |
|Spostamento successivo della finestra del documento|**CTRL+TAB**| Window.NextDocumentWindowNav |
|Riquadro successivo|**ALT+F6**| Window.NextPane |
|Riquadro di divisione successivo|**F6**| Window.NextSplitPane |
|Scheda successiva|**CTRL+ALT+PGGIÙ**<br /><br /> oppure<br /><br /> **Ctrl+PgDn**| Window.NextTab |
|Scheda Avanti e aggiungi alla selezione|**CTRL+MAIUSC+ALT+PGGIÙ**| Window.NextTabandAddtoSelection |
|Spostamento successivo della finestra degli strumenti|**ALT+F7**| Window.NextToolWindowNav |
|Finestra del documento precedente|**CTRL+MAIUSC+F6**| Window.PreviousDocumentWindow |
|Spostamento della finestra del documento precedente|**CTRL+MAIUSC+TAB**| Window.PreviousDocumentWindowNav |
|Riquadro precedente|**MAIUSC+ALT+F6**| Window.PreviousPane |
|Riquadro di divisione precedente|**MAIUSC+F6**| Window.PreviousSplitPane |
|Scheda precedente|**CTRL+ALT+PGSU**<br /><br /> oppure<br /><br /> **CTRL+PGSU**| Window.PreviousTab |
|Scheda precedente e aggiunta alla selezione|**CTRL+MAIUSC+ALT+PGSU**| Window.PreviousTabandAddtoSelection |
|Spostamento della finestra degli strumenti precedente|**MAIUSC+ALT+F7**| Window.PreviousToolWindowNav |
|Avvio rapido|**Ctrl+Q**| Window.QuickLaunch |
|Categoria precedente avvio veloce|**CTRL+MAIUSC+Q**| Window.QuickLaunchPreviousCategory |
|Mostra menu ancoraggio|**ALT+-**| Window.ShowDockMenu |
|Visualizzare l'elenco di file Ex MDI|**CTRL+ALT+Freccia GIÙ**| Window.ShowEzMDIFileList |
|Ricerca in Esplora soluzioni|**CTRL+;**| Window.SolutionExplorerSearch |
|Ricerca di finestre|**ALT+'**| Window.WindowSearch |

## <a name="context-specific-shortcuts"></a>Tasti di scelta rapida specifici del contesto
Questi tasti di scelta rapida sono specifici del contesto, il che significa che è possibile usarli con menu ed elementi in Visual Studio specifici per un tipo di progetto, un linguaggio di programmazione o una piattaforma.

- [ADO.NET Entity Data Model Designer](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_adonet-entity-data-model-designer-context-specific-shortcuts)
- [Diagramma classi](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_class-diagram-context-specific-shortcuts)
- [Editor di test codificati dell'interfaccia utente](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_coded-ui-test-editor-context-specific-shortcuts)
- [Editor set di dati](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_dataset-editor-context-specific-shortcuts)
- [Visualizzatore differenze](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_difference-viewer-context-specific-shortcuts)
- [DOM Explorer](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_dom-explorer-context-specific-shortcuts)
- [F# Interactive](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_f-interactive-context-specific-shortcuts)
- [Editor di documento grafico](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_graph-document-editor-context-specific-shortcuts)
- [Diagnostica della grafica](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_graphics-diagnostics-context-specific-shortcuts)
- [Editor HTML](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_html-editor-context-specific-shortcuts)
- [Visualizzazione Progettazione editor HTML](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_html-editor-design-view-context-specific-shortcuts)
- [Visualizzazione origine editor HTML](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_html-editor-source-view-context-specific-shortcuts)
- [Diagramma livello](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_layer-diagram-context-specific-shortcuts)
- [Editor risorse gestite](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_managed-resources-editor-context-specific-shortcuts)
- [Finestra editor merge](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_merge-editor-window-context-specific-shortcuts)
- [Microsoft SQL Server Data Tools, confronto schema](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_microsoft-sql-server-data-tools-schema-compare-context-specific-shortcuts)
- [Microsoft SQL Server Strumenti dati, Progettazione tabelle](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_microsoft-sql-server-data-tools-table-designer-context-specific-shortcuts)
- [Microsoft SQL Server Strumenti dati, editor di SQL T](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_microsoft-sql-server-data-tools-t-sql-editor-context-specific-shortcuts)
- [Microsoft SQL Server Strumenti dati, editor T-SQL PDW](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_microsoft-sql-server-data-tools-t-sql-pdw-editor-context-specific-shortcuts)
- [Controllo pagina](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_page-inspector-context-specific-shortcuts)
- [Progettazione query](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_query-designer-context-specific-shortcuts)
- [Risultati query](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_query-results-context-specific-shortcuts)
- [Progettazione report](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_report-designer-context-specific-shortcuts)
- [Diagramma sequenza](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_sequence-diagram-context-specific-shortcuts)
- [Impostazioni Designer](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_settings-designer-context-specific-shortcuts)
- [Esplora soluzioni](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_solution-explorer-context-specific-shortcuts)
- [Team Explorer](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_team-explorer-context-specific-shortcuts)
- [Esplora test](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_test-explorer-context-specific-shortcuts)
- [Editor di testo](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_text-editor-context-specific-shortcuts)
- [Diagramma di attività UML](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_uml-activity-diagram-context-specific-shortcuts)
- [Diagramma classi UML](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_uml-class-diagram-context-specific-shortcuts)
- [Diagramma dei componenti UML](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_uml-component-diagram-context-specific-shortcuts)
- [Diagramma caso di utilizzo UML](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_uml-use-case-diagram-context-specific-shortcuts)
- [Editor tasti di scelta rapida VC](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_vc-accelerator-editor-context-specific-shortcuts)
- [Editor finestre di VC](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_vc-dialog-editor-context-specific-shortcuts)
- [Editor di immagini di VC](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_vc-image-editor-context-specific-shortcuts)
- [Editor stringhe di VC](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_vc-string-editor-context-specific-shortcuts)
- [Progettazione viste](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_view-designer-context-specific-shortcuts)
- [Visual Studio](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_visual-studio-context-specific-shortcuts)
- [Progettazione Windows Form](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_windows-forms-designer-context-specific-shortcuts)
- [Editor elementi di lavoro](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_work-item-editor-context-specific-shortcuts)
- [Elemento di lavoro visualizzazione Query](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_work-item-query-view-context-specific-shortcuts)
- [Visualizzazione risultati elementi di lavoro](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_work-item-results-view-context-specific-shortcuts)
- [Progettazione flussi di lavoro](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_workflow-designer-context-specific-shortcuts)
- [Finestra di progettazione dell'interfaccia utente XAML](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_xaml-ui-designer-context-specific-shortcuts)
- [Editor XML (testo)](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_xml-text-editor-context-specific-shortcuts)
- [Progettazione XML Schema](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_xml-schema-designer-context-specific-shortcuts)

### <a name="adonet-entity-data-model-designer-context-specific-shortcuts"></a><a name="bkmk_adonet-entity-data-model-designer-context-specific-shortcuts"></a>ADO.NET Entity Data Model progettazione: tasti di scelta rapida specifici del contesto

I tasti di scelta rapida specifici per questo contesto sono:

|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Giù|**ALT+Freccia GIÙ**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Down |
|Down 5|**ALT+PGGIÙ**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Down5 |
|Verso il basso|**ALT+FINE**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.ToBottom |
|Verso l'alto|**ALT+Home**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.ToTop |
|Su|**ALT+freccia SU**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Up |
|Fino a 5|**ALT+PGSU**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Up5 |
|Rinominare|**CTRL+R, R**| OtherContextMenus.MicrosoftDataEntityDesignContext.Refactor.Rename |
|Rimuovi da diagramma|**MAIUSC+CANC**| OtherContextMenus.MicrosoftDataEntityDesignContext.RemovefromDiagram |
|Browser entity data model|**CTRL+1**| View.EntityDataModelBrowser |
|Dettagli del mapping di Entity Data Model|**CTRL+2**| View.EntityDataModelMappingDetails |

### <a name="class-diagram-context-specific-shortcuts"></a><a name="bkmk_class-diagram-context-specific-shortcuts"></a> Diagramma classi: tasti di scelta rapida specifici del contesto

I tasti di scelta rapida specifici per questo contesto sono:


|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Comprimi|**Num -**| ClassDiagram.Collapse |
|Espandere|**NUM +**| ClassDiagram.Expand |
|Elimina|**CTRL+CANC**| Edit.Delete |
|Espandere l'elenco dei tipi di base compressi|**MAIUSC+ALT+B**| Edit.ExpandCollapseBaseTypeList |
|Passare a lollipop|**MAIUSC+ALT+L**| Edit.NavigateToLollipop |
|Rimuovi da diagramma|**Elimina**| Edit.RemovefromDiagram |
|Visualizzare il codice|**INVIO**| View.ViewCode |

### <a name="coded-ui-test-editor-context-specific-shortcuts"></a><a name="bkmk_coded-ui-test-editor-context-specific-shortcuts"></a> Editor di test codificati dell'interfaccia utente: tasti di scelta rapida specifici del contesto

I tasti di scelta rapida specifici per questo contesto sono:


|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Copiare il riferimento negli Appunti|**CTRL+C**| OtherContextMenus.UITestEditorContextMenu.CopyReferencetoClipboard |
|Ritardo inserimento prima|**CTRL+ALT+D**| OtherContextMenus.UITestEditorContextMenu.InsertDelayBefore |
|Individua tutto|**MAIUSC+ALT+L**| OtherContextMenus.UITestEditorContextMenu.LocateAll |
|Individuare il controllo dell'interfaccia utente|**CTRL+MAIUSC+L**| OtherContextMenus.UITestEditorContextMenu.LocatetheUIControl |
|Spostare il codice|**CTRL+ALT+C**| OtherContextMenus.UITestEditorContextMenu.Movecode |
|Dividere in un nuovo metodo|**CTRL+MAIUSC+T**| OtherContextMenus.UITestEditorContextMenu.Splitintoanewmethod |

### <a name="dataset-editor-context-specific-shortcuts"></a><a name="bkmk_dataset-editor-context-specific-shortcuts"></a> Editor DataSet: tasti di scelta rapida specifici del contesto

I tasti di scelta rapida specifici per questo contesto sono:


|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Inserisci colonna|**Inserimento**| OtherContextMenus.ColumnContext.InsertColumn |
|Colonna|**CTRL+L**| OtherContextMenus.DbTableContext.Add.Column |

### <a name="difference-viewer-context-specific-shortcuts"></a><a name="bkmk_difference-viewer-context-specific-shortcuts"></a> Visualizzatore differenze: tasti di scelta rapida specifici del contesto

I tasti di scelta rapida specifici per questo contesto sono:


|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Ignora taglia spazi vuoti|**\\CTRL+, CTRL+BARRA SPAZIATRICE**| Diff.IgnoreTrimWhitespace |
|Visualizzazione inline|**\\CTRL+, CTRL+1**| Diff.InlineView |
|Visualizzazione solo a sinistra|**\\CTRL+, CTRL+3**| Diff.LeftOnlyView |
|Differenza successiva|**F8**| Diff.NextDifference |
|Differenza precedente|**MAIUSC+F8**| Diff.PreviousDifference |
|Visualizzazione solo a destra|**\\CTRL+, CTRL+4**| Diff.RightOnlyView |
|Visualizzazione affiancata|**\\CTRL+, CTRL+2**| Diff.SideBySideView |
|Passare da sinistra a destra e da sinistra a destra|**\\CTRL+, CTRL+TAB**| Diff.SwitchBetweenLeftAndRight |
|Interruttore Sincronizza visualizzazione|**\\CTRL+, CTRL+freccia GIÙ**| Diff.SynchronizeViewToggle |
|Aggiungi commento|**CTRL+MAIUSC+K**| EditorContextMenus.CodeWindow.AddComment |
|Modificare il file locale|**CTRL+MAIUSC+P**| EditorContextMenus.CodeWindow.EditLocalFile |

### <a name="dom-explorer-context-specific-shortcuts"></a><a name="bkmk_dom-explorer-context-specific-shortcuts"></a> DOM Explorer: scelte rapide specifiche del contesto

I tasti di scelta rapida specifici per questo contesto sono:


|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Aggiorna|**F5**| DOMExplorer.Refresh |
|Seleziona elemento|**CTRL+B**| DOMExplorer.SelectElement |
|Mostra layout|**CTRL+MAIUSC+I**| DOMExplorer.ShowLayout |

### <a name="f-interactive-context-specific-shortcuts"></a><a name="bkmk_f-interactive-context-specific-shortcuts"></a> F# Interactive: scelte rapide specifiche del contesto

I tasti di scelta rapida specifici per questo contesto sono:


|Comando|Tasto di scelta rapida|ID comando|
|-|-|-|
|Annullare la valutazione interattiva|**CTRL+INTERR**| OtherContextMenus.FSIConsoleContext.CancelInteractiveEvaluation |

### <a name="graph-document-editor-context-specific-shortcuts"></a><a name="bkmk_graph-document-editor-context-specific-shortcuts"></a>Graph Editor documenti: scelte rapide specifiche del contesto

I tasti di scelta rapida specifici per questo contesto sono:


|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Aggiungere un nodo|**Inserimento**| ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Add.AddNode |
|Entrambe le dipendenze|**B**| ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Select.BothDependencies |
|Dipendenze in ingresso|**I**| ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Select.IncomingDependencies |
|Dipendenze in uscita|**O**| ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Select.OutgoingDependencies |
|Nuovo commento|**CTRL+MAIUSC+K**<br /><br /> oppure<br /><br /> **CTRL+E, C**| ArchitectureContextMenus.DirectedGraphContextMenu.NewComment |
|Rimuovi|**Elimina**| ArchitectureContextMenus.DirectedGraphContextMenu.Remove |
|Rinominare|**F2**| ArchitectureContextMenus.DirectedGraphContextMenu.Rename |

### <a name="graphics-diagnostics-context-specific-shortcuts"></a><a name="bkmk_graphics-diagnostics-context-specific-shortcuts"></a> Diagnostica della grafica: scelte rapide specifiche del contesto

I tasti di scelta rapida specifici per questo contesto sono:


|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Frame di acquisizione|Nessuno| Debug.Graphics.CaptureFrame |
|Spostare la selezione dei pixel verso il basso|**MAIUSC+ALT+Freccia GIÙ**| Graphics.MovePixelSelectionDown |
|Sposta selezione pixel a sinistra|**MAIUSC+ALT+Freccia SINISTRA**| Graphics.MovePixelSelectionLeft |
|Sposta selezione pixel a destra|**MAIUSC+ALT+Freccia DESTRA**| Graphics.MovePixelSelectionRight |
|Spostare la selezione dei pixel verso l'alto|**MAIUSC+ALT+Freccia SU**| Graphics.MovePixelSelectionUp |
|Fare zoom in base alla dimensione effettiva|**MAIUSC+ALT+0** (zero)| Graphics.ZoomToActualSize |
|Adatta alla finestra|**MAIUSC+ALT+9**| Graphics.ZoomToFitInWindow |
|Zoom avanti|**MAIUSC+ALT+=**| Graphics.ZoomIn |
|Zoom indietro|**MAIUSC+ALT+-**| Graphics.ZoomOut |

### <a name="html-editor-context-specific-shortcuts"></a><a name="bkmk_html-editor-context-specific-shortcuts"></a> Editor HTML: tasti di scelta rapida specifici del contesto

I tasti di scelta rapida specifici per questo contesto sono:


|Comando|Tasto di scelta rapida|ID comando|
|-|-|-|
|Passare al controller|**CTRL+M, CTRL+G**| OtherContextMenus.HTMLContext.GoToController |

### <a name="html-editor-design-view-context-specific-shortcuts"></a><a name="bkmk_html-editor-design-view-context-specific-shortcuts"></a> Visualizzazione progettazione editor HTML: tasti di scelta rapida specifici del contesto

I tasti di scelta rapida specifici per questo contesto sono:


|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Spostare il controllo verso il basso|**CTRL+Freccia GIÙ**| Edit.MoveControlDown |
|Sposta controllo verso l'alto|**CTRL+Freccia SU**| Edit.MoveControlUp |
|Bold|**CTRL+B**| Format.Bold |
|Converti in collegamento ipertestuale|**CTRL+L**| Format.ConverttoHyperlink |
|Inserisci segnalibro|**CTRL+MAIUSC+L**| Format.InsertBookmark |
|Corsivo|**CTRL+I**| Format.Italic |
|Sottolineato|**CTRL+U**| Format.Underline |
|Pagina Aggiungi contenuto|**CTRL+M, CTRL+C**| Project.AddContentPage |
|Colonna a sinistra|**CTRL+ALT+FRECCIA SINISTRA**| Table.ColumntotheLeft |
|Colonna a destra|**CTRL+ALT+Freccia DESTRA**| Table.ColumntotheRight |
|Riga precedente|**CTRL+ALT+FRECCIA SU**| Table.RowAbove |
|Riga sotto|**CTRL+ALT+FRECCIA GIÙ**| Table.RowBelow |
|Controlli net non visuali|**CTRL+MAIUSC+N**| View.ASP.NETNonvisualControls |
|Modificare il master|**Ctrl+M, Ctrl+M**| View.EditMaster |
|Visualizzazione successiva|**Ctrl+PgDn**| View.NextView |
|Mostra smart tag|**MAIUSC+ALT+F10**| View.ShowSmartTag |
|Visualizzare il markup|**MAIUSC+F7**| View.ViewMarkup |
|Scheda precedente|**CTRL+PGSU**| Window.PreviousTab |

### <a name="html-editor-source-view-context-specific-shortcuts"></a><a name="bkmk_html-editor-source-view-context-specific-shortcuts"></a> Visualizzazione origine editor HTML: tasti di scelta rapida specifici del contesto

I tasti di scelta rapida specifici per questo contesto sono:


|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Passare al controller|**CTRL+M, CTRL+G**| OtherContextMenus.HTMLContext.GoToController |
|Visualizzazione successiva|**Ctrl+PgDn**| View.NextView |
|Sincronizzare le visualizzazioni|**CTRL+MAIUSC+Y**| View.SynchronizeViews |
|Progettazione vista|**MAIUSC+F7**| View.ViewDesigner |
|Scheda precedente|**CTRL+PGSU**| Window.PreviousTab |

### <a name="layer-diagram-context-specific-shortcuts"></a><a name="bkmk_layer-diagram-context-specific-shortcuts"></a> Diagramma livello: tasti di scelta rapida specifici del contesto

I tasti di scelta rapida specifici per questo contesto sono:


|Comando|Tasto di scelta rapida|ID comando|
|-|-|-|
|Elimina|**MAIUSC+CANC**| Edit.Delete |

### <a name="managed-resources-editor-context-specific-shortcuts"></a><a name="bkmk_managed-resources-editor-context-specific-shortcuts"></a> Editor risorse gestite: tasti di scelta rapida specifici del contesto

I tasti di scelta rapida specifici per questo contesto sono:


|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Modifica cella|**F2**| Edit.EditCell |
|Rimuovi|**Elimina**| Edit.Remove |
|Remove row|**CTRL+CANC**| Edit.RemoveRow |
|Annullamento della selezione|**Carattere speciale di escape**| Edit.SelectionCancel |
|Audio|**CTRL+4**| Resources.Audio |
|File|**CTRL+5**| Resources.Files |
|Icone|**CTRL+3**| Resources.Icons |
|Immagini|**CTRL+2**| Resources.Images |
|Altro|**CTRL+6**| Resources.Other |
|Stringhe|**CTRL+1**| Resources.Strings |

### <a name="merge-editor-window-context-specific-shortcuts"></a><a name="bkmk_merge-editor-window-context-specific-shortcuts"></a> Finestra editor di merge: scelte rapide specifiche del contesto

I tasti di scelta rapida specifici per questo contesto sono:


|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Impostare lo stato attivo sulla finestra a sinistra|**ALT+1**| TeamFoundationContextMenus.MergeContextMenu.SetFocusonLeftWindow |
|Impostare lo stato attivo sulla finestra dei risultati|**ALT+2**| TeamFoundationContextMenus.MergeContextMenu.SetFocusonResultWindow |
|Impostare lo stato attivo sulla finestra a destra|**ALT+3**| TeamFoundationContextMenus.MergeContextMenu.SetFocusonRightWindow |

### <a name="microsoft-sql-server-data-tools-schema-compare-context-specific-shortcuts"></a><a name="bkmk_microsoft-sql-server-data-tools-schema-compare-context-specific-shortcuts"></a>Microsoft SQL Server Strumenti dati, confronto schemi: scelte rapide specifiche del contesto

I tasti di scelta rapida specifici per questo contesto sono:


|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Confronto schema SSDT|**MAIUSC+ALT+C**| SQL.SSDTSchemaCompareCompare |
|Genera script di generazione confronto schema SSDT|**MAIUSC+ALT+G**| SQL.SSDTSchemaCompareGenerateScript |
|Modifica successiva del confronto dello schema di SSDT|**MAIUSC+ALT+.**| SQL.SSDTSchemaCompareNextChange |
|Confronto schema SSDT - Modifica precedente|**MAIUSC+ALT+,**| SQL.SSDTSchemaComparePreviousChange |
|Arresto confronto schema SSDT|**ALT+INTERR**| SQL.SSDTSchemaCompareStop |
|Confronto schema SSDT - Aggiornamenti di scrittura|**MAIUSC+ALT+U**| SQL.SSDTSchemaCompareWriteUpdates |

### <a name="microsoft-sql-server-data-tools-table-designer-context-specific-shortcuts"></a><a name="bkmk_microsoft-sql-server-data-tools-table-designer-context-specific-shortcuts"></a>Microsoft SQL Server Strumenti dati, Progettazione tabelle: tasti di scelta rapida specifici del contesto

I tasti di scelta rapida specifici per questo contesto sono:


|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|CommitAllEdits|**MAIUSC+ALT+U**|
|Espandere i caratteri jolly|**CTRL+R, E**<br /><br /> oppure<br /><br /> **CTRL+R, CTRL+E**| SQL.ExpandWildcards |
|Nomi completi|**CTRL+R, Q**<br /><br /> oppure<br /><br /> **CTRL+R, CTRL+Q**| SQL.FullyqualifyNames |
|Passare allo schema|**CTRL+R, M**<br /><br /> oppure<br /><br /> **CTRL+R, CTRL+M**| SQL.MovetoSchema |
|Rinominare|**F2**<br /><br /> oppure<br /><br /> **CTRL+R, R**<br /><br /> oppure<br /><br /> **CTRL+R, CTRL+R**| SQL.Rename |
|ViewFileInScriptPanel|**MAIUSC+ALT+PGGIÙ**| |

### <a name="microsoft-sql-server-data-tools-t-sql-editor-context-specific-shortcuts"></a><a name="bkmk_microsoft-sql-server-data-tools-t-sql-editor-context-specific-shortcuts"></a>Microsoft SQL Server Strumenti dati, Editor T-SQL: tasti di scelta rapida specifici del contesto

I tasti di scelta rapida specifici per questo contesto sono:


|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|CommitAllEdits|**MAIUSC+ALT+U**|
|Eseguire con il debugger|**ALT+F5**| SQL.ExecuteWithDebugger |
|Espandere i caratteri jolly|**CTRL+R, E**<br /><br /> oppure<br /><br /> **CTRL+R, CTRL+E**| SQL.ExpandWildcards |
|Nomi completi|**CTRL+R, Q**<br /><br /> oppure<br /><br /> **CTRL+R, CTRL+Q**| SQL.FullyqualifyNames |
|Passare allo schema|**CTRL+R, M**<br /><br /> oppure<br /><br /> **CTRL+R, CTRL+M**| SQL.MovetoSchema |
|Rinominare|**F2**<br /><br /> oppure<br /><br /> **CTRL+R, R**<br /><br /> oppure<br /><br /> **CTRL+R, CTRL+R**| SQL.Rename |
|Annullamento query SQL editor T|**ALT+INTERR**| SQL.TSqlEditorCancelQuery |
|Query SQL'editor T|**CTRL+MAIUSC+E**| SQL.TSqlEditorExecuteQuery |
|T SQL risultati dell'editor come file|**CTRL+D, F**| SQL.TSqlEditorResultsAsFile |
|T SQL risultati dell'editor come griglia|**CTRL+D, G**| SQL.TSqlEditorResultsAsGrid |
|T SQL risultati dell'editor come testo|**CTRL+D, T**| SQL.TSqlEditorResultsAsText |
|T SQL editor mostra piano stimato|**CTRL+D, E**| SQL.TSqlEditorShowEstimatedPlan |
|Editor di SQL attiva/disattiva piano di esecuzione|**CTRL+D, A**| SQL.TSqlEditorToggleExecutionPlan |
|Riquadro SQL dei risultati dell'editor T|**CTRL+D, R**| SQL.TSqlEditorToggleResultsPane |
|Query clone SQL editor T|**CTRL+ALT+N**|SQL. TSqlEditorCloneQuery |
|Casella combinata SQL database dell'editor T|**MAIUSC+ALT+PGGIÙ**|SQL. TSqlEditorDatabaseCombo |

### <a name="microsoft-sql-server-data-tools-t-sql-pdw-editor-context-specific-shortcuts"></a><a name="bkmk_microsoft-sql-server-data-tools-t-sql-pdw-editor-context-specific-shortcuts"></a>Microsoft SQL Server Strumenti dati, Editor T-SQL PDW: tasti di scelta rapida specifici del contesto

I tasti di scelta rapida specifici per questo contesto sono:


|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Annullamento query SQL editor T|**ALT+INTERR**| SQL.TSqlEditorCancelQuery |
|Query SQL'editor T|**CTRL+MAIUSC+E**| SQL.TSqlEditorExecuteQuery |
|T SQL risultati dell'editor come file|**CTRL+D, F**| SQL.TSqlEditorResultsAsFile |
|T SQL risultati dell'editor come griglia|**CTRL+D, G**| SQL.TSqlEditorResultsAsGrid |
|T SQL risultati dell'editor come testo|**CTRL+D, T**| SQL.TSqlEditorResultsAsText |
|T SQL editor mostra piano stimato|**CTRL+D, E**| SQL.TSqlEditorShowEstimatedPlan |
|Editor di SQL attiva/disattiva piano di esecuzione|**CTRL+D, A**| SQL.TSqlEditorToggleExecutionPlan |
|Riquadro SQL dei risultati dell'editor T|**CTRL+D, R**| SQL.TSqlEditorToggleResultsPane |
|Query clone SQL editor T|**CTRL+ALT+N**|SQL. TSqlEditorCloneQuery |
|Query clone SQL editor T|**MAIUSC+ALT+PGGIÙ**|SQL. TSqlEditorCloneQuery |

### <a name="page-inspector-context-specific-shortcuts"></a><a name="bkmk_page-inspector-context-specific-shortcuts"></a>Controllo pagina: scelte rapide specifiche del contesto

I tasti di scelta rapida specifici per questo contesto sono:


|Comando|Tasto di scelta rapida|ID comando|
|-|-|-|
|Riduci|**F12**| PageInspector.Minimize |

### <a name="query-designer-context-specific-shortcuts"></a><a name="bkmk_query-designer-context-specific-shortcuts"></a> Progettazione query: scelte rapide specifiche del contesto

I tasti di scelta rapida specifici per questo contesto sono:


|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Annullare il recupero dei dati|**CTRL+T**| QueryDesigner.CancelRetrievingData |
|Criteri|**CTRL+2**| QueryDesigner.Criteria |
|Diagramma|**CTRL+1**| QueryDesigner.Diagram |
|Esegui SQL|**CTRL+R**| QueryDesigner.ExecuteSQL |
|Goto row|**CTRL+G**| QueryDesigner.GotoRow |
|Modalità join|**CTRL+MAIUSC+J**| QueryDesigner.JoinMode |
|Risultati|**CTRL+4**| QueryDesigner.Results |
|Sql|**CTRL+3**| QueryDesigner.SQL |

### <a name="query-results-context-specific-shortcuts"></a><a name="bkmk_query-results-context-specific-shortcuts"></a> Risultati della query: tasti di scelta rapida specifici del contesto

I tasti di scelta rapida specifici per questo contesto sono:


|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Nuova riga dei risultati della query|**ALT+FINE**| SQL.QueryResultsNewRow |
|Aggiornamento dei risultati della query|**MAIUSC+ALT+R**| SQL.QueryResultsRefresh |
|Interruzione dei risultati della query|**ALT+INTERR**| SQL.QueryResultsStop |

### <a name="report-designer-context-specific-shortcuts"></a><a name="bkmk_report-designer-context-specific-shortcuts"></a> Progettazione report: tasti di scelta rapida specifici del contesto

I tasti di scelta rapida specifici per questo contesto sono:


|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Riga di interruzione|**INVIO**| Edit.BreakLine |
|Carattere a sinistra|**Freccia SINISTRA**| Edit.CharLeft |
|Estensione a sinistra del carattere|**MAIUSC+freccia SINISTRA**| Edit.CharLeftExtend |
|Carattere a destra|**Freccia DESTRA**| Edit.CharRight |
|Estensione a destra del carattere|**MAIUSC+freccia DESTRA**| Edit.CharRightExtend |
|Scheda Inserisci|**TAB**| Edit.InsertTab |
|Giù di una riga|**Freccia GIÙ**| Edit.LineDown |
|Estensione della linea verso il basso|**MAIUSC+freccia GIÙ**| Edit.LineDownExtend |
|Su di una riga|**Freccia SU**| Edit.LineUp |
|Estensione line-up|**MAIUSC+freccia SU**| Edit.LineUpExtend |
|Spostare il controllo verso il basso|**CTRL+FRECCIA GIÙ**| Edit.MoveControlDown |
|Spostare il controllo a sinistra|**CTRL+FRECCIA SINISTRA**| Edit.MoveControlLeft |
|Spostare il controllo a destra|**CTRL+FRECCIA DESTRA**| Edit.MoveControlRight |
|Spostare il controllo verso l'alto|**CTRL+FRECCIA SU**| Edit.MoveControlUp |
|Annullamento della selezione|**ESC**| Edit.SelectionCancel |
|Controllo delle dimensioni verso il basso|**CTRL+MAIUSC+freccia GIÙ**| Edit.SizeControlDown |
|Controllo dimensioni a sinistra|**CTRL+MAIUSC+Freccia SINISTRA**| Edit.SizeControlLeft |
|Controllo dimensioni a destra|**CTRL+MAIUSC+freccia DESTRA**| Edit.SizeControlRight |
|Controllo delle dimensioni in alto|**CTRL+MAIUSC+freccia SU**| Edit.SizeControlUp |
|Tab a sinistra|**MAIUSC+TAB**| Edit.TabLeft |
|Dati di report|**CTRL+ALT+D**| View.ReportData |

### <a name="sequence-diagram-context-specific-shortcuts"></a><a name="bkmk_sequence-diagram-context-specific-shortcuts"></a> Diagramma di sequenza: tasti di scelta rapida specifici del contesto

I tasti di scelta rapida specifici per questo contesto sono:


|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Passare al codice|**F12**| ArchitectureDesigner.Sequence.NavigateToCode |
|Elimina|**MAIUSC+CANC**| Edit.Delete |

### <a name="settings-designer-context-specific-shortcuts"></a><a name="bkmk_settings-designer-context-specific-shortcuts"></a>Impostazioni Finestra di progettazione: tasti di scelta rapida specifici del contesto

I tasti di scelta rapida specifici per questo contesto sono:


|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Modifica cella|**F2**| Edit.EditCell |
|Remove row|**CTRL+CANC**| Edit.RemoveRow |
|Annullamento della selezione|**ESC**| Edit.SelectionCancel |
|Visualizzare il codice|**F7**| View.ViewCode |

### <a name="solution-explorer-context-specific-shortcuts"></a><a name="bkmk_solution-explorer-context-specific-shortcuts"></a> Esplora soluzioni: tasti di scelta rapida specifici del contesto

I tasti di scelta rapida specifici per questo contesto sono:


|Comando|Tasto di scelta rapida|ID comando|
|-|-|-|
|Visualizzazione nel controllo pagina|**CTRL+K, CTRL+G**| ClassViewContextMenus.ClassViewProject.View.ViewinPageInspector |

### <a name="team-explorer-context-specific-shortcuts"></a><a name="bkmk_team-explorer-context-specific-shortcuts"></a> Team Explorer: tasti di scelta rapida specifici del contesto

I tasti di scelta rapida specifici per questo contesto sono:


|Comando|Tasto di scelta rapida|ID comando|
|-|-|-|
|Elimina|**Elimina**| Edit.Delete |
|Rinominare|**F2**| File.Rename |
|Passare al riquadro di spostamento di Team Explorer|**ALT+Home**| TeamFoundationContextMenus.Commands.GoToTeamExplorerNavigation |
|Passare al contenuto della sezione successiva di Team Explorer|**ALT+freccia GIÙ**| TeamFoundationContextMenus.Commands.GoToTeamExplorerNextSectionContent |
|Passare al contenuto della pagina di Team Explorer|**ALT+0** (zero)| TeamFoundationContextMenus.Commands.GoToTeamExplorerPageContent |
|Passare al contenuto della sezione precedente di Team Explorer|**ALT+freccia SU**| TeamFoundationContextMenus.Commands.GoToTeamExplorerPreviousSectionContent |
|Passare al contenuto della sezione 1 di Team Explorer|**ALT+1**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection1Content |
|Passare al contenuto della sezione 2 di Team Explorer|**ALT+2**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection2Content |
|Passare al contenuto della sezione 3 di Team Explorer|**ALT+3**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection3Content |
|Passare al contenuto della sezione 4 di Team Explorer|**ALT+4**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection4Content |
|Passare al contenuto della sezione 5 di Team Explorer|**ALT+5**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection5Content |
|Passare al contenuto della sezione 6 di Team Explorer|**ALT+6**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection6Content |
|Passare al contenuto della sezione 7 di Team Explorer|**ALT+7**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection7Content |
|Passare al contenuto della sezione 8 di Team Explorer|**ALT+8**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection8Content |
|Passare al contenuto della sezione 9 di Team Explorer|**ALT+9**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection9Content |
|Esplora team consente di spostarsi all'indietro|**ALT+freccia SINISTRA**| TeamFoundationContextMenus.Commands.TeamExplorerNavigateBackward |
|Esplora team consente di spostarsi in avanti|**ALT+freccia DESTRA**| TeamFoundationContextMenus.Commands.TeamExplorerNavigateForward |
|Contesto TFS la pagina di lavoro crea copia wi|**MAIUSC+ALT+C**| TeamFoundationContextMenus.MyWorkPageInProgress.TfsContextMyWorkPageCreateCopyWI |
|Contesto TFS nuova pagina di lavoro collegata wi|**MAIUSC+ALT+L**| TeamFoundationContextMenus.MyWorkPageInProgress.TfsContextMyWorkPageNewLinkedWI |
|Aggiorna|**F5**| View.Refresh |

### <a name="test-explorer-context-specific-shortcuts"></a><a name="bkmk_test-explorer-context-specific-shortcuts"></a> Esplora test: tasti di scelta rapida specifici del contesto

I tasti di scelta rapida specifici per questo contesto sono:


|Comando|Tasto di scelta rapida|ID comando|
|-|-|-|
|Aprire il test|**F12**| TestExplorer.OpenTest |

### <a name="text-editor-context-specific-shortcuts"></a><a name="bkmk_text-editor-context-specific-shortcuts"></a> Editor di testo: tasti di scelta rapida specifici del contesto

I tasti di scelta rapida specifici per questo contesto sono:


| Comandi | Tasti di scelta rapida |ID comando|
|-|-|-|
|Riga di interruzione| **INVIO**<br /><br /> oppure<br /><br /> **MAIUSC+INVIO** | Edit.BreakLine |
|Carattere a sinistra| **Freccia SINISTRA** | Edit.CharLeft |
|Estensione a sinistra del carattere| **MAIUSC+freccia SINISTRA** | Edit.CharLeftExtend |
|Colonna di estensione a sinistra del carattere| **MAIUSC+ALT+freccia SINISTRA** | Edit.CharLeftExtendColumn |
|Carattere a destra| **Freccia DESTRA** | Edit.CharRight |
|Estensione a destra del carattere| **MAIUSC+freccia DESTRA** | Edit.CharRightExtend |
|Colonna di estensione a destra del carattere| **MAIUSC+ALT+freccia DESTRA** | Edit.CharRightExtendColumn |
|Cancellare segnalibri| **Ctrl+K, Ctrl+L** | Edit.ClearBookmarks |
|Comprimi tutte le struttura| **Ctrl+M, Ctrl+A** | Edit.CollapseAllOutlining |
|Comprimi area corrente| **Ctrl+M, Ctrl+S** | Edit.CollapseCurrentRegion |
|Comprimi tag| **CTRL+M, CTRL+T** | Edit.CollapseTag |
|Comprimi in definizioni| **CTRL+M, CTRL+O** (lettera "O") | Edit.CollapseToDefinitions |
|Comprimere la selezione| **MAIUSC+ALT+-** | Edit.ContractSelection |
|Selezione dei commenti| **Ctrl+K, Ctrl+C** | Edit.CommentSelection |
|Completare una parola| **CTRL+BARRA SPAZIATRICE**<br /><br /> oppure<br /><br /> **ALT+freccia DESTRA** | Edit.CompleteWord |
|Copiare il suggerimento sul parametro| **CTRL+MAIUSC+ALT+C** | Edit.CopyParameterTip |
|Ridurre il livello di filtro| **ALT+,** | Edit.DecreaseFilterLevel |
|Eliminare all'indietro| **Backspace**<br /><br /> oppure<br /><br /> **MAIUSC+BACKSPACE** | Edit.DeleteBackwards |
|Eliminare gli spazi vuoti orizzontali| **Ctrl+K, Ctrl+\\** | Edit.DeleteHorizontalWhiteSpace |
|Fine documento| **CTRL+FINE** | Edit.DocumentEnd |
|Estensione della fine del documento| **CTRL+MAIUSC+FINE** | Edit.DocumentEndExtend |
|Inizio documento| **CTRL+HOME** | Edit.DocumentStart |
|Estensione dell'inizio del documento| **CTRL+MAIUSC+HOME** | Edit.DocumentStartExtend |
|Espandere tutte le struttura| **Ctrl+M, Ctrl+X** | Edit.ExpandAllOutlining |
|Espandere l'area corrente| **Ctrl+M, Ctrl+E** | Edit.ExpandCurrentRegion |
|Espandere la selezione| **MAIUSC+ALT+=** | Edit.ExpandSelection |
|Espandere la selezione nel blocco contenitore| **MAIUSC+ALT+]** | Edit.ExpandSelectiontoContainingBlock |
|Formatta documento| **Ctrl+K, Ctrl+D** | Edit.FormatDocument |
|Selezione di Formatta| **Ctrl+K, Ctrl+F** | Edit.FormatSelection |
|Goto all| **CTRL+T**<br /><br /> oppure<br /><br /> **CTRL+,** | Edit.GotoAll |
|Parentesi graffa goto| **CTRL+]** | Edit.GotoBrace |
|Parentesi graffa goto extend| **CTRL+MAIUSC+]** | Edit.GotoBraceExtend |
|Goto recent| **CTRL+T,R** | Edit.GotoRecent |
|Goto next issue in file (Problema successivo nel file)| **ALT+PGGIÙ** | Edit.GotoNextIssueinFile |
|Problema precedente nel file| **ALT+PGSU** | Edit.GotoPreviousIssueinFile |
|Nascondere la selezione| **Ctrl+M, Ctrl+H** | Edit.HideSelection |
|Aumentare il livello di filtro| **ALT+.** | Edit.IncreaseFilterLevel |
|Ricerca incrementale| **CTRL+I** | Edit.IncrementalSearch |
|Inserire i caratteri di inserimento in corrispondenza di tutte le corrispondenze| **MAIUSC+ALT+;** | Edit.InsertCaretsatAllMatching |
|Inserire il successivo caret corrispondente| **MAIUSC+ALT+.** | Edit.InsertNextMatchingCaret |
|Scheda Inserisci| **TAB** | Edit.InsertTab |
|Taglio di linea| **CTRL+L** | Edit.LineCut |
|Eliminazione riga| **CTRL+MAIUSC+L** | Edit.LineDelete |
|Giù di una riga| **Freccia GIÙ** | Edit.LineDown |
|Estensione linea verso il basso| **MAIUSC+Freccia GIÙ** | Edit.LineDownExtend |
|Estendere la colonna verso il basso| **MAIUSC+ALT+Freccia GIÙ** | Edit.LineDownExtendColumn |
|Fine riga| **Fine** | Edit.LineEnd |
|Estensione fine riga| **MAIUSC+FINE** | Edit.LineEndExtend |
|Estensione colonna fine riga| **MAIUSC+ALT+FINE** | Edit.LineEndExtendColumn |
|Riga aperta sopra| **CTRL+INVIO** | Edit.LineOpenAbove |
|Riga aperta sotto| **CTRL+MAIUSC+INVIO** | Edit.LineOpenBelow |
|Inizio riga| **Home** | Edit.LineStart |
|Estensione inizio riga| **MAIUSC+HOME** | Edit.LineStartExtend |
|Estensione colonna inizio riga| **MAIUSC+ALT+HOME** | Edit.LineStartExtendColumn |
|Trasposizione di righe| **MAIUSC+ALT+T** | Edit.LineTranspose |
|Su di una riga| **Freccia SU** | Edit.LineUp |
|Estensione della linea verso l'alto| **MAIUSC+Freccia SU** | Edit.LineUpExtend |
|Allineare la colonna di estensione| **MAIUSC+ALT+Freccia SU** | Edit.LineUpExtendColumn |
|Elencare i membri| **CTRL+J** | Edit.ListMembers |
|Creare lettere minuscole| **CTRL+U** | Edit.MakeLowercase |
|Maiuscole| **CTRL+MAIUSC+U** | Edit.MakeUppercase |
|Sposta le righe selezionate verso il basso| **ALT+Freccia GIÙ** | Edit.MoveSelectedLinesDown |
|Spostare le righe selezionate verso l'alto| **ALT+freccia SU** | Edit.MoveSelectedLinesUp |
|Riferimento evidenziato successivo| **CTRL+MAIUSC+freccia GIÙ** | Edit.NextHighlightedReference |
|Modalità sovrascritta| **Inserimento** | Edit.OvertypeMode |
|Giù di una pagina| **PGGIÙ** | Edit.PageDown |
|Pagina successiva estendere| **MAIUSC+PgDn** | Edit.PageDownExtend |
|Su di una pagina| **PGSU** | Edit.PageUp |
|Pagina precedente estendere| **MAIUSC+PGSU** | Edit.PageUpExtend |
|Informazioni sui parametri| **CTRL+MAIUSC+BARRA SPAZIATRICE** | Edit.ParameterInfo |
|Incollare il suggerimento sul parametro| **CTRL+MAIUSC+ALT+P** | Edit.PasteParameterTip |
|Visualizzare all'indietro| **CTRL+ALT+-** | Edit.PeekBackward |
|Visualizzare la definizione| **ALT+F12** | Edit.PeekDefinition |
|Anteprima| **CTRL+ALT+=** | Edit.PeekForward |
|Riferimento evidenziato precedente| **CTRL+MAIUSC+FRECCIA SU** | Edit.PreviousHighlightedReference |
|Informazioni rapide| **Ctrl+K, Ctrl+I** | Edit.QuickInfo |
|Ricerca incrementale inversa| **CTRL+MAIUSC+I** | Edit.ReverseIncrementalSearch |
|Scorrere la riga verso il basso| **CTRL+FRECCIA GIÙ** | Edit.ScrollLineDown |
|Scorrere la riga verso l'alto| **CTRL+FRECCIA SU** | Edit.ScrollLineUp |
|Selezionare la parola corrente| **CTRL+W** | Edit.SelectCurrentWord |
|Annullamento della selezione| **Carattere speciale di escape** | Edit.SelectionCancel |
|Selezionare per tornare indietro per l'ultima volta| **CTRL+=** | Edit.SelectToLastGoBack |
|Menu Mostra obiettivo codice| **Ctrl+K, Ctrl+\`** | Edit.ShowCodeLensMenu |
|Mostra menu di navigazione| **ALT+\`** | Edit.ShowNavigateMenu |
|Interrompi nascondi corrente| **Ctrl+M, Ctrl+U** | Edit.StopHidingCurrent |
|Interrompere la struttura| **Ctrl+M, Ctrl+P** | Edit.StopOutlining |
|Scambiare l'ancoraggio| **Ctrl+K, Ctrl+A** | Edit.SwapAnchor |
|Tab a sinistra| **MAIUSC+TAB** | Edit.TabLeft |
|Attiva/Disattiva tutte le struttura| **Ctrl+M, Ctrl+L** | Edit.ToggleAllOutlining |
|Attiva/disattiva il segnalibro| **Ctrl+K, Ctrl+K** | Edit.ToggleBookmark |
|Attivare/disattivare la modalità di completamento| **CTRL+ALT+BARRA SPAZIATRICE** | Edit.ToggleCompletionMode |
|Attivare/disattivare l'espansione della struttura| **Ctrl+M, Ctrl+M** | Edit.ToggleOutliningExpansion |
|Attivare o disattivare il collegamento all'elenco attività| **Ctrl+K, Ctrl+H** | Edit.ToggleTaskListShortcut |
|Attivare o disattivare il ritorno a capo automatico| **CTRL+E, CTRL+W** | Edit.ToggleWordWrap |
|Rimuovere il commento dalla selezione| **Ctrl+K, Ctrl+U** | Edit.UncommentSelection |
|Visualizza in basso| **Ctrl+PgDn** | Edit.ViewBottom |
|Visualizzare l'estensione inferiore| **Ctrl+Maiusc+PgDn** | Edit.ViewBottomExtend |
|Visualizza in alto| **CTRL+PGSU** | Edit.ViewTop |
|Visualizzare l'estensione superiore| **CTRL+MAIUSC+PGSU** | Edit.ViewTopExtend |
|Visualizzare gli spazi vuoti| **Ctrl+R, Ctrl+W** | Edit.ViewWhiteSpace |
|Eliminazione di word fino alla fine| **CTRL+CANC** | Edit.WordDeleteToEnd |
|Eliminazione di word per iniziare| **CTRL+BACKSPACE** | Edit.WordDeleteToStart |
|Parola successiva| **CTRL+FRECCIA DESTRA** | Edit.WordNext |
|Estensione successiva di Word| **CTRL+MAIUSC+freccia DESTRA** | Edit.WordNextExtend |
|Colonna di estensione successiva di Word| **CTRL+MAIUSC+ALT+Freccia DESTRA** | Edit.WordNextExtendColumn |
|Parola precedente| **CTRL+FRECCIA SINISTRA** | Edit.WordPrevious |
|Estensione precedente di Word| **CTRL+MAIUSC+Freccia SINISTRA** | Edit.WordPreviousExtend |
|Colonna di estensione precedente di Word| **CTRL+MAIUSC+ALT+Freccia SINISTRA** | Edit.WordPreviousExtendColumn |
|Trasposizione di parole| **CTRL+MAIUSC+T** | Edit.WordTranspose |
|Eseguire in modalità interattiva| **ALT+INVIO** | EditorContextMenus.CodeWindow.ExecuteInInteractive |
|Eseguire una riga in modo interattivo| **ALT+'** | EditorContextMenus.CodeWindow.ExecuteLineInInteractive |
|Visualizzazione nel controllo pagina| **CTRL+K, CTRL+G** | OtherContextMenus.HTMLContext.ViewinPageInspector |
|TFS annotare l'area successiva| **ALT+PGGIÙ** | TeamFoundationContextMenus.Annotate.TfsAnnotateMoveNextRegion |
|TFS annotare l'area precedente| **ALT+PGSU** | TeamFoundationContextMenus.Annotate.TfsAnnotateMovePreviousRegion |

### <a name="uml-activity-diagram-context-specific-shortcuts"></a><a name="bkmk_uml-activity-diagram-context-specific-shortcuts"></a> Diagramma di attività UML: tasti di scelta rapida specifici del contesto

I tasti di scelta rapida specifici per questo contesto sono:


|Comando|Tasto di scelta rapida|ID comando|
|-|-|-|
|Elimina|**MAIUSC+CANC**| Edit.Delete |

### <a name="uml-class-diagram-context-specific-shortcuts"></a><a name="bkmk_uml-class-diagram-context-specific-shortcuts"></a> Diagramma classi UML: tasti di scelta rapida specifici del contesto

I tasti di scelta rapida specifici per questo contesto sono:


|Comando|Tasto di scelta rapida|ID comando|
|-|-|-|
|Elimina dal modello|**MAIUSC+CANC**| Edit.DeleteFromModel |

### <a name="uml-component-diagram-context-specific-shortcuts"></a><a name="bkmk_uml-component-diagram-context-specific-shortcuts"></a> Diagramma dei componenti UML: tasti di scelta rapida specifici del contesto

I tasti di scelta rapida specifici per questo contesto sono:


|Comando|Tasto di scelta rapida|ID comando|
|-|-|-|
|Elimina dal modello|**MAIUSC+CANC**| Edit.DeleteFromModel |

### <a name="uml-use-case-diagram-context-specific-shortcuts"></a><a name="bkmk_uml-use-case-diagram-context-specific-shortcuts"></a> Diagramma del caso d'uso UML: tasti di scelta rapida specifici del contesto

I tasti di scelta rapida specifici per questo contesto sono:


|Comando|Tasto di scelta rapida|ID comando|
|-|-|-|
|Elimina dal modello|**MAIUSC+CANC**| Edit.DeleteFromModel |

### <a name="vc-accelerator-editor-context-specific-shortcuts"></a><a name="bkmk_vc-accelerator-editor-context-specific-shortcuts"></a> Editor tasti di scelta rapida DI VC: tasti di scelta rapida specifici del contesto

I tasti di scelta rapida specifici per questo contesto sono:


|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Nuovo acceleratore|**Inserimento**| Edit.NewAccelerator |
|Chiave successiva digitata|**CTRL+W**| Edit.NextKeyTyped |

### <a name="vc-dialog-editor-context-specific-shortcuts"></a><a name="bkmk_vc-dialog-editor-context-specific-shortcuts"></a> Editor finestre di VC: tasti di scelta rapida specifici del contesto

I tasti di scelta rapida specifici per questo contesto sono:


|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Spostare il controllo verso il basso|**Freccia GIÙ**| Edit.MoveControlDown |
|Spostare il controllo a sinistra|**Freccia SINISTRA**| Edit.MoveControlLeft |
|Spostare il controllo a destra|**Freccia DESTRA**| Edit.MoveControlRight |
|Spostare il controllo verso l'alto|**Freccia SU**| Edit.MoveControlUp |
|Scorrere la colonna a sinistra|**CTRL+FRECCIA SINISTRA**| Edit.ScrollColumnLeft |
|Scorrere la colonna a destra|**CTRL+FRECCIA DESTRA**| Edit.ScrollColumnRight |
|Scorrere la riga verso il basso|**CTRL+FRECCIA GIÙ**| Edit.ScrollLineDown |
|Scorrere la riga verso l'alto|**CTRL+FRECCIA SU**| Edit.ScrollLineUp |
|Controllo delle dimensioni verso il basso|**MAIUSC+freccia GIÙ**| Edit.SizeControlDown |
|Controllo dimensioni a sinistra|**MAIUSC+freccia SINISTRA**| Edit.SizeControlLeft |
|Controllo dimensioni a destra|**MAIUSC+freccia DESTRA**| Edit.SizeControlRight |
|Controllo delle dimensioni in alto|**MAIUSC+freccia SU**| Edit.SizeControlUp |
|Allineare i dati in basso|**CTRL+MAIUSC+freccia GIÙ**| Format.AlignBottoms |
|Allineare i centri|**MAIUSC+F9**| Format.AlignCenters |
|Allinea a sinistra|**CTRL+MAIUSC+Freccia SINISTRA**| Format.AlignLefts |
|Allineare al centro|**F9**| Format.AlignMiddles |
|Allineare i diritti|**CTRL+MAIUSC+freccia DESTRA**| Format.AlignRights |
|Allineare i vertici|**CTRL+MAIUSC+FRECCIA SU**| Format.AlignTops |
|Pulsante in basso|**CTRL+B**| Format.ButtonBottom |
|Pulsante a destra|**CTRL+R**| Format.ButtonRight |
|Centra orizzontalmente|**CTRL+MAIUSC+F9**| Format.CenterHorizontal |
|Centra verticale|**CTRL+F9**| Format.CenterVertical |
|Controlla i tasti di scelta|**CTRL+M**| Format.CheckMnemonics |
|Dimensioni del contenuto|**MAIUSC+F7**| Format.SizetoContent |
|Spazio tra|**ALT+freccia DESTRA**<br /><br /> oppure<br /><br /> **ALT+freccia SINISTRA**| Format.SpaceAcross |
|Spazio in basso|**ALT+freccia SU**<br /><br /> oppure<br /><br /> **ALT+freccia GIÙ**| Format.SpaceDown |
|Ordine di tabulazione|**CTRL+D**| Format.TabOrder |
|Finestra di dialogo Test|**CTRL+T**| Format.TestDialog |
|Attivare/disattivare le guide|**CTRL+G**| Format.ToggleGuides |

### <a name="vc-image-editor-context-specific-shortcuts"></a><a name="bkmk_vc-image-editor-context-specific-shortcuts"></a> Editor di immagini VC: tasti di scelta rapida specifici del contesto

I tasti di scelta rapida specifici per questo contesto sono:


|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Strumento Airbrush|**CTRL+A**| Image.AirBrushTool |
|Strumento Pennello|**CTRL+B**| Image.BrushTool |
|Copiare e strutturare la selezione|**CTRL+MAIUSC+U**| Image.CopyandOutlineSelection |
|Disegnare opaco|**CTRL+J**| Image.DrawOpaque |
|Strumento Ellisse|**ALT+P**| Image.EllipseTool |
|Strumento Di cancellazione|**CTRL+MAIUSC+I**| Image.EraseTool |
|Strumento ellisse con riempimento|**CTRL+MAIUSC+ALT+P**| Image.FilledEllipseTool |
|Strumento Rettangolo pieno|**CTRL+MAIUSC+ALT+R**| Image.FilledRectangleTool |
|Strumento rettangolo arrotondato riempito|**CTRL+MAIUSC+ALT+W**| Image.FilledRoundedRectangleTool |
|Riempimento (strumento)|**CTRL+F**| Image.FillTool |
|Capovolgi orizzontalmente|**CTRL+H**| Image.FlipHorizontal |
|Capovolgi verticalmente|**MAIUSC+ALT+H**| Image.FlipVertical |
|Pennello più grande|**CTRL+=**| Image.LargerBrush |
|Strumento Linea|**CTRL+L**| Image.LineTool |
|Strumento di ingrandimento|**CTRL+M**| Image.MagnificationTool |
|Ingrandire|**CTRL+MAIUSC+M**| Image.Magnify |
|Nuovo tipo di immagine|**Inserimento**| Image.NewImageType |
|Colore successivo|**CTRL+]**<br /><br /> oppure<br /><br /> **CTRL+FRECCIA DESTRA**| Image.NextColor |
|Colore successivo a destra|**CTRL+MAIUSC+]**<br /><br /> oppure<br /><br /> **CTRL+MAIUSC+freccia DESTRA**| Image.NextRightColor |
|Strumento ellisse con contorno|**MAIUSC+ALT+P**| Image.OutlinedEllipseTool |
|Strumento rettangolo con contorni|**MAIUSC+ALT+R**| Image.OutlinedRectangleTool |
|Strumento rettangolo arrotondato con contorno|**MAIUSC+ALT+W**| Image.OutlinedRoundedRectangleTool |
|Strumento matita|**CTRL+I**| Image.PencilTool |
|Colore precedente|**CTRL+[**<br /><br /> oppure<br /><br /> **CTRL+FRECCIA SINISTRA**| Image.PreviousColor |
|Colore a destra precedente|**CTRL+MAIUSC+[**<br /><br /> oppure<br /><br /> **CTRL+MAIUSC+Freccia SINISTRA**| Image.PreviousRightColor |
|Strumento di selezione del rettangolo|**MAIUSC+ALT+S**| Image.RectangleSelectionTool |
|Strumento Rettangolo|**ALT+R**| Image.RectangleTool |
|Rotazione di 90° gradi|**CTRL+MAIUSC+H**| Image.Rotate90Degrees |
|Strumento rettangolo arrotondato|**ALT+W**| Image.RoundedRectangleTool |
|Mostra griglia|**CTRL + ALT + S**| Image.ShowGrid |
|Mostra griglia riquadri|**CTRL+MAIUSC+ALT+S**| Image.ShowTileGrid |
|Pennello piccolo|**CTRL+.**| Image.SmallBrush |
|Pennello più piccolo|**CTRL+-**| Image.SmallerBrush |
|Strumento testo|**CTRL+T**| Image.TextTool |
|Usare la selezione come pennello|**CTRL+U**| Image.UseSelectionAsBrush |
|Zoom avanti|**CTRL+MAIUSC+.**<br /><br /> oppure<br /><br /> **CTRL+FRECCIA SU**| Image.ZoomIn |
|Zoom indietro|**CTRL+MAIUSC+,**<br /><br /> oppure<br /><br /> **CTRL+FRECCIA GIÙ**| Image.ZoomOut |

### <a name="vc-string-editor-context-specific-shortcuts"></a><a name="bkmk_vc-string-editor-context-specific-shortcuts"></a> Editor di stringhe VC: tasti di scelta rapida specifici del contesto

I tasti di scelta rapida specifici per questo contesto sono:


|Comando|Tasto di scelta rapida|ID comando|
|-|-|-|
|NewString|**Inserimento**| Edit.NewString |

### <a name="view-designer-context-specific-shortcuts"></a><a name="bkmk_view-designer-context-specific-shortcuts"></a> Progettazione visualizzazioni: tasti di scelta rapida specifici del contesto

I tasti di scelta rapida specifici per questo contesto sono:


|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Annullare il recupero dei dati|**CTRL+T**| QueryDesigner.CancelRetrievingData |
|Criteri|**CTRL+2**| QueryDesigner.Criteria |
|Diagramma|**CTRL+1**| QueryDesigner.Diagram |
|Esegui SQL|**CTRL+R**| QueryDesigner.ExecuteSQL |
|Riga Goto|**CTRL+G**| QueryDesigner.GotoRow |
|Modalità join|**CTRL+MAIUSC+J**| QueryDesigner.JoinMode |
|Risultati|**CTRL+4**| QueryDesigner.Results |
|Sql|**CTRL+3**| QueryDesigner.SQL |

### <a name="visual-studio-context-specific-shortcuts"></a><a name="bkmk_visual-studio-context-specific-shortcuts"></a>Visual Studio: tasti di scelta rapida specifici del contesto

I tasti di scelta rapida specifici per questo contesto sono:


|Comando|Tasto di scelta rapida|ID comando|
|-|-|-|
|Riquadro Nascondi metodi|**CTRL+1**| OtherContextMenus.ORDesignerContext.HideMethodsPane |

### <a name="windows-forms-designer-context-specific-shortcuts"></a><a name="bkmk_windows-forms-designer-context-specific-shortcuts"></a>Windows Progettazione moduli: tasti di scelta rapida specifici del contesto

I tasti di scelta rapida specifici per questo contesto sono:


|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Riga di interruzione|**INVIO**| Edit.BreakLine |
|Carattere a sinistra|**Freccia SINISTRA**| Edit.CharLeft |
|Estensione a sinistra del carattere|**MAIUSC+freccia SINISTRA**| Edit.CharLeftExtend |
|Carattere a destra|**Freccia DESTRA**| Edit.CharRight |
|Estensione a destra del carattere|**MAIUSC+freccia DESTRA**| Edit.CharRightExtend |
|Fine documento|**Fine**| Edit.DocumentEnd |
|Estensione della fine del documento|**MAIUSC+FINE**| Edit.DocumentEndExtend |
|Inizio documento|**Home**| Edit.DocumentStart |
|Estensione dell'inizio del documento|**MAIUSC+HOME**| Edit.DocumentStartExtend |
|Scheda Inserisci|**TAB**| Edit.InsertTab |
|Giù di una riga|**Freccia GIÙ**| Edit.LineDown |
|Estensione linea verso il basso|**MAIUSC+Freccia SU**| Edit.LineDownExtend |
|Su di una riga|**Freccia SU**| Edit.LineUp |
|Estensione della linea verso l'alto|**MAIUSC+Freccia GIÙ**| Edit.LineUpExtend |
|Spostare il controllo verso il basso|**CTRL+Freccia GIÙ**| Edit.MoveControlDown |
|Sposta il controllo a sinistra|**CTRL+Freccia SINISTRA**| Edit.MoveControlLeft |
|Spostare il controllo a destra|**CTRL+Freccia DESTRA**| Edit.MoveControlRight |
|Sposta controllo verso l'alto|**CTRL+Freccia SU**| Edit.MoveControlUp |
|Annullamento della selezione|**Carattere speciale di escape**| Edit.SelectionCancel |
|Controllo delle dimensioni in basso|**CTRL+MAIUSC+Freccia GIÙ**| Edit.SizeControlDown |
|Controllo delle dimensioni a sinistra|**CTRL+MAIUSC+Freccia SINISTRA**| Edit.SizeControlLeft |
|Controllo delle dimensioni a destra|**CTRL+MAIUSC+Freccia DESTRA**| Edit.SizeControlRight |
|Controllo delle dimensioni in alto|**CTRL+MAIUSC+Freccia SU**| Edit.SizeControlUp |
|Tabulazione a sinistra|**MAIUSC+TAB**| Edit.TabLeft |

### <a name="work-item-editor-context-specific-shortcuts"></a><a name="bkmk_work-item-editor-context-specific-shortcuts"></a> Editor elementi di lavoro: tasti di scelta rapida specifici del contesto

I tasti di scelta rapida specifici per questo contesto sono:


|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Creare una copia dell'elemento di lavoro|**MAIUSC+ALT+C**| Edit.CreateCopyofWorkItem |
|Aggiornare un elemento di lavoro|**F5**| Edit.RefreshWorkItem |
|Nuovo elemento di lavoro collegato|**MAIUSC+ALT+L**| Team.NewLinkedWorkItem |

### <a name="work-item-query-view-context-specific-shortcuts"></a><a name="bkmk_work-item-query-view-context-specific-shortcuts"></a> Elemento di lavoro visualizzazione Query: tasti di scelta rapida specifici del contesto

I tasti di scelta rapida specifici per questo contesto sono:


|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Creare una copia dell'elemento di lavoro|**MAIUSC+ALT+C**| Edit.CreateCopyofWorkItem |
|Impostare un rientro|**MAIUSC+ALT+Freccia DESTRA**| Edit.Indent |
|Riduci rientro|**MAIUSC+ALT+Freccia SINISTRA**| Edit.Outdent |
|Nuovo elemento di lavoro collegato|**MAIUSC+ALT+L**| Team.NewLinkedWorkItem |
|Aggiorna|**F5**| Team.Refresh |
|Toggle|**MAIUSC+ALT+V**| Window.Toggle |

### <a name="work-item-results-view-context-specific-shortcuts"></a><a name="bkmk_work-item-results-view-context-specific-shortcuts"></a> Visualizzazione risultati elemento di lavoro: scelte rapide specifiche del contesto

I tasti di scelta rapida specifici per questo contesto sono:


|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Creare una copia dell'elemento di lavoro|**MAIUSC+ALT+C**| Edit.CreateCopyofWorkItem |
|Impostare un rientro|**MAIUSC+ALT+Freccia DESTRA**| Edit.Indent |
|Riduci rientro|**MAIUSC+ALT+Freccia SINISTRA**| Edit.Outdent |
|Goto next work item|**MAIUSC+ALT+N**| Team.GotoNextWorkItem |
|Goto previous work item (Goto elemento di lavoro precedente)|**MAIUSC+ALT+P**| Team.GotoPreviousWorkItem |
|Nuovo elemento di lavoro collegato|**MAIUSC+ALT+L**| Team.NewLinkedWorkItem |
|Aggiorna|**F5**| Team.Refresh |
|Toggle|**MAIUSC+ALT+V**| Window.Toggle |

### <a name="workflow-designer-context-specific-shortcuts"></a><a name="bkmk_workflow-designer-context-specific-shortcuts"></a> Progettazione flussi di lavoro: tasti di scelta rapida specifici del contesto

I tasti di scelta rapida specifici per questo contesto sono:


|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Completare una parola|**CTRL+K, W**<br /><br /> oppure<br /><br /> **Ctrl+K, Ctrl+W**<br /><br /> oppure<br /><br /> **CTRL+BARRA SPAZIATRICE**<br /><br /> oppure<br /><br /> **ALT+freccia DESTRA**| Edit.CompleteWord |
|Ridurre il livello di filtro|**ALT+,**| Edit.DecreaseFilterLevel |
|Aumentare il livello di filtro|**ALT+.**| Edit.IncreaseFilterLevel |
|Elencare i membri|**CTRL+K, L**<br /><br /> oppure<br /><br /> **Ctrl+K, Ctrl+L**<br /><br /> oppure<br /><br /> **CTRL+J**| Edit.ListMembers |
|Informazioni sui parametri|**CTRL+K, P**<br /><br /> oppure<br /><br /> **Ctrl+K, Ctrl+P**<br /><br /> oppure<br /><br /> **CTRL+MAIUSC+BARRA SPAZIATRICE**| Edit.ParameterInfo |
|Informazioni rapide|**CTRL+K, I**<br /><br /> oppure<br /><br /> **Ctrl+K, Ctrl+I**| Edit.QuickInfo |
|Comprimi|**CTRL+E, CTRL+C**<br /><br /> oppure<br /><br /> **CTRL+E, C**| WorkflowDesigner.Collapse |
|Comprimi tutto|oppure| WorkflowDesigner.CollapseAll |
|Connessione nodi|**CTRL+E, CTRL+F**<br /><br /> oppure<br /><br /> **CTRL+E, F**| WorkflowDesigner.ConnectNodes |
|Creare una variabile|**CTRL+E, CTRL+N**<br /><br /> oppure<br /><br /> **CTRL+E, N**| WorkflowDesigner.CreateVariable |
|Espandi tutto|**CTRL+E, CTRL+X**<br /><br /> oppure<br /><br /> **CTRL+E, X**| WorkflowDesigner.ExpandAll |
|Espandere sul posto|**CTRL+E, CTRL+E**<br /><br /> oppure<br /><br /> **CTRL+E, E**| WorkflowDesigner.ExpandInPlace |
|Passare all'elemento padre|**CTRL+E, CTRL+P**<br /><br /> oppure<br /><br /> **CTRL+E, P**| WorkflowDesigner.GoToParent |
|Spostare lo stato attivo|**CTRL+E, CTRL+M**<br /><br /> oppure<br /><br /> **Ctrl+E, M**| WorkflowDesigner.MoveFocus |
|Spostarsi all'interno della finestra di progettazione|**CTRL+ALT+F6**| WorkflowDesigner.NavigateThroughDesigner |
|Restore|**CTRL+E, CTRL+R**<br /><br /> oppure<br /><br /> **CTRL+E, R**| WorkflowDesigner.Restore |
|Mostra finestra di progettazione argomenti nascondi|**CTRL+E, CTRL+A**<br /><br /> oppure<br /><br /> **CTRL+E, A**| WorkflowDesigner.ShowHideArgumentDesigner |
|Mostra nascondi finestra di progettazione importazioni|**CTRL+E, CTRL+I**<br /><br /> oppure<br /><br /> **CTRL+E, I**| WorkflowDesigner.ShowHideImportsDesigner |
|Mostra nascondi mappa panoramica|**CTRL+E, CTRL+O** (lettera "O")<br /><br /> oppure<br /><br /> **CTRL+E, O**| WorkflowDesigner.ShowHideOverviewMap |
|Mostra finestra di progettazione delle variabili nascondi|**CTRL+E, CTRL+V**<br /><br /> oppure<br /><br /> **CTRL+E, V**| WorkflowDesigner.ShowHideVariableDesigner |
|Attiva/Disattiva selezione|**CTRL+E, CTRL+S**<br /><br /> oppure<br /><br /> **CTRL+E, S**| WorkflowDesigner.ToggleSelection |
|Zoom avanti|**CTRL+NUM +**| WorkflowDesigner.ZoomIn |
|Zoom indietro|**CTRL+NUM -**| WorkflowDesigner.ZoomOut |

### <a name="xaml-ui-designer-context-specific-shortcuts"></a><a name="bkmk_xaml-ui-designer-context-specific-shortcuts"></a> Finestra di progettazione dell'interfaccia utente XAML: scelte rapide specifiche del contesto

I tasti di scelta rapida specifici per questo contesto sono:


|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Adattare tutto|**CTRL+0** (zero)| Design.FitAll |
|Mostra handle|**F9**| Design.ShowHandles |
|Zoom avanti|**CTRL+ALT+=**| Design.ZoomIn |
|Zoom indietro|**CTRL+ALT+-**| Design.ZoomOut |
|Opzioni per i progettisti|**CTRL+MAIUSC+;**|
|Modificare il testo|**F2**| Format.EditText |
|Tutti|**CTRL+MAIUSC+R**| Format.ResetLayout.All |
|Esegui codice del progetto|**CTRL+F9**|
|Nascondi (solo Blend)|**CTRL+H**| Timeline.Hide (solo Blend) |
|Blocca (solo Blend)|**CTRL+L**| Timeline.Lock (solo Blend) |
|Mostra (solo Blend)|**CTRL+MAIUSC+H**| Timeline.Show (solo Blend) |
|Sblocca (solo Blend)|**CTRL+MAIUSC+L**| Timeline.Unlock (solo Blend) |
|Spostamento a sinistra del bordo verso sinistra|**CTRL+MAIUSC+,**| View.EdgeLeftMoveLeft |
|Spostamento a sinistra del bordo verso destra|**CTRL+MAIUSC+.**| View.EdgeLeftMoveRight |
|Spostamento a destra del bordo verso sinistra|**CTRL+MAIUSC+ALT+,**| View.EdgeRightMoveLeft |
|Spostamento a destra del bordo|**CTRL+MAIUSC+ALT+.**| View.EdgeRightMoveRight |
|Menu Mostra marcatore proprietà|**CTRL+BARRA SPAZIATRICE**| View.ShowPropertyMarkerMenu |

### <a name="xml-text-editor-context-specific-shortcuts"></a><a name="bkmk_xml-text-editor-context-specific-shortcuts"></a> Editor XML (testo): tasti di scelta rapida specifici del contesto

I tasti di scelta rapida specifici per questo contesto sono:


|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Avviare il debug XSLT|**ALT+F5**| XML.StartXSLTDebugging |
|Avviare XSLT senza eseguire il debug|**CTRL+Alt+F5**| XML.StartXSLTWithoutDebugging |

### <a name="xml-schema-designer-context-specific-shortcuts"></a><a name="bkmk_xml-schema-designer-context-specific-shortcuts"></a> Progettazione XML Schema: scelte rapide specifiche del contesto

I tasti di scelta rapida specifici per questo contesto sono:


|Comandi|Tasti di scelta rapida|ID comando|
|-|-|-|
|Dal basso verso l'alto|**ALT+freccia SU**| GraphView.BottomtoTop |
|Da sinistra a destra|**ALT+Freccia DESTRA**| GraphView.LefttoRight |
|Da destra a sinistra|**ALT+freccia SINISTRA**| GraphView.RighttoLeft |
|Dall'alto verso il basso|**ALT+freccia GIÙ**| GraphView.ToptoBottom |
|Rimuovere dall'area di lavoro|**Elimina**| OtherContextMenus.GraphView.RemovefromWorkspace |
|Mostra visualizzazione modello di contenuto|**CTRL+2**| XsdDesigner.ShowContentModelView |
|Mostra visualizzazione grafico|**CTRL+3**| XsdDesigner.ShowGraphView |
|Mostra visualizzazione iniziale|**CTRL+1**| XsdDesigner.ShowStartView |

