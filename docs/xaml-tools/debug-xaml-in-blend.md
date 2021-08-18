---
title: Eseguire il debug di XAML in Blend | Microsoft Docs
description: Informazioni su come usare gli strumenti in Blend per Visual Studio rilevare, eseguire il debug e risolvere gli errori XAML nell'app.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 29a37182-2a2c-47e4-a4a9-2d5412738fed
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xaml-tools
ms.workload:
- uwp
ms.openlocfilehash: 5cd32b2eab82cd148bec4f21fa7a6f5e1f95c5b9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122135091"
---
# <a name="debug-xaml-in-blend"></a>Debug XAML in Blend

È possibile usare gli strumenti in Blend per Visual Studio eseguire il debug del codice XAML nell'app. Quando compili un progetto, eventuali errori vengono visualizzati nel pannello **Risultati**. Fai doppio clic su un errore per trovare il markup correlato all'errore. Se è necessario più spazio per lavorare, è possibile nascondere **il** pannello Risultati premendo **F12.**

## <a name="syntax-errors"></a>Errori di sintassi

Si verificano errori di sintassi se il codice XAML o i file code-behind non rispettano le regole di formattazione del linguaggio. La descrizione dell'errore ti aiuterà a capire come risolverlo. L'elenco specifica anche il nome del file e il numero della riga in cui è presente l'errore. Gli errori XAML sono elencati nella scheda **Markup** del pannello **Risultati**.

> [!TIP]
> XAML è un linguaggio di markup basato su XML che segue le regole di sintassi XML.

Di seguito sono elencate alcune cause comuni degli errori di sintassi XAML:

- In una parola chiave è presente un errore di ortografia oppure l'uso delle lettere maiuscole/minuscole non è corretto.

- Le stringhe di testo o gli attributi non sono racchiusi tra virgolette.

- In un elemento XAML manca un tag di chiusura.

- È presente un elemento XAML in una posizione non consentita.

Per ulteriori informazioni sulla sintassi XAML comune, vedi [Guida alla sintassi XAML di base](/windows/uwp/xaml-platform/xaml-syntax-guide).

È anche possibile identificare e risolvere semplici errori di sintassi code-behind, errori di compilazione ed errori di runtime in Blend. Ricorda, tuttavia, che gli errori code-behind sono più facilmente individuabili e risolvibili in Visual Studio.

### <a name="debugging-sample-xaml-code"></a>Debug di codice XAML di esempio

L'esempio seguente illustra una semplice sessione di debug XAML in Blend.

#### <a name="to-create-a-project"></a>Per creare un progetto

1. In Blend aprire il menu **File** e quindi fare clic su **Nuovo Project**.

    Nella finestra di dialogo **Nuovo progetto** viene visualizzato un elenco di tipi di progetto sul lato sinistro. Quando fai clic su un tipo di progetto, i modelli di progetto a esso associati vengono visualizzati a destra.

2. Nell'elenco dei tipi di progetto fare clic **Windows universale.**

3. Nell'elenco dei modelli di progetto fare clic **su App vuota (universal Windows)**.

4. Nella casella **di** testo Nome digitare `DebuggingSample` .

5. Nella casella di testo **Percorso** verifica il percorso del progetto.

6. Nell'elenco **Linguaggio** fai clic su **Visual C#**, quindi scegli **OK** per creare il progetto.

7. Fai clic con il pulsante destro del mouse sull'area di progettazione, quindi scegli **Visualizza origine** per passare alla visualizzazione **divisa**.

8. Copia il codice seguente facendo clic sul link **Copia** nell'angolo in alto a destra del codice.

   ```xml
   <Grid HorizontalAlignment="Left" Height="222" VerticalAlignment="Top>
        <Button content="Button" x:Mame="Home" HorizontalAlignment="Left" VerticalAlignment="Top"/>
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,38,0,0">
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,75,0,0"/>
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,112,0,0"/>
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top Margin="0,149,0,0"/>
   </Grid>
   ```

9. Individua l'oggetto **Grid** predefinito e incolla il codice tra i tag **Grid** di apertura e chiusura. Al termine, il codice dovrebbe risultare simile al seguente:

    ```xml
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
         <Grid HorizontalAlignment="Left" Height="222" VerticalAlignment="Top>
              <Button content="Button" x:Mame="Home" HorizontalAlignment="Left" VerticalAlignment="Top"/>
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,38,0,0">
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,75,0,0"/>
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,112,0,0"/>
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top Margin="0,149,0,0"/>
         </Grid>
    </Grid>
    ```

10. Premere **CTRL** + **MAIUSC** + **B per** compilare il progetto.

    Un messaggio di errore ti avvisa che il progetto non può essere compilato e nella parte superiore dell'app appare il pannello **Risultati**, che elenca gli errori.

    ![Eseguire il debug di XAML in Blend per Visual Studio](../debugger/media/blend_debugxaml_xaml.png "blend_debugXAML_XAML")

### <a name="resolve-xaml-errors"></a>Risolvere gli errori XAML

Quando vengono rilevati errori XAML, nell'area di progettazione viene visualizzato un avviso che indica che il progetto contiene markup non valido. Mentre risolvi gli errori, il relativo elenco nel pannello **Risultati** si aggiorna automaticamente. Dopo che avrai risolto tutti gli errori, l'area di progettazione sarà abilitata e visualizzerà l'app.

#### <a name="to-resolve-the-xaml-errors"></a>Per risolvere gli errori XAML

1. Fai doppio clic sul primo errore nell'elenco. La descrizione è "Il valore '<' non è valido in un attributo". Quando fai doppio clic sull'errore, il puntatore trova la posizione corrispondente nel codice. Il valore `<` che precede `Button` è valido e non è un attributo come suggerito nel messaggio di errore. Se osservi la riga di codice precedente, noterai che le virgolette di chiusura per l'attributo `Top` sono mancanti. Digita le virgolette di chiusura. L'elenco degli errori presente nel pannello **Risultati** si aggiorna automaticamente per riflettere le modifiche.

2. Fare doppio clic sulla descrizione "'0' non è valido all'inizio di un nome". `Margin="0,149,0,0"` sembra essere ben formato. Nota che la codifica colori di `Margin` non corrisponde alle altre istanze di `Margin` nel codice. Poiché le virgolette di chiusura mancano nella coppia nome/valore precedente (`VerticalAlignment="Top`), `Margin="` viene letto come parte del valore dell'attributo precedente e 0 viene letto come carattere iniziale di una coppia nome/valore. Digita le virgolette di chiusura per `Top`. L'elenco degli errori presente nel pannello **Risultati** si aggiorna automaticamente per riflettere le modifiche.

3. Fai doppio clic sull'errore rimanente, "Tag XML di chiusura 'Button' non corrispondente". Il puntatore si trova in corrispondenza del tag **Grid** di chiusura (`</Grid>`), suggerendo che l'errore si trova all'interno dell'oggetto `Grid`. Nota che il secondo oggetto `Button` è privo del tag di chiusura. Dopo aver aggiunto il tag `/` di chiusura, l'elenco del pannello **Risultati** viene aggiornato. Ora che questi errori iniziali sono stati risolti, ne vengono identificati altri due.

4. Fai doppio clic su "Membro 'content' non riconosciuto o non accessibile". `c` in `content` deve essere maiuscolo. Sostituisci la lettera "c" minuscola con una "c" maiuscola.

5. Fare doppio clic su "La proprietà 'Mame' non esiste nello spazio dei `http://schemas.microsoft.com/winfx/2006/xaml` nomi". La "M" di "Mame" dovrebbe essere una "N". Sostituisci la lettera "M" con una "N". Ora che il codice XAML può essere analizzato, l'app compare nell'area di progettazione.

    ![Debug di XAML in Blend per Visual Studio](../debugger/media/blend_debugartboard_xaml.png "blend_debugArtboard_XAML")

    Premere **CTRL** + **MAIUSC** + **B** per compilare il progetto e verificare che non siano presenti errori rimanenti.

## <a name="debug-in-visual-studio"></a>Eseguire il debug in Visual Studio

È possibile aprire progetti Blend in Visual Studio per eseguire più facilmente il debug del codice nell'app. Per aprire un progetto Blend in Visual Studio, fare  clic con il pulsante destro del mouse sul progetto nel pannello Progetti e quindi scegliere **Modifica in** Visual Studio . Al termine della sessione di debug in Visual Studio, premere CTRL+MAIUSC+S per salvare tutte le modifiche e quindi tornare a Blend. Ti verrà chiesto di ricaricare il progetto. Fare **clic su Sì per tutti** per continuare a lavorare in Blend.

Per altre informazioni sul debug dell'app, vedere [Eseguire il debug di app UWP in Visual Studio](../debugger/debugging-windows-store-and-windows-universal-apps.md).

## <a name="get-help"></a>Ottieni supporto

Per altre informazioni sul debug dell'app Blend, è possibile cercare nei forum della community delle [app UWP](https://social.msdn.microsoft.com/Forums/windowsapps/home?category=windowsapps) i post correlati al problema o pubblicare una domanda.
