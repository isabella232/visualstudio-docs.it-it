---
title: Eseguire il debug di XAML in Blend | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 29a37182-2a2c-47e4-a4a9-2d5412738fed
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: beea8cd3ad6ac12bef284e0d5fda9e995a8613c5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434089"
---
# <a name="debug-xaml-in-blend"></a>Debug XAML in Blend
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puoi usare gli strumenti disponibili in [!INCLUDE[blend_first](../includes/blend-first-md.md)] per eseguire il debug del codice XAML nell'app. Quando compili un progetto, eventuali errori vengono visualizzati nel pannello **Risultati**. Fai doppio clic su un errore per trovare il markup correlato all'errore. Se desideri avere più spazio per lavorare, puoi nascondere il pannello **Risultati** premendo F12.  
  
## <a name="syntax-errors"></a>Errori di sintassi  
 Si verificano errori di sintassi se il codice XAML o i file code-behind non rispettano le regole di formattazione del linguaggio. La descrizione dell'errore ti aiuterà a capire come risolverlo. L'elenco specifica anche il nome del file e il numero della riga in cui è presente l'errore. Gli errori XAML sono elencati nella scheda **Markup** del pannello **Risultati**.  
  
> [!TIP]
> XAML è un linguaggio di markup basato su XML che segue le regole di sintassi XML.  
  
 Di seguito sono elencate alcune cause comuni degli errori di sintassi XAML:  
  
- In una parola chiave è presente un errore di ortografia oppure l'uso delle lettere maiuscole/minuscole non è corretto.  
  
- Le stringhe di testo o gli attributi non sono racchiusi tra virgolette.  
  
- In un elemento XAML manca un tag di chiusura.  
  
- È presente un elemento XAML in una posizione non consentita.  
  
  Per ulteriori informazioni sulla sintassi XAML comune, vedi [Guida alla sintassi XAML di base](http://go.microsoft.com/fwlink/?LinkId=329942).  
  
  Puoi anche identificare e risolvere semplici errori di sintassi code-behind, errori di compilazione ed errori di runtime in [!INCLUDE[blend_subs](../includes/blend-subs-md.md)]. Ricorda, tuttavia, che gli errori code-behind sono più facilmente individuabili e risolvibili in Visual Studio.  
  
### <a name="debugging-sample-xaml-code"></a>Debug di codice XAML di esempio  
 L'esempio riportato di seguito descrive una semplice sessione di debug XAML in [!INCLUDE[blend_subs](../includes/blend-subs-md.md)].  
  
##### <a name="to-create-a-project"></a>Per creare un progetto  
  
1. In [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] apri il menu **File**, quindi scegli **Nuovo progetto**.  
  
    Nella finestra di dialogo **Nuovo progetto** viene visualizzato un elenco di tipi di progetto sul lato sinistro. Quando fai clic su un tipo di progetto, i modelli di progetto a esso associati vengono visualizzati a destra.  
  
2. Nell'elenco dei tipi di progetto, fare clic su **XAML (Windows Store)**.  
  
3. Nell'elenco dei modelli di progetto, fare clic su **applicazione vuota**.  
  
4. Nel **Name** casella di testo, digitare `DebuggingSample`.  
  
5. Nella casella di testo **Percorso** verifica il percorso del progetto.  
  
6. Nell'elenco **Linguaggio** fai clic su **Visual C#**, quindi scegli **OK** per creare il progetto.  
  
7. Fai clic con il pulsante destro del mouse sull'area di progettazione, quindi scegli **Visualizza origine** per passare alla visualizzazione **divisa**.  
  
8. Copia il codice seguente facendo clic sul link **Copia** nell'angolo in alto a destra del codice.  
  
   ```  
   <Grid HorizontalAlignment="Left" Height="222" VerticalAlignment="Top>  
        <Button content="Button" x:Mame="Home" HorizontalAlignment="Left" VerticalAlignment="Top"/>  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,38,0,0">  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,75,0,0"/>  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,112,0,0"/>  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top Margin="0,149,0,0"/>  
   </Grid>  
  
   ```  
  
9. Individua l'oggetto**Grid** predefinito e incolla il codice tra i tag **Grid** di apertura e chiusura. Al termine, il codice dovrebbe risultare simile al seguente:  
  
    ```  
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
  
10. Premi CTRL+MAIUSC+B per compilare il progetto.  
  
    Un messaggio di errore ti avvisa che il progetto non può essere compilato e nella parte superiore dell'app appare il pannello **Risultati**, che elenca gli errori.  
  
    ![Eseguire il debug di XAML in Blend per Visual Studio](../debugger/media/blend-debugxaml-xaml.png "blend_debugXAML_XAML")  
  
### <a name="resolving-xaml-errors"></a>Risoluzione degli errori XAML  
 Quando vengono rilevati errori XAML, nell'area di progettazione viene visualizzato un avviso che indica che il progetto contiene markup non valido. Mentre risolvi gli errori, il relativo elenco nel pannello **Risultati** si aggiorna automaticamente. Dopo che avrai risolto tutti gli errori, l'area di progettazione sarà abilitata e visualizzerà l'app.  
  
##### <a name="to-resolve-the-xaml-errors"></a>Per risolvere gli errori XAML  
  
1. Fai doppio clic sul primo errore nell'elenco. La descrizione è "il valore ' <' non è valido in un attributo." Quando fai doppio clic sull'errore, il puntatore trova la posizione corrispondente nel codice. Il valore `<` che precede `Button` è valido e non è un attributo come suggerito nel messaggio di errore. Se osservi la riga di codice precedente, noterai che le virgolette di chiusura per l'attributo `Top` sono mancanti. Digita le virgolette di chiusura. L'elenco degli errori presente nel pannello **Risultati** si aggiorna automaticamente per riflettere le modifiche.  
  
2. Fare doppio clic sulla descrizione "'0' non è valido all'inizio di un nome." `Margin="0,149,0,0"` sembra essere corretto. Nota che la codifica colori di `Margin` non corrisponde alle altre istanze di `Margin` nel codice. Poiché le virgolette di chiusura mancano nella coppia nome/valore precedente (`VerticalAlignment="Top`), `Margin="` viene letto come parte del valore dell'attributo precedente e 0 viene letto come carattere iniziale di una coppia nome/valore. Digita le virgolette di chiusura per `Top`. L'elenco degli errori presente nel pannello **Risultati** si aggiorna automaticamente per riflettere le modifiche.  
  
3. Fai doppio clic sull'errore rimanente, "Tag XML di chiusura 'Button' non corrispondente". Il puntatore si trova in corrispondenza del tag **Grid** di chiusura (`</Grid>`), suggerendo che l'errore si trova all'interno dell'oggetto `Grid`. Nota che il secondo oggetto `Button` è privo del tag di chiusura. Dopo aver aggiunto il tag `/` di chiusura, l'elenco del pannello **Risultati** viene aggiornato. Ora che questi errori iniziali sono stati risolti, ne vengono identificati altri due.  
  
4. Fai doppio clic su "Membro 'content' non riconosciuto o non accessibile". `c` in `content` deve essere maiuscolo. Sostituisci la lettera "c" minuscola con una "c" maiuscola.  
  
5. Fare doppio clic su "la proprietà 'Mame' non esiste nel '<http://schemas.microsoft.com/winfx/2006/xaml>' dello spazio dei nomi." La "M" di "Mame" dovrebbe essere una "N". Sostituisci la lettera "M" con una "N". Ora che il codice XAML può essere analizzato, l'app compare nell'area di progettazione.  
  
    ![Debug di XAML in Blend per Visual Studio](../debugger/media/blend-debugartboard-xaml.png "blend_debugArtboard_XAML")  
  
    Premi CTRL+MAIUSC+B per compilare il progetto e confermare che non vi sono altri errori.  
  
## <a name="debugging-in-visual-studio"></a>Debug in Visual Studio  
 Puoi aprire progetti [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] in Visual Studio per eseguire più facilmente il debug del codice nell'app. Per aprire un progetto di [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] in Visual Studio, fai clic con il pulsante destro del mouse sul progetto nel pannello **Progetti**, quindi scegli **Modifica in Visual Studio**. Una volta completata la sessione di debug in Visual Studio, premi CTRL+MAIUSC+S per salvare tutte le modifiche e poi torna a [!INCLUDE[blend_subs](../includes/blend-subs-md.md)]. Ti verrà chiesto di ricaricare il progetto. Fai clic su **Sì tutti** per continuare a lavorare in [!INCLUDE[blend_subs](../includes/blend-subs-md.md)].  
  
 Per altre informazioni sul debug dell'app, vedere [app di Debug Windows Store in Visual Studio](http://go.microsoft.com/fwlink/?LinkId=329944).  
  
## <a name="getting-help"></a>Per ulteriori informazioni  
 Se è necessario ulteriori informazioni sul debug di [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] app, è possibile cercare la [forum delle community delle app Windows Store](http://go.microsoft.com/fwlink/?LinkId=280308) per post correlati al problema riscontrato oppure inserire una domanda.
