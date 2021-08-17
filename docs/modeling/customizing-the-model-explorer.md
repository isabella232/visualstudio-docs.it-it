---
title: Personalizzazione di Esplora modelli
description: Informazioni su come modificare l'aspetto e il comportamento di Esplora risorse per la finestra di progettazione del linguaggio specifico di dominio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.dsldesigner.explorerbehavior
helpviewer_keywords:
- Domain-Specific Language Tools, Domain-Specific Language Explorer
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 0fbfa847fb6b5cc2b52a4d3d3d94cfe86e77cb00ba1a05bb09d89bdceec68820
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121231613"
---
# <a name="customizing-the-model-explorer"></a>Personalizzazione di Esplora modelli
È possibile modificare l'aspetto e il comportamento di Esplora risorse per la finestra di progettazione del linguaggio specifico di dominio come indicato di seguito:

- Modificare il titolo della finestra.

- Modificare l'icona della scheda.

- Modificare le icone per i nodi.

- Nascondere i nodi.

## <a name="changing-the-window-title"></a>Modifica del titolo della finestra
 Per modificare il titolo della finestra di esplorazione generata, selezionare Comportamento esplora  **risorse** in **Esplora DSL** e quindi nella finestra Proprietà impostare la proprietà **Titolo** sul titolo desiderato.

## <a name="changing-the-tab-icon"></a>Modifica dell'icona della scheda
 Per modificare l'icona della scheda per lo strumento di esplorazione, usare un'icona di 16 x 16 pixel in un file .bmp file. Inserire il file dell'icona nella cartella \DslPackage\Resources\ e quindi modificare il nome del file **inModelExplorerToolWindowBitmaps.bmp**. Ad esempio, è possibile modificare il file Visual Studio'icona setup.ico .bmp e rinominarlo **inDSLLanguageName\DslPackage\Resources\ModelExplorerToolWindowBitmaps.bmp**. La finestra di progettazione generata visualizza questa icona nella scheda dello explorer quando è ancorata insieme a **Esplora soluzioni**.

## <a name="setting-custom-icons-on-explorer-nodes"></a>Impostazione di icone personalizzate nei nodi di Esplora risorse
 È possibile personalizzare i nodi in Esplora risorse usando le impostazioni dei nodi di Esplora risorse. La procedura seguente illustra come aggiungere un'icona a un nodo.

#### <a name="to-add-an-icon-to-an-explorer-node"></a>Per aggiungere un'icona a un nodo di esplorazione

1. Creare una [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] soluzione usando il modello di Flow attività.

2. Inserire un file .bmp contenente un'icona di 16x16 pixel nella cartella **Dsl\Resources** nella soluzione.

3. In **Esplora DSL fare** clic con il pulsante destro **del mouse** su Comportamento esplora risorse e quindi scegliere Aggiungi nuovo nodo esplora **Impostazioni**.

    Viene **visualizzato un nodo ExplorerNodeSettings** sotto il nodo Nodo personalizzato **Impostazioni** nodo.

4. Selezionare **ExplorerNodeSettings** e quindi nella **finestra Proprietà** impostare **Classe** su **Actor**.

5. Impostare **Icona da visualizzare** sul percorso del file dell'icona.

6. Trasformare tutti i modelli e quindi compilare ed eseguire la soluzione.

7. Nella finestra di progettazione generata aprire il diagramma di esempio.

    In Esplora risorse dovrebbero essere visualizzati tre **nodi Actor** con l'icona.

> [!NOTE]
> Se è stata impostata un'icona del nodo per qualsiasi elemento visualizzato nella finestra di esplorazione generata, tutti i nodi di esplorazione visualizzano l'icona. Se non è stata impostata alcuna icona, nei nodi verrà visualizzata l'icona predefinita.

## <a name="changing-the-name-displayed-on-an-explorer-node"></a>Modifica del nome visualizzato in un nodo di Esplora risorse
 È possibile modificare la modalità di visualizzazione dei nomi degli elementi del modello in Esplora risorse. La procedura seguente illustra come visualizzare il nome **dell'attività** a cui fa riferimento un **commento** nel nodo commento.

#### <a name="to-display-a-property"></a>Per visualizzare una proprietà

1. Aprire la soluzione creata nella procedura precedente.

2. Assicurarsi che comment **faccia** riferimento solo a una singola classe di dominio impostando la molteplicità del ruolo con il nome di proprietà **Subjects** su 0..1. Il nome della proprietà deve diventare **Subject** e il nome della relazione deve diventare **CommentReferencesSubject.**

3. In **Esplora DSL fare** clic con il pulsante destro **del mouse** su Comportamento esplora risorse e quindi scegliere Aggiungi nuovo nodo esplora **Impostazioni**.

     Viene **visualizzato un nodo ExplorerNodeSettings** sotto il nodo Nodo personalizzato **Impostazioni** nodo.

4. Selezionare **ExplorerNodeSettings** e quindi nella **finestra Proprietà** impostare **Classe** su **Commento**.

5. Fare clic con il pulsante destro **del mouse** sul nodo Commento e quindi scegliere Aggiungi nuovo **percorso proprietà**.

     Verrà visualizzato un nuovo nodo denominato **Proprietà visualizzata**.

6. Selezionare **Proprietà visualizzata** e quindi nella finestra **Proprietà** fare clic sul campo valore percorso **proprietà**. Selezionare **Commento**, quindi **CommentReferencesSubject**, quindi **FlowElement**. Il percorso risultante dovrebbe essere simile **a CommentReferencesSubject.Subject/! Oggetto**.

7. Nel campo valore di **Proprietà** selezionare **Nome**.

8. Trasformare tutti i modelli e quindi compilare ed eseguire la soluzione.

9. Nella finestra di progettazione generata aprire il diagramma di esempio.

10. Disegnare un **connettore commento** tra l'elemento comment e **l'elemento Task1** nel diagramma.

     Il nodo Explorer dovrebbe visualizzare il commento **come Task1.**

## <a name="hiding-nodes"></a>Nascondere i nodi
 È possibile nascondere un nodo in Esplora risorse aggiungendone il percorso al **nodo Nodi** nascosti di **Esplora DSL.** La procedura seguente illustra come nascondere i **nodi** Comment.

#### <a name="to-hide-an-explorer-node"></a>Per nascondere un nodo di esplorazione

1. Aprire la soluzione creata nella procedura precedente.

2. In **Esplora DSL fare** clic con il pulsante destro del mouse su **Comportamento esplora** risorse e quindi scegliere Aggiungi nuovo percorso **dominio**.

     In **Nodi nascosti viene** visualizzato un nodo Percorso di **dominio**.

3. Selezionare **Percorso dominio** e quindi nella finestra **Proprietà** fare clic sul campo valore di Definizione **percorso**. Selezionare **FlowGraph** e **quindi FlowGraphHasComments.** Il percorso risultante dovrebbe essere simile **a FlowGraphHasComments.Comments**

4. Trasformare tutti i modelli e quindi compilare ed eseguire la soluzione.

5. Nella finestra di progettazione generata aprire il diagramma di esempio.

     Lo explorer dovrebbe visualizzare solo un **nodo Actors** e non il **nodo Comments.**

## <a name="see-also"></a>Vedi anche

- [Glossario di Strumenti Domain-Specific Language](/previous-versions/bb126564(v=vs.100))