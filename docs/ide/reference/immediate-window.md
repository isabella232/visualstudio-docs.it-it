---
title: Finestra di controllo immediato
description: Informazioni su come usare la finestra Controllo immediato per eseguire il debug e la valutazione di espressioni, eseguire istruzioni e stampare valori di variabili.
ms.custom: SEO-VS-2020
ms.date: 02/25/2019
ms.topic: reference
dev_langs:
- VB
f1_keywords:
- VS.ImmediateWindow
helpviewer_keywords:
- design-time expression evaluation
- Immediate window
- first-chance exception notifications
ms.assetid: d33e7937-73f3-4c69-9df0-777a8713c6f2
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 2dcc91c8f7b9fa5cc33d9368d377c2a002b55107
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122157787"
---
# <a name="immediate-window"></a>Controllo immediato (finestra)

Usare la finestra **Controllo immediato** per eseguire il debug e valutare le espressioni, eseguire le istruzioni e stampare i valori delle variabili. La finestra **Immediato** valuta le espressioni creando e usando il progetto correntemente selezionato.

Per visualizzare la finestra **Controllo immediato** aprire un progetto per la modifica e quindi scegliere **Debug** > **Windows** > **Controllo immediato** o premere **CTRL**+**ALT**+**I**. È anche possibile immettere **Debug.Immediate** nella **finestra di comando**.

La finestra **Controllo immediato** supporta IntelliSense.

## <a name="display-the-values-of-variables"></a>Visualizzare i valori delle variabili

La finestra **Controllo immediato** è particolarmente utile durante il debug di un'app. Ad esempio, per controllare il valore di una variabile `varA` , è possibile usare il comando [Stampa](../../ide/reference/print-command.md):

```cmd
>Debug.Print varA
```

Il punto interrogativo (?) è un alias di `Debug.Print`. Questo comando può quindi essere scritto anche nel modo seguente:

```cmd
? varA
```

Entrambe le versioni di questo comando restituiscono il valore della variabile `varA`.

> [!TIP]
> Per immettere un comando di Visual Studio nella finestra **Controllo immediato**, far precedere al comando un segno di maggiore di (>). Per immettere più comandi, passare alla [finestra di comando](command-window.md).

## <a name="design-time-expression-evaluation"></a>Valutazione delle espressioni in fase di progettazione

È possibile utilizzare il **immediato** finestra per eseguire una funzione o subroutine in fase di progettazione.

### <a name="execute-a-function-at-design-time"></a>Eseguire una funzione in fase di progettazione

1. Copiare il codice seguente in un'app console di Visual Basic:

   ```vb
   Module Module1

       Sub Main()
           MyFunction(5)
       End Sub

       Function MyFunction(ByVal input as Integer) As Integer
           Return input * 2
       End Function

   End Module
   ```

2. Nel menu **Debug** scegliere **Finestre** > **Controllo immediato**.

3. Digitare `?MyFunction(2)` nella finestra **Controllo immediato** e premere **INVIO**.

    La finestra **Controllo immediato** esegue `MyFunction` e visualizza `4`.

Se la funzione o la subroutine contiene un punto di interruzione, Visual Studio interrompe l'esecuzione nel punto appropriato. È quindi possibile usare le finestre del debugger per esaminare lo stato del programma. Per altre informazioni, vedere [Procedura dettagliata: debug in fase di progettazione.](../../debugger/walkthrough-debugging-at-design-time.md)

Non è possibile usare la valutazione delle espressioni in fase di progettazione nei tipi di progetto che richiedono l'avvio di un ambiente di esecuzione, tra cui progetti Visual Studio Tools per Office, progetti Web, progetti Smart Device e progetti SQL.

### <a name="design-time-expression-evaluation-in-multi-project-solutions"></a>Valutazione delle espressioni in fase di progettazione nelle soluzioni multiprogetto

Per determinare il contesto di valutazione delle espressioni in fase di progettazione, Visual Studio fa riferimento al progetto selezionato in Esplora soluzioni. Se in Esplora soluzioni non è selezionato nessun progetto, Visual Studio prova a valutare la funzione in base al progetto di avvio. Se la funzione non può essere valutata nel contesto corrente, si riceverà un messaggio di errore. Se si sta tentando di valutare una funzione in un progetto che non è il progetto di avvio per la soluzione e viene visualizzato un errore, provare a selezionare il progetto in Esplora soluzioni e tentare nuovamente la valutazione.

## <a name="enter-commands"></a>Immettere comandi

Immettere il segno di maggiore di (>) per aggiungere comandi di Visual Studio nella finestra **Controllo immediato**. Usare i tasti **FRECCIA SU** e **FRECCIA GIÙ** per scorrere i comandi usati in precedenza.

|Attività|Soluzione|Esempio|
|----------|--------------|-------------|
|Valutare un'espressione.|Anteporre un punto interrogativo (?) all'espressione.|`? a+b`|
|Passare temporaneamente alla modalità di comando mentre è attiva la modalità immediata (per eseguire un singolo comando).|Immettere il comando anteponendo il segno di maggiore (>).|`>alias`|
|Passa alla finestra di comando.|Immettere `cmd` nella finestra anteponendo il segno di maggiore (>).|`>cmd`|
|Tornare alla finestra di controllo immediato.|Immettere `immed` nella finestra senza il segno di maggiore (>)|`immed`|

## <a name="mark-mode"></a>Modalità Indicatore

Quando fa clic su qualsiasi riga precedente nel **immediato** finestra, si passa automaticamente in modalità indicatore. Questa modalità consente di selezionare, modificare e copiare il testo dei comandi precedenti in qualsiasi editor di testo e incollarlo nella riga corrente.

## <a name="examples"></a>Esempio

L'esempio seguente mostra quattro espressioni e i relativi risultati nella finestra **Controllo immediato** per un progetto Visual Basic.

```cmd
j = 2
Expression has been evaluated and has no value

? j
2

j = DateTime.Now.Day
Expression has been evaluated and has no value

? j
26
```

## <a name="first-chance-exception-notifications"></a>Notifiche di eccezioni first-chance

In alcune configurazioni, le notifiche di eccezioni first-chance vengono visualizzate nel **immediato** finestra.

### <a name="toggle-first-chance-exception-notifications-in-the-immediate-window"></a>Attivare o disattivare le notifiche di eccezioni first-chance nella finestra Controllo immediato

1. Scegliere **Altre finestre** dal menu **Visualizza** e quindi fare clic su **Output**.

2. Fare clic con il pulsante destro del mouse sull'area di testo della finestra **Output** e selezionare o deselezionare **Messaggi di eccezione**.

## <a name="see-also"></a>Vedi anche

- [Spostarsi nel codice con il Debugger](../../debugger/navigating-through-code-with-the-debugger.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Presentazione del debugger](../../debugger/debugger-feature-tour.md)
- [Procedura dettagliata: debug in fase di progettazione](../../debugger/walkthrough-debugging-at-design-time.md)
- [Visual Studio Alias dei comandi](../../ide/reference/visual-studio-command-aliases.md)
- [Uso delle espressioni regolari in Visual Studio](../../ide/using-regular-expressions-in-visual-studio.md)
