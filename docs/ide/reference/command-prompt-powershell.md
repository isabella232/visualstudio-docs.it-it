---
title: Shell della riga di comando & prompt per gli sviluppatori
description: Avviare dal menu Strumenti > riga di comando. Visual Studio Prompt dei comandi per gli sviluppatori, PowerShell per sviluppatori e il terminale consentono di usare più facilmente gli strumenti .NET e C++.
author: TerryGLee
ms.author: tglee
ms.date: 06/11/2021
ms.topic: reference
ms.custom: contperf-fy21q4
helpviewer_keywords:
- Visual Studio command prompt
- command prompt, Visual Studio
- Developer Command Prompt
- Developer PowerShell
- Visual Studio terminal
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
no-loc: cmdlet
ms.openlocfilehash: fef783475304bb1faa1788bde591a22ed610d528
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628775"
---
# <a name="visual-studio-developer-command-prompt-and-developer-powershell"></a>Visual Studio Prompt dei comandi per gli sviluppatori PowerShell per sviluppatori

Visual Studio 2019 include due shell della riga di comando per gli sviluppatori:

- **Visual Studio Prompt dei comandi per gli sviluppatori:** prompt dei comandi standard con determinate variabili di ambiente impostate per semplificare l'uso degli strumenti di sviluppo da riga di comando. Disponibile a partire Visual Studio 2015.

- **Visual Studio PowerShell per sviluppatori:** più potente di un prompt dei comandi. Ad esempio, è possibile passare l'output di un comando (noto come ) a *cmdlet* un altro cmdlet . Questa shell ha le stesse variabili di ambiente impostate Prompt dei comandi per gli sviluppatori. Disponibile a partire Visual Studio 2019.

:::image type="content" source="media/developer-command-prompt-for-vs/command-prompt.png" alt-text="Prompt dei comandi per gli sviluppatori per Visual Studio lo strumento clrver":::

A partire Visual Studio 2019 versione 16.5, Visual Studio include un **terminale** integrato che può ospitare una di queste shell (Prompt dei comandi per gli sviluppatori e PowerShell per sviluppatori). È anche possibile aprire più schede di ogni shell. Il terminale Visual Studio è basato su [Terminale Windows](/windows/terminal/). Per aprire il terminale in Visual Studio, scegliere **Visualizza**  >  **terminale.**

:::image type="content" source="media/developer-command-prompt-for-vs/vs-terminal.png" alt-text="Visual Studio terminale che mostra più schede":::

Quando si apre una delle shell per sviluppatori da Visual Studio, come app separata o nella finestra terminale, si apre la directory della soluzione corrente (se è stata caricata una soluzione). Questo comportamento semplifica l'esecuzione di comandi sulla soluzione o i relativi progetti.

Entrambe le shell hanno variabili di ambiente specifiche impostate che consentono di usare più facilmente gli strumenti di sviluppo da riga di comando. Dopo aver aperto una di queste shell, è possibile immettere i comandi per utilità diverse senza dover sapere dove si trovano. 

|Comandi comuni|Descrizione|
|--|--|
|[`MSBuild`](../../msbuild/msbuild-command-line-reference.md)|Compilare un progetto o una soluzione|
|[`clrver`](/dotnet/framework/tools/clrver-exe-clr-version-tool)| Strumento [.NET Framework per](/dotnet/framework/tools/index) CLR|
|[`ildasm`](/dotnet/framework/tools/ildasm-exe-il-disassembler)|Strumento [.NET Framework per](/dotnet/framework/tools/index) il disassembler|
|[`dotnet`](/dotnet/core/tools/dotnet)|Comando [dell'interfaccia della riga di comando .NET](/dotnet/core/tools/index)|
|[`dotnet run`](/dotnet/core/tools/dotnet-run)|Comando [dell'interfaccia della riga di comando .NET](/dotnet/core/tools/index)|
|[`CL`](/cpp/build/reference/compiler-command-line-syntax)|Strumento di compilazione C/C++|
|[`NMAKE`](/cpp/build/reference/running-nmake)|Strumento di compilazione C/C++|
|[`LIB`](/cpp/build/reference/lib-reference)| Strumento di compilazione C/C++|
|[`DUMPBIN`](/cpp/build/reference/dumpbin-reference)| Strumento di compilazione C/C++|


## <a name="start-in-visual-studio"></a>Iniziare da Visual Studio

Seguire questa procedura per aprire powershell Prompt dei comandi per gli sviluppatori o Developer dall'interno Visual Studio:

1. Aprire Visual Studio.

1. Sulla barra dei menu scegliere **Strumenti**  >  **Riga di comando Prompt dei comandi per gli sviluppatori** o  >   **PowerShell per sviluppatori.**

   ![Voce di menu del prompt dei comandi in Visual Studio](./media/developer-command-prompt-for-vs/vs-menu.png)

## <a name="start-from-windows-menu"></a>Avviare dal menu Windows

Un altro modo per avviare le shell è dalla menu Start. Possono essere presenti più prompt dei comandi, a seconda della versione di Visual Studio e di eventuali SDK e carichi di lavoro aggiuntivi installati. 

### <a name="windows-10"></a>Windows 10

1. Selezionare **Start** ![ Windows il tasto logo sulla tastiera.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) e scorrere fino alla lettera **V**.

1. Espandere la **Visual Studio 2019.**

1. Scegliere **Prompt dei comandi per gli sviluppatori per Visual Studio 2019** o **PowerShell per sviluppatori per VS 2019.**

   In alternativa, è possibile iniziare a digitare il nome della shell nella casella di ricerca sulla barra delle applicazioni e scegliere il risultato desiderato quando l'elenco dei risultati inizia a visualizzare le corrispondenze di ricerca.

   ![Gif animata che mostra il comportamento di ricerca in Windows 10](./media/developer-command-prompt-for-vs/windows-10-search.gif)

### <a name="windows-81"></a>Windows 8.1

1. Andare alla schermata **Start** ad esempio premendo il tasto WINDOWS![tasto WINDOWS sulla tastiera.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) sulla tastiera.

1. Nella schermata **Start** premere **CTRL TAB** + **per** aprire l'elenco App e quindi premere **V**.  Verrà visualizzato un elenco che include tutti i prompt dei Visual Studio installati.

1. Scegliere **Prompt dei comandi per gli sviluppatori per Visual Studio 2019** o **PowerShell per sviluppatori per VS 2019.**

### <a name="windows-7"></a>Windows 7

1. Fare **clic sul pulsante Start** e quindi espandere Tutti i **programmi.**

1. Scegliere **Visual Studio 2019** Strumenti di Visual Studio Prompt dei comandi per gli sviluppatori visual studio  >    >  **2019** o PowerShell per sviluppatori **per VS 2019.**

   ![Windows 7 menu Start con il prompt dei comandi evidenziato](./media/developer-command-prompt-for-vs/windows-7-menu.png)

Se sono installati altri SDK, ad esempio [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) o versioni [precedenti,](https://developer.microsoft.com/windows/downloads/sdk-archive)potrebbero essere visualizzati prompt dei comandi aggiuntivi. Consultare la documentazione dei diversi strumenti per determinare quale versione del prompt dei comandi usare.

## <a name="start-from-file-browser"></a>Avviare dal browser di file 

In genere, i collegamenti per le shell installate vengono inseriti nella cartella **Menu Start** per Visual Studio, ad esempio in *%ProgramData%\Microsoft\Windows\Menu Start\Programmi\Visual Studio 2019\Strumenti di Visual Studio*. Se tuttavia la ricerca del prompt dei comandi non produce i risultati previsti, è possibile provare a individuare manualmente i file nel computer.

### <a name="developer-command-prompt"></a>Prompt dei comandi per gli sviluppatori

Cercare il nome del file del prompt dei comandi, *ovveroVsDevCmd.bat,* o passare alla cartella Strumenti per Visual Studio, ad esempio *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools* (il percorso cambia in base alla versione, all'edizione e al percorso di installazione di Visual Studio).

Dopo aver individuato il file del prompt dei comandi, aprirlo immettendo il comando seguente in una normale finestra del prompt dei comandi:

```cmd
"%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"
```

Oppure immettere il comando seguente nella finestra Windows **finestra di** dialogo Esegui:

```cmd
%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"
```

> [!TIP]
> Sarà necessario modificare il percorso in modo che corrisponda all'Visual Studio installazione.

### <a name="developer-powershell"></a>PowerShell per sviluppatori

Cercare un file script di PowerShell denominato *Launch-VsDevShell.ps1* o passare alla cartella Strumenti per Visual Studio, ad esempio *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools*. Il percorso cambia in base alla versione Visual Studio, all'edizione e al percorso di installazione. Dopo aver individuato il file di PowerShell, eseguirlo immettendo il comando seguente al prompt Windows PowerShell o PowerShell 6:

```powershell
& 'C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\Launch-VsDevShell.ps1'
```

Per impostazione predefinita, l'istanza di PowerShell per sviluppatori che viene avviata è configurata per l'installazione Visual Studio il cui percorso di installazione *Launch-VsDevShell.ps1* in cui si trova il file di installazione.

> [!TIP]
> I [criteri di esecuzione](/powershell/module/microsoft.powershell.core/about/about_execution_policies) devono essere impostati per l'esecuzione di cmdlet .

## <a name="see-also"></a>Vedi anche

- [Terminale Windows](/windows/terminal/)
- [Strumenti di .NET Framework](/dotnet/framework/tools/index)
- [Usare il set di strumenti Microsoft C++ dalla riga di comando](/cpp/build/building-on-the-command-line)
- [Visual Studio Code utenti](https://code.visualstudio.com/docs/cpp/config-msvc#:~:text=To%20open%20the%20Developer%20Command,item%20to%20open%20the%20prompt.)
