---
title: 'Passaggio 2: Aggiungere un oggetto casuale e un elenco di icone'
description: Informazioni su come creare un set di simboli corrispondenti per il gioco.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
dev_langs:
- CSharp
- VB
ms.assetid: 95faea28-eddc-4cfa-95fb-3b34b5a976d7
author: j-martens
ms.author: jmartens
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 8909162a7eb0ffbdd9694341fa368eb6f8893f88
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122143469"
---
# <a name="step-2-add-a-random-object-and-a-list-of-icons"></a>Passaggio 2: Aggiungere un oggetto casuale e un elenco di icone

In questo passaggio verrà creato un set di simboli corrispondenti per il gioco. Ciascun simbolo viene aggiunto a due celle casuali in TableLayoutPanel nel form. A tale scopo verranno utilizzate due istruzioni `new` per creare due oggetti. Il primo è un oggetto <xref:System.Random>, simile a quello utilizzato nel quiz matematico. Viene utilizzato in questo codice per scegliere casualmente le celle in TableLayoutPanel. Il secondo oggetto, che potrebbe essere nuovo per l'utente, è un oggetto <xref:System.Collections.Generic.List%601> utilizzato per archiviare i simboli scelti in modo casuale.

## <a name="to-add-a-random-object-and-a-list-of-icons"></a>Per aggiungere un oggetto casuale e un elenco di icone

1. In **Esplora soluzioni** scegliere *Form1.cs* se si usa C# o *Form1.vb* se si usa Visual Basic e quindi scegliere Visualizza codice sulla barra dei  >  menu. In alternativa, è possibile premere **F7** oppure fare doppio clic su **Form1** in **Esplora soluzioni**.

     Verrà visualizzato il modulo di codice dietro Form1.

2. Nel codice esistente aggiungere il seguente codice:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb" id="Snippet1":::

      > [!IMPORTANT]
      > Usare il controllo del linguaggio di programmazione in alto a destra in questa pagina per visualizzare il frammento di codice C# o il frammento Visual Basic codice.<br><br>![Controllo del linguaggio di programmazione per Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

      Se si usa C#, assicurarsi di inserire il codice dopo la parentesi graffa di apertura e subito dopo la dichiarazione di classe ( `public partial class Form1 : Form` ). Se si utilizza Visual Basic, inserire il codice subito dopo la dichiarazione di classe (`Public Class Form1`).

3. Quando si aggiunge l'oggetto List, osservare la finestra di **IntelliSense** visualizzata. Di seguito è riportato un esempio in C#, ma viene visualizzato un testo simile quando si aggiunge un elenco in Visual Basic.

     ![Finestra Proprietà con evento Click visualizzato](../ide/media/express_listintellisense.png)<br/>***Finestra di IntelliSense***

    > [!NOTE]
    > La finestra di IntelliSense viene visualizzata solo quando si immette il codice manualmente. Se si utilizzano le operazioni di copia e incolla, il codice non verrà visualizzato.

     Se si analizza il codice (e le note) in piccole sezioni, è più facile da comprendere. I programmi possono usare oggetti elenco per tenere traccia di molti diversi tipi di elementi. Un elenco può contenere numeri, valori true/false, testo o altri oggetti. È anche possibile avere un oggetto elenco che contiene altri oggetti elenco. Gli oggetti contenuti in un elenco sono detti elementi e ogni elenco contiene un solo tipo di elemento. Un elenco di numeri, ad esempio, può contenere solo numeri; non è possibile aggiungervi testo. In modo analogo, non è possibile aggiungere numeri a un elenco di valori true/false.

     Quando si crea un oggetto `List` utilizzando un'istruzione `new`, è necessario specificare il tipo di dati da archiviare al suo interno. Per questo la descrizione comando in cima alla finestra di **IntelliSense** visualizza i tipi di elementi nell'elenco. Questo è anche il significato `List<string>` (in C#) e (in Visual Basic): si tratta di un oggetto che contiene elementi di `List(Of String)` tipo di `List` `string` dati. Il programma usa le stringhe per archiviare il testo, vale a dire l'indicazione contenuta nella descrizione comandi a destra della finestra di **IntelliSense**.

4. Si consideri il Visual Basic necessario creare prima una matrice temporanea, ma in C# l'elenco può essere creato con un'istruzione . Questo perché il linguaggio C# dispone di *inizializzatori di raccolta*, che preparano l'elenco ad accettare valori. In Visual Basic è possibile utilizzare un inizializzatore di raccolta. Tuttavia, per motivi di compatibilità con la versione precedente di Visual Basic, si consiglia di utilizzare il codice precedente.

     Quando si usa un inizializzatore di insieme con un'istruzione `new`, una volta creato il nuovo oggetto List, il programma vi inserisce i dati forniti tra parentesi graffe. In questo caso, si ottiene un elenco di icone con nomi in formato stringa e l'elenco sarà inizializzato in modo da contenere sedici stringhe. Ognuna di quelle stringhe è una singola lettera, e insieme corrispondono alle icone che saranno nelle etichette. Il gioco conterrà quindi una coppia di punti esclamativi, una coppia di lettere N maiuscole, una coppia di virgole e così via. Quando questi caratteri sono impostati sul tipo di carattere Webdings, verranno visualizzati come simboli, ad esempio un bus, una bicicletta, un bus e così via. L'oggetto elenco avrà sedici stringhe in tutto, una per ogni cella nel pannello TableLayoutPanel.

    > [!NOTE]
    > In Visual Basic si ottiene lo stesso risultato, ma prima le stringhe vengono inserite in una matrice temporanea, che viene quindi convertita in un oggetto elenco. Una matrice è simile a un elenco, salvo ad esempio che le matrici vengono create con una dimensione fissa. Gli elenchi possono essere ridotti o ingranditi in base alle necessità, caratteristica importante in questo programma.

## <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione

- Per andare al passaggio successivo dell'esercitazione, vedere [**Passaggio 3: Assegnare un'icona casuale a ogni etichetta.**](../ide/step-3-assign-a-random-icon-to-each-label.md)

- Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 1: Creare un progetto e aggiungere una tabella al modulo.](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)
