---
title: Shell della riga di comando per gli sviluppatori
description: Informazioni su come trovare e usare il Prompt dei comandi per gli sviluppatori per Visual Studio, Developer PowerShell e Visual Studio Terminal, che consentono di usare più facilmente gli strumenti .NET e C++.
ms.date: 03/04/2021
ms.custom: contperf-fy21q3
helpviewer_keywords:
- Visual Studio command prompt
- command prompt, Visual Studio
- Developer Command Prompt
- Developer PowerShell
- Visual Studio terminal
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
no-loc: cmdlet
ms.openlocfilehash: 406ef4e7d475df82a0e36732dd5e777959ea3b96
ms.sourcegitcommit: 79a6be815244f1cfc7b4123afff29983fce0555c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/06/2021
ms.locfileid: "102249739"
---
# <a name="developer-command-prompt-and-developer-powershell"></a>PowerShell per sviluppatori e Prompt dei comandi per gli sviluppatori

Visual Studio 2019 include due shell della riga di comando per gli sviluppatori:

- **Prompt dei comandi per gli sviluppatori per Visual Studio** : un prompt dei comandi standard con determinate variabili di ambiente impostate per semplificare l'uso degli strumenti di sviluppo da riga di comando.
- **Developer PowerShell** : più potente di un prompt dei comandi. Ad esempio, è possibile passare l'output di un comando (noto come *cmdlet* ) a un altro cmdlet . Questa shell ha le stesse variabili di ambiente impostate come Prompt dei comandi per gli sviluppatori.

Per entrambe le shell sono impostate variabili di ambiente specifiche che consentono di usare più facilmente gli strumenti di sviluppo da riga di comando. Dopo aver aperto una di queste shell, è possibile immettere i comandi per le diverse utilità senza doverne individuare il percorso. I comandi che è possibile eseguire includono:

- [`MSBuild`](../../msbuild/msbuild-command-line-reference.md), per compilare un progetto o una soluzione.
- [Strumenti di .NET Framework](/dotnet/framework/tools/index), ad esempio [`clrver`](/dotnet/framework/tools/clrver-exe-clr-version-tool) e [`ildasm`](/dotnet/framework/tools/ildasm-exe-il-disassembler) .
- Strumenti di compilazione C/C++, ad esempio [`CL`](/cpp/build/reference/compiler-command-line-syntax) e [`NMAKE`](/cpp/build/reference/running-nmake) .
- Strumenti di compilazione C/C++ aggiuntivi, ad esempio [`LIB`](/cpp/build/reference/lib-reference) e [`DUMPBIN`](/cpp/build/reference/dumpbin-reference) .
- [Comandi dell'interfaccia](/dotnet/core/tools/index)della riga di comando di .NET, ad esempio [`dotnet`](/dotnet/core/tools/dotnet) e [`dotnet run`](/dotnet/core/tools/dotnet-run) . Questi comandi sono disponibili anche da un prompt dei comandi normale.

:::image type="content" source="media/developer-command-prompt-for-vs/command-prompt.png" alt-text="Prompt dei comandi per gli sviluppatori per Visual Studio che mostra lo strumento Clrver":::

A partire da Visual Studio 2019 versione 16,5, Visual Studio include un **terminale** integrato che può ospitare uno di questi gusci (prompt dei comandi per gli sviluppatori e PowerShell per sviluppatori). È inoltre possibile aprire più schede di ogni shell. Il terminale di Visual Studio è basato sul [terminale di Windows](/windows/terminal/). Per aprire il terminale in Visual Studio, scegliere **Visualizza**  >  **terminale**.

:::image type="content" source="media/developer-command-prompt-for-vs/vs-terminal.png" alt-text="Terminale di Visual Studio che Mostra più schede":::

Quando si apre una delle shell per sviluppatori da Visual Studio, come un'app separata o nella finestra del terminale, si apre alla directory della soluzione corrente (se è stata caricata una soluzione). Questo comportamento semplifica l'esecuzione dei comandi sulla soluzione o sui relativi progetti.

## <a name="prerequisites"></a>Prerequisiti

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

## <a name="start-the-shell-from-inside-visual-studio"></a>Avviare la Shell dall'interno di Visual Studio

Per aprire Prompt dei comandi per gli sviluppatori o Developer PowerShell da Visual Studio, seguire questa procedura:

1. Aprire Visual Studio.

1. Sulla barra dei menu scegliere **strumenti**  >  **prompt dei comandi per gli sviluppatori riga di comando**  >   o **Developer PowerShell**.

   ![Voce di menu del prompt dei comandi in Visual Studio](./media/developer-command-prompt-for-vs/vs-menu.png)

## <a name="use-the-windows-start-menu"></a>Usare il menu Start di Windows

È possibile che siano presenti più prompt dei comandi, a seconda della versione di Visual Studio e di eventuali SDK e carichi di lavoro aggiuntivi installati. Se i passaggi seguenti non funzionano, è possibile provare a [individuare manualmente i file nel computer](#manually-locate-the-file) o [avviare la Shell dall'interno di Visual Studio](#start-the-shell-from-inside-visual-studio).

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

## <a name="manually-locate-the-file"></a>Individuare manualmente il file

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
