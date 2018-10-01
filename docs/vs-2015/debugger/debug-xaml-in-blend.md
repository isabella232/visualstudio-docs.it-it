---
title: Eseguire il debug di XAML in Blend | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 29a37182-2a2c-47e4-a4a9-2d5412738fed
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a1fe1c312c747e25fc1b1e93a51e26d6e67c4a9b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47532067"
---
# <a name="debug-xaml-in-blend"></a>Debug XAML in Blend
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [eseguire il Debug di XAML in Blend](https://docs.microsoft.com/visualstudio/debugger/debug-xaml-in-blend).  
  
Puoi usare gli strumenti disponibili in [!INCLUDE[blend_first](../includes/blend-first-md.md)] per eseguire il debug del codice XAML nell'app. Quando si compila un progetto, eventuali errori vengono visualizzati nei **risultati** pannello. Fai doppio clic su un errore per trovare il markup correlato all'errore. Se è necessario più spazio per lavorare, è possibile nascondere il **risultati** pannello premendo F12.  
  
## <a name="syntax-errors"></a>Errori di sintassi  
 Si verificano errori di sintassi se il codice XAML o i file code-behind non rispettano le regole di formattazione del linguaggio. La descrizione dell'errore ti aiuterà a capire come risolverlo. L'elenco specifica anche il nome del file e il numero della riga in cui è presente l'errore. Gli errori XAML sono elencati nel **Markup** scheda le **risultati** pannello.  
  
> [!TIP]
>  XAML è un linguaggio di markup basato su XML che segue le regole di sintassi XML.  
  
 Di seguito sono elencate alcune cause comuni degli errori di sintassi XAML:  
  
-   In una parola chiave è presente un errore di ortografia oppure l'uso delle lettere maiuscole/minuscole non è corretto.  
  
-   Le stringhe di testo o gli attributi non sono racchiusi tra virgolette.  
  
-   In un elemento XAML manca un tag di chiusura.  
  
-   È presente un elemento XAML in una posizione non consentita.  
  
 Per altre informazioni sulla sintassi XAML comune, vedere [Guida alla sintassi XAML di base](http://go.microsoft.com/fwlink/?LinkId=329942).  
  
 Puoi anche identificare e risolvere semplici errori di sintassi code-behind, errori di compilazione ed errori di runtime in [!INCLUDE[blend_subs](../includes/blend-subs-md.md)]. Ricorda, tuttavia, che gli errori code-behind sono più facilmente individuabili e risolvibili in Visual Studio.  
  
### <a name="debugging-sample-xaml-code"></a>Debug di codice XAML di esempio  
 L'esempio riportato di seguito descrive una semplice sessione di debug XAML in [!INCLUDE[blend_subs](../includes/blend-subs-md.md)].  
  
##### <a name="to-create-a-project"></a>Per creare un progetto  
  
1.  Nelle [!INCLUDE[blend_subs](../includes/blend-subs-md.md)], aprire il **File** menu e quindi fare clic su **nuovo progetto**.  
  
     Nel **nuovo progetto** nella finestra di dialogo viene visualizzato di un elenco dei tipi di progetto sul lato sinistro. Quando fai clic su un tipo di progetto, i modelli di progetto a esso associati vengono visualizzati a destra.  
  
2.  Nell'elenco dei tipi di progetto, fare clic su **XAML (Windows Store)**.  
  
3.  Nell'elenco dei modelli di progetto, fare clic su **applicazione vuota**.  
  
4.  Nel **Name** casella di testo, digitare `DebuggingSample`.  
  
5.  Nel **posizione** testo casella, verificare il percorso del progetto.  
  
6.  Nel **Language** fare clic su **Visual c#**, quindi fare clic su **OK** per creare il progetto.  
  
7.  Fare doppio clic nell'area di progettazione e quindi fare clic su **Visualizza origine** per passare alla **Split** visualizzazione.  
  
8.  Copiare il codice seguente facendo il **copia** collegamento nell'angolo superiore destro del codice.  
  
    ```  
    <Grid HorizontalAlignment="Left" Height="222" VerticalAlignment="Top>  
         <Button content="Button" x:Mame="Home" HorizontalAlignment="Left" VerticalAlignment="Top"/>  
         <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,38,0,0">  
         <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,75,0,0"/>  
         <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,112,0,0"/>  
         <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top Margin="0,149,0,0"/>  
    </Grid>  
  
    ```  
  
9. Individuare il valore predefinito **griglia**e incollare il codice tra l'apertura e chiusura **griglia** tag. Al termine, il codice dovrebbe risultare simile al seguente:  
  
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
  
 Viene visualizzato un messaggio di errore ti avvisa che non è possibile compilare il progetto, e il **risultati** pannello elenca gli errori viene visualizzato nella parte inferiore dell'app.  
  
 ![Eseguire il debug di XAML in Blend per Visual Studio](../debugger/media/blend-debugxaml-xaml.png "blend_debugXAML_XAML")  
  
### <a name="resolving-xaml-errors"></a>Risoluzione degli errori XAML  
 Quando vengono rilevati errori XAML, nell'area di progettazione viene visualizzato un avviso che indica che il progetto contiene markup non valido. Mentre Risolvi gli errori, l'elenco degli errori nel **risultati** pannello viene aggiornato. Dopo che avrai risolto tutti gli errori, l'area di progettazione sarà abilitata e visualizzerà l'app.  
  
##### <a name="to-resolve-the-xaml-errors"></a>Per risolvere gli errori XAML  
  
1.  Fai doppio clic sul primo errore nell'elenco. La descrizione è "Il valore '<' non è valido in un attributo". Quando fai doppio clic sull'errore, il puntatore trova la posizione corrispondente nel codice. Il valore `<` che precede `Button` è valido e non è un attributo come suggerito nel messaggio di errore. Se osservi la riga di codice precedente, noterai che le virgolette di chiusura per l'attributo `Top` sono mancanti. Digita le virgolette di chiusura. Si noti che l'errore nell'elenco il **risultati** pannello Aggiorna automaticamente per riflettere le modifiche.  
  
2.  Fare doppio clic sulla descrizione "'0' non è valido all'inizio di un nome." `Margin="0,149,0,0"` sembra essere corretto. Nota che la codifica colori di `Margin` non corrisponde alle altre istanze di `Margin` nel codice. Poiché le virgolette di chiusura mancano nella coppia nome/valore precedente (`VerticalAlignment="Top`), `Margin="` viene letto come parte del valore dell'attributo precedente e 0 viene letto come carattere iniziale di una coppia nome/valore. Digita le virgolette di chiusura per `Top`. L'elenco di errori nel **risultati** pannello Aggiorna automaticamente per riflettere le modifiche.  
  
3.  Fai doppio clic sull'errore rimanente, "Tag XML di chiusura 'Button' non corrispondente". Il puntatore è posizionato alla chiusura **griglia** tag (`</Grid>`), suggerendo che l'errore si trova all'interno di `Grid` oggetto. Nota che il secondo oggetto `Button` è privo del tag di chiusura. Dopo aver aggiunto la chiusura `/`, il **risultati** pannello elenco viene aggiornato. Ora che questi errori iniziali sono stati risolti, ne vengono identificati altri due.  
  
4.  Fai doppio clic su "Membro 'content' non riconosciuto o non accessibile". `c` in `content` deve essere maiuscolo. Sostituisci la lettera "c" minuscola con una "c" maiuscola.  
  
5.  Fare doppio clic su "la proprietà 'Mame' non esiste nel 'http://schemas.microsoft.com/winfx/2006/xaml' dello spazio dei nomi." La "M" di "Mame" dovrebbe essere una "N". Sostituisci la lettera "M" con una "N". Ora che il codice XAML può essere analizzato, l'app compare nell'area di progettazione.  
  
     ![Debug di XAML in Blend per Visual Studio](../debugger/media/blend-debugartboard-xaml.png "blend_debugArtboard_XAML")  
  
     Premi CTRL+MAIUSC+B per compilare il progetto e confermare che non vi sono altri errori.  
  
## <a name="debugging-in-visual-studio"></a>Debug in Visual Studio  
 Puoi aprire progetti [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] in Visual Studio per eseguire più facilmente il debug del codice nell'app. Per aprire una [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] del progetto in Visual Studio, fare clic sul progetto nel **progetti** pannello e quindi fare clic su **modifica in Visual Studio**. Una volta completata la sessione di debug in Visual Studio, premi CTRL+MAIUSC+S per salvare tutte le modifiche e poi torna a [!INCLUDE[blend_subs](../includes/blend-subs-md.md)]. Ti verrà chiesto di ricaricare il progetto. Fare clic su **Sì a tutti** per continuare a utilizzare [!INCLUDE[blend_subs](../includes/blend-subs-md.md)].  
  
 Per altre informazioni sul debug dell'app, vedere [app di Debug Windows Store in Visual Studio](http://go.microsoft.com/fwlink/?LinkId=329944).  
  
## <a name="getting-help"></a>Per ulteriori informazioni  
 Se è necessario ulteriori informazioni sul debug di [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] app, è possibile cercare la [forum delle community delle app Windows Store](http://go.microsoft.com/fwlink/?LinkId=280308) per post correlati al problema riscontrato oppure inserire una domanda.



