---
title: Shell della riga di comando & prompt per gli sviluppatori
description: Avviare dal menu strumenti > riga di comando. Visual Studio Prompt dei comandi per gli sviluppatori, Developer PowerShell e terminal consentono di usare più facilmente gli strumenti .NET e C++.
ms.date: 04/11/2021
ms.custom: contperf-fy21q4
helpviewer_keywords:
- Visual Studio command prompt
- command prompt, Visual Studio
- Developer Command Prompt
- Developer PowerShell
- Visual Studio terminal
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
no-loc: cmdlet
ms.openlocfilehash: 57cbc93f4b6e8cf64dd5149462788e0cde833350
ms.sourcegitcommit: 52b093e000334f53d87c6165d1418347e4f45dec
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2021
ms.locfileid: "107221731"
---
# <a name="visual-studio-developer-command-prompt-and-developer-powershell"></a>Visual Studio Prompt dei comandi per gli sviluppatori e PowerShell per sviluppatori

Visual Studio 2019 include due shell della riga di comando per gli sviluppatori:

- **Visual Studio prompt dei comandi per gli sviluppatori** : un prompt dei comandi standard con determinate variabili di ambiente impostate per semplificare l'uso degli strumenti di sviluppo da riga di comando. Disponibile a partire da Visual Studio 2015.

- **PowerShell per sviluppatori di Visual Studio** : più potente di un prompt dei comandi. Ad esempio, è possibile passare l'output di un comando (noto come *cmdlet* ) a un altro cmdlet . Questa shell ha le stesse variabili di ambiente impostate come Prompt dei comandi per gli sviluppatori. Disponibile a partire da Visual Studio 2019.


:::image type="content" source="media/developer-command-prompt-for-vs/command-prompt.png" alt-text="Prompt dei comandi per gli sviluppatori per Visual Studio che mostra lo strumento Clrver":::

A partire da Visual Studio 2019 versione 16,5, Visual Studio include un **terminale** integrato che può ospitare uno di questi gusci (prompt dei comandi per gli sviluppatori e PowerShell per sviluppatori). È inoltre possibile aprire più schede di ogni shell. Il terminale di Visual Studio è basato sul [terminale di Windows](/windows/terminal/). Per aprire il terminale in Visual Studio, scegliere **Visualizza**  >  **terminale**.

:::image type="content" source="media/developer-command-prompt-for-vs/vs-terminal.png" alt-text="Terminale di Visual Studio che Mostra più schede":::

Quando si apre una delle shell per sviluppatori da Visual Studio, come un'app separata o nella finestra del terminale, si apre alla directory della soluzione corrente (se è stata caricata una soluzione). Questo comportamento semplifica l'esecuzione dei comandi sulla soluzione o sui relativi progetti.

Per entrambe le shell sono impostate variabili di ambiente specifiche che consentono di usare più facilmente gli strumenti di sviluppo da riga di comando. Dopo aver aperto una di queste shell, è possibile immettere i comandi per le diverse utilità senza doverne individuare il percorso. 

|Comandi comuni|Descrizione|
|--|--|
|[`MSBuild`](../../msbuild/msbuild-command-line-reference.md)|Compilare un progetto o una soluzione|
|[`clrver`](/dotnet/framework/tools/clrver-exe-clr-version-tool)| [Strumenti di .NET Framework](/dotnet/framework/tools/index) per CLR.|
|[`ildasm`](/dotnet/framework/tools/ildasm-exe-il-disassembler)|[Strumento .NET Framework](/dotnet/framework/tools/index) per disassembler.|
|[`dotnet`](/dotnet/core/tools/dotnet)|[Comando CLI .NET](/dotnet/core/tools/index)|
|[`dotnet run`](/dotnet/core/tools/dotnet-run)|[Comando CLI .NET](/dotnet/core/tools/index)|
|[`CL`](/cpp/build/reference/compiler-command-line-syntax)|Strumento di compilazione C/C++|
|[`NMAKE`](/cpp/build/reference/running-nmake)|Strumento di compilazione C/C++|
|[`LIB`](/cpp/build/reference/lib-reference)| Strumento di compilazione C/C++|
|[`DUMPBIN`](/cpp/build/reference/dumpbin-reference)| Strumento di compilazione C/C++|


## <a name="start-in-visual-studio"></a>Inizia in Visual Studio

Per aprire Prompt dei comandi per gli sviluppatori o Developer PowerShell da Visual Studio, seguire questa procedura:

1. Aprire Visual Studio.

1. Sulla barra dei menu scegliere **strumenti**  >  **prompt dei comandi per gli sviluppatori riga di comando**  >   o **Developer PowerShell**.

   ![Voce di menu del prompt dei comandi in Visual Studio](./media/developer-command-prompt-for-vs/vs-menu.png)

## <a name="start-from-windows-menu"></a>Avvio dal menu Windows

Un altro modo per avviare le shell è dal menu Start. È possibile che siano presenti più prompt dei comandi, a seconda della versione di Visual Studio e di eventuali SDK e carichi di lavoro aggiuntivi installati. 

### <a name="windows-10"></a>Windows 10

1. Selezionare **Avvia** ![ il tasto logo Windows sulla tastiera.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) e scorrere fino alla lettera **V**.

1. Espandere la cartella **Visual Studio 2019** .

1. Scegliere **prompt dei comandi per gli sviluppatori per vs 2019** o **Developer PowerShell per vs 2019**.

   In alternativa, è possibile iniziare a digitare il nome della shell nella casella di ricerca sulla barra delle applicazioni e scegliere il risultato desiderato, in quanto l'elenco dei risultati inizia a visualizzare le corrispondenze di ricerca.

   ![Gif animata che mostra il comportamento di ricerca in Windows 10](./media/developer-command-prompt-for-vs/windows-10-search.gif)

### <a name="windows-81"></a>Windows 8.1

1. Andare alla schermata **Start** ad esempio premendo il tasto WINDOWS![tasto WINDOWS sulla tastiera.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) sulla tastiera.

1. Nella schermata **Start** premere **CTRL** + **Tab** per aprire l'elenco **app** e quindi premere **V**. Viene visualizzato un elenco che include tutti i prompt dei comandi di Visual Studio installati.

1. Scegliere **prompt dei comandi per gli sviluppatori per vs 2019** o **Developer PowerShell per vs 2019**.

### <a name="windows-7"></a>Windows 7

1. Scegliere **Start** , quindi espandere **tutti i programmi**.

1. Scegliere **Visual Studio 2019**  >  **strumenti di Visual Studio**  >  **prompt dei comandi per gli sviluppatori per vs 2019** o **Developer PowerShell per vs 2019**.

   ![Menu Start di Windows 7 con il prompt dei comandi evidenziato](./media/developer-command-prompt-for-vs/windows-7-menu.png)

Se sono installati altri SDK, ad esempio [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) o [versioni precedenti](https://developer.microsoft.com/windows/downloads/sdk-archive), è possibile visualizzare prompt dei comandi aggiuntivi. Consultare la documentazione dei diversi strumenti per determinare quale versione del prompt dei comandi usare.

## <a name="start-from-file-browser"></a>Avvia da file browser 

In genere, i tasti di scelta rapida per le shell installate vengono inseriti nella cartella del **menu Start** per Visual Studio, ad esempio in *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019 \ strumenti di Visual Studio*. Tuttavia, se la ricerca del prompt dei comandi non produce i risultati previsti, è possibile provare a individuare manualmente i file nel computer.

### <a name="developer-command-prompt"></a>Prompt dei comandi per gli sviluppatori

Cercare il nome del file del prompt dei comandi, che è *VsDevCmd.bat* o passare alla cartella strumenti di Visual Studio, ad esempio *% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Community\Common7\Tools* (percorso modificato in base alla versione, all'edizione e al percorso di installazione di Visual Studio).

Dopo aver individuato il file del prompt dei comandi, aprirlo immettendo il comando seguente in una normale finestra del prompt dei comandi:

```cmd
"%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"
```

In alternativa, immettere il comando seguente nella finestra di dialogo Windows **Run** :

```cmd
%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"
```

> [!TIP]
> È necessario modificare il percorso in modo che corrisponda all'installazione di Visual Studio.

### <a name="developer-powershell"></a>PowerShell per sviluppatori

Cercare un file di script di PowerShell denominato *Launch-VsDevShell.ps1* o passare alla cartella strumenti di Visual Studio, ad esempio *% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Community\Common7\Tools*. Il percorso cambia in base alla versione, all'edizione e al percorso di installazione di Visual Studio. Dopo aver individuato il file di PowerShell, eseguirlo immettendo il comando seguente in un prompt di Windows PowerShell o PowerShell 6:

```powershell
& 'C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\Launch-VsDevShell.ps1'
```

Per impostazione predefinita, il PowerShell per sviluppatori che avvia viene configurato per l'installazione di Visual Studio il cui percorso di installazione si trova nel file di *Launch-VsDevShell.ps1* .

> [!TIP]
> È necessario impostare i [criteri di esecuzione](/powershell/module/microsoft.powershell.core/about/about_execution_policies) per consentire l' cmdlet esecuzione di.

## <a name="see-also"></a>Vedi anche

- [PowerShell per sviluppatori](https://devblogs.microsoft.com/visualstudio/the-powershell-you-know-and-love-now-with-a-side-of-visual-studio/)
- [Salutare il nuovo terminale di Visual Studio](https://devblogs.microsoft.com/visualstudio/say-hello-to-the-new-visual-studio-terminal/)
- [Terminale Windows](/windows/terminal/)
- [Strumenti di .NET Framework](/dotnet/framework/tools/index)
- [Gestire strumenti esterni](../managing-external-tools.md)
- [Usare il set di strumenti di Microsoft C++ dalla riga di comando](/cpp/build/building-on-the-command-line)
